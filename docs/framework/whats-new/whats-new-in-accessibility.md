---
title: What's new in ułatwień dostępu w programie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afd4b77529f64852e77926b7fecc0e15033e7735
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979982"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>What's new in ułatwień dostępu w programie .NET Framework

Celem jest udostępnienie aplikacji dla użytkowników programu .NET Framework. Funkcje ułatwień dostępu, Zezwalaj na aplikację zapewnić odpowiednie środowisko dla użytkowników technologii pomocniczej. Począwszy od .NET Framework 4.7.1 .NET Framework zawiera dużą liczbę ulepszenia ułatwień dostępu, które umożliwiają deweloperom tworzyć aplikacje dostępne.

## <a name="accessibility-switches"></a>Przełączniki ułatwień dostępu

Można skonfigurować aplikację, aby skorzystać z funkcji ułatwień dostępu, jeśli jest przeznaczony dla .NET Framework 4.7 lub starszej wersji, ale działa w programie .NET Framework 4.7.1 lub nowszej. Możesz także skonfigurować aplikację do używania starszych funkcji (i nie korzystaj z funkcji ułatwień dostępu), jeśli jest ono przeznaczone dla platformy .NET Framework 4.7.1 lub nowszej. Każda wersja programu .NET Framework, która obejmuje funkcje ułatwień dostępu ma przełącznika ułatwień dostępu specyficzny dla wersji, możesz dodać do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji z pliku konfiguracji aplikacji. Obsługiwane przełączniki są następujące:

|Wersja|Przełącznik|
|---|---|
|.NET Framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|.NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|
|.NET Framework 4.8|"Switch.UseLegacyAccessibilityFeatures.3"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Korzystając z zalet udoskonalonym ułatwieniom dostępu

Nowe funkcje ułatwień dostępu są włączone domyślnie dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszy. Ponadto aplikacje, które kątem starszej wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.7.1 lub później zdecydować się poza zachowania dostępności starszej wersji (i ten sposób korzystać z zalet ulepszenia ułatwień dostępu), dodając przełączników do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) części pliku konfiguracyjnego aplikacji i ich wartości `false`. Poniżej przedstawiono sposób korzystania z opcji w celu ulepszenia ułatwień dostępu, wprowadzone w programie .NET Framework 4.7.1:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Jeśli zdecydujesz się zgadzaj się na funkcje ułatwień dostępu w nowszej wersji programu .NET Framework, musi również jawnie zgody na uczestnictwo w funkcje z wcześniejszych wersji programu .NET Framework. Konfigurowanie aplikacji w taki sposób, aby wykorzystać ulepszenia ułatwień dostępu w systemie zarówno .NET Framework 4.7.1 i 4.7.2 wymaga następujących [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

Konfigurowanie aplikacji w taki sposób, aby wykorzystać ulepszenia ułatwień dostępu w programie .NET Framework 4.7.1 4.7.2 i 4.8 wymaga następujących [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Przywracanie starsze zachowanie

Aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od 4.7.1 można wyłączyć funkcje ułatwień dostępu, dodając przełączniki [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji plik konfiguracji aplikacji i ich wartości `true`. Na przykład następująca konfiguracja oznacza brak zgody na funkcje ułatwień dostępu, które wprowadzono w programie .NET Framework 4.7.2:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a>What's new in ułatwień dostępu w programie .NET Framework 4.8

.NET framework 4.8 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Forms](#winforms48)

- [Windows Presentation Foundation (WPF)](#wpf48)

- [Projektant przepływu pracy Windows Workflow Foundation (WF)](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a>Windows Forms

W .NET Framework 4,8 Windows Forms dodaje obsługę LiveRegions i zdarzenia powiadomień do wielu najczęściej używane kontrolki. Dodaje również obsługę dla etykietki narzędzi, gdy użytkownik przechodzi do formantu za pomocą klawiatury.

**Obsługa LiveRegions automatyzacji interfejsu użytkownika w etykiety i StatusStrip**

LiveRegions automatyzacji interfejsu użytkownika umożliwiają deweloperom aplikacji do powiadamiania czytniki zawartości ekranu zmiany tekstu w kontrolce, która znajduje się niezależnie od lokalizacji, w którym pracuje użytkownik. Jest to przydatne, na przykład w przypadku <xref:System.Windows.Forms.StatusStrip> kontrolka, która pokazuje stan połączenia. Jeśli połączenie zostanie porzucone, a zmiany stanu, deweloper może chcieć Powiadom czytnika zawartości ekranu.

Począwszy od programu .NET Framework 4.8 formularze Windows implementuje LiveRegions automatyzacji interfejsu użytkownika dla obu <xref:System.Windows.Forms.Label> i <xref:System.Windows.Forms.StatusStrip> kontrolki. Na przykład w poniższym kodzie użyto LiveRegion w <xref:System.Windows.Forms.Label> formantu o nazwie `label1`:

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

Narrator ogłasza "Gotowe", niezależnie od tego, gdzie użytkownik prowadzi interakcję z aplikacją.

Możesz również wdrożyć swoje <xref:System.Windows.Forms.UserControl> jako LiveRegion:

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

**Zdarzenia powiadomień automatyzacji interfejsu użytkownika**

Zdarzenia powiadomień automatyzacji interfejsu użytkownika, wprowadzone w programie Windows 10 Fall Creators Update umożliwia wywoływanie zdarzeń automatyzacji interfejsu użytkownika, który prowadzi do Narrator, po prostu co anons, na podstawie tekstu podać ze zdarzeniem, bez konieczności posiadania odpowiednią kontrolować w interfejsie użytkownika aplikacji. W niektórych przypadkach jest to prosty sposób znacznie zwiększyć dostępność aplikacji. W również może być przydatne do powiadomienia o postępie niektóre procesy, które może zająć dużo czasu. Aby uzyskać więcej informacji na temat zdarzenia powiadomień automatyzacji interfejsu użytkownika, zobacz [aplikację klasyczną mogą korzystać z nowego zdarzenia powiadomień interfejsu użytkownika?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).

Poniższy przykład wywołuje [zdarzenie powiadomienia](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

**Etykietki narzędzi na dostęp za pomocą klawiatury**

W aplikacjach przeznaczonych dla środowiska .NET Framework 4.7.2 i wcześniejszymi wersjami, formant [etykietki narzędzia](xref:System.Windows.Forms.ToolTip) tylko można wyzwolić do pop się przesuwając wskaźnik myszy w formancie. Począwszy od programu .NET Framework 4.8 użytkownika klawiatury może wyzwalać formantu etykietki narzędzia, koncentrując się kontrolka, za pomocą klawisza Tab lub klawisze strzałek z lub bez klawisze modyfikujące. To ulepszenie ułatwień dostępu w szczególności wiąże się z dodatkowymi [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):

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

Na poniższej ilustracji przedstawiono etykietkę narzędzia, gdy użytkownik wybrał przycisk za pomocą klawiatury.

![Etykietka narzędzia, gdy użytkownik przechodzi do przycisku za pomocą klawiatury](media/tooltip.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Począwszy od programu .NET Framework 4.8 WPF zawiera szereg ulepszeń w ułatwienia dostępu.

**Narrators ekranu nie są już ogłaszamy elementów o widoczności zwinięte lub ukryte**

Elementy o widoczności zwinięty czy ukryty już nie są anonsowane przez czytnik zawartości ekranu. Interfejsy użytkownika, które zawierać elementów o widoczność <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> lub <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> może być podawanie fałszywych informacji przez czytniki zawartości ekranu w przypadku ich obsłudze zostaną opublikowane dla użytkownika. Począwszy od programu .NET Framework 4.8 WPF nie zawiera już zwinięty lub ukryte elementy w widoku kontrolnym drzewa biblioteki UIAutomation, więc czytniki zawartości ekranu nie są już może poinformować o tych elementów.

**Właściwość SelectionTextBrush do użytku z programem — moduł definiowania układu na podstawie zaznaczenia tekstu**

W .NET Framework 4.7.2 WPF dodaje pobierające <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox> zaznaczonego tekstu bez korzystania z warstwy moduł definiowania układu kodu. Kolor pierwszego planu zaznaczony tekst w tym scenariuszu zostało podyktowanej <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.

.NET framework 4.8 dodaje nową właściwość `SelectionTextBrush`, która umożliwia deweloperom wybrać określone Pędzel zaznaczony tekst, gdy za pomocą innego niż moduł definiowania układu na podstawie zaznaczonego tekstu. Ta właściwość działa tylko w systemie <xref:System.Windows.Controls.Primitives.TextBoxBase>-pochodnych kontrolek i <xref:System.Windows.Controls.PasswordBox> kontrolki w aplikacji WPF przy użyciu wybór podstawie moduł definiowania układu tekstu, włączone. Nie działa na <xref:System.Windows.Controls.RichTextBox> kontroli. Jeśli zaznaczenie tekstu podstawie moduł definiowania układu kodu nie jest włączona, ta właściwość jest ignorowana.

Aby używać tej właściwości, dodaj go do kodu XAML i za pomocą odpowiednich pędzla lub powiązania. Wynikowy zaznaczonego tekstu wygląda następująco:

![Etykietka narzędzia, gdy użytkownik przechodzi do przycisku za pomocą klawiatury](media/selectiontextbrush-property.png)

Można połączyć użytkowania `SelectionBrush` i `SelectionTextBrush` właściwości, aby wygenerować żadnych tła i pierwszego planu kolor połączeniem, które uznasz za stosowny.

**Obsługa biblioteki UIAutomation ControllerFor właściwość**

Biblioteki firmy UIAutomation `ControllerFor` właściwość zwraca tablicę elementów automatyzacji, które są zmieniane przez element automatyzacji, który obsługuje tej właściwości. Ta właściwość jest często używana do automatycznego sugerowania ułatwień dostępu. `ControllerFor` jest używana podczas automatyzacji element ma wpływ na jeden lub więcej segmentów w interfejsie użytkownika aplikacji lub pulpitu. W przeciwnym razie jest trudny do skojarzenia wpływ operacji kontroli elementów interfejsu użytkownika. Ta funkcja dodaje możliwość dla formantów podać wartość dla `ControllerFor` właściwości.

.NET framework 4.8 dodaje nowej metody wirtualnej <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>. Aby podać wartość dla `ControllerFor` właściwość, po prostu zastąpić tę metodę i zwraca `List<AutomationPeer>` dla formantów podlegający manipulowaniu to <xref:System.Windows.Automation.Peers.AutomationPeer>:

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

**Etykietki narzędzi na dostęp za pomocą klawiatury**

W programie .NET Framework 4.7.2 i wcześniejszych wersjach wyświetlania w etykietkach ekranowych tylko wtedy, gdy użytkownik ustawi wskaźnik myszy nad formantem. W .NET Framework 4,8 etykietki narzędzi także wyświetlać na klawiaturę, a także za pomocą skrótów klawiaturowych.

Aby włączyć tę funkcję, aplikacja musi platformą docelową jest program .NET Framework 4.8 lub wymaga zgody na uczestnictwo przy użyciu `Switch.UseLegacyAccessibilityFeatures.3` i `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) przełączników. Oto przykładowy plik konfiguracji aplikacji:

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

Po włączeniu wszystkich kontrolek, które zawierają etykietka narzędzia wyświetlić po formant uzyskuje fokus klawiatury. Etykietka narzędzia może być ukryty w czasie lub podczas zmiany fokus klawiatury. Użytkownicy mogą również odrzucić etykietki narzędzia ręcznie przy użyciu nowego skrótu klawiaturowego Ctrl + Shift + F10. Gdy etykietka narzędzia został odrzucony. może być wyświetlany ponownie przy użyciu tego samego skrótu klawiaturowego.

> [!NOTE]
> [Etykietki narzędzi wstążki] (xref:System.Windows.Controls.Ribbon.RibbonToolTips > na <xref:System.Windows.Controls.Ribbon.Ribbon> kontrolek nie zostanie wyświetlona na klawiaturę; pokazują za pomocą skrótów klawiaturowych.

**Dodano obsługę SizeOfSet i biblioteki PositionInSet UIAutomation właściwości**

Windows 10 wprowadzono dwie nowe właściwości biblioteki UIAutomation `SizeOfSet` i `PositionInSet`, które są używane przez aplikacje do opisania liczba elementów w zestawie. Biblioteki UIAutomation aplikacji klienckich, takich jak czytniki zawartości ekranu można zbadać aplikacji dla tych właściwości i ogłaszamy dokładne odzwierciedlenia Interfejsem użytkownika aplikacji.

Począwszy od programu .NET Framework 4.8 WPF udostępnia te dwie właściwości do biblioteki UIAutomation w aplikacjach WPF. Można to zrobić na dwa sposoby:

- Za pomocą właściwości zależności.

   WPF dodaje dwie nowe właściwości zależności <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>. Projektant umożliwia XAML ustawienia ich wartości:

   ```xaml
   <Button AutomationProperties.SizeOfSet="3"
     AutomationProperties.PositionInSet="1">Button 1</Button>

   <Button AutomationProperties.SizeOfSet="3"
     AutomationProperties.PositionInSet="2">Button 2</Button>

   <Button AutomationProperties.SizeOfSet="3"
     AutomationProperties.PositionInSet="3">Button 3</Button>
   ```

- Przez zastąpienie AutomationPeer metod wirtualnych.

   <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> metody wirtualne zostały dodane do klasy AutomationPeer. Deweloper opracowuje wartości `SizeOfSet` i `PositionInSet` przez zastąpienie tych metod, jak pokazano w poniższym przykładzie:

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

Ponadto elementy w <xref:System.Windows.Controls.ItemsControl> wystąpienia oferują wartości tych właściwości, które automatycznie bez dodatkowych działań od dewelopera. Jeśli <xref:System.Windows.Controls.ItemsControl> są grupowane, kolekcję grup jest reprezentowany jako zestaw, a każda grupa jest traktowana jako oddzielny zestaw z każdym elementem w tej grupie, podając jego pozycja w tej grupie, a także rozmiar grupy. Automatyczne wartości nie dotyczy wirtualizacji. Nawet wtedy, gdy element nie jest wykonywane, nadal jest wliczane do łączny rozmiar zestawu i ma wpływ na położenie w zestawie z jego elementów równorzędnych.

Automatyczne wartości są podane tylko, jeśli aplikacja jest przeznaczony dla .NET Framework 4.8. W przypadku aplikacji przeznaczonych dla starszej wersji programu .NET Framework, można ustawić `Switch.UseLegacyAccessibilityFeatures.3` [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak pokazano w następującym pliku App.config:

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Projektant przepływu pracy Windows Workflow Foundation (WF)

Projektant przepływu pracy zawiera następujące zmiany w .NET Framework 4.8:

- Za pomocą programu Narrator będzie towarzyszyć poprawę FlowSwitch etykiet wielkości liter.

- Za pomocą programu Narrator będzie towarzyszyć ulepszenia w opisach przycisku.

- Użytkownicy, którzy wysokiego kontrastu, motywów zobaczą poprawę widoczność projektanta przepływów pracy i jego formantów, takie jak lepsza współczynniki kontrastu między elementami i lepiej widoczne pola wyboru używany do elementów zespołu.

Jeśli aplikacja jest przeznaczony dla .NET Framework 4.7.2 lub starszej wersji, możesz zdecydować się na te zmiany, ustawiając `Switch.UseLegacyAccessibilityFeatures.3` [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `false` w pliku konfiguracyjnym aplikacji. Aby uzyskać więcej informacji, zobacz [zalet udoskonalonym ułatwieniom dostępu](#taking-advantage-of-accessibility-enhancements) sekcję w tym artykule.

## <a name="whats-new-in-accessibility-in-net-framework-472"></a>What's new in ułatwień dostępu w programie .NET Framework 4.7.2

.NET framework 4.7.2 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a>Windows Forms

**Zdefiniowane przez system operacyjny kolory wysokiego kontrastu, motywów**

Począwszy od .NET Framework 4.7.2 formularze Windows używa kolorów zdefiniowanych przez system operacyjny w wysokiego kontrastu, motywów. Dotyczy to następujących formantów:

- Strzałki listy rozwijanej z <xref:System.Windows.Forms.ToolStripDropDownButton> kontroli.

- <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> steruje się za pomocą <xref:System.Windows.Forms.ButtonBase.FlatStyle> równa <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>. Wcześniej wybranych kolorów tekstu i tła nie zostały kontrastujących i były trudne do odczytania.

- Kontrolek znajdujących się w obrębie <xref:System.Windows.Forms.GroupBox> zawierający jego <xref:System.Windows.Forms.Control.Enabled> właściwością `false`.

- <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, I <xref:System.Windows.Forms.ToolStripDropDownButton> formanty, które mają większą jasność współczynnik kontrastu w trybie wysokiego kontrastu.

- <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Ulepszenia Narrator**

Począwszy od .NET Framework 4.7.2 obsługi programu Narrator został rozszerzony w następujący sposób:

- Ogłasza, wartość <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> właściwości ogłoszenie tekst <xref:System.Windows.Forms.ToolStripMenuItem>.

- Oznacza to, kiedy <xref:System.Windows.Forms.ToolStripMenuItem> ma jego <xref:System.Windows.Forms.Control.Enabled> właściwością `false`.

- Przekazuje opinie dotyczące stanu pola wyboru gdy <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> właściwość jest ustawiona na `true`.

- Program Narrator firmy Skanuj tryb koncentracji uwagi kolejność jest zgodna z visual kolejność kontrolek w oknie dialogowym pobierania ClickOnce.

**Ulepszenia w formancie DataGridView**

Począwszy od .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> kontroli ma wprowadzono następujące ulepszenia ułatwień dostępu:

- Za pomocą klawiatury można sortować wiersze. Użytkownik może używać klawisz F3, aby posortować według bieżącej kolumny.

- Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, nagłówek kolumny zmieni kolor, aby wskazać bieżącej kolumny jako karty użytkownika za pośrednictwem komórek w bieżącym wierszu.

- <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> zwraca kontrolki nadrzędnej poprawne.

**Ulepszone podpowiedzi wizualne**

- <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> kontrolek z pustą <xref:System.Windows.Forms.ButtonBase.Text> właściwości wyświetlania wskaźnika fokus, gdy one zostać ustawiony fokus.

**Obsługa siatki właściwości ulepszone**

- <xref:System.Windows.Forms.PropertyGrid> Kontrolować elementy podrzędne, które teraz zwracany `true` dla <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> właściwości tylko wtedy, gdy PropertyGrid element jest włączony.

- <xref:System.Windows.Forms.PropertyGrid> Kontrolować elementy podrzędne zwracany `false` dla <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> właściwości tylko wtedy, gdy PropertyGrid element mogą być zmieniane przez użytkownika.

**Ulepszone klawiatury**

- <xref:System.Windows.Forms.ToolStripButton> Kontrolka zezwala na fokus, gdy jest zawarty w ramach <xref:System.Windows.Forms.ToolStripPanel> zawierający <xref:System.Windows.Forms.ToolStripPanel.TabStop> właściwością `true`

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Zmiany do kontrolki pola wyboru i RadioButton**

W programie .NET Framework 4.7.1 i wcześniejszymi wersjami, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> i <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> formanty mają niespójne i, w modelu klasycznym oraz wysokiego kontrastu motywy niepoprawne koncentracji uwagi wizualizacji.  Te problemy występują w przypadkach, gdy formanty nie mają żadnych zestawu zawartości.  Dzięki temu może być przejście pomiędzy motywów mylące i element wizualny fokusu trudne do zobaczenia.

W programie .NET Framework 4.7.2 te wizualizacje są teraz bardziej spójny między motywy i widoczność w klasycznej sieci wirtualnej i wysokiego kontrastu motywów.

**Formanty formularzy WinForm hostowany w aplikacji WPF**

Kontrolki WinForms hostowaną w aplikacji WPF, .NET Framework 4.7.1 i wcześniejszych wersjach, użytkownicy nie karcie poza warstwy WinForms w przypadku pierwszej lub ostatniej kontroli w tej warstwie WPF <xref:System.Windows.Forms.Integration.ElementHost> kontroli. W programie .NET Framework 4.7.2 użytkownicy mogą teraz kartę z warstwy WinForms.

Jednak automatycznych aplikacji, które zależą od fokus nigdy nie anulowania zapewnianego element warstwy WinForms może przestać działać zgodnie z oczekiwaniami.

## <a name="whats-new-in-accessibility-in-net-framework-471"></a>What's new in ułatwień dostępu w programie .NET Framework 4.7.1

.NET framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [Kontrolki sieci web platformy ASP.NET](#aspnet471)

- [.NET SDK Tools](#tools471)

- [Projektanta przepływów pracy programu Windows Workflow Foundation (WF)](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ulepszenia czytnika ekranu**

Jeśli ulepszenia ułatwień dostępu są włączone, .NET Framework 4.7.1 obejmuje następujące ulepszenia, które wpływają na czytniki zawartości ekranu:

- W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.Expander> formanty zostały odczytywana przez czytniki zawartości ekranu jako przyciski. Począwszy od .NET Framework 4.7.1 ich obsłudze zostaną poprawnie opublikowane jako rozwijania/zwijane grupy.

- W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.DataGridCell> formantów była odczytywana przez czytniki ekranu jako "niestandardowe". Począwszy od .NET Framework 4.7.1 one są teraz prawidłowo od niedawna komórce siatki danych (zlokalizowany).

- Począwszy od .NET Framework 4.7.1 czytniki zawartości ekranu ogłaszamy nazwę można edytować <xref:System.Windows.Controls.ComboBox>.

- W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.PasswordBox> formanty zostały ogłaszany jako "Brak elementów w widoku" lub ma inny sposób niepoprawne zachowanie. Ten problem jest rozwiązany, począwszy od .NET Framework 4.7.1.

**Obsługa biblioteki UIAutomation LiveRegion**

Czytniki zawartości ekranu, np. osób pomocy Narrator odczytać zawartość interfejsu użytkownika aplikacji, zwykle zamiany tekstu na mowę dane wyjściowe zawartości interfejsu użytkownika, który ma fokus. Jeśli jednak element interfejsu użytkownika zmiany i nie ma fokus, użytkownik nie może otrzymywać powiadomienia i może pominąć ważne informacje. Regiony na żywo na celu rozwiązanie tego problemu. Projektant umożliwia ich poinformować czytnika zawartości ekranu lub inne zgłaszający istotnych zmian do elementu interfejsu użytkownika klienta biblioteki UIAutomation. Czytnik zawartości ekranu możesz zdecydować, jak i kiedy poinformowania użytkownika o tej zmianie.

Aby zapewnić obsługę regionów na żywo, następujące interfejsy API zostały dodane do platformy WPF:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pola, które identyfikują **LiveSetting** właściwości i **LiveRegionChanged** zdarzeń. Można ich ustawić przy użyciu XAML.

- **AutomationProperties.LiveSetting** dołączona właściwość, która informuje o czytnika zawartości ekranu znaczenie zmiany interfejsu użytkownika dla użytkownika.

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Właściwość, która identyfikuje **AutomationProperties.LiveSetting** dołączona właściwość.

- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metody, która może zostać zastąpiona w celu zapewnienia **LiveSetting** wartości.

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, które get i set **LiveSetting** wartości.

- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Wyliczenia, który definiuje następujące możliwości **LiveSetting** wartości:

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Element nie wysyła powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Elementu wysyła-interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.

   - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Elementu wysyła interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.

Można utworzyć LiveRegion, ustawiając **AutomationProperties.LiveSetting** właściwości w elemencie zainteresowania, jak pokazano w poniższym przykładzie:

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Gdy zmieniają się dane w regionie na żywo i należy poinformować czytnika ekranu, należy jawnie wywołać zdarzenie, jak pokazano w następującym przykładzie.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Duży kontrast**

Począwszy od .NET Framework 4.7.1 o wysokim kontraście wprowadzono ulepszenia do różnych formantów WPF. Są one teraz widoczne podczas <xref:System.Windows.SystemParameters.HighContrast%2A> ustawiono motywu. Należą do nich następujące elementy:

- <xref:System.Windows.Controls.Expander> Kontrolki

    Fokus visual dla <xref:System.Windows.Controls.Expander> kontroli jest teraz widoczna. Wizualizacje klawiatury dla <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.RadioButton> formanty są również widoczne. Na przykład:

    Przed: 

    ![Formant ekspandera fokus przed ulepszenia ułatwień dostępu](media/expander-before.png)

    Po: 

    ![Formant ekspandera fokus po ulepszenia ułatwień dostępu](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów

    Tekst w <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> kontrolki jest teraz lepiej widoczne po wybraniu w wysokiego kontrastu, motywów. Na przykład:

    Przed: 

    ![Przycisk radiowy o wysokim kontraście fokus przed ulepszenia ułatwień dostępu](media/radio-button-before.png)

    Po: 

    ![Przycisk radiowy o wysokim kontraście fokus po ulepszenia ułatwień dostępu](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> Kontrolki

    Począwszy od .NET Framework 4.7.1, obramowania wyłączone <xref:System.Windows.Controls.ComboBox> formant jest kolor wyłączonego tekstu. Na przykład:

    Przed: 

     ![Pole kombi wyłączone obramowanie i tekst przed ulepszenia ułatwień dostępu](media/combo-disabled-before.png)

    Po:   

     ![Pole kombi wyłączony obramowanie i tekstu po ulepszenia ułatwień dostępu](media/combo-disabled-after.png)

    Ponadto wyłączone i skoncentrowany przyciski używają kolor motywu poprawne.

    Przed:

    ![Kolory motywu przycisk przed ulepszenia ułatwień dostępu](media/button-themes-before.png) 

    Po: 

    ![Kolory motywu przycisku po ulepszenia ułatwień dostępu](media/button-themes-after.png) 

    Na koniec w .NET Framework 4.7 i wcześniejszymi wersjami, ustawienie <xref:System.Windows.Controls.ComboBox> stylu kontrolki do `Toolbar.ComboBoxStyleKey` spowodowane strzałkę listy rozwijanej, aby była niewidoczna. Ten problem jest rozwiązany, począwszy od .NET Framework 4.7.1. Na przykład:

    Przed: 

    ![Toolbar.ComboBoxStyleKey przed ulepszenia ułatwień dostępu](media/comboboxstylekey-before.png) 

    Po: 

    ![Toolbar.ComboBoxStyleKey po ulepszenia ułatwień dostępu](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> Kontrolki

    Począwszy od .NET Framework 4.7.1, strzałkę wskaźnika sortowania w <xref:System.Windows.Controls.DataGrid> kontroluje teraz używa Popraw kolory motywu. Na przykład:

    Przed: 

    ![Sortowanie strzałkę wskaźnika przed ulepszenia ułatwień dostępu](media/sort-indicator-before.png) 

    Po:   

    ![Strzałka wskaźnika sortowania po ulepszenia ułatwień dostępu](media/sort-indicator-after.png) 

    Ponadto w i wcześniejszych wersji programu .NET Framework 4.7, domyślnego stylu łącze zmieniana na niepoprawny kolor na myszy w trybach o wysokim kontraście. Ten problem został rozwiązany, począwszy od .NET Framework 4.7.1. Podobnie <xref:System.Windows.Controls.DataGrid> wyboru kolumn używa oczekiwanego kolorów opinii fokus klawiatury, począwszy od .NET Framework 4.7.1.

    Przed: 

    ![Styl łącza domyślne DataGrid przed ulepszenia ułatwień dostępu](media/default-link-style-before.png) 

    Po:    

    ![Styl łącza domyślne DataGrid po ulepszenia ułatwień dostępu](media/default-link-style-after.png) 

Aby uzyskać więcej informacji na temat ulepszenia ułatwień dostępu programu WPF w programie .NET Framework 4.7.1, zobacz [ulepszenia ułatwień dostępu w programie WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a>Ulepszenia ułatwień dostępu w Windows Forms

W programie .NET Framework 4.7.1 Windows Forms (WinForms) zawiera zmiany ułatwień dostępu w następujących obszarach.

**Ulepszone wyświetlaną w trybie dużego kontrastu**

Począwszy od .NET Framework 4.7.1 różne formanty formularzy WinForm oferuje ulepszoną renderowania w trybach HighContrast dostępne w systemie operacyjnym. Windows 10 została zmieniona wartości dla niektórych dużego kontrastu kolorów systemu i formularze Windows opiera się na platformę Windows 10 Win32. Aby uzyskać najlepsze wyniki Uruchom w najnowszej wersji systemu Windows, a następnie Zezwól na korzystanie z najnowszych zmian systemu operacyjnego, dodając plik app.manifest w aplikacji testowej i un-comment systemu Windows 10 obsługiwanych wiersza systemu operacyjnego wyglądającą następujące czynności:

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

Niektóre zmiany o wysokim kontraście należą:

- Zaznaczeń w <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.

- Po wybraniu wyłączone <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.

- Tekst w wybranych <xref:System.Windows.Forms.Button> kontrolować różni się od kolor wyboru.

- Wyłączony tekst jest łatwiejsza do odczytania. Na przykład:

    Przed:

    ![Wyłączony tekst przed ulepszenia ułatwień dostępu](media/wf-disabled-before.png) 

    Po:

    ![Wyłączony tekst po ulepszenia ułatwień dostępu](media/wf-disabled-after.png) 

- Duży kontrast ulepszenia w oknie dialogowym wyjątku wątku.

**Ulepszona obsługa Narrator**

Windows Forms w programie .NET Framework 4.7.1 obejmuje następujące ulepszenia ułatwień dostępu w programie Narrator:

- <xref:System.Windows.Forms.MonthCalendar> Kontroli jest możliwy, Narrator, a także innymi narzędziami automatyzacji interfejsu użytkownika.

- <xref:System.Windows.Forms.CheckedListBox> Kontroli powiadamia program Narrator, gdy stan zaznaczenia elementu została zmieniona, dzięki czemu użytkownik jest powiadamiany one zmieniono wartość elementu listy.

- <xref:System.Windows.Forms.DataGridViewCell> Kontroli raporty prawidłowy stan tylko do odczytu do Narrator.

- Narrator, teraz mogą odczytywać wyłączone <xref:System.Windows.Forms.ToolStripMenuItem> tekstu, należy wcześniej może pominąć elementów menu wyłączone.

**Rozszerzona obsługa biblioteki UIAutomation ułatwień dostępu wzorców**

Począwszy od .NET Framework 4.7.1 deweloperów technologii ułatwień dostępu mogą korzystać z typowych wzorców ułatwień dostępu do interfejsu API i właściwości dla kilku formantów formularzy WinForm. Te ulepszenia ułatwień dostępu, obejmują:

- <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ToolStripSplitButton> obsługują teraz [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> Obsługuje teraz [wzorca przełącznika](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).

- <xref:System.Windows.Forms.ToolStripItem> Kontrolować obsługuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości i [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.NumericUpDown> i <xref:System.Windows.Forms.DomainUpDown> kontroluje pomocy technicznej <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości.

**Ulepszone właściwość przeglądania**

Formularze Windows począwszy od .NET Framework 4.7.1 obejmuje:

- Lepsze nawigacji za pomocą klawiatury przez różne okna wyboru z listy rozwijanej.
- Ograniczenia niepotrzebne tabulatorów.
- Lepiej raportowanie typów formantów.
- Ulepszone narrator zachowanie.

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a>Kontrolki sieci web platformy ASP.NET

Począwszy od .NET Framework 4.7.1 i Visual Studio 2017 15.3, ASP.NET poprawia działanie kontrolki sieci web platformy ASP.NET przy użyciu technologii ułatwień dostępu w programie Visual Studio. Następujące zmiany:

- Zmiany do zaimplementowania Brak wzorce dostępności interfejsu użytkownika w kontrolkach, takie jak **Dodaj pole** okna dialogowego w **widoku szczegółów** kreatora lub **skonfigurować ListView** okna dialogowego z **ListView** kreatora.

- Zmiany w celu wyświetlania w trybie dużego kontrastu, takie jak **Edytor pola pagera danych**.

- Zmiany w celu polepszenia nawigacji klawiatury napotyka formanty, takie jak **pola** okna dialogowego w **Edytuj pola pagera** kreatora formantu DataPager **konfigurowania obiektu ObjectContext**  okno dialogowe, lub **Konfigurowanie wyboru danych** dialogowego **skonfigurować źródło danych** kreatora.

<a name="tools471"></a>

### <a name="net-sdk-tools"></a>.NET SDK Tools

[Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) i [narzędzie śledzenia usług (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) zostały ulepszone przez Rozwiązywanie problemów zależeć od dostępności. Większość z nich zostały się niewielkie problemy, takie jak nazwy, nie zostały zdefiniowane lub niektóre wzorce automatyzacji interfejsu użytkownika nie jest zaimplementowana poprawnie. Gdy wielu użytkowników nie należy pamiętać o tych niepoprawne wartości, klienci korzystający z technologiami pomocniczymi, takich jak czytniki zawartości ekranu znajduje się tych narzędzi zestawu SDK łatwiej dostępne.

Te ulepszenia zmianę niektórych zachowań poprzedniej, takich jak kolejność fokus klawiatury.

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Projektanta przepływów pracy programu Windows Workflow Foundation (WF)

Następujące zmiany w ułatwienia dostępu w Projektancie przepływu pracy:

- Zmienia kolejność tabulacji od lewej do prawej i od góry do dołu w niektóre kontrolki:

  - W oknie korelacji inicjowanie korelacji danych dla <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.

  - W oknie definicji zawartości <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działań.

- Więcej funkcji są dostępne za pośrednictwem klawiatury:

  - Podczas edytowania właściwości działania, grupy właściwości można zwinąć, klawiatury są skupia się po raz pierwszy.

  - Ikony ostrzeżenia są dostępne dla klawiatury.

  - **Więcej właściwości** znajdujący się w **właściwości** okno jest dostępny za pomocą klawiatury.

  - Klawiatura, użytkownicy mogą uzyskiwać dostęp elementy nagłówka w **argumenty** i **zmienne** okienka projektanta przepływów pracy.

- Ulepszona widoczność elementów z fokusem, takie jak czas:

  - Dodawanie wierszy do siatki danych używane przez projektantów projektanta przepływów pracy i działania.

  - TAB pól w <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply> działań.

  - Ustawianie wartości domyślnych dla zmiennych lub argumentów

- Czytniki zawartości ekranu teraz mógł prawidłowo rozpoznać:

  - Punkty przerwania ustawione w Projektancie przepływu pracy.

  - <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, I <xref:System.ServiceModel.Activities.CorrelationScope> działań.
  - Zawartość <xref:System.ServiceModel.Activities.Receive> działania.

  - Typ docelowy dla <xref:System.Activities.Statements.InvokeMethod> działania.

  - Pole kombi wyjątek i na koniec sekcji <xref:System.Activities.Statements.TryCatch> działania.

  - Pole kombi typu komunikatu, podziału w oknie Dodaj inicjatory korelacji, okno definicji zawartości i okna definice Vlastnosti Correlateson działań dotyczących komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>).

  - Automat stanów przejścia i przeniesie miejsc docelowych.

  - Adnotacje i łączników na <xref:System.Activities.Statements.FlowDecision> działań.

  - Menu kontekstowe (kliknij prawym przyciskiem myszy), działań.

  - Edytory wartości właściwości, przycisk Wyczyść wyszukiwanie, według kategorii i przyciski sortowania alfabetycznego i okno dialogowe Edytor wyrażeń w siatce właściwości.

  - Procent powiększenia w Projektancie przepływu pracy.

  - Separator w <xref:System.Activities.Statements.Parallel> i <xref:System.Activities.Statements.Pick> działań.

  - <xref:System.Activities.Statements.InvokeDelegate> Działania.

  - W oknie Wybierz typy działań słownika (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`itp.).

  - Przeglądanie i wybieranie typu .NET okna.

  - Linki do stron nadrzędnych w Projektancie przepływu pracy.

- Użytkownicy, którzy wysokiego kontrastu, motywów zobaczą wiele ulepszeń w widoczność projektanta przepływów pracy i jego formantów, takie jak lepsza współczynniki kontrastu między elementami i lepiej widoczne pola wyboru używany do elementów zespołu.

## <a name="see-also"></a>Zobacz także

- [What's new in .NET Framework](whats-new.md)
