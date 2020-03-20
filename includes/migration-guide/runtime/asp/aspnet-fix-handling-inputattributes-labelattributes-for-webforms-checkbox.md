---
ms.openlocfilehash: ea0e1583cd611a624cf2d2edf9defb2294eb89d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802701"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET Fix obsługi inputAttributes i LabelAttributes for WebForms CheckBox control

|   |   |
|---|---|
|Szczegóły|Dla aplikacji, które docelowe .NET Framework 4.7.2 i wcześniejszych wersjach <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> które są programowo dodawane do formantu WebForms <xref:System.Web.UI.WebControls.CheckBox> są tracone po postback. W przypadku aplikacji docelowych .NET Framework 4.8 lub nowszych wersji są one zachowywane po wprowadzeniu zwrotu zwrotnego.|
|Sugestia|Aby uzyskać poprawne zachowanie do przywracania atrybutów na postback, ustaw na <code>targetFrameworkVersion</code> 4.8 lub wyższe. Przykład:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ustawienie go niższe lub wcale, zachowuje stare niepoprawne zachowanie.|
|Zakres|Nieznane|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
