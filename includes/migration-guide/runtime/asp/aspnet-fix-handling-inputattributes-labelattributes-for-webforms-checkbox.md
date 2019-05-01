---
ms.openlocfilehash: ea0e1583cd611a624cf2d2edf9defb2294eb89d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665705"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET poprawki obsługi InputAttributes i LabelAttributes dla formantu CheckBox formularzy WebForms

|   |   |
|---|---|
|Szczegóły|Dla aplikacji przeznaczonych dla środowiska .NET Framework 4.7.2 i wcześniejszymi wersjami <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> programowo dodawane do formularzy sieci Web <xref:System.Web.UI.WebControls.CheckBox> kontrolki są tracone po odświeżeniu strony. Dla aplikacji przeznaczonych dla platformy .NET Framework 4.8 lub nowszej wersji zostaną zachowane po odświeżeniu strony.|
|Sugestia|Poprawne zachowanie przywracania atrybutów na odświeżenie strony, można ustawić <code>targetFrameworkVersion</code> 4.8 lub wyższej. Na przykład:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ustawienie niższej lub wcale, zachowuje stary nieprawidłowe zachowanie.|
|Zakres|Nieznany|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
