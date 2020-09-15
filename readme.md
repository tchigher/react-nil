[![Build Size](https://img.shields.io/bundlephobia/min/react-nil?label=bunlde%20size&style=flat&colorA=000000&colorB=000000)](https://bundlephobia.com/result?p=react-nil)
[![Build Status](https://img.shields.io/travis/react-spring/react-nil/master?style=flat&colorA=000000&colorB=000000)](https://travis-ci.org/react-spring/react-nil)
[![Version](https://img.shields.io/npm/v/react-nil?style=flat&colorA=000000&colorB=000000)](https://www.npmjs.com/package/react-nil)
[![Downloads](https://img.shields.io/npm/dt/react-nil.svg?style=flat&colorA=000000&colorB=000000)](https://www.npmjs.com/package/react-nil)

This is a custom react renderer that renders `null`, literally. It has no native elements. That sounds crazy to you? Well, it still executes logical React components, which now opens the flood gates to many things that would otherwise be very hard to implement. How hard is managing async side effects in Node? In React you can mark and pack away effects into useEffect, you can memoize via useMemo, there is Suspense to orchestrate async requests, context to communicate data. And of course — the entire React eco system is now at your finger tips: Redux, Recoil, GraphQl, whatever you need.

```bash
npm install react-nil
```

```jsx
import { render } from "react-nil"

function Foo() {
  const [active, set] = useState(false)
  useEffect(() => void setInterval(() => set((a) => !a), 1000), [])
  console.log(active)

  // This is a logical component without a view, it renders nothing,
  // but it has a real lifecycle and is managed by React regardless.
  return null
}

render(<Foo />)
```