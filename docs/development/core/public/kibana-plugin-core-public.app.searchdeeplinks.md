<!-- Do not edit this file. It is automatically generated by API Documenter. -->

[Home](./index.md) &gt; [kibana-plugin-core-public](./kibana-plugin-core-public.md) &gt; [App](./kibana-plugin-core-public.app.md) &gt; [searchDeepLinks](./kibana-plugin-core-public.app.searchdeeplinks.md)

## App.searchDeepLinks property

Array of links that represent secondary in-app locations for the app.

<b>Signature:</b>

```typescript
searchDeepLinks?: AppSearchDeepLink[];
```

## Remarks

Used to populate navigational search results (where available). Can be updated using the [App.updater$](./kibana-plugin-core-public.app.updater_.md) observable. See  for more details.

## Example

The `path` property on deep links should not include the application's `appRoute`<!-- -->:

```ts
core.application.register({
  id: 'my_app',
  title: 'My App',
  searchDeepLinks: [
    { id: 'sub1', title: 'Sub1', path: '/sub1' },
    {
      id: 'sub2',
      title: 'Sub2',
      searchDeepLinks: [
        { id: 'subsub', title: 'SubSub', path: '/sub2/sub' }
      ]
    }
  ],
  mount: () => { ... },
})

```
Will produce deep links on these paths: - `/app/my_app/sub1` - `/app/my_app/sub2/sub`

