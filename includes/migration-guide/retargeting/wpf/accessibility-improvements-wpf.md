---
ms.openlocfilehash: 47d3829748deef2c7c3610816b8941bf88da7ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614922"
---
### <a name="accessibility-improvements-in-wpf"></a>Ulepszenia ułatwień dostępu w programie WPF

#### <a name="details"></a>Szczegóły

**Udoskonalenia duży kontrast**
<ul><li>Fokus dla <xref:System.Windows.Controls.Expander> kontrolki jest teraz widoczny. W poprzednich wersjach .NET Framework nie była.
-Tekst w obszarze <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> kontrolki, gdy są wybrane, jest teraz łatwiejszy do sprawdzenia niż w poprzednich wersjach .NET Framework.
-Obramowanie wyłączone <xref:System.Windows.Controls.ComboBox> ma teraz taki sam kolor jak wyłączony tekst. W poprzednich wersjach .NET Framework nie była.
-Przyciski wyłączone i priorytetowe teraz używają poprawnego koloru motywu. W poprzednich wersjach .NET Framework nie zostały one wykonane.
-Przycisk rozwijalny jest teraz widoczny, gdy <xref:System.Windows.Controls.ComboBox> styl kontrolki jest ustawiony na <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> , w poprzednich wersjach .NET Framework, nie był.
-Strzałka sortowania w <xref:System.Windows.Controls.DataGrid> kontrolce używa teraz kolorów motywu. W poprzednich wersjach .NET Framework nie zostało to zrobione.
-Domyślny styl hiperlinku zmieni się na prawidłowy kolor motywu na wskaźniku myszy. W poprzednich wersjach .NET Framework nie zostało to zrobione.
-Fokus klawiatury na przyciskach radiowych jest teraz widoczny. W poprzednich wersjach .NET Framework nie była.
-<xref:System.Windows.Controls.DataGrid>Kolumna pola wyboru kontrolki używa teraz oczekiwanych kolorów dla opinii o fokusie klawiatury. W poprzednich wersjach .NET Framework nie zostało to zrobione.
-wizualizacje fokusu klawiatury są teraz widoczne dla <xref:System.Windows.Controls.ComboBox> i w <xref:System.Windows.Controls.ListBox> kontrolkach. W poprzednich wersjach .NET Framework nie była.</p>
**Ulepszenia interakcji czytnika ekranu**
<ul><li><xref:System.Windows.Controls.Expander>kontrolki są teraz prawidłowo anonsowane jako grupy (Rozwiń/Zwiń) przez czytniki zawartości ekranu.
- <xref:System.Windows.Controls.DataGridCell>kontrolki są teraz prawidłowo anonsowane jako komórki siatki danych (zlokalizowane) przez czytniki zawartości ekranu.
-Czytniki zawartości ekranu będą teraz ogłaszać nazwę edytowalną <xref:System.Windows.Controls.ComboBox> .
- <xref:System.Windows.Controls.PasswordBox>kontrolki nie są już ogłaszane jako &quot; elementy wyświetlane &quot; przez czytniki zawartości ekranu.</p>
**Obsługa LiveRegion** Czytniki ekranu, takie jak Narrator, pomagają użytkownikom znać zawartość interfejsu użytkownika aplikacji, zwykle przez opisywanie czegoś o interfejsie użytkownika, który jest obecnie skoncentrowany, ponieważ jest to prawdopodobnie element najbardziej interesujący dla użytkownika. Jeśli jednak element interfejsu użytkownika zmieni się na ekranie i nie ma fokusu, użytkownik może nie być informowany i nie przegap ważnych informacji. LiveRegions mają na celu rozwiązanie tego problemu. Programista może użyć ich do informowania czytnika ekranu lub innego klienta [automatyzacji interfejsu użytkownika](~/docs/framework/ui-automation/ui-automation-overview.md) o tym, że wprowadzono ważną zmianę w elemencie interfejsu użytkownika. Czytnik ekranu może następnie zdecydować, jak i kiedy należy poinformować użytkownika o tej zmianie. Właściwość LiveSetting umożliwia również czytelnikowi ekranu znać, jak ważne jest, aby poinformować użytkownika o zmianach wprowadzonych w interfejsie użytkownika.

#### <a name="suggestion"></a>Sugestia

**Jak wybrać lub wycofać te zmiany** Aby aplikacja mogła korzystać z tych zmian, musi ona działać na .NET Framework 4.7.1 lub nowszym. Aplikacja może korzystać z tych zmian w jeden z następujących sposobów:

- Docelowa .NET Framework 4.7.1. Jest to zalecane podejście. Te zmiany ułatwień dostępu są domyślnie włączone w aplikacjach WPF przeznaczonych dla .NET Framework 4.7.1 lub nowszych.
- Powoduje to wypróbowanie starszych zachowań dostępności przez dodanie następującego [przełącznika AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w `<runtime>` sekcji pliku konfiguracyjnego aplikacji i ustawienie go na `false` , jak pokazano w poniższym przykładzie.

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Aplikacje, które są przeznaczone dla .NET Framework 4.7.1 lub nowszych i chcą zachować starsze zachowanie ułatwień dostępu, mogą zrezygnować z używania starszych funkcji ułatwień dostępu przez jawne ustawienie tego przełącznika AppContext na `true` .
Aby zapoznać się z omówieniem automatyzacji interfejsu użytkownika, zobacz [Omówienie automatyzacji interfejsu użytkownika](~/docs/framework/ui-automation/ui-automation-overview.md).

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting(System.Windows.DependencyObject,System.Windows.Automation.AutomationLiveSetting)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting(System.Windows.DependencyObject)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore?displayProperty=nameWithType>
