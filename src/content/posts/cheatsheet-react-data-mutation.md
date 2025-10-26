---
title: 'Cheatsheet React Data Mutation'
published: 2025-10-26
draft: false
tags: ['react', 'data-mutation', 'cheatsheet']
description: 'Summary of common data mutation techniques in React applications.'
---

## 1. Mutating Data with useState() and fetch()

```jsx
import React, { useState } from 'react';

function DataMutationComponent() {
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState(null);
  const [data, setData] = useState(null);

  const createUser = async (userData) => {
    setIsLoading(true);
    setError(null);

    try {
      const response = await fetch('https://api.example.com/users', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(userData),
      });

      if (!response.ok) {
        throw new Error('Failed to create user');
      }

      const result = await response.json();
      setData(result);
    } catch (err) {
      setError(err.message);
    } finally {
      setIsLoading(false);
    }
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    createUser({ name: 'John Doe', email: 'john@example.com' });
  };

  return (
    <div>
      <button onClick={handleSubmit} disabled={isLoading}>
        {isLoading ? 'Creating...' : 'Create User'}
      </button>
      {error && <div>Error: {error}</div>}
      {data && <div>Success: {JSON.stringify(data)}</div>}
    </div>
  );
}
```

## 2. Mutating Data with Tanstack Query

```jsx
import React from 'react';
import { useMutation, useQueryClient } from '@tanstack/react-query';

function DataMutationComponent() {
  const queryClient = useQueryClient();

  const mutation = useMutation({
    mutationFn: (userData) => {
      return fetch('https://api.example.com/users', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(userData),
      }).then((res) => res.json());
    },
    onSuccess: () => {
      // Invalidate and refetch
      queryClient.invalidateQueries({ queryKey: ['users'] });
    },
  });

  const handleSubmit = (e) => {
    e.preventDefault();
    mutation.mutate({ name: 'John Doe', email: 'john@example.com' });
  };

  return (
    <div>
      <button onClick={handleSubmit} disabled={mutation.isPending}>
        {mutation.isPending ? 'Creating...' : 'Create User'}
      </button>
      {mutation.isError && <div>Error: {mutation.error.message}</div>}
      {mutation.isSuccess && <div>User created successfully!</div>}
    </div>
  );
}
```

## 3. Mutating Data with SWR

```jsx
import React from 'react';
import useSWR, { useSWRConfig } from 'swr';

const fetcher = (url) => fetch(url).then((res) => res.json());

function DataMutationComponent() {
  const { mutate } = useSWRConfig();
  const { data: users } = useSWR('https://api.example.com/users', fetcher);

  const createUser = async (userData) => {
    // Optimistic update
    const newUser = { id: Date.now(), ...userData };
    mutate(
      'https://api.example.com/users',
      [...(users || []), newUser],
      false
    );

    try {
      const response = await fetch('https://api.example.com/users', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(userData),
      });

      const result = await response.json();

      // Revalidate
      mutate('https://api.example.com/users');

      return result;
    } catch (error) {
      // Rollback on error
      mutate('https://api.example.com/users');
      throw error;
    }
  };

  const handleSubmit = async (e) => {
    e.preventDefault();
    await createUser({ name: 'John Doe', email: 'john@example.com' });
  };

  return (
    <div>
      <button onClick={handleSubmit}>Create User</button>
    </div>
  );
}
```

## 4. Mutating Data with Server Actions (Next.js)

```jsx
// app/actions.js
'use server';

import { revalidatePath } from 'next/cache';

export async function createUser(formData) {
  const userData = {
    name: formData.get('name'),
    email: formData.get('email'),
  };

  const response = await fetch('https://api.example.com/users', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(userData),
  });

  if (!response.ok) {
    throw new Error('Failed to create user');
  }

  const result = await response.json();

  // Revalidate the page to show updated data
  revalidatePath('/users');

  return result;
}

// app/components/CreateUserForm.js
'use client';

import { useFormStatus } from 'react-dom';
import { createUser } from '../actions';

function SubmitButton() {
  const { pending } = useFormStatus();

  return (
    <button type="submit" disabled={pending}>
      {pending ? 'Creating...' : 'Create User'}
    </button>
  );
}

export default function CreateUserForm() {
  return (
    <form action={createUser}>
      <input type="text" name="name" placeholder="Name" required />
      <input type="email" name="email" placeholder="Email" required />
      <SubmitButton />
    </form>
  );
}
```

## 5. Mutating Data with useOptimistic()

```jsx
'use client';

import React, { useOptimistic } from 'react';
import { createUser } from './actions';

export default function UserList({ users }) {
  const [optimisticUsers, addOptimisticUser] = useOptimistic(
    users,
    (state, newUser) => [...state, newUser]
  );

  const handleSubmit = async (formData) => {
    const newUser = {
      id: crypto.randomUUID(),
      name: formData.get('name'),
      email: formData.get('email'),
    };

    // Add optimistically
    addOptimisticUser(newUser);

    // Perform actual mutation
    await createUser(formData);
  };

  return (
    <div>
      <form action={handleSubmit}>
        <input type="text" name="name" placeholder="Name" required />
        <input type="email" name="email" placeholder="Email" required />
        <button type="submit">Create User</button>
      </form>

      <ul>
        {optimisticUsers.map((user) => (
          <li key={user.id}>
            {user.name} - {user.email}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

## 6. Mutating Data with useTransition()

```jsx
'use client';

import React, { useState, useTransition } from 'react';

export default function DataMutationComponent() {
  const [isPending, startTransition] = useTransition();
  const [users, setUsers] = useState([]);
  const [error, setError] = useState(null);

  const createUser = async (userData) => {
    const response = await fetch('https://api.example.com/users', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(userData),
    });

    if (!response.ok) {
      throw new Error('Failed to create user');
    }

    return response.json();
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    const formData = new FormData(e.target);
    const userData = {
      name: formData.get('name'),
      email: formData.get('email'),
    };

    startTransition(async () => {
      try {
        const newUser = await createUser(userData);
        setUsers((prev) => [...prev, newUser]);
        setError(null);
      } catch (err) {
        setError(err.message);
      }
    });
  };

  return (
    <div>
      <form onSubmit={handleSubmit}>
        <input type="text" name="name" placeholder="Name" required />
        <input type="email" name="email" placeholder="Email" required />
        <button type="submit" disabled={isPending}>
          {isPending ? 'Creating...' : 'Create User'}
        </button>
      </form>
      {error && <div>Error: {error}</div>}
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            {user.name} - {user.email}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

## 7. Mutating Data with useActionState()

```jsx
'use client';

import React, { useActionState } from 'react';

async function createUserAction(previousState, formData) {
  const userData = {
    name: formData.get('name'),
    email: formData.get('email'),
  };

  try {
    const response = await fetch('https://api.example.com/users', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(userData),
    });

    if (!response.ok) {
      throw new Error('Failed to create user');
    }

    const newUser = await response.json();

    return {
      success: true,
      message: 'User created successfully!',
      user: newUser,
      error: null,
    };
  } catch (error) {
    return {
      success: false,
      message: null,
      user: null,
      error: error.message,
    };
  }
}

export default function DataMutationComponent() {
  const [state, formAction, isPending] = useActionState(createUserAction, {
    success: false,
    message: null,
    user: null,
    error: null,
  });

  return (
    <div>
      <form action={formAction}>
        <input type="text" name="name" placeholder="Name" required />
        <input type="email" name="email" placeholder="Email" required />
        <button type="submit" disabled={isPending}>
          {isPending ? 'Creating...' : 'Create User'}
        </button>
      </form>

      {state.error && <div>Error: {state.error}</div>}
      {state.success && (
        <div>
          {state.message}
          <pre>{JSON.stringify(state.user, null, 2)}</pre>
        </div>
      )}
    </div>
  );
}
```