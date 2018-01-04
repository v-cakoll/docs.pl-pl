---
title: "What's new in ułatwień dostępu w programie .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe4b24f14dd8f08d1168cc26b91e04faa4bf183
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>What's new in ułatwień dostępu w programie .NET Framework

Celem jest tworzenie aplikacji więcej accessibile dla użytkowników programu .NET Framework. Funkcje ułatwień dostępu zezwala aplikacji zapewnić odpowiednie funkcje użytkowników korzystających z technologii pomocniczej. Począwszy od programu .NET Framework 4.7.1, .NET Framework zawiera wiele ulepszeń ułatwień dostępu, które umożliwiają deweloperom tworzenie aplikacji dostępny. 

Nowe funkcje ułatwień dostępu są włączone domyślnie dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszej. Ponadto aplikacje, które są stosowane do wcześniejszej wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.7.1 lub później włączyć zachowań starszych ułatwień dostępu (i tym samym zgłosić się do poprawy ułatwień dostępu w programie .NET Framework 4.7.1) przez Dodawanie do następującego przełącznika [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji pliku konfiguracji aplikacji. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Podobnie, aplikacji, które odnoszą się do wersji programu .NET Framework, począwszy od 4.7.1 można wyłączyć funkcje ułatwień dostępu, dodając następujący przełącznik do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji pliku konfiguracji aplikacji. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>What's new in ułatwień dostępu w programie .NET Framework 4.7.1

.NET Framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

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

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>., Element nie wysyła powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>., Element wysyła powiadomienia interruptive zmiana zawartości na żywo regionu.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>., Element wysyła interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.   

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

- <xref:System.Windows.Controls.Expander>Formant

    Fokus visual dla <xref:System.Windows.Controls.Expander> kontroli jest teraz widoczne. Elementy wizualne klawiatury dla <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.RadioButton> formanty są również widoczne. Na przykład:

    Przed: 
    
    ![Kontrolkę Expander z fokusem przed ulepszenia ułatwień dostępu](media/expander-before.png)

    Po: 

    ![Kontrolkę Expander z fokusem po ulepszenia ułatwień dostępu](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox>i <xref:System.Windows.Controls.RadioButton> formantów
 
    Tekst w <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów jest teraz lepiej widoczne po wybraniu w kompozycji dużego kontrastu. Na przykład:

    Przed: 

    ![Przycisk radiowy duży kontrast z fokusem przed ulepszenia ułatwień dostępu](media/radio-button-before.png)
    
    Po: 

    ![Przycisk radiowy duży kontrast z fokusem po ulepszenia ułatwień dostępu](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox>Formant
 
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

- <xref:System.Windows.Controls.DataGrid>Formant

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

## <a name="windows-forms-accessibility-improvements"></a>Ulepszenia dostępność formularzy systemu Windows

W programie .NET Framework 4.7.1 formularze systemu Windows (WinForms) zawiera zmiany ułatwień dostępu w następujących obszarach.

**Ulepszone wyświetlania w trybie dużego kontrastu**

Począwszy od programu .NET Framework 4.7.1 różnych formantów WinForms oferują ulepszoną renderowania w trybach HighContrast dostępne w systemie operacyjnym. Windows 10 zmienił wartości dla niektórych kolorów systemu duży kontrast, i formularze systemu Windows jest oparta na platformę Windows 10 Win32. Aby uzyskać najlepsze wyniki należy uruchomić na najnowszej wersji systemu Windows i korzystania z najnowszych zmian systemu operacyjnego przez dodawanie pliku app.manifest aplikacja testowa i un komentarz systemu Windows 10 obsługiwane wiersza systemu operacyjnego, aby wyglądały one następujące:

```xml
<!– Windows 10 –>
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
 
- <xref:System.Windows.Forms.ToolStripItem> Sterowanie obsługuje <xref:System.Windows.Automation.AutomationElement.Name> właściwości i [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.NumericUpDown> i <xref:System.Windows.Forms.DomainUpDown> formanty obsługi <xref:System.Windows.Automation.automationElement.Name> właściwości.

**Ulepszone właściwości przeglądania**

Formularze systemu Windows w programie .NET Framework 4.7.1, obejmują:

- Lepsze nawigacji klawiatury przez różne okna wyboru z listy rozwijanej.
- Zmniejszenie niepotrzebnych tabulatorów.
- Lepiej raportowanie typy formantów.
- Ulepszone narrator zachowanie.
 
## <a name="see-also"></a>Zobacz też
[Co to jest nowe w programie .NET Framework](whats-new.md)   
 