---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394478"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>Umowy OSP: SpaServices i NodeServices oznaczone jako przestarzałe

Zawartość następujących pakietów NuGet wszystkie były niepotrzebne od ASP.NET Core 2.1. W związku z tym następujące pakiety są oznaczone jako przestarzałe:

- [Usługi Microsoft.AspNetCore.SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Usługi Microsoft.AspNetCore.NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Z tego samego powodu następujące moduły npm są oznaczane jako przestarzałe:

- [kątowy aspnet](https://www.npmjs.com/package/aspnet-angular)
- [aspnet-prerendering](https://www.npmjs.com/package/aspnet-prerendering)
- [aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack)
- [aspnet-webpack-react](https://www.npmjs.com/package/aspnet-webpack-react)
- [zadanie domeny](https://www.npmjs.com/package/domain-task)

Poprzednie pakiety i moduły npm zostaną później usunięte w .NET 5.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Przestarzałe pakiety i moduły npm miały na celu integrację ASP.NET Core z różnymi platformami aplikacji jednostronicowych (SPA). Takie ramy obejmują Angular, React i React with Redux.

#### <a name="new-behavior"></a>Nowe zachowanie

W pakiecie [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet istnieje nowy mechanizm integracji. Pakiet pozostaje podstawą szablonów projektów Angular i React od czasu ASP.NET Core 2.1.

#### <a name="reason-for-change"></a>Przyczyna zmiany

ASP.NET Core obsługuje integrację z różnymi platformami aplikacji jednostronicowych (SPA), w tym Angular, React i React with Redux. Początkowo integracja z tymi strukturami została dokonana za pomocą ASP.NET składników specyficznych dla rdzenia, które obsługiwały scenariusze, takie jak wstępne renderowanie po stronie serwera i integracja z pakietem Webpack. W miarę upływu czasu zmieniały się standardy branżowe. Każda z platform SPA wydała własne standardowe interfejsy wiersza polecenia. Na przykład kątowe CLI i tworzenie-react-app.

Kiedy w maju 2018 roku ASP.NET Core 2.1, zespół zareagował na zmianę standardów. Zapewniono nowszy i prostszy sposób integracji z własnymi łańcuchami narzędzi SPA. Nowy mechanizm integracji istnieje `Microsoft.AspNetCore.SpaServices.Extensions` w pakiecie i pozostaje podstawą szablonów projektu Angular i React od ASP.NET Core 2.1.

Aby wyjaśnić, że starsze ASP.NET składniki specyficzne dla rdzenia nie mają znaczenia i nie są zalecane:

- Mechanizm integracji pre-2.1 jest oznaczony jako przestarzały.
- Pakiety npm pomocnicze są oznaczone jako przestarzałe.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli używasz tych pakietów, zaktualizuj aplikacje, aby korzystać z tych funkcji:

- W `Microsoft.AspNetCore.SpaServices.Extensions` opakowaniu.
- Dostarczane przez struktury SPA, których używasz

Aby włączyć funkcje, takie jak wstępne renderowanie po stronie serwera i ponowne ładowanie modułu, zapoznaj się z dokumentacją odpowiedniej struktury SPA. Funkcja w `Microsoft.AspNetCore.SpaServices.Extensions` *nie* jest przestarzała i będzie nadal obsługiwana.

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
