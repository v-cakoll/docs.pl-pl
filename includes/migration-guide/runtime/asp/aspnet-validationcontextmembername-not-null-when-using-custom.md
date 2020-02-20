---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466020"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext. MemberName nie ma wartości NULL w przypadku używania niestandardowych elementów DataAnnotation. ValidationAttribute

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7.2 i starszych wersjach przy użyciu <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>niestandardowych Właściwość <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> zwraca `null`. W wersji .NET Framework 4,8 wcześniejszej niż aktualizacja 2019 października zwróci nazwę elementu członkowskiego. Począwszy od [.NET Framework października 2019 wersji zapoznawczej jakości](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) dla .NET Framework 4,8, domyślnie zwróci `null`, ale można zrezygnować z zwracania nazwy elementu członkowskiego. |
|Sugestia|Dodaj następujące ustawienie do pliku *Web. config* , aby Właściwość zwracała nazwę elementu członkowskiego w [.NET Framework października 2019 Preview zestawienia jakości](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) dla .NET Framework 4,8 i nowszych wersji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>W wersji .NET Framework 4,8 wcześniejszej niż aktualizacja 2019 października Dodawanie tego do pliku *Web. config* przywraca poprzednie zachowanie, a właściwość zwraca `null`.|
|Zakres|Nieznane|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
