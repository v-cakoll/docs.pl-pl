---
ms.openlocfilehash: e605e0f2636d83745815ec4ed27bf72692f18d15
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802701"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET poprawki obsługi InputAttributes i LabelAttributes dla formantu CheckBox formularzy WebForms

|   |   |
|---|---|
|Szczegóły|Dla aplikacji przeznaczonych dla środowiska .NET Framework 4.7.2 i wcześniejszymi wersjami <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> programowo dodawane do formularzy sieci Web <xref:System.Web.UI.WebControls.CheckBox> kontrolki są tracone po odświeżeniu strony. Dla aplikacji przeznaczonych dla platformy .NET Framework 4.8 lub nowszej wersji zostaną zachowane po odświeżeniu strony.|
|Sugestia|Poprawne zachowanie przywracania atrybutów na odświeżenie strony, można ustawić <code>targetFrameworkVersion</code> 4.8 lub wyższej. Na przykład:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ustawienie niższej lub wcale, zachowuje stary nieprawidłowe zachowanie.|
|Scope|Nieznany|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|

