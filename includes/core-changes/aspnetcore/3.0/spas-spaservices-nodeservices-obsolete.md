---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394478"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>Aplikacji jednostronicowych: SpaServices i NodeServices oznaczone jako przestarzałe

Zawartość następujących pakietów NuGet była niepotrzebna, ponieważ ASP.NET Core 2,1. W związku z tym następujące pakiety są oznaczane jako przestarzałe:

- [Microsoft. AspNetCore. SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Microsoft. AspNetCore. NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Z tego samego powodu następujące moduły npm są oznaczane jako przestarzałe:

- [ASPNET — kątowy](https://www.npmjs.com/package/aspnet-angular)
- [Renderowanie wstępne ASPNET](https://www.npmjs.com/package/aspnet-prerendering)
- [ASPNET — WebPack](https://www.npmjs.com/package/aspnet-webpack)
- [ASPNET-WebPack — reagowanie](https://www.npmjs.com/package/aspnet-webpack-react)
- [Domena — zadanie](https://www.npmjs.com/package/domain-task)

Poprzednie pakiety i moduły npm zostaną później usunięte w programie .NET 5.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Przestarzałe pakiety i moduły npm zostały zaprojektowane w celu zintegrowania ASP.NET Core z różnymi strukturami aplikacji jednostronicowych (SPA). Takie struktury obejmują kątowy, reagowanie i reagowanie na Redux.

#### <a name="new-behavior"></a>Nowe zachowanie

W pakiecie NuGet [Microsoft. AspNetCore. SpaServices. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) istnieje nowy mechanizm integracji. Pakiet pozostaje podstawą szablonów projektów kątowych i reaguje od ASP.NET Core 2,1.

#### <a name="reason-for-change"></a>Przyczyna zmiany

ASP.NET Core obsługuje integrację z różnymi strukturami aplikacji jednostronicowych (SPA), w tym między innymi z zakresu, reakcji i reagowania na Redux. Początkowo integracja z tymi platformami została zrealizowana przy użyciu składników specyficznych dla ASP.NET Core, które obsługują scenariusze takie jak wstępne renderowanie po stronie serwera i integrację z pakietem WebPack. Po przekroczeniu tego czasu normy branżowe uległy zmianie. Każdy z platform SPA wydał własne standardowe interfejsy wiersza polecenia. Na przykład kątowy interfejs wiersza polecenia i Utwórz-reaguje na aplikację.

Gdy ASP.NET Core 2,1 zostało wydane w maju 2018, zespół odpowiedział na zmiany w standardach. Podano nowszą i uproszczoną metodę integracji ze swoimi łańcuchy narzędziami. Nowy mechanizm integracji istnieje w pakiecie `Microsoft.AspNetCore.SpaServices.Extensions` i pozostaje podstawą szablonów projektów "skośne" i "reaguje" od ASP.NET Core 2,1.

Aby wyjaśnić, że starsze składniki specyficzne dla ASP.NET Core są nieistotne i nie są zalecane:

- Mechanizm integracji sprzed 2,1 został oznaczony jako przestarzały.
- Pomocnicze pakiety npm są oznaczone jako przestarzałe.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli używasz tych pakietów, zaktualizuj swoje aplikacje, aby korzystać z funkcji:

- W `Microsoft.AspNetCore.SpaServices.Extensions` pakiecie.
- Udostępnione przez używane platformy SPA

Aby włączyć funkcje takie jak wstępne renderowanie po stronie serwera i ponowne załadowanie modułu dynamicznego, zapoznaj się z dokumentacją odpowiedniej struktury SPA. Funkcje w programie `Microsoft.AspNetCore.SpaServices.Extensions` *nie* są przestarzałe i będą nadal obsługiwane.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
