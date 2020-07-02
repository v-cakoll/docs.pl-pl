---
ms.openlocfilehash: c8e1c91f4fee8aa896b6617c815fe2a4b6d22f2a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614889"
---
### <a name="accessibility-improvements-in-windows-forms-controls"></a>Ulepszenia ułatwień dostępu w kontrolkach Windows Forms

#### <a name="details"></a>Szczegóły

Windows Forms ulepsza sposób działania z technologiami ułatwień dostępu w celu lepszego wsparcia Windows Forms klientów. Obejmują one następujące zmiany, zaczynając od .NET Framework 4.7.1:

- Zmiany w celu usprawnienia wyświetlania w trybie duży kontrast.
- Zmiany w celu ulepszenia środowiska przeglądarki właściwości. Ulepszenia przeglądarki właściwości obejmują:
- Lepsza Nawigacja przy użyciu klawiatury w różnych oknach menu rozwijanego.
- Zredukowanie zbędnych tabulatorów.
- Lepsze raportowanie typów kontroli.
- Ulepszone zachowanie narratora.
- Zmiany w celu zaimplementowania brakujących wzorców dostępności interfejsu użytkownika w kontrolkach.

#### <a name="suggestion"></a>Sugestia

**Jak wybrać lub wycofać te zmiany** Aby aplikacja mogła korzystać z tych zmian, musi ona działać na .NET Framework 4.7.1 lub nowszym. Aplikacja może korzystać z tych zmian w jeden z następujących sposobów:

- Zostanie ponownie skompilowana w celu przekierowania .NET Framework 4.7.1. Te zmiany ułatwień dostępu są domyślnie włączone w Windows Forms aplikacjach przeznaczonych dla .NET Framework 4.7.1 lub nowszych.
- Przede wszystkim można wypróbować starsze zachowania dostępności, dodając następujący [przełącznik AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku app.config i ustawiając go na `false` , jak pokazano w poniższym przykładzie.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

Aplikacje, które są przeznaczone dla .NET Framework 4.7.1 lub nowszych i chcą zachować starsze zachowanie ułatwień dostępu, mogą zrezygnować z używania starszych funkcji ułatwień dostępu przez jawne ustawienie tego przełącznika AppContext na `true` .<p/>Aby zapoznać się z omówieniem automatyzacji interfejsu użytkownika, zobacz [Omówienie automatyzacji interfejsu użytkownika](~/docs/framework/ui-automation/ui-automation-overview.md).<p/>**Dodano obsługę wzorców i właściwości automatyzacji interfejsu użytkownika**<br/>Klienci dostępności mogą korzystać z nowych funkcji ułatwień dostępu narzędzi WinForms za pomocą wspólnych, publicznie opisanych wzorców wywołań. Wzorce te nie są specyficzne dla WinForms. Na przykład klienci dostępności mogą wywołać metodę QueryInterface w interfejsie IAccessible (MAAS) w celu uzyskania interfejsu IServiceProvider. Jeśli ten interfejs jest dostępny, klienci mogą użyć metody QueryService, aby zażądać interfejsu IAccessibleEx. Aby uzyskać więcej informacji, zobacz [Używanie IAccessibleEx z poziomu klienta](https://docs.microsoft.com/windows/desktop/WinAuto/using-iaccessibleex-from-a-client). Począwszy od .NET Framework 4.7.1, IServiceProvider i [IAccessibleEx](https://docs.microsoft.com/windows/desktop/WinAuto/iaccessibleex) (jeśli dotyczy) są dostępne dla obiektów ułatwień dostępu dla narzędzi WinForms.<p/>.NET Framework 4.7.1 dodaje obsługę następujących wzorców automatyzacji interfejsu użytkownika i właściwości:

- <xref:System.Windows.Forms.ToolStripSplitButton>Formanty i <xref:System.Windows.Forms.ComboBox> obsługują [wzorzec rozwijania/zwijania](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- <xref:System.Windows.Forms.ToolStripMenuItem>Kontrolka ma wartość właściwości [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.ToolStripItem>Kontrolka obsługuje <xref:System.Windows.Automation.AutomationElement.NameProperty> Właściwość oraz[wzorzec Rozwiń/Zwiń](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- <xref:System.Windows.Forms.ToolStripDropDownItem>Kontrolka obsługuje <xref:System.Windows.Forms.AccessibleEvents> StateChange i NameChange —, gdy rozwijanie jest rozwinięte lub zwinięte.
- <xref:System.Windows.Forms.ToolStripDropDownButton>Kontrolka ma właściwość [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) o wartości <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>Kontrolka obsługuje <xref:System.Windows.Automation.TogglePattern> .
- <xref:System.Windows.Forms.NumericUpDown>Formanty i <xref:System.Windows.Forms.DomainUpDown> obsługują <xref:System.Windows.Automation.AutomationElement.NameProperty> Właściwość oraz mają element [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md) z <xref:System.Windows.Automation.ControlType.Spinner?displayProperty=nameWithType> .</p>
**Ulepszenia kontrolki PropertyGrid** .NET Framework 4.7.1 dodaje następujące usprawnienia do kontrolki przeglądarka właściwości:

- Przycisk **szczegóły** w oknie dialogowym błędu, który jest wyświetlany, gdy użytkownik wprowadza niepoprawną wartość w <xref:System.Windows.Forms.PropertyGrid> kontrolce obsługuje [wzorzec rozwijania/zwijania](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md), powiadomienia o zmianie stanu i nazwy oraz Właściwość [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) o wartości <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> .
- Okienko komunikatu wyświetlane po rozwinięciu przycisku **szczegóły** okna dialogowego błędu jest teraz dostępne z klawiatury i umożliwia programowi Narrator ogłaszanie zawartości komunikatu o błędzie.
- <xref:System.Windows.Forms.AccessibleRole>Wiersze w <xref:System.Windows.Forms.PropertyGrid> kontrolce zostały zmienione z &quot; wierszy &quot; na &quot; komórkę &quot; . Komórka mapuje do elementu UIA ControlType &quot; &quot; , który umożliwia obsługę odpowiednich skrótów klawiaturowych i anonsów programu Narrator.
- <xref:System.Windows.Forms.PropertyGrid>Wiersze kontrolki, które reprezentują elementy nagłówka, gdy <xref:System.Windows.Forms.PropertyGrid> kontrolka ma <xref:System.Windows.Forms.PropertyGrid.PropertySort> ustawioną właściwość <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) o wartości <xref:System.Windows.Automation.ControlType.Button?displayProperty=nameWithType> .
- <xref:System.Windows.Forms.PropertyGrid>Wiersze kontrolki, które reprezentują elementy nagłówka, gdy <xref:System.Windows.Forms.PropertyGrid> kontrolka ma <xref:System.Windows.Forms.PropertyGrid.PropertySort> ustawioną właściwość, aby <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> obsługiwać [wzorzec rozwijania/zwijania](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- Ulepszona nawigacja klawiatury między siatką i paskiem narzędzi nad nią. Naciśnięcie klawisza &quot; SHIFT-TAB &quot; spowoduje wybranie pierwszego przycisku paska narzędzi, a nie całego paska narzędzi.
- <xref:System.Windows.Forms.PropertyGrid>kontrolki wyświetlane w trybie duży kontrast teraz rysują prostokąt fokus wokół przycisku paska narzędzi, który odpowiada bieżącej <xref:System.Windows.Forms.PropertyGrid.PropertySort> wartości właściwości.
- <xref:System.Windows.Forms.PropertyGrid>kontrolki wyświetlane w trybie duży kontrast i z <xref:System.Windows.Forms.PropertyGrid.PropertySort> właściwością ustawioną na <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> teraz będą wyświetlać tło nagłówków kategorii w kolorze o wysokim kontraście.
- <xref:System.Windows.Forms.PropertyGrid>formanty są lepiej odróżniające od elementów paska narzędzi z fokusem i elementami paska narzędzi, które wskazują bieżącą wartość <xref:System.Windows.Forms.PropertyGrid.PropertySort> właściwości. Ta poprawka obejmuje zmianę duży kontrast i zmianę w scenariuszach nieduży kontrastowych.
- <xref:System.Windows.Forms.PropertyGrid>elementy paska narzędzi kontrolki, które wskazują bieżącą wartość <xref:System.Windows.Forms.PropertyGrid.PropertySort> właściwości, obsługują <xref:System.Windows.Automation.TogglePattern> .
- Ulepszono obsługę Narratora w celu odróżnienia zaznaczonego wyrównania w selektorze wyrównania.
- Gdy <xref:System.Windows.Forms.PropertyGrid> w formularzu zostanie wyświetlona pusta kontrolka, będzie ona teraz otrzymywać fokus, w którym wcześniej nie byłoby.

**Używanie kolorów zdefiniowanych w systemie operacyjnym w duży kontrast motywach**

- <xref:System.Windows.Forms.Button>Formanty i <xref:System.Windows.Forms.CheckBox> wraz z ich <xref:System.Windows.Forms.ButtonBase.FlatStyle> właściwością ustawioną na <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> , która jest stylem domyślnym, teraz używają kolorów zdefiniowanych w systemie operacyjnym w motywie duży kontrast po zaznaczeniu. Wcześniej kolory tekstu i tła nie były kontrastowe i trudno je odczytać.
- <xref:System.Windows.Forms.Button>Elementy, <xref:System.Windows.Forms.CheckBox> , <xref:System.Windows.Forms.RadioButton> , <xref:System.Windows.Forms.Label> , <xref:System.Windows.Forms.LinkLabel> i <xref:System.Windows.Forms.GroupBox> kontrolki z <xref:System.Windows.Forms.Control.Enabled> właściwością ustawioną na **wartość false** używają kolor cieniowania, aby renderować tekst w motywach duży kontrast, co skutkuje niskim kontrastem w tle. Teraz te kontrolki używają &quot; kolor tekstu wyłączonego &quot; zdefiniowanego przez system operacyjny. Ta poprawka ma zastosowanie do kontrolek z `FlatStyle` właściwością ustawioną na wartość inną niż <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> . Te ostatnie kontrolki są renderowane przez system operacyjny.
- <xref:System.Windows.Forms.DataGridView>teraz renderuje widoczny prostokąt wokół zawartości komórki, która ma bieżący fokus. Wcześniej nie było to widoczne w niektórych duży kontrast motywów.
- <xref:System.Windows.Forms.ToolStripMenuItem>kontrolki z <xref:System.Windows.Forms.ToolStripMenuItem.Enabled> właściwością ustawioną na **wartość false** teraz używają &quot; wyłączonego &quot; koloru tekstu zdefiniowanego przez system operacyjny.
- <xref:System.Windows.Forms.ToolStripMenuItem>kontrolki z <xref:System.Windows.Forms.ToolStripMenuItem.Checked> właściwością ustawioną na **wartość true** teraz renderują skojarzony znacznik wyboru w kolorze systemu kontrastowego.  Wcześniej kolor znacznika wyboru nie był wystarczająco kontrastowy i nie jest widoczny w motywach duży kontrast.
Uwaga: system Windows 10 zmienił wartości dla niektórych kolorów systemu o dużym kontraście. Platforma Windows Forms Framework jest oparta na platformie Win32. Aby uzyskać najlepsze środowisko, uruchom polecenie w najnowszej wersji systemu Windows i zapoznaj się z najnowszymi zmianami systemu operacyjnego przez dodanie pliku App. manifest do aplikacji testowej i cofnięcie komentarza do następującego kodu:

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**Ulepszone nawigowanie po klawiaturze**

- Gdy <xref:System.Windows.Forms.ComboBox> kontrolka ma <xref:System.Windows.Forms.ComboBox.DropDownStyle> ustawioną właściwość na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList?displayProperty=nameWithType> i jest pierwszą kontrolką w kolejności tabulacji w formularzu, teraz wyświetla prostokąt fokusu, gdy formularz nadrzędny zostanie otwarty przy użyciu klawiatury. Przed wprowadzeniem tej zmiany fokus klawiatury był na tym formancie, ale wskaźnik fokusu nie został renderowany.

**Ulepszona obsługa Narratora**

- <xref:System.Windows.Forms.MonthCalendar>Kontrolka dodała obsługę technologii pomocniczych w celu uzyskania dostępu do kontrolki, w tym możliwość odczytywania przez program Narrator wartości kontrolki, gdy wcześniej jej nie było możliwe.

- <xref:System.Windows.Forms.CheckedListBox>Kontrolka teraz powiadamia program Narrator, gdy <xref:System.Windows.Forms.CheckBox.CheckState?displayProperty=nameWithType> Właściwość została zmieniona. Wcześniej program Narrator nie otrzymał powiadomienia i w związku z tym użytkownicy nie otrzymali informacji o tym, że <xref:System.Windows.Forms.CheckBox.CheckState> Właściwość została zaktualizowana.
- <xref:System.Windows.Forms.LinkLabel>Kontrolka zmieniła sposób, w jaki powiadamia Narratora o tekście w kontrolce. Wcześniej narrator ogłosił ten tekst dwukrotnie i odczytuje &quot; &amp; &quot; symbole jako prawdziwy tekst, mimo że nie są widoczne dla użytkownika. Zduplikowany tekst został usunięty z anonsów programu Narrator, a także niepotrzebnych &quot; &amp; &quot; symboli.
- <xref:System.Windows.Forms.DataGridViewCell>Teraz typy kontrolek poprawnie raportują stan tylko do odczytu do programu Narrator i innych technologii pomocniczych.
- Program Narrator może teraz odczytać menu systemowe okien podrzędnych w temacie [wiele dokumentów interfejsu] ~/docs/Framework/WinForms/Advanced/Multiple-Document-Interface-MDI-Applications.MD).
- Program Narrator może teraz odczytywać <xref:System.Windows.Forms.ToolStripMenuItem> kontrolki z <xref:System.Windows.Forms.ToolStripItem.Enabled?displayProperty=nameWithType> właściwością ustawioną na **wartość false**. Wcześniej program Narrator nie mógł skoncentrować się na wyłączonych elementach menu w celu odczytania zawartości.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4,8         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.ToolStripDropDownButton.CreateAccessibilityInstance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownAccessibleObject.Name?displayProperty=nameWithType>
- [MonthCalendar. AccessibilityObject](xref:System.Windows.Forms.Control.AccessibilityObject)
