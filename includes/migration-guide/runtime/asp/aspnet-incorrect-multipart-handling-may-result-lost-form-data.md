---
ms.openlocfilehash: 135d59de135c8416d384b221379f912c8a9172ad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622069"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="75173-101">Niewłaściwa obsługa wieloczęściowej ASP.NET może spowodować utratę danych formularza.</span><span class="sxs-lookup"><span data-stu-id="75173-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="75173-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="75173-102">Details</span></span>

<span data-ttu-id="75173-103">W aplikacjach, które są przeznaczone .NET Framework 4.7.2 i starszych wersji, ASP.Net może niepoprawnie analizować wieloczęściowe wartości graniczne, dzięki czemu dane formularza są niedostępne podczas wykonywania żądania.</span><span class="sxs-lookup"><span data-stu-id="75173-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.Net might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="75173-104">Aplikacje przeznaczone dla .NET Framework 4,8 lub nowszych wersji poprawnie analizują wieloczęściowe dane, dlatego wartości formularza są dostępne podczas wykonywania żądania.</span><span class="sxs-lookup"><span data-stu-id="75173-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="75173-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="75173-105">Suggestion</span></span>

<span data-ttu-id="75173-106">Począwszy od aplikacji uruchomionych na .NET Framework 4,8, gdy element docelowy .NET Framework 4,8 lub nowszy przy użyciu <code>targetFrameworkVersion</code> elementu, domyślne zachowanie zostanie zmienione na ograniczniki paska.</span><span class="sxs-lookup"><span data-stu-id="75173-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="75173-107">Po przeznaczeniu do poprzednich wersji struktury lub nie używania <code>targetFrameworkVersion</code> , końcowe ograniczniki dla niektórych wartości są nadal zwracane. Takie zachowanie może być również jawnie kontrolowane za pomocą <code>appSetting</code> :</span><span class="sxs-lookup"><span data-stu-id="75173-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="75173-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="75173-108">Name</span></span>    | <span data-ttu-id="75173-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="75173-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="75173-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="75173-110">Scope</span></span>   |<span data-ttu-id="75173-111">Nieznane</span><span class="sxs-lookup"><span data-stu-id="75173-111">Unknown</span></span>|
|<span data-ttu-id="75173-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="75173-112">Version</span></span>|<span data-ttu-id="75173-113">4,8</span><span class="sxs-lookup"><span data-stu-id="75173-113">4.8</span></span>|
|<span data-ttu-id="75173-114">Typ</span><span class="sxs-lookup"><span data-stu-id="75173-114">Type</span></span>|<span data-ttu-id="75173-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="75173-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="75173-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="75173-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
