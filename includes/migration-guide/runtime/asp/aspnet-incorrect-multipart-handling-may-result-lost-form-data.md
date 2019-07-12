---
ms.openlocfilehash: 6a99ed916e4e86e85d7ebc2d6ea36a6372c00206
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802641"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>Nieprawidłowa obsługa wieloczęściowego ASP.NET może spowodować formularza utraty danych.

|   |   |
|---|---|
|Szczegóły|W aplikacjach przeznaczonych dla platformy .NET Framework 4.7.2 i wcześniejszych wersji programu ASP.Net może niepoprawnie przeanalizować wartości graniczne wieloczęściowej wiadomości, skutkuje dane formularza jest niedostępny podczas wykonywania żądania. Aplikacji przeznaczonych dla platformy .NET Framework 4.8 lub nowsze wersje poprawnie przeanalizować wieloczęściowych danych, dzięki czemu wartości formularza są dostępne podczas wykonywania żądania.|
|Sugestia|Począwszy od działających na .NET Framework 4,8, gdy przeznaczonych dla platformy .NET Framework 4.8 lub później za pomocą <code>targetFrameworkVersion</code> element, zmiany zachowania domyślnego oddzielić ograniczników. Gdy przeznaczonych dla poprzednich wersji framework lub nie używa <code>targetFrameworkVersion</code>, końcowe znaki rozdzielające dla niektórych wartości nadal są zwracane. To zachowanie można także jawnie kontrolowane za pomocą <code>appSetting</code>:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Nieznany|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

