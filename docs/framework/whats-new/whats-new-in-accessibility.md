---
title: What's new in ułatwień dostępu w programie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fe7e15e482028b9988d7e560b98be19b6c07427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509219"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>What's new in ułatwień dostępu w programie .NET Framework

Celem jest udostępnienie aplikacji użytkownikom programu .NET Framework. Funkcje ułatwień dostępu zezwala aplikacji zapewnić odpowiednie funkcje użytkowników korzystających z technologii pomocniczej. Począwszy od programu .NET Framework 4.7.1, .NET Framework zawiera wiele ulepszeń ułatwień dostępu, które umożliwiają deweloperom tworzenie aplikacji dostępny. 

## <a name="accessibility-switches"></a>Przełączniki ułatwień dostępu

Można skonfigurować aplikację do uczestnictwa w funkcje ułatwień dostępu, jeśli celem .NET Framework 4.7 lub starszej wersji, ale działa w programie .NET Framework 4.7.1 lub nowszym. Można także skonfigurować aplikację, aby korzystać z funkcji starszej wersji (i nie korzystać z funkcji ułatwień dostępu), jeśli jest on przeznaczony dla programu .NET Framework 4.7.1 lub nowszym. Każda wersja programu .NET Framework, która obejmuje funkcje ułatwień dostępu ma przełącznika dostępności określonej wersji, który można dodać do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji pliku konfiguracji aplikacji. Przełączniki obsługiwane są następujące:

|Wersja|Przełącznik|
|---|---|
|.NET Framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|.NET framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Korzystanie z rozszerzeń ułatwień dostępu

Nowe funkcje ułatwień dostępu są włączone domyślnie dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszej. Ponadto aplikacje, które są stosowane do wcześniejszej wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.7.1 lub później włączyć zachowań starszych ułatwień dostępu (i tym samym korzystając z usprawnień ułatwień dostępu), dodając przełączników do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji pliku konfiguracji aplikacji i ustawienie ich wartości `false`. Poniżej przedstawiono sposób korzystania z rozszerzeń ułatwień dostępu, które wprowadzono w programie .NET Framework 4.7.1:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Jeśli wybierzesz opcję korzystania z funkcji ułatwień dostępu w nowszej wersji programu .NET Framework, musi również jawnie przystąpieniu do funkcji z wcześniejszych wersji programu .NET Framework. Konfigurowanie aplikacji, korzystając z usprawnień ułatwień dostępu w obu programu .NET Framework 4.7.1 i 4.7.2 wymaga następujących [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Przywracanie starsze zachowanie

Aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od 4.7.1 można wyłączyć funkcje ułatwień dostępu, dodając przełącza do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji plik konfiguracji aplikacji i ustawienie ich wartości `true`. Na przykład następująca konfiguracja zdecyduje się poza wprowadzone w programie .NET Framework 4.7.2 funkcje ułatwień dostępu:  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a>What's new in ułatwień dostępu w programie .NET Framework 4.7.2

.NET Framework 4.7.2 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a>Windows Forms

**Zdefiniowane przez system operacyjny kolorów w kompozycji duży kontrast**

W programie .NET Framework 4.7.2, formularze systemu Windows używa kolorów zdefiniowanych przez system operacyjny w duży kontrast motywów. Ma to wpływ na następujące sterowniki:

- Strzałkę listy rozwijanej <xref:System.Windows.Forms.ToolStripDropDownButton> formantu.

- <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> formanty z <xref:System.Windows.Forms.ButtonBase.FlatStyle> ustawioną <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>. Poprzednio wybrane kolory tła i tekstu nie zostały kontrastem i był trudny do odczytania.

- Formanty zawarte w <xref:System.Windows.Forms.GroupBox> mający jego <xref:System.Windows.Forms.Control.Enabled> ustawioną właściwość `false`.
 
- <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, I <xref:System.Windows.Forms.ToolStripDropDownButton> formanty, które mają współczynnik kontrastu Zwiększona jasność w trybie wysokiej kontrastu.

- <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Ulepszenia Narrator**

Począwszy od programu .NET Framework 4.7.2 Narrator Obsługa została rozszerzona w następujący sposób:

- Ogłasza, wartość <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> właściwość podczas anonsowania tekst <xref:System.Windows.Forms.ToolStripMenuItem>. 

- Wskazuje, kiedy <xref:System.Windows.Forms.ToolStripMenuItem> ma jego <xref:System.Windows.Forms.Control.Enabled> ustawioną właściwość `false`.

- Udostępnia informacji zwrotnych dotyczących stanu pola wyboru po <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> właściwość jest ustawiona na `true`.

- Kolejność fokus tryb skanowania przez program Narrator jest zgodna z visual kolejności kontrolek w oknie dialogowym pobierania ClickOnce.

**Ulepszenia DataGridView**

Począwszy od programu .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> formantu ma wprowadzono następujące ulepszenia dotyczące ułatwień dostępu:

- Za pomocą klawiatury można sortować wierszy. Użytkownik może używać klawisz F3, aby posortować według bieżącej kolumny.

- Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ma ustawioną wartość <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, nagłówek kolumny zmienia kolor, aby wskazać bieżącej kolumny jako karty użytkownika za pośrednictwem komórek w bieżącym wierszu.

- <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> zwraca formantu nadrzędnego poprawne.

**Ulepszone podpowiedzi wizualne**

- <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> formantów z pustą <xref:System.Windows.Forms.ButtonBase.Text> właściwości wyświetlania wskaźnika fokus po otrzymaniu fokus.

**Obsługa siatki właściwości ulepszone**

- <xref:System.Windows.Forms.PropertyGrid> Sterowanie teraz zwracane elementy podrzędne `true` dla <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> właściwość tylko wtedy, gdy PropertyGrid element jest włączony.

- <xref:System.Windows.Forms.PropertyGrid> Kontrolować zwracane elementy podrzędne `false` dla <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> właściwość tylko wtedy, gdy PropertyGrid element można zmienić przez użytkownika.

**Ulepszone klawiatury nawigacji**

- <xref:System.Windows.Forms.ToolStripButton> Kontroli umożliwia fokus, gdy jest zawarty w <xref:System.Windows.Forms.ToolStripPanel> mający <xref:System.Windows.Forms.ToolStripPanel.TabStop> ustawioną właściwość `true`

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Zmiany do formantów wyboru i RadioButton**

W programie .NET Framework 4.7.1 i wcześniejszych wersjach, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> i <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> formanty mają niespójne i, w klasycznym i wysoki kontrast kompozycje fokus niepoprawne elementy wizualne.  Te problemy występują w przypadkach, gdy kontrolki nie mają żadnych zestawu zawartości.  Możliwość trudno Zobacz przejścia między mylące kompozycje i visual fokus.

W programie .NET Framework 4.7.2 te elementy wizualne są teraz bardziej spójność w ramach kompozycje i widoczność w klasycznym i duży kontrast motywów.

**Formanty WinForms hostowanych w aplikacji WPF**

Do formant WinForms hostowanych w aplikacji WPF w programie .NET Framework 4.7.1 i wcześniejszych wersjach, użytkownicy nie karty poza warstwą WinForms, jeśli formant pierwszego lub ostatniego w tej warstwie jest WPF <xref:System.Windows.Forms.Integration.ElementHost> formantu. W programie .NET Framework 4.7.2 użytkownicy mogą teraz karcie poza warstwą WinForms.

Jednak automatyczne aplikacje, które są oparte na fokus nigdy nie anulowanie warstwy WinForms może przestać działać zgodnie z oczekiwaniami.

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>What's new in ułatwień dostępu w programie .NET Framework 4.7.1

.NET Framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [Formanty sieci web ASP.NET](#aspnet471)

- [Narzędzia zestawu SDK .NET](#tools471)

- [Projektanta przepływów pracy programu Windows Workflow Foundation (WF)](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ulepszenia czytnika ekranu**

Włączenie ulepszenia ułatwień dostępu programu .NET Framework 4.7.1 obejmuje następujące rozszerzenia, które mają wpływ na czytników ekranu:

- .NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.Expander> formanty ogłoszeniu czytników ekranu jako przyciski. Począwszy od programu .NET Framework 4.7.1 ich obsłudze zostaną poprawnie opublikowane jako rozwijania/zwijanej grupy.

- .NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.DataGridCell> formanty ogłoszeniu czytników ekranu jako "custom". Począwszy od programu .NET Framework 4.7.1 one są teraz prawidłowo anonsowane jako komórki siatki danych (zlokalizowany).
 
- Począwszy od programu .NET Framework 4.7.1 czytników ekranu ogłaszamy nazwę można edytować <xref:System.Windows.Controls.ComboBox>.

- .NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.PasswordBox> formanty zostały ogłoszenia jako "nie elementu w widoku" lub ma inaczej niepoprawnego zachowania. Tego problemu w programie .NET Framework 4.7.1.

**Obsługa biblioteki UIAutomation LiveRegion**

Czytników ekranu, takie jak osoby pomocy Narrator odczytywać zawartość interfejsu użytkownika aplikacji, zwykle tekst na mowę dane wyjściowe zawartości interfejsu użytkownika, który ma fokus. Jednak jeśli elementu interfejsu użytkownika zmiany i nie ma fokus, użytkownik nie może zostać zgłoszone i może pominąć ważne informacje. Regiony na żywo na celu rozwiązanie tego problemu. Deweloper może użyć ich poinformować odczytywania zawartości ekranu lub inne klienta biblioteki UIAutomation, który wprowadzono istotne zmiany do elementu interfejsu użytkownika. Czytnik następnie można zdecydować, jak i kiedy informują użytkownika o tej zmiany. 

Do obsługi na żywo regionów, WPF dodano następujące interfejsy API:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pola, które identyfikują **LiveSetting** właściwości i **LiveRegionChanged** zdarzeń. Można ich ustawiać przy użyciu języka XAML.

- **AutomationProperties.LiveSetting** dołączona właściwość, która informuje czytnik ważne zmiany interfejsu użytkownika dla użytkownika.

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Właściwość, która identyfikuje **AutomationProperties.LiveSetting** dołączona właściwość.
 
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metodę, która może zostać zastąpiona w celu zapewnienia **LiveSetting** wartości.

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody get i set **LiveSetting** wartości.
 
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Wyliczenia, który definiuje następujące możliwości **LiveSetting** wartości:

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Element nie wysyła powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Element wysyła powiadomienia interruptive zmiana zawartości na żywo regionu.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Element wysyła interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.   

Można utworzyć LiveRegion przez ustawienie **AutomationProperties.LiveSetting** właściwości w elemencie zainteresowań, jak pokazano w poniższym przykładzie:   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Podczas zmiany danych w regionie na żywo i należy poinformować czytnika ekranu, należy jawnie wywołaj zdarzenie, jak pokazano w poniższym przykładzie.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Duży kontrast**

Począwszy od programu .NET Framework 4.7.1 ulepszenia duży kontrast zostały wprowadzone do różnych formantów WPF. Teraz są one widoczne podczas <xref:System.Windows.SystemParameters.HighContrast%2A> ustawiono motywu. Należą do nich następujące elementy:

- <xref:System.Windows.Controls.Expander> Formant

    Fokus visual dla <xref:System.Windows.Controls.Expander> kontroli jest teraz widoczne. Elementy wizualne klawiatury dla <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.RadioButton> formanty są również widoczne. Na przykład:

    Przed: 
    
    ![Kontrolkę Expander z fokusem przed ulepszenia ułatwień dostępu](media/expander-before.png)

    Po: 

    ![Kontrolkę Expander z fokusem po ulepszenia ułatwień dostępu](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów
 
    Tekst w <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów jest teraz lepiej widoczne po wybraniu w kompozycji dużego kontrastu. Na przykład:

    Przed: 

    ![Przycisk radiowy duży kontrast z fokusem przed ulepszenia ułatwień dostępu](media/radio-button-before.png)
    
    Po: 

    ![Przycisk radiowy duży kontrast z fokusem po ulepszenia ułatwień dostępu](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> Formant
 
    Począwszy od programu .NET Framework 4.7.1, obramowania wyłączone <xref:System.Windows.Controls.ComboBox> formant jest kolor wyłączonego tekstu. Na przykład:
    
    Przed: 

     ![ComboBox — wyłączone obramowania i tekst przed ulepszenia ułatwień dostępu](media/combo-disabled-before.png)

    Po:   

     ![ComboBox — wyłączone obramowania i tekst po ulepszenia ułatwień dostępu](media/combo-disabled-after.png)

    Ponadto przyciski wyłączone i skupiają się użyć kolor motywu poprawne.

    Przed:

    ![Przycisk motywu kolorów przed ulepszenia ułatwień dostępu](media/button-themes-before.png) 
    
    Po: 

    ![Przycisk motywu kolorów po ulepszenia ułatwień dostępu](media/button-themes-after.png) 

    Ponadto w .NET Framework 4.7 i wcześniejsze wersje, ustawienie <xref:System.Windows.Controls.ComboBox> stylu kontrolki do `Toolbar.ComboBoxStyleKey` spowodował strzałkę listy rozwijanej, aby była niewidoczna. Tego problemu w programie .NET Framework 4.7.1. Na przykład:

    Przed: 

    ![Toolbar.ComboBoxStyleKey przed ulepszenia ułatwień dostępu](media/comboboxstylekey-before.png) 
    
    Po: 

    ![Toolbar.ComboBoxStyleKey po ulepszenia ułatwień dostępu](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> Formant

    Począwszy od programu .NET Framework 4.7.1, Strzałka wskaźnika sortowania w <xref:System.Windows.Controls.DataGrid> steruje teraz używa Popraw kolorów motywu. Na przykład:

    Przed: 

    ![Sortowanie Strzałka wskaźnika przed ulepszenia ułatwień dostępu](media/sort-indicator-before.png) 
    
    Po:   
 
    ![Strzałka wskaźnika sortowania po ulepszenia ułatwień dostępu](media/sort-indicator-after.png) 
    
    Ponadto w programie .NET Framework 4.7 i wcześniejszych wersjach, domyślny styl łącza zmieniony na nieprawidłowy kolor na myszy za pośrednictwem w trybie dużego kontrastu. Ten problem został rozwiązany, począwszy od programu .NET Framework 4.7.1. Podobnie <xref:System.Windows.Controls.DataGrid> kolumn wyboru używa oczekiwanego kolorów w programie .NET Framework 4.7.1 opinii fokus klawiatury.

    Przed: 

    ![Styl łącza domyślne DataGrid przed ulepszenia ułatwień dostępu](media/default-link-style-before.png) 
 
    Po:    
  
    ![Styl łącza domyślne DataGrid po ulepszenia ułatwień dostępu](media/default-link-style-after.png)  

Aby uzyskać więcej informacji na WPF ulepszenia ułatwień dostępu w programie .NET Framework 4.7.1, zobacz [usprawnienia dostępu na platformie WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a>Ulepszenia dostępność formularzy systemu Windows

W programie .NET Framework 4.7.1 formularze systemu Windows (WinForms) zawiera zmiany ułatwień dostępu w następujących obszarach.

**Ulepszone wyświetlania w trybie dużego kontrastu**

Począwszy od programu .NET Framework 4.7.1 różnych formantów WinForms oferują ulepszoną renderowania w trybach HighContrast dostępne w systemie operacyjnym. Windows 10 zmienił wartości dla niektórych kolorów systemu duży kontrast, i formularze systemu Windows jest oparta na platformę Windows 10 Win32. Aby uzyskać najlepsze wyniki należy uruchomić na najnowszej wersji systemu Windows i korzystania z najnowszych zmian systemu operacyjnego przez dodawanie pliku app.manifest aplikacja testowa i un komentarz systemu Windows 10 obsługiwane wiersza systemu operacyjnego, aby wyglądały one następujące:

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
Niektóre zmiany duży kontrast należą:

- Zaznaczeń w <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.

- Po wybraniu wyłączone <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.

- Tekst w wybranej <xref:System.Windows.Forms.Button> kontrolować różni się od kolor zaznaczenia.

- Wyłączony tekst jest bardziej czytelne. Na przykład:

    Przed:

    ![Tekst wyłączone przed ulepszenia ułatwień dostępu](media/wf-disabled-before.png) 

    Po:

    ![Wyłączonego tekstu po ulepszenia ułatwień dostępu](media/wf-disabled-after.png) 

- Ulepszenia duży kontrast w oknie dialogowym wyjątków wątku.

**Ulepszona obsługa Narrator**

Formularze systemu Windows w programie .NET Framework 4.7.1 obejmuje następujące ulepszenia Narrator ułatwień dostępu:

- <xref:System.Windows.Forms.MonthCalendar> Kontroli jest dostępny program Narrator, a także innymi narzędziami automatyzacji interfejsu użytkownika.

- <xref:System.Windows.Forms.CheckedListBox> Kontroli powiadamia Narrator, gdy stan zaznaczenia elementu zostanie zmieniony, więc użytkownik jest powiadamiany o ich zmieniono wartość elementu listy.
 
- <xref:System.Windows.Forms.DataGridViewCell> Kontroli zaraportuje prawidłowe stanu tylko do odczytu do Narrator.
 
- Narrator, mogą teraz odczytywać wyłączone <xref:System.Windows.Forms.ToolStripMenuItem> tekstu, należy wcześniej może pominąć elementów menu wyłączone.

**Rozszerzona obsługa biblioteki UIAutomation wzorce ułatwień dostępu**

Deweloperzy technologii ułatwień dostępu w programie .NET Framework 4.7.1, można wykorzystać typowe wzorce ułatwień dostępu interfejsu API i właściwości dla kilku formantów WinForms. Ułatwienia dostępu do tych udoskonaleń należą:

- <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ToolStripSplitButton> obsługują teraz [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> Obsługuje teraz [toggle — wzorzec](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).
 
- <xref:System.Windows.Forms.ToolStripItem> Sterowanie obsługuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości i [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.NumericUpDown> i <xref:System.Windows.Forms.DomainUpDown> formanty obsługi <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości.

**Ulepszone właściwości przeglądania**

Formularze systemu Windows w programie .NET Framework 4.7.1, obejmują:

- Lepsze nawigacji klawiatury przez różne okna wyboru z listy rozwijanej.
- Zmniejszenie niepotrzebnych tabulatorów.
- Lepiej raportowanie typy formantów.
- Ulepszone narrator zachowanie.
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a>Formanty sieci web ASP.NET

Począwszy od programu .NET Framework 4.7.1 i 15 ustęp 3 programu Visual Studio 2017, ASP.NET poprawia działanie formantów sieci web ASP.NET przy użyciu technologii ułatwień dostępu w programie Visual Studio. Następujące zmiany:

- Zmiany w implementacji Brak wzorce ułatwień dostępu interfejsu użytkownika w formantach, tak samo, jak **Dodaj pole** okno dialogowe w **widoku szczegółów** kreatora lub **Konfiguruj element ListView** okna dialogowego z **ListView** kreatora.

- Zmiany w celu polepszenia wyświetlania w trybie dużego kontrastu, takie jak **Edytor pola modułu stronicowania danych**.

- Zmiany w celu polepszenia nawigacji klawiatury napotyka formanty, takie jak **pola** okno dialogowe w **Edytuj pola modułu stronicowania** Kreator formantu DataPager **skonfigurować ObjectContext**  okno dialogowe, lub **Konfigurowanie wyboru danych** okna dialogowego z **skonfiguruj źródło danych** kreatora.

<a name="tools471"></a>
## <a name="net-sdk-tools"></a>Narzędzia zestawu SDK .NET

[Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) i [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ulepszono napraw problemy z dostępem zróżnicowane. Większość tych były niewielkie problemy, jak nazwa nie jest zdefiniowany lub niektórych wzorce automatyzacji interfejsu użytkownika nie jest zaimplementowana poprawnie. Gdy wielu użytkowników nie należy pamiętać o tych niepoprawne wartości, klienci korzystający z ułatwieniami technologii, takich jak czytniki znajdzie te narzędzia zestawu SDK dostęp. 

Te ulepszenia zmienić niektóre zachowania poprzedniej, takich jak kolejność fokus klawiatury.

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a>Projektanta przepływów pracy programu Windows Workflow Foundation (WF)

Zmiany ułatwień dostępu w Projektancie przepływów pracy są następujące:

- Kolejność tabulacji zmiany od lewej do prawej i od góry do dołu w niektórych formantów:

  - W oknie korelacji zainicjować ustawienie dane korelacji dla <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.

  - W oknie definicję zawartości <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działań.

- Więcej funkcji dostępnych za pośrednictwem klawiatury:

  - Podczas edytowania właściwości działania, grup właściwości może zostać zwinięty przy klawiatury są koncentruje się po raz pierwszy.

  - Ostrzeżenie ikony są dostępny za pomocą klawiatury.

  - **Więcej właściwości** przycisk **właściwości** okno jest dostępny za pomocą klawiatury.

  - Klawiatura użytkownicy mogą uzyskiwać dostęp do elementy nagłówka w **argumenty** i **zmienne** okienka projektanta przepływów pracy.

- Lepszą widoczność elementów z fokusem, takie jak czas:

  - Dodawanie wierszy do siatek danych używane przez projektantów projektanta przepływów pracy i działania.

  - TAB pól w <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply> działań.

  - Ustawianie wartości domyślnych do zmiennych lub argumentów

- Czytniki teraz mógł prawidłowo rozpoznać:

  - Ustaw punkty przerwania w Projektancie przepływów pracy.

  - <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, I <xref:System.ServiceModel.Activities.CorrelationScope> działań.
  - Zawartość <xref:System.ServiceModel.Activities.Receive> działania.

  - Typ docelowy dla <xref:System.Activities.Statements.InvokeMethod> działania.

  - Pole kombi wyjątku i na koniec sekcji <xref:System.Activities.Statements.TryCatch> działania.

  - Pole kombi typ komunikatu, podziału w oknie Dodaj inicjatorów korelacji, okno definicji zawartości i oknie CorrelatesOn definicji działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>).

  - Automatu stanów przejścia i przejścia miejsc docelowych.

  - Adnotacje i łącznikami <xref:System.Activities.Statements.FlowDecision> działań.

  - Menu kontekstowe (kliknij prawym przyciskiem myszy) dla działań.

  - Edytory wartość właściwości, przycisk Wyczyść wyszukiwanie według kategorii i przyciski alfabetycznej sortowania i okno dialogowe Edytor wyrażeń w siatce właściwości.

  - Procent powiększenia w Projektancie przepływów pracy.

  - Separator w <xref:System.Activities.Statements.Parallel> i <xref:System.Activities.Statements.Pick> działań.

  - <xref:System.Activities.Statements.InvokeDelegate> Działania.

  - W oknie Wybierz typy działań słownika (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`itp.).

  - Przeglądaj i wybierz typ .NET okna.

  - Obszar nawigacji w Projektancie przepływów pracy.

- Użytkownicy, którzy wybierz motywów duży kontrast będą widzieć wiele ulepszeń w widoczność projektanta przepływów pracy i jego kontroli, jak lepiej współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używany do elementów zespołu.

## <a name="see-also"></a>Zobacz też

[Co to jest nowe w programie .NET Framework](whats-new.md)
 
