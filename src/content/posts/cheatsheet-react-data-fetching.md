---
title: 'Cheatsheet React Data Fetching'
published: 2025-10-22
draft: false
tags: ['react', 'data-fetching', 'cheatsheet']
description: 'Summary of common data fetching techniques in React applications.'
---

## 1. Fetching Data with useEffect()

```jsx
import React, { useState, useEffect } from 'react';

function DataFetchingComponent() {
  const [data, setData] = useState(null);
  const [isLoading, setIsLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then((response) => response.json())
      .then((data) => setData(data))
      .catch((error) => setError(error))
      .finally(() => setIsLoading(false));
  }, []);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error fetching data</div>;

  return <div>{JSON.stringify(data)}</div>;
}
```

## 2. Fetching Data with Tanstack Query

```jsx
import React from 'react';
import { useQuery } from '@tanstack/react-query';

function DataFetchingComponent() {
  const { data, error, isLoading } = useQuery(['data'], () =>
    fetch('https://api.example.com/data').then((res) => res.json())
  );

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error fetching data</div>;

  return <div>{JSON.stringify(data)}</div>;
}
```

## 3. Fetching Data with SWR

```jsx
import React from 'react';
import useSWR from 'swr';

const fetcher = (url) => fetch(url).then((res) => res.json());

function DataFetchingComponent() {
  const { data, error } = useSWR('https://api.example.com/data', fetcher);

  if (!data) return <div>Loading...</div>;
  if (error) return <div>Error fetching data</div>;

  return <div>{JSON.stringify(data)}</div>;
}
```

## 4. Fetching Data with SSR (Next.js Example)

```jsx
async function fetchUsers() {
  const response = await fetch('https://api.example.com/users');
  return response.json();
}

export default async function Page() {
  const users = await fetchUsers();

  return (
    <div>
      <ul>
        {users.map((user) => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

## 5. Fetching Data with use()

```jsx
// app.js (server component)
import React from 'react';

async function fetchUsers() {
  const response = await fetch('https://api.example.com/users');
  return response.json();
}

export default function App() {
  const usersPromise = fetchUsers();

  return (
    <ErrorBoundary fallback={<div>Error loading users</div>}>
      <Suspense fallback={<div>Loading users...</div>}>
        <Users usersPromise={usersPromise} />
      </Suspense>
    </ErrorBoundary>
  )
}

// Users.js (client component)
'use client';
import React, { use } from 'react';

export default function Users({ usersPromise }) {

  /**
   * As of today (Oct 2025), passing an uncached promise to `use()` will cause
   * infinite rerenders in React -> infinite network requests.
   * 
   * Therefore, we pass the promise from the server component because
   * it is already "cached" by React's server rendering.
   */
  const users = use(usersPromise);

  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```
