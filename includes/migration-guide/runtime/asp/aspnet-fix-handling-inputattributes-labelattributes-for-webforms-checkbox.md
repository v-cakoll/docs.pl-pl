---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622076"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET Rozwiązywanie problemów z obsługą InputAttributes i LabelAttributes dla kontrolki CheckBox dla formularzy WebForms

#### <a name="details"></a>Szczegóły

W przypadku aplikacji przeznaczonych do .NET Framework 4.7.2 i starszych wersji, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> które są programowo dodawane do formantu WebForms, <xref:System.Web.UI.WebControls.CheckBox> są tracone po odświeżeniu. W przypadku aplikacji przeznaczonych do .NET Framework 4,8 lub nowszych wersji są one zachowywane po odświeżeniu.

#### <a name="suggestion"></a>Sugestia

Aby mieć poprawne zachowanie w zakresie przywracania atrybutów na stronie ogłaszania zwrotnego, ustaw wartość <code>targetFrameworkVersion</code> na 4,8 lub wyższą. Przykład:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Ustawienie go na niższym poziomie lub w ogóle zachowuje stare nieprawidłowe zachowanie.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Nieznane|
|Wersja|4,8|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
