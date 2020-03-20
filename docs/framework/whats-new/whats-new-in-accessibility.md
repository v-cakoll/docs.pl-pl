---
title: Co nowego w ułatwieniach dostępu w platformie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 4dbc2024aa2e956b23030ae6eab987e65e006d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400184"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Co nowego w ułatwieniach dostępu w platformie .NET Framework

.NET Framework ma na celu uczynienie aplikacji bardziej dostępnymi dla użytkowników. Funkcje ułatwień dostępu umożliwiają aplikacji zapewnienie użytkownikom technologii ułatwień dostępu odpowiednie środowisko. Począwszy od programu .NET Framework 4.7.1, program .NET Framework zawiera wiele ulepszeń ułatwień dostępu, które umożliwiają deweloperom tworzenie aplikacji dostępnych.

## <a name="accessibility-switches"></a>Przełączniki ułatwień dostępu

Aplikację można skonfigurować tak, aby wybierała funkcje ułatwień dostępu, jeśli jest ona przeznaczona dla platformy .NET Framework 4.7 lub starszej wersji, ale jest uruchomiona w programie .NET Framework 4.7.1 lub nowszym. Można również skonfigurować aplikację do używania starszych funkcji (i nie korzystać z funkcji ułatwień dostępu), jeśli jest ona przeznaczona dla platformy .NET Framework 4.7.1 lub nowszej. Każda wersja programu .NET Framework, która zawiera funkcje ułatwień dostępu [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ma przełącznik [`<runtime>`](../configure-apps/file-schema/runtime/index.md) ułatwień dostępu specyficzne dla wersji, które można dodać do elementu w sekcji pliku konfiguracji aplikacji. Poniżej znajdują się obsługiwane przełączniki:

|Wersja|Przełącznik|
|---|---|
|.NET Framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
| .NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|
| .NET Framework 4.8|"Switch.UseLegacyAccessibilityFeatures.3"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Korzystanie z ulepszeń ułatwień dostępu

Nowe funkcje ułatwień dostępu są domyślnie włączone dla aplikacji docelowych .NET Framework 4.7.1 lub nowszych. Ponadto aplikacje przeznaczone dla starszej wersji programu .NET Framework, ale uruchomione w programie .NET Framework 4.7.1 lub nowszym, mogą zrezygnować ze [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) starszych [`<runtime>`](../configure-apps/file-schema/runtime/index.md) zachowań ułatwień dostępu (a tym `false`samym skorzystać z ulepszeń ułatwień dostępu), dodając przełączniki do elementu w sekcji pliku konfiguracyjnego aplikacji i ustawiając ich wartość na . Poniżej przedstawiono sposób wyrażenia zgody na ulepszenia ułatwień dostępu wprowadzone w systemie .NET Framework 4.7.1:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Jeśli zdecydujesz się wyrazić zgodę na funkcje ułatwień dostępu w nowszej wersji programu .NET Framework, należy również jawnie zdecydować się na funkcje z wcześniejszych wersji programu .NET Framework. Konfigurowanie aplikacji w celu skorzystania z ulepszeń ułatwień dostępu w programie .NET Framework 4.7.1 i 4.7.2 wymaga następującego [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

Konfigurowanie aplikacji w celu skorzystania z ulepszeń ułatwień dostępu w programie .NET Framework 4.7.1, 4.7.2 i 4.8 wymaga następującego [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Przywracanie starszego zachowania

Aplikacje docelowe wersji programu .NET Framework rozpoczynające się od wersji 4.7.1 [`<runtime>`](../configure-apps/file-schema/runtime/index.md) mogą wyłączyć funkcje ułatwień dostępu, `true`dodając przełączniki do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu w sekcji pliku konfiguracyjnego aplikacji i ustawiając ich wartość na . Na przykład następująca konfiguracja rezygnuje z funkcji ułatwień dostępu wprowadzonych w programie .NET Framework 4.7.2:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a>Co nowego w ułatwieniach dostępu w systemie .NET Framework 4.8

Program .NET Framework 4.8 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Forms](#winforms48)

- [Windows Presentation Foundation (WPF)](#wpf48)

- [Projektant przepływu pracy programu Windows Workflow Foundation (WF)](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a>Windows Forms

W programie .NET Framework 4.8 formularze systemu Windows dodaje obsługę LiveRegions i zdarzenia powiadomień do wielu często używanych formantów. Dodaje również obsługę etykietek narzędzi, gdy użytkownik przechodzi do formantu za pomocą klawiatury.

**Obsługa UIA LiveRegions w etykietach i paskach statusowych**

UIA LiveRegions umożliwiają deweloperom aplikacji powiadamianie czytników ekranu o zmianie tekstu w formancie, który znajduje się poza lokalizacją, w której użytkownik pracuje. Jest to przydatne, na <xref:System.Windows.Forms.StatusStrip> przykład dla formantu, który pokazuje stan połączenia. Jeśli połączenie zostanie przerwane, a stan ulegnie zmianie, deweloper może chcieć powiadomić czytnik ekranu.

Począwszy od programu .NET Framework 4.8, formularze systemu <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> Windows implementują UIA LiveRegions dla formantów i formantu. Na przykład następujący kod używa LiveRegion <xref:System.Windows.Forms.Label> w `label1`formancie o nazwie:

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

Narrator ogłasza "Gotowe", niezależnie od tego, gdzie użytkownik wchodzi w interakcję z aplikacją.

Można również zaimplementować <xref:System.Windows.Forms.UserControl> jako LiveRegion:

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

**Zdarzenia powiadomień UIA**

Zdarzenie powiadomienia UIA, wprowadzone w windows 10 Fall Creators Update, umożliwia aplikacji do podniesienia uia zdarzenia, co prowadzi do Narrator po prostu dokonywania anonsu na podstawie tekstu, który dostarczasz ze zdarzeniem, bez konieczności posiadania odpowiedniej kontroli w interfejsie użytkownika. W niektórych scenariuszach jest to prosty sposób, aby znacznie poprawić dostępność aplikacji. W może być również przydatne do powiadamiania o postępie niektórych procesów, które mogą zająć dużo czasu. Aby uzyskać więcej informacji na temat zdarzeń powiadomień uia, zobacz [Czy aplikacja komputerowa może korzystać z nowego zdarzenia powiadomienia o interfejsie użytkownika?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).

Poniższy przykład wywołuje [zdarzenie notification:](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

**Etykietki narzędzi dotyczące dostępu do klawiatury**

W aplikacjach, które są przeznaczone dla platformy .NET Framework 4.7.2 i wcześniejszych wersji, [etykietka narzędzia](xref:System.Windows.Forms.ToolTip) formantu można wyzwolić tylko do wyświetlenia przez przeniesienie wskaźnika myszy do formantu. Począwszy od programu .NET Framework 4.8, użytkownik klawiatury może wyzwolić etykietkę narzędzia formantu, koncentrując formant za pomocą klawisza Tab lub klawiszy strzałek z klawiszami modyfikuj lub bez. To szczególne ulepszenie ułatwień dostępu wymaga dodatkowego [przełącznika AppContext:](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

Na poniższej ilustracji przedstawiono etykietkę narzędzia, gdy użytkownik wybrał przycisk z klawiaturą.

![Zrzut ekranu przedstawiający etykietkę narzędzia, gdy użytkownik przechodzi do przycisku za pomocą klawiatury.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Począwszy od programu .NET Framework 4.8, WPF WPF zawiera szereg ulepszeń ułatwień dostępu.

**Narratory ekranów nie ogłaszają już elementów o widoczności Zwiniętej lub Ukrytej**

Elementy o zwiniętej lub ukrytej widoczności nie są już ogłaszane przez czytnik ekranu. Interfejsy użytkownika, które zawierają <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> elementy <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> o widoczności lub mogą być błędnie przedstawione przez czytniki ekranu, jeśli zostaną ogłoszone użytkownikowi. Począwszy od .NET Framework 4.8, WPF WPF nie zawiera już zwinięte lub ukryte elementy w widoku sterowania drzewa UIAutomation, więc czytniki ekranu nie mogą już ogłaszać tych elementów.

**Właściwość SelectionTextBrush do użytku z zaznaczeniem tekstu nienapartym na Adornerze**

W .NET Framework 4.7.2 WPF WPF <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> dodał możliwość rysowania i zaznaczania tekstu bez użycia warstwy Adorner. Kolor pierwszego planu zaznaczonego tekstu w tym scenariuszu był podyktowany programem <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.

.NET Framework 4.8 dodaje `SelectionTextBrush`nową właściwość, która umożliwia deweloperom zaznaczenie określonego pędzla dla zaznaczonego tekstu podczas korzystania z zaznaczenia tekstu opartego na adornerze. Ta właściwość <xref:System.Windows.Controls.Primitives.TextBoxBase>działa tylko na <xref:System.Windows.Controls.PasswordBox> formanty pochodne i formantu w aplikacjach WPF z nie-Adorner oparte na zaznaczeniu tekstu włączone. Nie działa na <xref:System.Windows.Controls.RichTextBox> formancie. Jeśli nie oparte na Adorner wybór tekstu nie jest włączona, ta właściwość jest ignorowana.

Aby użyć tej właściwości, wystarczy dodać go do kodu XAML i użyć odpowiedniego pędzla lub powiązania. Wynikowy wybór tekstu wygląda następująco:

![Zrzut ekranu przedstawiający aplikację z wybranymi słowami Hello World.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

Można połączyć użycie `SelectionBrush` właściwości `SelectionTextBrush` i do generowania dowolnej kombinacji kolorów tła i pierwszego planu, które uważasz za stosowne.

**Obsługa kontrolera uiautomationfor właściwości**

UIAutomation's `ControllerFor` właściwość zwraca tablicę elementów automatyzacji, które są manipulowane przez element automatyzacji, który obsługuje tę właściwość. Ta właściwość jest często używana dla funkcji autoprosić dostępności. `ControllerFor`jest używany, gdy element automatyzacji wpływa na jeden lub więcej segmentów interfejsu użytkownika aplikacji lub pulpitu. W przeciwnym razie trudno jest skojarzyć wpływ operacji sterowania z elementami interfejsu użytkownika. Ta funkcja dodaje możliwość formanty, `ControllerFor` aby zapewnić wartość dla właściwości.

Program .NET Framework 4.8 dodaje <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>nową metodę wirtualną, . Aby zapewnić wartość `ControllerFor` właściwości, po prostu zastąpić tę `List<AutomationPeer>` metodę i zwrócić formanty manipulowane przez to: <xref:System.Windows.Automation.Peers.AutomationPeer>

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

**Etykietki narzędzi dotyczące dostępu do klawiatury**

W .NET Framework 4.7.2 i wcześniejszych wersjach etykietki narzędzi są wyświetlane tylko wtedy, gdy użytkownik najedzie kursorem myszy nad formantem. W programie .NET Framework 4.8 etykietki narzędzi są również wyświetlane na ostrości klawiatury, a także za pomocą skrótu klawiaturowego.

Aby włączyć tę funkcję, aplikacja musi kierować .NET Framework 4.8 lub wyrazić zgodę przy użyciu przełączników `Switch.UseLegacyAccessibilityFeatures.3` i `Switch.UseLegacyToolTipDisplay` [AppContext.](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) Poniżej przedstawiono przykładowy plik konfiguracyjny aplikacji:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

Po włączeniu wszystkie formanty zawierające etykietkę narzędzia wyświetlają ją po odebraniu fokusu za pomocą klawiatury. Etykietka narzędzia może być odrzucona w czasie lub po zmianie ostrości klawiatury. Użytkownicy mogą również ręcznie odrzucić etykietkę narzędzia za pomocą nowego skrótu klawiaturowego Ctrl + Shift + F10. Po odrzuceniu etykietki narzędzia można ją ponownie wyświetlić za pomocą tego samego skrótu klawiaturowego.

> [!NOTE]
> [Etykietki narzędzi wstążki](xref:System.Windows.Controls.Ribbon.RibbonToolTip) na <xref:System.Windows.Controls.Ribbon.Ribbon> formanty nie będą wyświetlane na fokusie klawiatury; wyświetlane są tylko za pomocą skrótu klawiaturowego.

**Dodano obsługę właściwości SizeOfSet i PositionInSet UIAutomation**

System Windows 10 wprowadził dwie nowe właściwości `SizeOfSet` `PositionInSet`UIAutomation i , które są używane przez aplikacje do opisywania liczby elementów w zestawie. UIAutomation aplikacji klienckich, takich jak czytniki ekranu można następnie kwerendy aplikacji dla tych właściwości i ogłosić dokładną reprezentację interfejsu użytkownika aplikacji.

Począwszy od .NET Framework 4.8, WPF WPF udostępnia te dwie właściwości do UIAutomation w aplikacjach WPF. Można to osiągnąć na dwa sposoby:

- Za pomocą właściwości zależności.

  WPF WPF dodaje dwie <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> nowe <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>właściwości zależności i . Deweloper może użyć XAML, aby ustawić swoje wartości:

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- Przez zastąpienie AutomationPeer metod wirtualnych.

  I <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> wirtualne metody zostały dodane do AutomationPeer klasy. Deweloper może podać `SizeOfSet` wartości `PositionInSet` dla i przez zastąpienie tych metod, jak pokazano w poniższym przykładzie:

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

Ponadto elementy w <xref:System.Windows.Controls.ItemsControl> wystąpieniach zapewniają wartość dla tych właściwości automatycznie bez dodatkowych działań od dewelopera. Jeśli <xref:System.Windows.Controls.ItemsControl> jest zgrupowane, kolekcja grup jest reprezentowana jako zestaw, a każda grupa jest liczona jako oddzielny zestaw, z każdego elementu wewnątrz tej grupy, zapewniając swoją pozycję wewnątrz tej grupy, jak również rozmiar grupy. Wirtualizacja nie ma wpływu na wartości automatyczne. Nawet jeśli element nie jest realizowany, nadal jest wliczany do całkowitego rozmiaru zestawu i wpływa na pozycję w zestawie jego elementów równorzędnych.

Wartości automatyczne są dostarczane tylko wtedy, gdy obiekt docelowy aplikacji .NET Framework 4.8. W przypadku aplikacji przeznaczonych dla starszej wersji programu `Switch.UseLegacyAccessibilityFeatures.3` .NET Framework można ustawić [przełącznik AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak pokazano w następującym pliku App.config:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Projektant przepływu pracy programu Windows Workflow Foundation (WF)

Projektant przepływu pracy zawiera następujące zmiany w programie .NET Framework 4.8:

- Użytkownicy korzystający z Narratora zobaczą ulepszenia w etykietach przypadków FlowSwitch.

- Użytkownicy korzystający z Narratora zobaczą ulepszenia w opisach przycisków.

- Użytkownicy, którzy wybiorą motywy o wysokim kontraście, zobaczą ulepszenia w widoczności projektanta przepływu pracy i jego formantów, takie jak lepsze współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używane dla elementów fokusu.

Jeśli aplikacja jest przeznaczona dla platformy .NET Framework 4.7.2 lub `Switch.UseLegacyAccessibilityFeatures.3` wcześniejszej wersji, `false` można zdecydować się na te zmiany, ustawiając [przełącznik AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w pliku konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [korzystanie z ulepszeń ułatwień dostępu](#taking-advantage-of-accessibility-enhancements) w tym artykule.

## <a name="whats-new-in-accessibility-in-net-framework-472"></a>Co nowego w ułatwieniach dostępu w systemie .NET Framework 4.7.2

Program .NET Framework 4.7.2 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a>Windows Forms

**Kolory zdefiniowane w systemach operacyjnych w motywach o wysokim kontraście**

Począwszy od programu .NET Framework 4.7.2, windows forms używa kolorów zdefiniowanych przez system operacyjny w motywach o wysokim kontraście. Dotyczy to następujących kontrolek:

- Strzałka rozwijana formantu. <xref:System.Windows.Forms.ToolStripDropDownButton>

- Elementy <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.RadioButton> , <xref:System.Windows.Forms.CheckBox> i <xref:System.Windows.Forms.ButtonBase.FlatStyle> formanty z ustawionym <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub . <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> Wcześniej zaznaczone kolory tekstu i tła nie kontrastowały i były trudne do odczytania.

- Formanty zawarte <xref:System.Windows.Forms.GroupBox> w <xref:System.Windows.Forms.Control.Enabled> a, `false`który ma swoją właściwość ustawioną na .

- Elementy <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripDropDownButton> i elementy sterujące, które mają zwiększony współczynnik kontrastu jasności w trybie wysokiego kontrastu.

- Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> obiektu <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Ulepszenia Narratora**

Począwszy od programu .NET Framework 4.7.2, obsługa Narratora jest rozszerzona w następujący sposób:

- Ogłasza wartość nieruchomości <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> przy ogłaszaniu tekstu . <xref:System.Windows.Forms.ToolStripMenuItem>

- Wskazuje, kiedy <xref:System.Windows.Forms.ToolStripMenuItem> ma <xref:System.Windows.Forms.Control.Enabled> ustawioną `false`właściwość na .

- Przekazuje opinię na temat stanu pola <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> wyboru, gdy `true`właściwość jest ustawiona na .

- Kolejność ustawiania fokusu trybu skanowania narratora jest zgodna z kolejnością wizualną formantów w oknie dialogowym pobierania ClickOnce.

**Ulepszenia DataGridView**

Począwszy od programu .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> formant wprowadził następujące ulepszenia ułatwień dostępu:

- Wiersze można sortować za pomocą klawiatury. Użytkownik może użyć klawisza F3 w celu sortowania według bieżącej kolumny.

- Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, nagłówek kolumny zmienia kolor, aby wskazać bieżącą kolumnę jako kartę użytkownika w komórkach w bieżącym wierszu.

- Właściwość <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> zwraca <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> prawidłową kontrolkę nadrzędną.

**Ulepszone wskazówki wizualne**

- I <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> formanty <xref:System.Windows.Forms.ButtonBase.Text> z pustą właściwością wyświetlają wskaźnik ostrości po otrzymaniu fokusu.

**Ulepszona obsługa siatki właściwości**

- Elementy <xref:System.Windows.Forms.PropertyGrid> podrzędne formantu teraz zwraca `true` dla <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> właściwości tylko wtedy, gdy PropertyGrid element jest włączona.

- Elementy <xref:System.Windows.Forms.PropertyGrid> podrzędne formantu zwracają `false` dla <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> właściwości tylko wtedy, gdy PropertyGrid element może być zmieniony przez użytkownika.

**Ulepszona nawigacja za pomocą klawiatury**

- Formant <xref:System.Windows.Forms.ToolStripButton> umożliwia ustawianie ostrości, gdy znajduje się w obrębie <xref:System.Windows.Forms.ToolStripPanel> właściwości ustawionej na <xref:System.Windows.Forms.ToolStripPanel.TabStop>`true`

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Zmiany w formancie CheckBox i RadioButton**

W .NET Framework 4.7.1 i wcześniejszych <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> wersjach WPF I formanty mają niespójne i w klasycznych i kontrastu motywy niepoprawne wizualizacje fokusu.  Te problemy występują w przypadkach, gdy formanty nie mają żadnych zestaw zawartości.  Może to sprawić, że przejście między motywami jest mylące, a wizualizacja ostrości jest trudna do zobaczenia.

W programie .NET Framework 4.7.2 te wizualizacje są teraz bardziej spójne w różnych motywach i są łatwiej widoczne w motywach klasycznych i kontrastowych.

**Formanty WinForms hostowane w aplikacji WPF**

W przypadku formantu WinForms hostowanego w aplikacji WPF w systemie .NET Framework 4.7.1 i wcześniejszych wersjach użytkownicy nie mogą <xref:System.Windows.Forms.Integration.ElementHost> wyjmować karty z warstwy WinForms, jeśli pierwszym lub ostatnim formantem w tej warstwie jest formant WPF. W .NET Framework 4.7.2 użytkownicy mogą teraz wyjmować kartę z warstwy WinForms.

Jednak zautomatyzowane aplikacje, które opierają się na fokus nigdy nie ucieczki warstwy WinForms może nie działać zgodnie z oczekiwaniami.

## <a name="whats-new-in-accessibility-in-net-framework-471"></a>Co nowego w ułatwieniach dostępu w systemie .NET Framework 4.7.1

Program .NET Framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [ASP.NET kontrolki sieci Web](#aspnet471)

- [Narzędzia zestawu SDK platformy .NET](#tools471)

- [Projektant przepływu pracy programu Windows Workflow Foundation (WF)](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ulepszenia czytnika ekranu**

Jeśli ulepszenia ułatwień dostępu są włączone, program .NET Framework 4.7.1 zawiera następujące ulepszenia, które mają wpływ na czytniki ekranu:

- W .NET Framework 4.7 <xref:System.Windows.Controls.Expander> i wcześniejszych wersjach formanty zostały ogłoszone przez czytniki ekranu jako przyciski. Począwszy od programu .NET Framework 4.7.1, są one poprawnie ogłaszane jako rozwijalne/zwijane grupy.

- W .NET Framework 4.7 <xref:System.Windows.Controls.DataGridCell> i wcześniejszych wersjach formanty zostały ogłoszone przez czytniki ekranu jako "niestandardowe". Począwszy od programu .NET Framework 4.7.1, są one teraz poprawnie ogłoszone jako komórki siatki danych (zlokalizowane).

- Począwszy od programu .NET Framework 4.7.1, czytniki ekranu ogłaszają nazwę edytowalnej <xref:System.Windows.Controls.ComboBox>.

- W .NET Framework 4.7 <xref:System.Windows.Controls.PasswordBox> i wcześniejszych wersjach formanty zostały ogłoszone jako "nie element w widoku" lub miał w inny sposób niepoprawne zachowanie. Ten problem został rozwiązany, począwszy od programu .NET Framework 4.7.1.

**Pomoc techniczna usługi UIAutomation LiveRegion**

Czytniki ekranu, takie jak Narrator, pomagają osobom odczytać zawartość interfejsu użytkownika aplikacji, zwykle przez wyjście tekstowe na mowę zawartości interfejsu użytkownika, która ma fokus. Jednak jeśli element interfejsu użytkownika zmienia się i nie ma fokusu, użytkownik może nie zostać powiadomiony i może przegapić ważne informacje. Regiony na żywo mają na celu rozwiązanie tego problemu. Deweloper może ich używać do informowania czytnika ekranu lub innego klienta UIAutomation, że wprowadzono ważną zmianę w elemencie interfejsu użytkownika. Czytnik ekranu może następnie zdecydować, jak i kiedy poinformować użytkownika o tej zmianie.

Aby obsługiwać aktywne regiony, do WPF WPF dodano następujące interfejsy API:

- I <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pola, które identyfikują **LiveSetting** właściwości i **LiveRegionChanged** zdarzenia. Można je ustawić za pomocą xaml.

- Właściwość **AutomationProperties.LiveSetting** dołączone, która informuje czytnik ekranu o ważności zmiany interfejsu użytkownika.

- Właściwość, <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> która identyfikuje **AutomationProperties.LiveSetting** dołączone właściwości.

- Metoda, <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> która może zostać zastąpiona w celu zapewnienia wartości **LiveSetting.**

- I <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, które uzyskać i ustawić **livesetting** wartość.

- Wyliczenie, <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> które definiuje następujące możliwe wartości **LiveSetting:**

  - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Element nie wysyła powiadomień, jeśli zawartość regionu na żywo uległa zmianie.
  - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Element wysyła powiadomienia nie przerywane, jeśli zawartość regionu na żywo uległa zmianie.

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Element wysyła powiadomienia przerywane, jeśli zawartość regionu na żywo uległa zmianie.

LiveRegion można utworzyć, ustawiając **automationproperties.LiveSetting** właściwości na element zainteresowania, jak pokazano w poniższym przykładzie:

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Gdy dane w regionie na żywo zmienią się i musisz poinformować czytnik ekranu, jawnie należy wywołać zdarzenie, jak pokazano w poniższym przykładzie.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Wysoki kontrast**

Począwszy od .NET Framework 4.7.1, ulepszenia w wysokim kontraście zostały wprowadzone do różnych formantów WPF. Są one teraz widoczne, gdy <xref:System.Windows.SystemParameters.HighContrast%2A> motyw jest ustawiony. Należą do nich:

- <xref:System.Windows.Controls.Expander>Kontroli

  Wizualizacja fokusu <xref:System.Windows.Controls.Expander> dla formantu jest teraz widoczna. Widoczne są również <xref:System.Windows.Controls.ComboBox><xref:System.Windows.Controls.ListBox>wizualizacje <xref:System.Windows.Controls.RadioButton> klawiatury dla , i formanty. Przykład:

  Przed:

  ![Zrzut ekranu przedstawiający formant ekspandera z ostrości i bez wizualnej ostrości.](./media/whats-new-in-accessibility/expander-control-before.png)

  Po:

  ![Zrzut ekranu przedstawiający formant expandera z fokusem przedstawiający linię kropkowane wokół tekstu formantu.](./media/whats-new-in-accessibility/expander-control-after.png)

- <xref:System.Windows.Controls.CheckBox>i <xref:System.Windows.Controls.RadioButton> kontroli

  Tekst w <xref:System.Windows.Controls.CheckBox> formanty i <xref:System.Windows.Controls.RadioButton> jest teraz łatwiej widoczne, gdy zaznaczone w motywach o wysokim kontraście. Przykład:

  Przed:

  ![Zrzut ekranu przedstawiający przyciski radiowe i kontrolne ze słabą widocznością tekstu w motywach o wysokim kontraście.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  Po:

  ![Zrzut ekranu przedstawiający przyciski radiowe i kontrolne z lepszą widocznością tekstu w motywach o wysokim kontraście.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox>Kontroli

  Począwszy od programu .NET Framework 4.7.1 obramowanie wyłączonego <xref:System.Windows.Controls.ComboBox> formantu jest tym samym kolorem co wyłączony tekst. Przykład:

  Przed:

  ![Zrzut ekranu przedstawiający wyłączone pole kombi z tekstem obramowania i kontroli w różnych kolorach.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  Po:

  ![Zrzut ekranu przedstawiający wyłączone pole kombi z obramowaniem w tym samym kolorze co tekst formantu.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  Ponadto wyłączone i skoncentrowane przyciski używają prawidłowego koloru motywu.

  Przed:

  ![Zrzut ekranu przedstawiający czarny przycisk z szarym tekstem z napisem Focus Me.](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  Po:

  ![Zrzut ekranu przedstawiający niebieski przycisk z czarnym tekstem z napisem Focus Me.](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  Na koniec w .NET Framework 4.7 i <xref:System.Windows.Controls.ComboBox> wcześniejszych wersjach `Toolbar.ComboBoxStyleKey` ustawienie stylu formantu spowodowało, że strzałka listy rozwijanej jest niewidoczna. Ten problem został rozwiązany, począwszy od programu .NET Framework 4.7.1. Przykład:

  Przed:

  ![Zrzut ekranu przedstawiający kontrolkę ComboBox z niewidoczną strzałką rozwijaną.](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  Po:

  ![Zrzut ekranu przedstawiający kontrolkę ComBoxBox, wyświetlającą strzałkę rozwijaną.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <xref:System.Windows.Controls.DataGrid>Kontroli

  Począwszy od programu .NET Framework 4.7.1, strzałka wskaźnika sortowania w <xref:System.Windows.Controls.DataGrid> formantach używa teraz poprawnych kolorów motywu. Przykład:

  Przed:

  ![Zrzut ekranu przedstawiający strzałkę wskaźnika sortowania przed ulepszeniami.](./media/whats-new-in-accessibility/sort-indicator-before.png)

  Po:

  ![Zrzut ekranu przedstawiający strzałkę wskaźnika sortowania po ulepszeniach.](./media/whats-new-in-accessibility/sort-indicator-after.png)

  Ponadto w programie .NET Framework 4.7 i wcześniejszych wersjach domyślny styl łącza został zmieniony na niepoprawny kolor myszy na myszy w trybach wysokiego kontrastu. To jest rozwiązane począwszy od .NET Framework 4.7.1. Podobnie kolumny <xref:System.Windows.Controls.DataGrid> pola wyboru używa oczekiwanych kolorów dla opinii fokus klawiatury, począwszy od .NET Framework 4.7.1.

  Przed:

  ![Zrzut ekranu z linkiem z napisem Kliknij mnie! na czerwono.](./media/whats-new-in-accessibility/default-link-style-before.png)

  Po:

  ![Zrzut ekranu z linkiem z napisem Kliknij mnie! w kolorze żółtym.](./media/whats-new-in-accessibility/default-link-style-after.png)

Aby uzyskać więcej informacji na temat ulepszeń ułatwień dostępu WPF w programie .NET Framework 4.7.1, zobacz [ulepszenia ułatwień dostępu w programie WPF.](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a>Ulepszenia ułatwień dostępu formularzy systemu Windows

W programie .NET Framework 4.7.1 formularze systemu Windows (WinForms) zawierają zmiany ułatwień dostępu w następujących obszarach.

**Ulepszony wyświetlacz w trybie wysokiego kontrastu**

Począwszy od programu .NET Framework 4.7.1, różne formanty WinForms oferują ulepszone renderowanie w trybach HighContrast dostępnych w systemie operacyjnym. System Windows 10 zmienił wartości niektórych kolorów systemu o wysokim kontraście, a formularze systemu Windows są oparte na platformie Windows 10 Win32. Aby uzyskać najlepsze wrażenia, uruchom w najnowszej wersji systemu Windows i zdecyduj się na najnowsze zmiany systemu operacyjnego, dodając plik app.manifest w aplikacji testowej i odkomentuj obsługiwany system operacyjny systemu Windows 10, aby wyglądał następująco:

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

Oto kilka przykładów zmian o wysokim kontraście:

- Znaczniki wyboru <xref:System.Windows.Forms.MenuStrip> w elementach są łatwiejsze do wyświetlenia.

- Po wybraniu <xref:System.Windows.Forms.MenuStrip> tej opcji wyłączone elementy są łatwiejsze do wyświetlenia.

- Tekst w <xref:System.Windows.Forms.Button> zaznaczonym formancie kontrastuje z kolorem zaznaczenia.

- Wyłączony tekst jest łatwiejszy do odczytania. Przykład:

  Przed:

  ![Zrzut ekranu przedstawiający aplikację, która używa różnych formantów uruchomionych w trybie wysokiego kontrastu przed ulepszeniami ułatwień dostępu.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  Po:

  ![Zrzut ekranu przedstawiający aplikację, która używa różnych formantów działających w trybie wysokiego kontrastu po ulepszeniach ułatwień dostępu.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- Ulepszenia wysokiego kontrastu w oknie dialogowym wyjątków wątku.

**Ulepszona obsługa Narratora**

Formularze systemu Windows w programie .NET Framework 4.7.1 zawierają następujące ulepszenia ułatwień dostępu dla Narratora:

- Formant <xref:System.Windows.Forms.MonthCalendar> jest dostępny dla Narratora, a także przez inne narzędzia automatyzacji interfejsu użytkownika.

- Formant <xref:System.Windows.Forms.CheckedListBox> powiadamia Narratora, gdy stan sprawdzania elementu został zmieniony, więc użytkownik jest powiadamiany, że zmienił wartość elementu listy.

- Formant <xref:System.Windows.Forms.DataGridViewCell> zgłasza narratorowi poprawny stan tylko do odczytu.

- Narrator może teraz <xref:System.Windows.Forms.ToolStripMenuItem> odczytywać wyłączony tekst, podczas gdy wcześniej pomijał wyłączone elementy menu.

**Ulepszona obsługa wzorców ułatwień dostępu do interfejsu użytkownika**

Począwszy od programu .NET Framework 4.7.1, deweloperzy narzędzi technologii ułatwień dostępu mogą korzystać z typowych wzorców ułatwień dostępu interfejsu API i właściwości dla kilku formantów WinForms. Te ulepszenia ułatwień dostępu obejmują:

- I <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStripSplitButton> teraz obsługuje [rozwiń / zwiń wzorzec](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- Teraz <xref:System.Windows.Forms.DataGridViewCheckBoxCell> obsługuje [wzorzec przełącznika](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).

- Formant <xref:System.Windows.Forms.ToolStripItem> obsługuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwość i [wzorzec rozwiń/zwijania](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- I <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> kontroli obsługi <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości.

**Ulepszone środowisko przeglądarki właściwości**

Począwszy od programu .NET Framework 4.7.1, formularze systemu Windows obejmują:

- Lepsza nawigacja za pomocą klawiatury przez różne okna wyboru rozwijanej.
- Redukcja niepotrzebnych tabulatorów.
- Lepsze raportowanie typów kontroli.
- Poprawiono zachowanie narratora.

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a>ASP.NET kontrolki sieci Web

Począwszy od platformy .NET Framework 4.7.1 i programu Visual Studio 2017 w wersji 15.3, ASP.NET poprawia sposób pracy formantów sieci Web ASP.NET z technologią ułatwień dostępu w programie Visual Studio. Zmiany są następujące:

- Zmiany implementujące brakujące wzorce ułatwień dostępu interfejsu użytkownika w formantych, takie jak okno dialogowe **Dodawanie pola** w kreatorze **widoku szczegółów** lub okno dialogowe **Konfigurowanie widoku listy** **kreatora ListView.**

- Zmiany w celu poprawy wyświetlania w trybie wysokiego kontrastu, takie jak **Edytor pól pagera danych**.

- Zmiany ułatwiające nawigację za pomocą klawiatury dla kontrolek, takie jak okno dialogowe **Pola** w kreatorze **Edytowanie pól pagera** formantu DataPager, okno dialogowe **Konfigurowanie obiektuContext** lub Okno dialogowe **Konfigurowanie wyboru danych** **kreatora Konfigurowanie źródła danych.**

<a name="tools471"></a>

### <a name="net-sdk-tools"></a>Narzędzia zestawu SDK platformy .NET

[Narzędzie Edytor konfiguracji (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) i Narzędzie Podgląd śledzenia usług [(SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) zostały ulepszone przez naprawienie różnych problemów z dostępnością. Większość z nich były małe problemy, takie jak nazwa nie jest zdefiniowana lub niektórych wzorców automatyzacji interfejsu użytkownika nie są implementowane poprawnie. Podczas gdy wielu użytkowników nie będzie świadomych tych niepoprawnych wartości, klienci korzystający z technologii wspomagających, takich jak czytniki ekranu, znajdą te narzędzia zestawu SDK bardziej dostępne.

Te ulepszenia zmieniają niektóre poprzednie zachowania, takie jak kolejność fokusu klawiatury.

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Projektant przepływu pracy programu Windows Workflow Foundation (WF)

Zmiany ułatwień dostępu w Projektancie przepływu pracy są następujące:

- Kolejność kart zmienia się na lewo do prawej i od góry do dołu w niektórych formantach:

  - Okno korelacji inicjowania ustawiania danych <xref:System.ServiceModel.Activities.InitializeCorrelation> korelacji dla działania.

  - Okno definicji zawartości <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send>dla <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply> , i działań.

- Więcej funkcji jest dostępnych za pośrednictwem klawiatury:

  - Podczas edytowania właściwości działania grupy właściwości mogą być zwinięte za pomocą klawiatury przy pierwszym skupieniu.

  - Ikony ostrzeżeń są dostępne za pomocą klawiatury.

  - Przycisk **Więcej właściwości** w oknie **Właściwości** jest dostępny za pomocą klawiatury.

  - Użytkownicy klawiatury mogą uzyskiwać dostęp do elementów nagłówka w okienkach **Argumenty** i **zmienne** Projektanta przepływu pracy.

- Lepsza widoczność elementów z ostrością, na przykład kiedy:

  - Dodawanie wierszy do siatek danych używanych przez projektanta przepływu pracy i projektantów działań.

  - Tabbing przez pola <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> w i działań.

  - Ustawianie wartości domyślnych dla zmiennych lub argumentów

- Czytniki ekranu mogą teraz poprawnie rozpoznawać:

  - Punkty przerwania ustawione w projektancie przepływu pracy.

  - , <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowDecision>i <xref:System.ServiceModel.Activities.CorrelationScope> działań.
  - Zawartość <xref:System.ServiceModel.Activities.Receive> działania.

  - Typ docelowy <xref:System.Activities.Statements.InvokeMethod> dla działania.

  - Pole kombi Wyjątek i Finally <xref:System.Activities.Statements.TryCatch> sekcji w działaniu.

  - Pole kombi Typ wiadomości, rozdzielacz w oknie Dodaj inicjatory korelacji, okno Definicja zawartości i Okno Skoreluje definicję w działaniach obsługi<xref:System.ServiceModel.Activities.Receive>wiadomości ( , <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>).

  - Przejścia maszyny stanu i przejścia miejsc docelowych.

  - Adnotacje i łączniki dotyczące <xref:System.Activities.Statements.FlowDecision> działań.

  - Menu kontekstu (kliknięcie prawym przyciskiem myszy) dla działań.

  - Edytory wartości właściwości, przycisk Wyczyść wyszukiwanie, przyciski według kategorii i sortowania alfabetycznego oraz okno dialogowe Edytor wyrażeń w siatce właściwości.

  - Procent powiększenia w Projektancie przepływu pracy.

  - Separator <xref:System.Activities.Statements.Parallel> i <xref:System.Activities.Statements.Pick> działania.

  - Działanie. <xref:System.Activities.Statements.InvokeDelegate>

  - Okno Wybierz typy dla działań słownikowych (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`itp.).

  - Okno Przeglądaj i wybierz typ .NET.

  - Breadcrumbs w Projektancie przepływu pracy.

- Użytkownicy, którzy wybiorą motywy o wysokim kontraście, zobaczą wiele ulepszeń w widoczności projektanta przepływu pracy i jego formantów, takich jak lepsze współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używane dla elementów fokusu.

## <a name="see-also"></a>Zobacz też

- [Co nowego w programie .NET Framework](index.md)
