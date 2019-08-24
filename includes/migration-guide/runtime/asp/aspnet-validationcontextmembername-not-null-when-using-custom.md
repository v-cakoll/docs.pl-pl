---
ms.openlocfilehash: 3b94c88809513e31a5f226bcfce39abbfa4de378
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017375"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext. MemberName nie ma wartości NULL w przypadku używania niestandardowych elementów DataAnnotation. ValidationAttribute

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7.2 i starszych wersjach, w przypadku użycia niestandardowej <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> Właściwość zwraca <code>null</code>.  W .NET Framework 4,8 zwraca nazwę elementu członkowskiego.|
|Sugestia|Aby przywrócić poprzednie zachowanie, Dodaj następujące ustawienie do pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Takie zachowanie zostanie zmienione w nadchodzącej wersji usługi, gdy będzie konieczne jawne wprowadzenie do nowego zachowania. Właściwość zwróci wartość `ValidationAttribute` różną od null, `aspnet:GetValidationMemberName` Jeśli przełącznik jest ustawiony na `true`.|
|Scope|Nieznany|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
