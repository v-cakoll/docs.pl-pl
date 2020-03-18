---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394478"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="61d5c-101">Umowy OSP: SpaServices i NodeServices oznaczone jako przestarzałe</span><span class="sxs-lookup"><span data-stu-id="61d5c-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="61d5c-102">Zawartość następujących pakietów NuGet wszystkie były niepotrzebne od ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="61d5c-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="61d5c-103">W związku z tym następujące pakiety są oznaczone jako przestarzałe:</span><span class="sxs-lookup"><span data-stu-id="61d5c-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="61d5c-104">Usługi Microsoft.AspNetCore.SpaServices</span><span class="sxs-lookup"><span data-stu-id="61d5c-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="61d5c-105">Usługi Microsoft.AspNetCore.NodeServices</span><span class="sxs-lookup"><span data-stu-id="61d5c-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="61d5c-106">Z tego samego powodu następujące moduły npm są oznaczane jako przestarzałe:</span><span class="sxs-lookup"><span data-stu-id="61d5c-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="61d5c-107">kątowy aspnet</span><span class="sxs-lookup"><span data-stu-id="61d5c-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="61d5c-108">aspnet-prerendering</span><span class="sxs-lookup"><span data-stu-id="61d5c-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="61d5c-109">aspnet-webpack</span><span class="sxs-lookup"><span data-stu-id="61d5c-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="61d5c-110">aspnet-webpack-react</span><span class="sxs-lookup"><span data-stu-id="61d5c-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="61d5c-111">zadanie domeny</span><span class="sxs-lookup"><span data-stu-id="61d5c-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="61d5c-112">Poprzednie pakiety i moduły npm zostaną później usunięte w .NET 5.</span><span class="sxs-lookup"><span data-stu-id="61d5c-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="61d5c-113">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="61d5c-113">Version introduced</span></span>

<span data-ttu-id="61d5c-114">3.0</span><span class="sxs-lookup"><span data-stu-id="61d5c-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="61d5c-115">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="61d5c-115">Old behavior</span></span>

<span data-ttu-id="61d5c-116">Przestarzałe pakiety i moduły npm miały na celu integrację ASP.NET Core z różnymi platformami aplikacji jednostronicowych (SPA).</span><span class="sxs-lookup"><span data-stu-id="61d5c-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="61d5c-117">Takie ramy obejmują Angular, React i React with Redux.</span><span class="sxs-lookup"><span data-stu-id="61d5c-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="61d5c-118">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="61d5c-118">New behavior</span></span>

<span data-ttu-id="61d5c-119">W pakiecie [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet istnieje nowy mechanizm integracji.</span><span class="sxs-lookup"><span data-stu-id="61d5c-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="61d5c-120">Pakiet pozostaje podstawą szablonów projektów Angular i React od czasu ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="61d5c-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="61d5c-121">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="61d5c-121">Reason for change</span></span>

<span data-ttu-id="61d5c-122">ASP.NET Core obsługuje integrację z różnymi platformami aplikacji jednostronicowych (SPA), w tym Angular, React i React with Redux.</span><span class="sxs-lookup"><span data-stu-id="61d5c-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="61d5c-123">Początkowo integracja z tymi strukturami została dokonana za pomocą ASP.NET składników specyficznych dla rdzenia, które obsługiwały scenariusze, takie jak wstępne renderowanie po stronie serwera i integracja z pakietem Webpack.</span><span class="sxs-lookup"><span data-stu-id="61d5c-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="61d5c-124">W miarę upływu czasu zmieniały się standardy branżowe.</span><span class="sxs-lookup"><span data-stu-id="61d5c-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="61d5c-125">Każda z platform SPA wydała własne standardowe interfejsy wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61d5c-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="61d5c-126">Na przykład kątowe CLI i tworzenie-react-app.</span><span class="sxs-lookup"><span data-stu-id="61d5c-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="61d5c-127">Kiedy w maju 2018 roku ASP.NET Core 2.1, zespół zareagował na zmianę standardów.</span><span class="sxs-lookup"><span data-stu-id="61d5c-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="61d5c-128">Zapewniono nowszy i prostszy sposób integracji z własnymi łańcuchami narzędzi SPA.</span><span class="sxs-lookup"><span data-stu-id="61d5c-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="61d5c-129">Nowy mechanizm integracji istnieje `Microsoft.AspNetCore.SpaServices.Extensions` w pakiecie i pozostaje podstawą szablonów projektu Angular i React od ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="61d5c-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="61d5c-130">Aby wyjaśnić, że starsze ASP.NET składniki specyficzne dla rdzenia nie mają znaczenia i nie są zalecane:</span><span class="sxs-lookup"><span data-stu-id="61d5c-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="61d5c-131">Mechanizm integracji pre-2.1 jest oznaczony jako przestarzały.</span><span class="sxs-lookup"><span data-stu-id="61d5c-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="61d5c-132">Pakiety npm pomocnicze są oznaczone jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="61d5c-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="61d5c-133">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="61d5c-133">Recommended action</span></span>

<span data-ttu-id="61d5c-134">Jeśli używasz tych pakietów, zaktualizuj aplikacje, aby korzystać z tych funkcji:</span><span class="sxs-lookup"><span data-stu-id="61d5c-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="61d5c-135">W `Microsoft.AspNetCore.SpaServices.Extensions` opakowaniu.</span><span class="sxs-lookup"><span data-stu-id="61d5c-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="61d5c-136">Dostarczane przez struktury SPA, których używasz</span><span class="sxs-lookup"><span data-stu-id="61d5c-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="61d5c-137">Aby włączyć funkcje, takie jak wstępne renderowanie po stronie serwera i ponowne ładowanie modułu, zapoznaj się z dokumentacją odpowiedniej struktury SPA.</span><span class="sxs-lookup"><span data-stu-id="61d5c-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="61d5c-138">Funkcja w `Microsoft.AspNetCore.SpaServices.Extensions` *nie* jest przestarzała i będzie nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="61d5c-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="61d5c-139">Kategoria</span><span class="sxs-lookup"><span data-stu-id="61d5c-139">Category</span></span>

<span data-ttu-id="61d5c-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="61d5c-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="61d5c-141">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="61d5c-141">Affected APIs</span></span>

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
