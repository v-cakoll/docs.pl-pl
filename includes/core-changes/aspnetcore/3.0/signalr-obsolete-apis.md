---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394062"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a>Sygnalizujący: metody UseSignalR i UseConnections oznaczone jako przestarzałe

Metody `UseConnections` i `UseSignalR` oraz klasy `ConnectionsRouteBuilder` i `HubRouteBuilder` są oznaczane jako przestarzałe w ASP.NET Core 3,0.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Routing centrum sygnałów został skonfigurowany przy użyciu `UseSignalR` lub `UseConnections`.

#### <a name="new-behavior"></a>Nowe zachowanie

Stary sposób konfigurowania routingu został przestarzały i zastąpiony przez Routing punktów końcowych.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Oprogramowanie pośredniczące jest przenoszone do nowego systemu routingu punktu końcowego. Stary sposób dodawania oprogramowania pośredniczącego jest przestarzały.

#### <a name="recommended-action"></a>Zalecana akcja

Zastąp `UseSignalR` z `UseEndpoints`:

**Stary kod:**

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

**Nowy kod:**

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->
