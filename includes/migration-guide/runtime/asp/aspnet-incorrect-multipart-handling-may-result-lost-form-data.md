---
ms.openlocfilehash: 135d59de135c8416d384b221379f912c8a9172ad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622069"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>Niewłaściwa obsługa wieloczęściowej ASP.NET może spowodować utratę danych formularza.

#### <a name="details"></a>Szczegóły

W aplikacjach, które są przeznaczone .NET Framework 4.7.2 i starszych wersji, ASP.Net może niepoprawnie analizować wieloczęściowe wartości graniczne, dzięki czemu dane formularza są niedostępne podczas wykonywania żądania. Aplikacje przeznaczone dla .NET Framework 4,8 lub nowszych wersji poprawnie analizują wieloczęściowe dane, dlatego wartości formularza są dostępne podczas wykonywania żądania.

#### <a name="suggestion"></a>Sugestia

Począwszy od aplikacji uruchomionych na .NET Framework 4,8, gdy element docelowy .NET Framework 4,8 lub nowszy przy użyciu <code>targetFrameworkVersion</code> elementu, domyślne zachowanie zostanie zmienione na ograniczniki paska. Po przeznaczeniu do poprzednich wersji struktury lub nie używania <code>targetFrameworkVersion</code> , końcowe ograniczniki dla niektórych wartości są nadal zwracane. Takie zachowanie może być również jawnie kontrolowane za pomocą <code>appSetting</code> :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Nieznane|
|Wersja|4,8|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
