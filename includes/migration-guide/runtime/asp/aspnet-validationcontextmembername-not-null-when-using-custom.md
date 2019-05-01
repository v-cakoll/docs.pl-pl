---
ms.openlocfilehash: 86cb328052c7a643cbd6080d222348d40179fdad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764460"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName nie ma wartości NULL w przypadku korzystania z niestandardowych DataAnnotations.ValidationAttribute

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.2 i wcześniejszych wersjach, korzystając z niestandardowego <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> właściwość zwraca <code>null</code>.  W .NET Framework 4,8 zwraca nazwę elementu członkowskiego.|
|Sugestia|Domyślne zachowanie <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> właściwości pozostają takie same.  Aby pobrać prawidłową wartość z <code>ValidationContext.MemberName</code> właściwości, Dodaj następujące ustawienie do pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Nieznany|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
