---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77466020"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName nie jest null podczas korzystania z niestandardowych DataAnnotations.ValidationAttribute

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7.2 i wcześniejszych <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>wersjach, podczas korzystania z niestandardowego , <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> właściwość zwraca `null`. W wersji .NET Framework 4.8 przed aktualizacją z października 2019 r. zwraca nazwę elementu członkowskiego. Począwszy od [programu .NET Framework październik 2019 Podgląd zestawienia jakości](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) dla `null` platformy .NET Framework 4.8, zwraca domyślnie, ale zamiast tego można zdecydować się na zwrócenie nazwy elementu członkowskiego. |
|Sugestia|Dodaj następujące ustawienie do pliku *web.config* dla właściwości, aby zwrócić nazwę elementu członkowskiego w [systemie .NET Framework październik 2019 Podgląd zestawienia jakości](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) dla platformy .NET Framework 4.8 i nowszych wersji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>W wersji .NET Framework 4.8 przed aktualizacją z października 2019 r. dodanie tego do `null`pliku *web.config* przywraca poprzednie zachowanie, a właściwość zwraca .|
|Zakres|Nieznane|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
