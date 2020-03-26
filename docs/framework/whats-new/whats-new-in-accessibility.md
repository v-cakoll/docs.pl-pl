---
title: Co nowego w ułatwieniach dostępu w platformie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 4243599f44749e7b38ebe78ca88b8ec2a9390650
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249724"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="bba9b-102">Co nowego w ułatwieniach dostępu w platformie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bba9b-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="bba9b-103">.NET Framework ma na celu uczynienie aplikacji bardziej dostępnymi dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="bba9b-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="bba9b-104">Funkcje ułatwień dostępu umożliwiają aplikacji zapewnienie użytkownikom technologii ułatwień dostępu odpowiednie środowisko.</span><span class="sxs-lookup"><span data-stu-id="bba9b-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="bba9b-105">Począwszy od programu .NET Framework 4.7.1, program .NET Framework zawiera wiele ulepszeń ułatwień dostępu, które umożliwiają deweloperom tworzenie aplikacji dostępnych.</span><span class="sxs-lookup"><span data-stu-id="bba9b-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="bba9b-106">Przełączniki ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="bba9b-106">Accessibility switches</span></span>

<span data-ttu-id="bba9b-107">Aplikację można skonfigurować tak, aby wybierała funkcje ułatwień dostępu, jeśli jest ona przeznaczona dla platformy .NET Framework 4.7 lub starszej wersji, ale jest uruchomiona w programie .NET Framework 4.7.1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="bba9b-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="bba9b-108">Można również skonfigurować aplikację do używania starszych funkcji (i nie korzystać z funkcji ułatwień dostępu), jeśli jest ona przeznaczona dla platformy .NET Framework 4.7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="bba9b-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="bba9b-109">Każda wersja programu .NET Framework, która zawiera funkcje ułatwień dostępu [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ma przełącznik [`<runtime>`](../configure-apps/file-schema/runtime/index.md) ułatwień dostępu specyficzne dla wersji, które można dodać do elementu w sekcji pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bba9b-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="bba9b-110">Poniżej znajdują się obsługiwane przełączniki:</span><span class="sxs-lookup"><span data-stu-id="bba9b-110">The following are the supported switches:</span></span>

|<span data-ttu-id="bba9b-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="bba9b-111">Version</span></span>|<span data-ttu-id="bba9b-112">Przełącznik</span><span class="sxs-lookup"><span data-stu-id="bba9b-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="bba9b-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="bba9b-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="bba9b-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="bba9b-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="bba9b-115"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="bba9b-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="bba9b-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="bba9b-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="bba9b-117"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="bba9b-117">.NET Framework 4.8</span></span>|<span data-ttu-id="bba9b-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="bba9b-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="bba9b-119">Korzystanie z ulepszeń ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="bba9b-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="bba9b-120">Nowe funkcje ułatwień dostępu są domyślnie włączone dla aplikacji docelowych .NET Framework 4.7.1 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="bba9b-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="bba9b-121">Ponadto aplikacje przeznaczone dla starszej wersji programu .NET Framework, ale uruchomione w programie .NET Framework 4.7.1 lub nowszym, mogą zrezygnować ze [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) starszych [`<runtime>`](../configure-apps/file-schema/runtime/index.md) zachowań ułatwień dostępu (a tym `false`samym skorzystać z ulepszeń ułatwień dostępu), dodając przełączniki do elementu w sekcji pliku konfiguracyjnego aplikacji i ustawiając ich wartość na .</span><span class="sxs-lookup"><span data-stu-id="bba9b-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="bba9b-122">Poniżej przedstawiono sposób wyrażenia zgody na ulepszenia ułatwień dostępu wprowadzone w systemie .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="bba9b-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="bba9b-123">Jeśli zdecydujesz się wyrazić zgodę na funkcje ułatwień dostępu w nowszej wersji programu .NET Framework, należy również jawnie zdecydować się na funkcje z wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bba9b-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="bba9b-124">Konfigurowanie aplikacji w celu skorzystania z ulepszeń ułatwień dostępu w programie .NET Framework 4.7.1 i 4.7.2 wymaga następującego [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:</span><span class="sxs-lookup"><span data-stu-id="bba9b-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="bba9b-125">Konfigurowanie aplikacji w celu skorzystania z ulepszeń ułatwień dostępu w programie .NET Framework 4.7.1, 4.7.2 i 4.8 wymaga następującego [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:</span><span class="sxs-lookup"><span data-stu-id="bba9b-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="bba9b-126">Przywracanie starszego zachowania</span><span class="sxs-lookup"><span data-stu-id="bba9b-126">Restoring legacy behavior</span></span>

<span data-ttu-id="bba9b-127">Aplikacje docelowe wersji programu .NET Framework rozpoczynające się od wersji 4.7.1 [`<runtime>`](../configure-apps/file-schema/runtime/index.md) mogą wyłączyć funkcje ułatwień dostępu, `true`dodając przełączniki do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu w sekcji pliku konfiguracyjnego aplikacji i ustawiając ich wartość na .</span><span class="sxs-lookup"><span data-stu-id="bba9b-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="bba9b-128">Na przykład następująca konfiguracja rezygnuje z funkcji ułatwień dostępu wprowadzonych w programie .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="bba9b-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="bba9b-129">Co nowego w ułatwieniach dostępu w systemie .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="bba9b-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="bba9b-130">Program .NET Framework 4.8 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="bba9b-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="bba9b-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bba9b-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="bba9b-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="bba9b-133">Projektant przepływu pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="bba9b-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bba9b-134">Windows Forms</span></span>

<span data-ttu-id="bba9b-135">W programie .NET Framework 4.8 formularze systemu Windows dodaje obsługę LiveRegions i zdarzenia powiadomień do wielu często używanych formantów.</span><span class="sxs-lookup"><span data-stu-id="bba9b-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="bba9b-136">Dodaje również obsługę etykietek narzędzi, gdy użytkownik przechodzi do formantu za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bba9b-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="bba9b-137">**Obsługa UIA LiveRegions w etykietach i paskach statusowych**</span><span class="sxs-lookup"><span data-stu-id="bba9b-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="bba9b-138">UIA LiveRegions umożliwiają deweloperom aplikacji powiadamianie czytników ekranu o zmianie tekstu w formancie, który znajduje się poza lokalizacją, w której użytkownik pracuje.</span><span class="sxs-lookup"><span data-stu-id="bba9b-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="bba9b-139">Jest to przydatne, na <xref:System.Windows.Forms.StatusStrip> przykład dla formantu, który pokazuje stan połączenia.</span><span class="sxs-lookup"><span data-stu-id="bba9b-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="bba9b-140">Jeśli połączenie zostanie przerwane, a stan ulegnie zmianie, deweloper może chcieć powiadomić czytnik ekranu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="bba9b-141">Począwszy od programu .NET Framework 4.8, formularze systemu <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> Windows implementują UIA LiveRegions dla formantów i formantu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="bba9b-142">Na przykład następujący kod używa LiveRegion <xref:System.Windows.Forms.Label> w `label1`formancie o nazwie:</span><span class="sxs-lookup"><span data-stu-id="bba9b-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="bba9b-143">Narrator ogłasza "Gotowe", niezależnie od tego, gdzie użytkownik wchodzi w interakcję z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="bba9b-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="bba9b-144">Można również zaimplementować <xref:System.Windows.Forms.UserControl> jako LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="bba9b-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="bba9b-145">**Zdarzenia powiadomień UIA**</span><span class="sxs-lookup"><span data-stu-id="bba9b-145">**UIA notification events**</span></span>

<span data-ttu-id="bba9b-146">Zdarzenie powiadomienia UIA, wprowadzone w windows 10 Fall Creators Update, umożliwia aplikacji do podniesienia uia zdarzenia, co prowadzi do Narrator po prostu dokonywania anonsu na podstawie tekstu, który dostarczasz ze zdarzeniem, bez konieczności posiadania odpowiedniej kontroli w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bba9b-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="bba9b-147">W niektórych scenariuszach jest to prosty sposób, aby znacznie poprawić dostępność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bba9b-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="bba9b-148">W może być również przydatne do powiadamiania o postępie niektórych procesów, które mogą zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="bba9b-149">Aby uzyskać więcej informacji na temat zdarzeń powiadomień uia, zobacz [Czy aplikacja komputerowa może korzystać z nowego zdarzenia powiadomienia o interfejsie użytkownika?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span><span class="sxs-lookup"><span data-stu-id="bba9b-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="bba9b-150">Poniższy przykład wywołuje [zdarzenie notification:](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)</span><span class="sxs-lookup"><span data-stu-id="bba9b-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="bba9b-151">**Etykietki narzędzi dotyczące dostępu do klawiatury**</span><span class="sxs-lookup"><span data-stu-id="bba9b-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="bba9b-152">W aplikacjach, które są przeznaczone dla platformy .NET Framework 4.7.2 i wcześniejszych wersji, [etykietka narzędzia](xref:System.Windows.Forms.ToolTip) formantu można wyzwolić tylko do wyświetlenia przez przeniesienie wskaźnika myszy do formantu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="bba9b-153">Począwszy od programu .NET Framework 4.8, użytkownik klawiatury może wyzwolić etykietkę narzędzia formantu, koncentrując formant za pomocą klawisza Tab lub klawiszy strzałek z klawiszami modyfikuj lub bez.</span><span class="sxs-lookup"><span data-stu-id="bba9b-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="bba9b-154">To szczególne ulepszenie ułatwień dostępu wymaga dodatkowego [przełącznika AppContext:](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)</span><span class="sxs-lookup"><span data-stu-id="bba9b-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="bba9b-155">Na poniższej ilustracji przedstawiono etykietkę narzędzia, gdy użytkownik wybrał przycisk z klawiaturą.</span><span class="sxs-lookup"><span data-stu-id="bba9b-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Zrzut ekranu przedstawiający etykietkę narzędzia, gdy użytkownik przechodzi do przycisku za pomocą klawiatury.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="bba9b-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="bba9b-158">Począwszy od programu .NET Framework 4.8, WPF WPF zawiera szereg ulepszeń ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="bba9b-159">**Narratory ekranów nie ogłaszają już elementów o widoczności Zwiniętej lub Ukrytej**</span><span class="sxs-lookup"><span data-stu-id="bba9b-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="bba9b-160">Elementy o zwiniętej lub ukrytej widoczności nie są już ogłaszane przez czytnik ekranu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="bba9b-161">Interfejsy użytkownika, które zawierają <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> elementy <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> o widoczności lub mogą być błędnie przedstawione przez czytniki ekranu, jeśli zostaną ogłoszone użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="bba9b-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="bba9b-162">Począwszy od .NET Framework 4.8, WPF WPF nie zawiera już zwinięte lub ukryte elementy w widoku sterowania drzewa UIAutomation, więc czytniki ekranu nie mogą już ogłaszać tych elementów.</span><span class="sxs-lookup"><span data-stu-id="bba9b-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="bba9b-163">**Właściwość SelectionTextBrush do użytku z zaznaczeniem tekstu nienapartym na Adornerze**</span><span class="sxs-lookup"><span data-stu-id="bba9b-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="bba9b-164">W .NET Framework 4.7.2 WPF WPF <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> dodał możliwość rysowania i zaznaczania tekstu bez użycia warstwy Adorner.</span><span class="sxs-lookup"><span data-stu-id="bba9b-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="bba9b-165">Kolor pierwszego planu zaznaczonego tekstu w tym scenariuszu był podyktowany programem <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bba9b-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bba9b-166">.NET Framework 4.8 dodaje `SelectionTextBrush`nową właściwość, która umożliwia deweloperom zaznaczenie określonego pędzla dla zaznaczonego tekstu podczas korzystania z zaznaczenia tekstu opartego na adornerze.</span><span class="sxs-lookup"><span data-stu-id="bba9b-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="bba9b-167">Ta właściwość <xref:System.Windows.Controls.Primitives.TextBoxBase>działa tylko na <xref:System.Windows.Controls.PasswordBox> formanty pochodne i formantu w aplikacjach WPF z nie-Adorner oparte na zaznaczeniu tekstu włączone.</span><span class="sxs-lookup"><span data-stu-id="bba9b-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="bba9b-168">Nie działa na <xref:System.Windows.Controls.RichTextBox> formancie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="bba9b-169">Jeśli nie oparte na Adorner wybór tekstu nie jest włączona, ta właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="bba9b-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="bba9b-170">Aby użyć tej właściwości, wystarczy dodać go do kodu XAML i użyć odpowiedniego pędzla lub powiązania.</span><span class="sxs-lookup"><span data-stu-id="bba9b-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="bba9b-171">Wynikowy wybór tekstu wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="bba9b-171">The resulting text selection looks like this:</span></span>

![Zrzut ekranu przedstawiający aplikację z wybranymi słowami Hello World.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="bba9b-173">Można połączyć użycie `SelectionBrush` właściwości `SelectionTextBrush` i do generowania dowolnej kombinacji kolorów tła i pierwszego planu, które uważasz za stosowne.</span><span class="sxs-lookup"><span data-stu-id="bba9b-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="bba9b-174">**Obsługa kontrolera uiautomationfor właściwości**</span><span class="sxs-lookup"><span data-stu-id="bba9b-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="bba9b-175">UIAutomation's `ControllerFor` właściwość zwraca tablicę elementów automatyzacji, które są manipulowane przez element automatyzacji, który obsługuje tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="bba9b-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="bba9b-176">Ta właściwość jest często używana dla funkcji autoprosić dostępności.</span><span class="sxs-lookup"><span data-stu-id="bba9b-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="bba9b-177">`ControllerFor`jest używany, gdy element automatyzacji wpływa na jeden lub więcej segmentów interfejsu użytkownika aplikacji lub pulpitu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="bba9b-178">W przeciwnym razie trudno jest skojarzyć wpływ operacji sterowania z elementami interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bba9b-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="bba9b-179">Ta funkcja dodaje możliwość formanty, `ControllerFor` aby zapewnić wartość dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba9b-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="bba9b-180">Program .NET Framework 4.8 dodaje <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>nową metodę wirtualną, .</span><span class="sxs-lookup"><span data-stu-id="bba9b-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bba9b-181">Aby zapewnić wartość `ControllerFor` właściwości, po prostu zastąpić tę `List<AutomationPeer>` metodę i zwrócić formanty manipulowane przez to: <xref:System.Windows.Automation.Peers.AutomationPeer></span><span class="sxs-lookup"><span data-stu-id="bba9b-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="bba9b-182">**Etykietki narzędzi dotyczące dostępu do klawiatury**</span><span class="sxs-lookup"><span data-stu-id="bba9b-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="bba9b-183">W .NET Framework 4.7.2 i wcześniejszych wersjach etykietki narzędzi są wyświetlane tylko wtedy, gdy użytkownik najedzie kursorem myszy nad formantem.</span><span class="sxs-lookup"><span data-stu-id="bba9b-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="bba9b-184">W programie .NET Framework 4.8 etykietki narzędzi są również wyświetlane na ostrości klawiatury, a także za pomocą skrótu klawiaturowego.</span><span class="sxs-lookup"><span data-stu-id="bba9b-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="bba9b-185">Aby włączyć tę funkcję, aplikacja musi kierować .NET Framework 4.8 lub wyrazić zgodę przy użyciu przełączników `Switch.UseLegacyAccessibilityFeatures.3` i `Switch.UseLegacyToolTipDisplay` [AppContext.](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)</span><span class="sxs-lookup"><span data-stu-id="bba9b-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="bba9b-186">Poniżej przedstawiono przykładowy plik konfiguracyjny aplikacji:</span><span class="sxs-lookup"><span data-stu-id="bba9b-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="bba9b-187">Po włączeniu wszystkie formanty zawierające etykietkę narzędzia wyświetlają ją po odebraniu fokusu za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bba9b-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="bba9b-188">Etykietka narzędzia może być odrzucona w czasie lub po zmianie ostrości klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bba9b-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="bba9b-189">Użytkownicy mogą również ręcznie odrzucić etykietkę narzędzia za pomocą nowego skrótu klawiaturowego Ctrl + Shift + F10.</span><span class="sxs-lookup"><span data-stu-id="bba9b-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="bba9b-190">Po odrzuceniu etykietki narzędzia można ją ponownie wyświetlić za pomocą tego samego skrótu klawiaturowego.</span><span class="sxs-lookup"><span data-stu-id="bba9b-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="bba9b-191">[Etykietki narzędzi wstążki](xref:System.Windows.Controls.Ribbon.RibbonToolTip) na <xref:System.Windows.Controls.Ribbon.Ribbon> formanty nie będą wyświetlane na fokusie klawiatury; wyświetlane są tylko za pomocą skrótu klawiaturowego.</span><span class="sxs-lookup"><span data-stu-id="bba9b-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="bba9b-192">**Dodano obsługę właściwości SizeOfSet i PositionInSet UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="bba9b-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="bba9b-193">System Windows 10 wprowadził dwie nowe właściwości `SizeOfSet` `PositionInSet`UIAutomation i , które są używane przez aplikacje do opisywania liczby elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="bba9b-194">UIAutomation aplikacji klienckich, takich jak czytniki ekranu można następnie kwerendy aplikacji dla tych właściwości i ogłosić dokładną reprezentację interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bba9b-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="bba9b-195">Począwszy od .NET Framework 4.8, WPF WPF udostępnia te dwie właściwości do UIAutomation w aplikacjach WPF.</span><span class="sxs-lookup"><span data-stu-id="bba9b-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="bba9b-196">Można to osiągnąć na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="bba9b-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="bba9b-197">Za pomocą właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="bba9b-197">By using dependency properties.</span></span>

  <span data-ttu-id="bba9b-198">WPF WPF dodaje dwie <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> nowe <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>właściwości zależności i .</span><span class="sxs-lookup"><span data-stu-id="bba9b-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bba9b-199">Deweloper może użyć XAML, aby ustawić swoje wartości:</span><span class="sxs-lookup"><span data-stu-id="bba9b-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="bba9b-200">Przez zastąpienie AutomationPeer metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="bba9b-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="bba9b-201">I <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> wirtualne metody zostały dodane do AutomationPeer klasy.</span><span class="sxs-lookup"><span data-stu-id="bba9b-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="bba9b-202">Deweloper może podać `SizeOfSet` wartości `PositionInSet` dla i przez zastąpienie tych metod, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bba9b-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="bba9b-203">Ponadto elementy w <xref:System.Windows.Controls.ItemsControl> wystąpieniach zapewniają wartość dla tych właściwości automatycznie bez dodatkowych działań od dewelopera.</span><span class="sxs-lookup"><span data-stu-id="bba9b-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="bba9b-204">Jeśli <xref:System.Windows.Controls.ItemsControl> jest zgrupowane, kolekcja grup jest reprezentowana jako zestaw, a każda grupa jest liczona jako oddzielny zestaw, z każdego elementu wewnątrz tej grupy, zapewniając swoją pozycję wewnątrz tej grupy, jak również rozmiar grupy.</span><span class="sxs-lookup"><span data-stu-id="bba9b-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="bba9b-205">Wirtualizacja nie ma wpływu na wartości automatyczne.</span><span class="sxs-lookup"><span data-stu-id="bba9b-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="bba9b-206">Nawet jeśli element nie jest realizowany, nadal jest wliczany do całkowitego rozmiaru zestawu i wpływa na pozycję w zestawie jego elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="bba9b-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="bba9b-207">Wartości automatyczne są dostarczane tylko wtedy, gdy obiekt docelowy aplikacji .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="bba9b-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="bba9b-208">W przypadku aplikacji przeznaczonych dla starszej wersji programu `Switch.UseLegacyAccessibilityFeatures.3` .NET Framework można ustawić [przełącznik AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak pokazano w następującym pliku App.config:</span><span class="sxs-lookup"><span data-stu-id="bba9b-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="bba9b-209">Projektant przepływu pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="bba9b-210">Projektant przepływu pracy zawiera następujące zmiany w programie .NET Framework 4.8:</span><span class="sxs-lookup"><span data-stu-id="bba9b-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="bba9b-211">Użytkownicy korzystający z Narratora zobaczą ulepszenia w etykietach przypadków FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="bba9b-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="bba9b-212">Użytkownicy korzystający z Narratora zobaczą ulepszenia w opisach przycisków.</span><span class="sxs-lookup"><span data-stu-id="bba9b-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="bba9b-213">Użytkownicy, którzy wybiorą motywy o wysokim kontraście, zobaczą ulepszenia w widoczności projektanta przepływu pracy i jego formantów, takie jak lepsze współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używane dla elementów fokusu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="bba9b-214">Jeśli aplikacja jest przeznaczona dla platformy .NET Framework 4.7.2 lub `Switch.UseLegacyAccessibilityFeatures.3` wcześniejszej wersji, `false` można zdecydować się na te zmiany, ustawiając [przełącznik AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bba9b-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="bba9b-215">Aby uzyskać więcej informacji, zobacz [korzystanie z ulepszeń ułatwień dostępu](#taking-advantage-of-accessibility-enhancements) w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="bba9b-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="bba9b-216">Co nowego w ułatwieniach dostępu w systemie .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="bba9b-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="bba9b-217">Program .NET Framework 4.7.2 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="bba9b-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="bba9b-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bba9b-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="bba9b-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="bba9b-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bba9b-220">Windows Forms</span></span>

<span data-ttu-id="bba9b-221">**Kolory zdefiniowane w systemach operacyjnych w motywach o wysokim kontraście**</span><span class="sxs-lookup"><span data-stu-id="bba9b-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="bba9b-222">Począwszy od programu .NET Framework 4.7.2, windows forms używa kolorów zdefiniowanych przez system operacyjny w motywach o wysokim kontraście.</span><span class="sxs-lookup"><span data-stu-id="bba9b-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="bba9b-223">Dotyczy to następujących kontrolek:</span><span class="sxs-lookup"><span data-stu-id="bba9b-223">This affects the following controls:</span></span>

- <span data-ttu-id="bba9b-224">Strzałka rozwijana formantu. <xref:System.Windows.Forms.ToolStripDropDownButton></span><span class="sxs-lookup"><span data-stu-id="bba9b-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="bba9b-225">Elementy <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.RadioButton> , <xref:System.Windows.Forms.CheckBox> i <xref:System.Windows.Forms.ButtonBase.FlatStyle> formanty z ustawionym <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub . <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bba9b-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bba9b-226">Wcześniej zaznaczone kolory tekstu i tła nie kontrastowały i były trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="bba9b-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="bba9b-227">Formanty zawarte <xref:System.Windows.Forms.GroupBox> w <xref:System.Windows.Forms.Control.Enabled> a, `false`który ma swoją właściwość ustawioną na .</span><span class="sxs-lookup"><span data-stu-id="bba9b-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="bba9b-228">Elementy <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripDropDownButton> i elementy sterujące, które mają zwiększony współczynnik kontrastu jasności w trybie wysokiego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="bba9b-229">Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> obiektu <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="bba9b-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="bba9b-230">**Ulepszenia Narratora**</span><span class="sxs-lookup"><span data-stu-id="bba9b-230">**Narrator improvements**</span></span>

<span data-ttu-id="bba9b-231">Począwszy od programu .NET Framework 4.7.2, obsługa Narratora jest rozszerzona w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bba9b-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="bba9b-232">Ogłasza wartość nieruchomości <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> przy ogłaszaniu tekstu . <xref:System.Windows.Forms.ToolStripMenuItem></span><span class="sxs-lookup"><span data-stu-id="bba9b-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="bba9b-233">Wskazuje, kiedy <xref:System.Windows.Forms.ToolStripMenuItem> ma <xref:System.Windows.Forms.Control.Enabled> ustawioną `false`właściwość na .</span><span class="sxs-lookup"><span data-stu-id="bba9b-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="bba9b-234">Przekazuje opinię na temat stanu pola <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> wyboru, gdy `true`właściwość jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="bba9b-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="bba9b-235">Kolejność ustawiania fokusu trybu skanowania narratora jest zgodna z kolejnością wizualną formantów w oknie dialogowym pobierania ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="bba9b-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="bba9b-236">**Ulepszenia DataGridView**</span><span class="sxs-lookup"><span data-stu-id="bba9b-236">**DataGridView improvements**</span></span>

<span data-ttu-id="bba9b-237">Począwszy od programu .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> formant wprowadził następujące ulepszenia ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="bba9b-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="bba9b-238">Wiersze można sortować za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bba9b-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="bba9b-239">Użytkownik może użyć klawisza F3 w celu sortowania według bieżącej kolumny.</span><span class="sxs-lookup"><span data-stu-id="bba9b-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="bba9b-240">Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, nagłówek kolumny zmienia kolor, aby wskazać bieżącą kolumnę jako kartę użytkownika w komórkach w bieżącym wierszu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="bba9b-241">Właściwość <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> zwraca <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> prawidłową kontrolkę nadrzędną.</span><span class="sxs-lookup"><span data-stu-id="bba9b-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="bba9b-242">**Ulepszone wskazówki wizualne**</span><span class="sxs-lookup"><span data-stu-id="bba9b-242">**Improved visual cues**</span></span>

- <span data-ttu-id="bba9b-243">I <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> formanty <xref:System.Windows.Forms.ButtonBase.Text> z pustą właściwością wyświetlają wskaźnik ostrości po otrzymaniu fokusu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="bba9b-244">**Ulepszona obsługa siatki właściwości**</span><span class="sxs-lookup"><span data-stu-id="bba9b-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="bba9b-245">Elementy <xref:System.Windows.Forms.PropertyGrid> podrzędne formantu teraz zwraca `true` dla <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> właściwości tylko wtedy, gdy PropertyGrid element jest włączona.</span><span class="sxs-lookup"><span data-stu-id="bba9b-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="bba9b-246">Elementy <xref:System.Windows.Forms.PropertyGrid> podrzędne formantu zwracają `false` dla <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> właściwości tylko wtedy, gdy PropertyGrid element może być zmieniony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bba9b-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="bba9b-247">**Ulepszona nawigacja za pomocą klawiatury**</span><span class="sxs-lookup"><span data-stu-id="bba9b-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="bba9b-248">Formant <xref:System.Windows.Forms.ToolStripButton> umożliwia ustawianie ostrości, gdy znajduje się w obrębie <xref:System.Windows.Forms.ToolStripPanel> właściwości ustawionej na <xref:System.Windows.Forms.ToolStripPanel.TabStop>`true`</span><span class="sxs-lookup"><span data-stu-id="bba9b-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="bba9b-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="bba9b-250">**Zmiany w formancie CheckBox i RadioButton**</span><span class="sxs-lookup"><span data-stu-id="bba9b-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="bba9b-251">W .NET Framework 4.7.1 i wcześniejszych <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> wersjach WPF I formanty mają niespójne i w klasycznych i kontrastu motywy niepoprawne wizualizacje fokusu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="bba9b-252">Te problemy występują w przypadkach, gdy formanty nie mają żadnych zestaw zawartości.</span><span class="sxs-lookup"><span data-stu-id="bba9b-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="bba9b-253">Może to sprawić, że przejście między motywami jest mylące, a wizualizacja ostrości jest trudna do zobaczenia.</span><span class="sxs-lookup"><span data-stu-id="bba9b-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="bba9b-254">W programie .NET Framework 4.7.2 te wizualizacje są teraz bardziej spójne w różnych motywach i są łatwiej widoczne w motywach klasycznych i kontrastowych.</span><span class="sxs-lookup"><span data-stu-id="bba9b-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="bba9b-255">**Formanty WinForms hostowane w aplikacji WPF**</span><span class="sxs-lookup"><span data-stu-id="bba9b-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="bba9b-256">W przypadku formantu WinForms hostowanego w aplikacji WPF w systemie .NET Framework 4.7.1 i wcześniejszych wersjach użytkownicy nie mogą <xref:System.Windows.Forms.Integration.ElementHost> wyjmować karty z warstwy WinForms, jeśli pierwszym lub ostatnim formantem w tej warstwie jest formant WPF.</span><span class="sxs-lookup"><span data-stu-id="bba9b-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="bba9b-257">W .NET Framework 4.7.2 użytkownicy mogą teraz wyjmować kartę z warstwy WinForms.</span><span class="sxs-lookup"><span data-stu-id="bba9b-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="bba9b-258">Jednak zautomatyzowane aplikacje, które opierają się na fokus nigdy nie ucieczki warstwy WinForms może nie działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="bba9b-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="bba9b-259">Co nowego w ułatwieniach dostępu w systemie .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="bba9b-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="bba9b-260">Program .NET Framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="bba9b-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="bba9b-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="bba9b-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bba9b-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="bba9b-263">ASP.NET kontrolki sieci Web</span><span class="sxs-lookup"><span data-stu-id="bba9b-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="bba9b-264">Narzędzia zestawu SDK platformy .NET</span><span class="sxs-lookup"><span data-stu-id="bba9b-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="bba9b-265">Projektant przepływu pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="bba9b-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="bba9b-267">**Ulepszenia czytnika ekranu**</span><span class="sxs-lookup"><span data-stu-id="bba9b-267">**Screen reader improvements**</span></span>

<span data-ttu-id="bba9b-268">Jeśli ulepszenia ułatwień dostępu są włączone, program .NET Framework 4.7.1 zawiera następujące ulepszenia, które mają wpływ na czytniki ekranu:</span><span class="sxs-lookup"><span data-stu-id="bba9b-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="bba9b-269">W .NET Framework 4.7 <xref:System.Windows.Controls.Expander> i wcześniejszych wersjach formanty zostały ogłoszone przez czytniki ekranu jako przyciski.</span><span class="sxs-lookup"><span data-stu-id="bba9b-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="bba9b-270">Począwszy od programu .NET Framework 4.7.1, są one poprawnie ogłaszane jako rozwijalne/zwijane grupy.</span><span class="sxs-lookup"><span data-stu-id="bba9b-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="bba9b-271">W .NET Framework 4.7 <xref:System.Windows.Controls.DataGridCell> i wcześniejszych wersjach formanty zostały ogłoszone przez czytniki ekranu jako "niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="bba9b-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="bba9b-272">Począwszy od programu .NET Framework 4.7.1, są one teraz poprawnie ogłoszone jako komórki siatki danych (zlokalizowane).</span><span class="sxs-lookup"><span data-stu-id="bba9b-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="bba9b-273">Począwszy od programu .NET Framework 4.7.1, czytniki ekranu ogłaszają nazwę edytowalnej <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="bba9b-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="bba9b-274">W .NET Framework 4.7 <xref:System.Windows.Controls.PasswordBox> i wcześniejszych wersjach formanty zostały ogłoszone jako "nie element w widoku" lub miał w inny sposób niepoprawne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="bba9b-275">Ten problem został rozwiązany, począwszy od programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bba9b-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="bba9b-276">**Pomoc techniczna usługi UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="bba9b-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="bba9b-277">Czytniki ekranu, takie jak Narrator, pomagają osobom odczytać zawartość interfejsu użytkownika aplikacji, zwykle przez wyjście tekstowe na mowę zawartości interfejsu użytkownika, która ma fokus.</span><span class="sxs-lookup"><span data-stu-id="bba9b-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="bba9b-278">Jednak jeśli element interfejsu użytkownika zmienia się i nie ma fokusu, użytkownik może nie zostać powiadomiony i może przegapić ważne informacje.</span><span class="sxs-lookup"><span data-stu-id="bba9b-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="bba9b-279">Regiony na żywo mają na celu rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="bba9b-280">Deweloper może ich używać do informowania czytnika ekranu lub innego klienta UIAutomation, że wprowadzono ważną zmianę w elemencie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bba9b-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="bba9b-281">Czytnik ekranu może następnie zdecydować, jak i kiedy poinformować użytkownika o tej zmianie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="bba9b-282">Aby obsługiwać aktywne regiony, do WPF WPF dodano następujące interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="bba9b-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="bba9b-283">I <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pola, które identyfikują **LiveSetting** właściwości i **LiveRegionChanged** zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bba9b-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="bba9b-284">Można je ustawić za pomocą xaml.</span><span class="sxs-lookup"><span data-stu-id="bba9b-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="bba9b-285">Właściwość **AutomationProperties.LiveSetting** dołączone, która informuje czytnik ekranu o ważności zmiany interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bba9b-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="bba9b-286">Właściwość, <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> która identyfikuje **AutomationProperties.LiveSetting** dołączone właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba9b-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="bba9b-287">Metoda, <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> która może zostać zastąpiona w celu zapewnienia wartości **LiveSetting.**</span><span class="sxs-lookup"><span data-stu-id="bba9b-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="bba9b-288">I <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, które uzyskać i ustawić **livesetting** wartość.</span><span class="sxs-lookup"><span data-stu-id="bba9b-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="bba9b-289">Wyliczenie, <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> które definiuje następujące możliwe wartości **LiveSetting:**</span><span class="sxs-lookup"><span data-stu-id="bba9b-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="bba9b-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bba9b-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bba9b-291">Element nie wysyła powiadomień, jeśli zawartość regionu na żywo uległa zmianie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="bba9b-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bba9b-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bba9b-293">Element wysyła powiadomienia nie przerywane, jeśli zawartość regionu na żywo uległa zmianie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="bba9b-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bba9b-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bba9b-295">Element wysyła powiadomienia przerywane, jeśli zawartość regionu na żywo uległa zmianie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="bba9b-296">LiveRegion można utworzyć, ustawiając **automationproperties.LiveSetting** właściwości na element zainteresowania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bba9b-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="bba9b-297">Gdy dane w regionie na żywo zmienią się i musisz poinformować czytnik ekranu, jawnie należy wywołać zdarzenie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="bba9b-298">**Wysoki kontrast**</span><span class="sxs-lookup"><span data-stu-id="bba9b-298">**High contrast**</span></span>

<span data-ttu-id="bba9b-299">Począwszy od .NET Framework 4.7.1, ulepszenia w wysokim kontraście zostały wprowadzone do różnych formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="bba9b-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="bba9b-300">Są one teraz widoczne, gdy <xref:System.Windows.SystemParameters.HighContrast%2A> motyw jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="bba9b-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="bba9b-301">Należą do nich:</span><span class="sxs-lookup"><span data-stu-id="bba9b-301">These include:</span></span>

- <span data-ttu-id="bba9b-302"><xref:System.Windows.Controls.Expander>Kontroli</span><span class="sxs-lookup"><span data-stu-id="bba9b-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="bba9b-303">Wizualizacja fokusu <xref:System.Windows.Controls.Expander> dla formantu jest teraz widoczna.</span><span class="sxs-lookup"><span data-stu-id="bba9b-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="bba9b-304">Widoczne są również <xref:System.Windows.Controls.ComboBox><xref:System.Windows.Controls.ListBox>wizualizacje <xref:System.Windows.Controls.RadioButton> klawiatury dla , i formanty.</span><span class="sxs-lookup"><span data-stu-id="bba9b-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="bba9b-305">Przykład:</span><span class="sxs-lookup"><span data-stu-id="bba9b-305">For example:</span></span>

  <span data-ttu-id="bba9b-306">Przed:</span><span class="sxs-lookup"><span data-stu-id="bba9b-306">Before:</span></span>

  ![Zrzut ekranu przedstawiający formant ekspandera z ostrości i bez wizualnej ostrości.](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="bba9b-308">Po:</span><span class="sxs-lookup"><span data-stu-id="bba9b-308">After:</span></span>

  ![Zrzut ekranu przedstawiający formant expandera z fokusem przedstawiający linię kropkowane wokół tekstu formantu.](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="bba9b-310"><xref:System.Windows.Controls.CheckBox>i <xref:System.Windows.Controls.RadioButton> kontroli</span><span class="sxs-lookup"><span data-stu-id="bba9b-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="bba9b-311">Tekst w <xref:System.Windows.Controls.CheckBox> formanty i <xref:System.Windows.Controls.RadioButton> jest teraz łatwiej widoczne, gdy zaznaczone w motywach o wysokim kontraście.</span><span class="sxs-lookup"><span data-stu-id="bba9b-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="bba9b-312">Przykład:</span><span class="sxs-lookup"><span data-stu-id="bba9b-312">For example:</span></span>

  <span data-ttu-id="bba9b-313">Przed:</span><span class="sxs-lookup"><span data-stu-id="bba9b-313">Before:</span></span>

  ![Zrzut ekranu przedstawiający przyciski radiowe i kontrolne ze słabą widocznością tekstu w motywach o wysokim kontraście.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="bba9b-315">Po:</span><span class="sxs-lookup"><span data-stu-id="bba9b-315">After:</span></span>

  ![Zrzut ekranu przedstawiający przyciski radiowe i kontrolne z lepszą widocznością tekstu w motywach o wysokim kontraście.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="bba9b-317"><xref:System.Windows.Controls.ComboBox>Kontroli</span><span class="sxs-lookup"><span data-stu-id="bba9b-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="bba9b-318">Począwszy od programu .NET Framework 4.7.1 obramowanie wyłączonego <xref:System.Windows.Controls.ComboBox> formantu jest tym samym kolorem co wyłączony tekst.</span><span class="sxs-lookup"><span data-stu-id="bba9b-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="bba9b-319">Przykład:</span><span class="sxs-lookup"><span data-stu-id="bba9b-319">For example:</span></span>

  <span data-ttu-id="bba9b-320">Przed:</span><span class="sxs-lookup"><span data-stu-id="bba9b-320">Before:</span></span>

  ![Zrzut ekranu przedstawiający wyłączone pole kombi z tekstem obramowania i kontroli w różnych kolorach.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="bba9b-322">Po:</span><span class="sxs-lookup"><span data-stu-id="bba9b-322">After:</span></span>

  ![Zrzut ekranu przedstawiający wyłączone pole kombi z obramowaniem w tym samym kolorze co tekst formantu.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="bba9b-324">Ponadto wyłączone i skoncentrowane przyciski używają prawidłowego koloru motywu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="bba9b-325">Przed:</span><span class="sxs-lookup"><span data-stu-id="bba9b-325">Before:</span></span>

  ![Zrzut ekranu przedstawiający czarny przycisk z szarym tekstem z napisem Focus Me.](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  <span data-ttu-id="bba9b-327">Po:</span><span class="sxs-lookup"><span data-stu-id="bba9b-327">After:</span></span>

  ![Zrzut ekranu przedstawiający niebieski przycisk z czarnym tekstem z napisem Focus Me.](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  <span data-ttu-id="bba9b-329">Na koniec w .NET Framework 4.7 i <xref:System.Windows.Controls.ComboBox> wcześniejszych wersjach `Toolbar.ComboBoxStyleKey` ustawienie stylu formantu spowodowało, że strzałka listy rozwijanej jest niewidoczna.</span><span class="sxs-lookup"><span data-stu-id="bba9b-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="bba9b-330">Ten problem został rozwiązany, począwszy od programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bba9b-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="bba9b-331">Przykład:</span><span class="sxs-lookup"><span data-stu-id="bba9b-331">For example:</span></span>

  <span data-ttu-id="bba9b-332">Przed:</span><span class="sxs-lookup"><span data-stu-id="bba9b-332">Before:</span></span>

  ![Zrzut ekranu przedstawiający kontrolkę ComboBox z niewidoczną strzałką rozwijaną.](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  <span data-ttu-id="bba9b-334">Po:</span><span class="sxs-lookup"><span data-stu-id="bba9b-334">After:</span></span>

  ![Zrzut ekranu przedstawiający kontrolkę ComBoxBox, wyświetlającą strzałkę rozwijaną.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <span data-ttu-id="bba9b-336"><xref:System.Windows.Controls.DataGrid>Kontroli</span><span class="sxs-lookup"><span data-stu-id="bba9b-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="bba9b-337">Począwszy od programu .NET Framework 4.7.1, strzałka wskaźnika sortowania w <xref:System.Windows.Controls.DataGrid> formantach używa teraz poprawnych kolorów motywu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="bba9b-338">Przykład:</span><span class="sxs-lookup"><span data-stu-id="bba9b-338">For example:</span></span>

  <span data-ttu-id="bba9b-339">Przed:</span><span class="sxs-lookup"><span data-stu-id="bba9b-339">Before:</span></span>

  ![Zrzut ekranu przedstawiający strzałkę wskaźnika sortowania przed ulepszeniami.](./media/whats-new-in-accessibility/sort-indicator-before.png)

  <span data-ttu-id="bba9b-341">Po:</span><span class="sxs-lookup"><span data-stu-id="bba9b-341">After:</span></span>

  ![Zrzut ekranu przedstawiający strzałkę wskaźnika sortowania po ulepszeniach.](./media/whats-new-in-accessibility/sort-indicator-after.png)

  <span data-ttu-id="bba9b-343">Ponadto w programie .NET Framework 4.7 i wcześniejszych wersjach domyślny styl łącza został zmieniony na niepoprawny kolor myszy na myszy w trybach wysokiego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="bba9b-344">To jest rozwiązane począwszy od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bba9b-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="bba9b-345">Podobnie kolumny <xref:System.Windows.Controls.DataGrid> pola wyboru używa oczekiwanych kolorów dla opinii fokus klawiatury, począwszy od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bba9b-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="bba9b-346">Przed:</span><span class="sxs-lookup"><span data-stu-id="bba9b-346">Before:</span></span>

  ![Zrzut ekranu z linkiem z napisem Kliknij mnie!](./media/whats-new-in-accessibility/default-link-style-before.png)

  <span data-ttu-id="bba9b-349">Po:</span><span class="sxs-lookup"><span data-stu-id="bba9b-349">After:</span></span>

  ![Zrzut ekranu z linkiem z napisem Kliknij mnie!](./media/whats-new-in-accessibility/default-link-style-after.png)

<span data-ttu-id="bba9b-352">Aby uzyskać więcej informacji na temat ulepszeń ułatwień dostępu WPF w programie .NET Framework 4.7.1, zobacz [ulepszenia ułatwień dostępu w programie WPF.](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)</span><span class="sxs-lookup"><span data-stu-id="bba9b-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="bba9b-353">Ulepszenia ułatwień dostępu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bba9b-353">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="bba9b-354">W programie .NET Framework 4.7.1 formularze systemu Windows (WinForms) zawierają zmiany ułatwień dostępu w następujących obszarach.</span><span class="sxs-lookup"><span data-stu-id="bba9b-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="bba9b-355">**Ulepszony wyświetlacz w trybie wysokiego kontrastu**</span><span class="sxs-lookup"><span data-stu-id="bba9b-355">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="bba9b-356">Począwszy od programu .NET Framework 4.7.1, różne formanty WinForms oferują ulepszone renderowanie w trybach HighContrast dostępnych w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="bba9b-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="bba9b-357">System Windows 10 zmienił wartości niektórych kolorów systemu o wysokim kontraście, a formularze systemu Windows są oparte na platformie Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="bba9b-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="bba9b-358">Aby uzyskać najlepsze wrażenia, uruchom w najnowszej wersji systemu Windows i zdecyduj się na najnowsze zmiany systemu operacyjnego, dodając plik app.manifest w aplikacji testowej i odkomentuj obsługiwany system operacyjny systemu Windows 10, aby wyglądał następująco:</span><span class="sxs-lookup"><span data-stu-id="bba9b-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="bba9b-359">Oto kilka przykładów zmian o wysokim kontraście:</span><span class="sxs-lookup"><span data-stu-id="bba9b-359">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="bba9b-360">Znaczniki wyboru <xref:System.Windows.Forms.MenuStrip> w elementach są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="bba9b-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="bba9b-361">Po wybraniu <xref:System.Windows.Forms.MenuStrip> tej opcji wyłączone elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="bba9b-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="bba9b-362">Tekst w <xref:System.Windows.Forms.Button> zaznaczonym formancie kontrastuje z kolorem zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="bba9b-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="bba9b-363">Wyłączony tekst jest łatwiejszy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="bba9b-363">Disabled text is easier to read.</span></span> <span data-ttu-id="bba9b-364">Przykład:</span><span class="sxs-lookup"><span data-stu-id="bba9b-364">For example:</span></span>

  <span data-ttu-id="bba9b-365">Przed:</span><span class="sxs-lookup"><span data-stu-id="bba9b-365">Before:</span></span>

  ![Zrzut ekranu przedstawiający aplikację, która używa różnych formantów uruchomionych w trybie wysokiego kontrastu przed ulepszeniami ułatwień dostępu.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  <span data-ttu-id="bba9b-367">Po:</span><span class="sxs-lookup"><span data-stu-id="bba9b-367">After:</span></span>

  ![Zrzut ekranu przedstawiający aplikację, która używa różnych formantów działających w trybie wysokiego kontrastu po ulepszeniach ułatwień dostępu.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- <span data-ttu-id="bba9b-369">Ulepszenia wysokiego kontrastu w oknie dialogowym wyjątków wątku.</span><span class="sxs-lookup"><span data-stu-id="bba9b-369">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="bba9b-370">**Ulepszona obsługa Narratora**</span><span class="sxs-lookup"><span data-stu-id="bba9b-370">**Improved Narrator support**</span></span>

<span data-ttu-id="bba9b-371">Formularze systemu Windows w programie .NET Framework 4.7.1 zawierają następujące ulepszenia ułatwień dostępu dla Narratora:</span><span class="sxs-lookup"><span data-stu-id="bba9b-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="bba9b-372">Formant <xref:System.Windows.Forms.MonthCalendar> jest dostępny dla Narratora, a także przez inne narzędzia automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bba9b-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="bba9b-373">Formant <xref:System.Windows.Forms.CheckedListBox> powiadamia Narratora, gdy stan sprawdzania elementu został zmieniony, więc użytkownik jest powiadamiany, że zmienił wartość elementu listy.</span><span class="sxs-lookup"><span data-stu-id="bba9b-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="bba9b-374">Formant <xref:System.Windows.Forms.DataGridViewCell> zgłasza narratorowi poprawny stan tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="bba9b-375">Narrator może teraz <xref:System.Windows.Forms.ToolStripMenuItem> odczytywać wyłączony tekst, podczas gdy wcześniej pomijał wyłączone elementy menu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="bba9b-376">**Ulepszona obsługa wzorców ułatwień dostępu do interfejsu użytkownika**</span><span class="sxs-lookup"><span data-stu-id="bba9b-376">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="bba9b-377">Począwszy od programu .NET Framework 4.7.1, deweloperzy narzędzi technologii ułatwień dostępu mogą korzystać z typowych wzorców ułatwień dostępu interfejsu API i właściwości dla kilku formantów WinForms.</span><span class="sxs-lookup"><span data-stu-id="bba9b-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="bba9b-378">Te ulepszenia ułatwień dostępu obejmują:</span><span class="sxs-lookup"><span data-stu-id="bba9b-378">These accessibility improvements include:</span></span>

- <span data-ttu-id="bba9b-379">I <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStripSplitButton> teraz obsługuje [rozwiń / zwiń wzorzec](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="bba9b-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="bba9b-380">Teraz <xref:System.Windows.Forms.DataGridViewCheckBoxCell> obsługuje [wzorzec przełącznika](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="bba9b-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="bba9b-381">Formant <xref:System.Windows.Forms.ToolStripItem> obsługuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwość i [wzorzec rozwiń/zwijania](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="bba9b-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="bba9b-382">I <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> kontroli obsługi <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba9b-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="bba9b-383">**Ulepszone środowisko przeglądarki właściwości**</span><span class="sxs-lookup"><span data-stu-id="bba9b-383">**Improved property browser experience**</span></span>

<span data-ttu-id="bba9b-384">Począwszy od programu .NET Framework 4.7.1, formularze systemu Windows obejmują:</span><span class="sxs-lookup"><span data-stu-id="bba9b-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="bba9b-385">Lepsza nawigacja za pomocą klawiatury przez różne okna wyboru rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="bba9b-385">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="bba9b-386">Redukcja niepotrzebnych tabulatorów.</span><span class="sxs-lookup"><span data-stu-id="bba9b-386">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="bba9b-387">Lepsze raportowanie typów kontroli.</span><span class="sxs-lookup"><span data-stu-id="bba9b-387">Better reporting of control types.</span></span>
- <span data-ttu-id="bba9b-388">Poprawiono zachowanie narratora.</span><span class="sxs-lookup"><span data-stu-id="bba9b-388">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="bba9b-389">ASP.NET kontrolki sieci Web</span><span class="sxs-lookup"><span data-stu-id="bba9b-389">ASP.NET web controls</span></span>

<span data-ttu-id="bba9b-390">Począwszy od platformy .NET Framework 4.7.1 i programu Visual Studio 2017 w wersji 15.3, ASP.NET poprawia sposób pracy formantów sieci Web ASP.NET z technologią ułatwień dostępu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bba9b-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="bba9b-391">Zmiany są następujące:</span><span class="sxs-lookup"><span data-stu-id="bba9b-391">Changes include the following:</span></span>

- <span data-ttu-id="bba9b-392">Zmiany implementujące brakujące wzorce ułatwień dostępu interfejsu użytkownika w formantych, takie jak okno dialogowe **Dodawanie pola** w kreatorze **widoku szczegółów** lub okno dialogowe **Konfigurowanie widoku listy** **kreatora ListView.**</span><span class="sxs-lookup"><span data-stu-id="bba9b-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="bba9b-393">Zmiany w celu poprawy wyświetlania w trybie wysokiego kontrastu, takie jak **Edytor pól pagera danych**.</span><span class="sxs-lookup"><span data-stu-id="bba9b-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="bba9b-394">Zmiany ułatwiające nawigację za pomocą klawiatury dla kontrolek, takie jak okno dialogowe **Pola** w kreatorze **Edytowanie pól pagera** formantu DataPager, okno dialogowe **Konfigurowanie obiektuContext** lub Okno dialogowe **Konfigurowanie wyboru danych** **kreatora Konfigurowanie źródła danych.**</span><span class="sxs-lookup"><span data-stu-id="bba9b-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="bba9b-395">Narzędzia zestawu SDK platformy .NET</span><span class="sxs-lookup"><span data-stu-id="bba9b-395">.NET SDK Tools</span></span>

<span data-ttu-id="bba9b-396">[Narzędzie Edytor konfiguracji (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) i Narzędzie Podgląd śledzenia usług [(SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) zostały ulepszone przez naprawienie różnych problemów z dostępnością.</span><span class="sxs-lookup"><span data-stu-id="bba9b-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="bba9b-397">Większość z nich były małe problemy, takie jak nazwa nie jest zdefiniowana lub niektórych wzorców automatyzacji interfejsu użytkownika nie są implementowane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="bba9b-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="bba9b-398">Podczas gdy wielu użytkowników nie będzie świadomych tych niepoprawnych wartości, klienci korzystający z technologii wspomagających, takich jak czytniki ekranu, znajdą te narzędzia zestawu SDK bardziej dostępne.</span><span class="sxs-lookup"><span data-stu-id="bba9b-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="bba9b-399">Te ulepszenia zmieniają niektóre poprzednie zachowania, takie jak kolejność fokusu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bba9b-399">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="bba9b-400">Projektant przepływu pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="bba9b-400">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="bba9b-401">Zmiany ułatwień dostępu w Projektancie przepływu pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="bba9b-401">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="bba9b-402">Kolejność kart zmienia się na lewo do prawej i od góry do dołu w niektórych formantach:</span><span class="sxs-lookup"><span data-stu-id="bba9b-402">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="bba9b-403">Okno korelacji inicjowania ustawiania danych <xref:System.ServiceModel.Activities.InitializeCorrelation> korelacji dla działania.</span><span class="sxs-lookup"><span data-stu-id="bba9b-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="bba9b-404">Okno definicji zawartości <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send>dla <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply> , i działań.</span><span class="sxs-lookup"><span data-stu-id="bba9b-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="bba9b-405">Więcej funkcji jest dostępnych za pośrednictwem klawiatury:</span><span class="sxs-lookup"><span data-stu-id="bba9b-405">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="bba9b-406">Podczas edytowania właściwości działania grupy właściwości mogą być zwinięte za pomocą klawiatury przy pierwszym skupieniu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="bba9b-407">Ikony ostrzeżeń są dostępne za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bba9b-407">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="bba9b-408">Przycisk **Więcej właściwości** w oknie **Właściwości** jest dostępny za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bba9b-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="bba9b-409">Użytkownicy klawiatury mogą uzyskiwać dostęp do elementów nagłówka w okienkach **Argumenty** i **zmienne** Projektanta przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bba9b-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="bba9b-410">Lepsza widoczność elementów z ostrością, na przykład kiedy:</span><span class="sxs-lookup"><span data-stu-id="bba9b-410">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="bba9b-411">Dodawanie wierszy do siatek danych używanych przez projektanta przepływu pracy i projektantów działań.</span><span class="sxs-lookup"><span data-stu-id="bba9b-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="bba9b-412">Tabbing przez pola <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> w i działań.</span><span class="sxs-lookup"><span data-stu-id="bba9b-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="bba9b-413">Ustawianie wartości domyślnych dla zmiennych lub argumentów</span><span class="sxs-lookup"><span data-stu-id="bba9b-413">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="bba9b-414">Czytniki ekranu mogą teraz poprawnie rozpoznawać:</span><span class="sxs-lookup"><span data-stu-id="bba9b-414">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="bba9b-415">Punkty przerwania ustawione w projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bba9b-415">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="bba9b-416">, <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowDecision>i <xref:System.ServiceModel.Activities.CorrelationScope> działań.</span><span class="sxs-lookup"><span data-stu-id="bba9b-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="bba9b-417">Zawartość <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="bba9b-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="bba9b-418">Typ docelowy <xref:System.Activities.Statements.InvokeMethod> dla działania.</span><span class="sxs-lookup"><span data-stu-id="bba9b-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="bba9b-419">Pole kombi Wyjątek i Finally <xref:System.Activities.Statements.TryCatch> sekcji w działaniu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="bba9b-420">Pole kombi Typ wiadomości, rozdzielacz w oknie Dodaj inicjatory korelacji, okno Definicja zawartości i Okno Skoreluje definicję w działaniach obsługi<xref:System.ServiceModel.Activities.Receive>wiadomości ( , <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="bba9b-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="bba9b-421">Przejścia maszyny stanu i przejścia miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="bba9b-421">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="bba9b-422">Adnotacje i łączniki dotyczące <xref:System.Activities.Statements.FlowDecision> działań.</span><span class="sxs-lookup"><span data-stu-id="bba9b-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="bba9b-423">Menu kontekstu (kliknięcie prawym przyciskiem myszy) dla działań.</span><span class="sxs-lookup"><span data-stu-id="bba9b-423">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="bba9b-424">Edytory wartości właściwości, przycisk Wyczyść wyszukiwanie, przyciski według kategorii i sortowania alfabetycznego oraz okno dialogowe Edytor wyrażeń w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="bba9b-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="bba9b-425">Procent powiększenia w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bba9b-425">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="bba9b-426">Separator <xref:System.Activities.Statements.Parallel> i <xref:System.Activities.Statements.Pick> działania.</span><span class="sxs-lookup"><span data-stu-id="bba9b-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="bba9b-427">Działanie. <xref:System.Activities.Statements.InvokeDelegate></span><span class="sxs-lookup"><span data-stu-id="bba9b-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="bba9b-428">Okno Wybierz typy dla działań słownikowych (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`itp.).</span><span class="sxs-lookup"><span data-stu-id="bba9b-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="bba9b-429">Okno Przeglądaj i wybierz typ .NET.</span><span class="sxs-lookup"><span data-stu-id="bba9b-429">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="bba9b-430">Breadcrumbs w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bba9b-430">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="bba9b-431">Użytkownicy, którzy wybiorą motywy o wysokim kontraście, zobaczą wiele ulepszeń w widoczności projektanta przepływu pracy i jego formantów, takich jak lepsze współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używane dla elementów fokusu.</span><span class="sxs-lookup"><span data-stu-id="bba9b-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="bba9b-432">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bba9b-432">See also</span></span>

- [<span data-ttu-id="bba9b-433">Co nowego w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bba9b-433">What's new in the .NET Framework</span></span>](index.md)
