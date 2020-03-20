---
ms.openlocfilehash: e6b0387d9d04aa979de289ea0c5caa6c76f4d1be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802641"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET Nieprawidłowa obsługa wieloczęściowa może spowodować utratę danych formularza.

|   |   |
|---|---|
|Szczegóły|W aplikacjach, które docelowe .NET Framework 4.7.2 i wcześniejszych wersjach ASP.Net może niepoprawnie przeanalizować wartości granic wieloczęściowych, w wyniku czego dane formularza są niedostępne podczas wykonywania żądania. Aplikacje przeznaczone dla platformy .NET Framework 4.8 lub nowszych poprawnie analizują dane wieloczęściowe, więc wartości formularza są dostępne podczas wykonywania żądania.|
|Sugestia|Począwszy od aplikacji uruchomionych w programie .NET Framework 4.8, gdy kierowanie <code>targetFrameworkVersion</code> .NET Framework 4.8 lub nowsze przy użyciu elementu, domyślne zachowanie zmienia się na ograniczniki paskowania. Podczas kierowania na poprzednie wersje <code>targetFrameworkVersion</code>struktury lub nie przy użyciu, końcowe ograniczniki dla niektórych wartości są nadal zwracane. To zachowanie może być również <code>appSetting</code>jawnie kontrolowane za pomocą:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Nieznane|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
