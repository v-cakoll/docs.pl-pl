---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441556"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a>Autoryzacja: zasób w routingu punktu końcowego jest obiektem HttpContext

W przypadku korzystania z routingu punktów końcowych w ASP.NET Core 3,1, zasób używany do autoryzacji jest punktem końcowym. Takie podejście było niewystarczające do uzyskania dostępu do danych trasy ( <xref:Microsoft.AspNetCore.Routing.RouteData> ). Wcześniej w MVC <xref:Microsoft.AspNetCore.Http.HttpContext> zasób został przekazano, co umożliwia dostęp do punktu końcowego ( <xref:Microsoft.AspNetCore.Http.Endpoint> ) i danych trasy. Ta zmiana gwarantuje, że zasób przeszedł do autoryzacji jest zawsze `HttpContext` .

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 7

#### <a name="old-behavior"></a>Stare zachowanie

W przypadku używania routingu punktów końcowych i atrybutów autoryzacji oprogramowania pośredniczącego ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) lub [[autoryzuje]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) zasób przeszedł do autoryzacji jest zgodnym punktem końcowym.

#### <a name="new-behavior"></a>Nowe zachowanie

Routing punktów końcowych przekazuje `HttpContext` do autoryzacji.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Możesz przejść do punktu końcowego z `HttpContext` . Nie ma jednak możliwości uzyskania od punktu końcowego do elementów, takich jak dane trasy. Nastąpiła utrata funkcjonalności z poziomu routingu spoza punktu końcowego.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli aplikacja korzysta z zasobu punktu końcowego, wywołaj polecenie, <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> `HttpContext` Aby kontynuować dostęp do punktu końcowego.

W ASP.NET Core 5,0 wersji zapoznawczej 8 i nowszych można przywrócić stare zachowanie przy użyciu programu <xref:System.AppContext.SetSwitch%2A> . Przykład:

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
