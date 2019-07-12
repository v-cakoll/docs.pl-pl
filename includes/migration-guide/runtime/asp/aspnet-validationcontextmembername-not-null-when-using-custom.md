---
ms.openlocfilehash: df13f6938ebaf8e96bb2825c1495044621f1c31b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802616"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName nie ma wartości NULL w przypadku korzystania z niestandardowych DataAnnotations.ValidationAttribute

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.7.2 i wcześniejszych wersjach, korzystając z niestandardowego <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> właściwość zwraca <code>null</code>.  W .NET Framework 4,8 zwraca nazwę elementu członkowskiego.|
|Sugestia|Domyślne zachowanie <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> właściwości pozostają takie same.  Aby pobrać prawidłową wartość z <code>ValidationContext.MemberName</code> właściwości, Dodaj następujące ustawienie do pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Nieznany|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|

