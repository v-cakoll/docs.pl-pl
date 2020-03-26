---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291637"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR: UseSignalR i UseConnections metody usunięte

W ASP.NET Core 3.0 SignalR przyjął routing punktu końcowego. W ramach tej <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>zmiany, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, i niektóre powiązane metody zostały oznaczone jako przestarzałe. W ASP.NET Core 5.0 te przestarzałe metody zostały usunięte. Aby uzyskać pełną listę metod, zobacz [interfejsy API, których dotyczy problem](#affected-apis).

Aby do dyskusji na ten temat, zobacz [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).

#### <a name="version-introduced"></a>Wprowadzono wersję

5.0 Wersja zapoznawcza 3

#### <a name="old-behavior"></a>Stare zachowanie

Koncentratory signalr i programy obsługi połączeń mogą być `UseSignalR` rejestrowane `UseConnections` w potoku oprogramowania pośredniczącego przy użyciu lub metod.

#### <a name="new-behavior"></a>Nowe zachowanie

Koncentratory SignalR i programy obsługi <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> połączeń <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> powinny <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> być <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>rejestrowane przy użyciu i metody rozszerzenia na .

#### <a name="reason-for-change"></a>Powód zmiany

Stare metody miały niestandardową logikę routingu, która nie wchodziła w interakcje z innymi składnikami routingu w ASP.NET Core. W ASP.NET Core 3.0 wprowadzono nowy system routingu ogólnego przeznaczenia, zwany routingiem punktów końcowych. Routing punktu końcowego umożliwił SignalR interakcję z innymi składnikami routingu. Przełączenie do tego modelu umożliwia użytkownikom realizację pełnych zalet routingu punktu końcowego. W związku z tym stare metody zostały usunięte.

#### <a name="recommended-action"></a>Zalecana akcja

Usuń kod, `UseSignalR` `UseConnections` który wywołuje lub `Startup.Configure` z metody projektu. Wymień go `MapHub` `MapConnectionHandler`na połączenia lub, odpowiednio, w `UseEndpoints`treści połączenia do . Przykład:

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

Ogólnie `MapHub` rzecz biorąc, poprzednie i `MapConnectionHandler` połączenia mogą być `UseSignalR` przesyłane bezpośrednio z ciała i `UseConnections` do `UseEndpoints` niej z małą lub żadną zmianą.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
