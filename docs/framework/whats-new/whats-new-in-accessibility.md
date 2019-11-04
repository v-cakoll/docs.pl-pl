---
title: Co nowego w ułatwieniach dostępu w .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 22d70d0ee976d9c1a6aabd57e5d13dc70cd2d081
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454259"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="41ff5-102">Co nowego w ułatwieniach dostępu w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="41ff5-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="41ff5-103">.NET Framework ma na celu zwiększenie dostępności aplikacji dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="41ff5-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="41ff5-104">Funkcje ułatwień dostępu umożliwiają aplikacji zapewnienie odpowiedniego środowiska dla użytkowników technologii pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="41ff5-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="41ff5-105">Począwszy od .NET Framework 4.7.1, .NET Framework obejmuje dużą liczbę ulepszeń ułatwień dostępu, które umożliwiają deweloperom tworzenie dostępnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41ff5-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="41ff5-106">Przełączniki ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="41ff5-106">Accessibility switches</span></span>

<span data-ttu-id="41ff5-107">Można skonfigurować aplikację do korzystania z funkcji ułatwień dostępu, jeśli jest ona przeznaczona dla .NET Framework 4,7 lub wcześniejszej wersji, ale działa w systemie .NET Framework 4.7.1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="41ff5-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="41ff5-108">Możesz również skonfigurować aplikację tak, aby korzystała ze starszych funkcji (i nie korzystać z funkcji ułatwień dostępu), jeśli jest ona przeznaczona dla .NET Framework 4.7.1 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="41ff5-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="41ff5-109">Każda wersja .NET Framework, która obejmuje funkcje ułatwień dostępu, ma przełącznik dostępności specyficzny dla wersji, który można dodać do elementu [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w sekcji [`<runtime>`](../configure-apps/file-schema/runtime/index.md) pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41ff5-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="41ff5-110">Obsługiwane są następujące przełączniki:</span><span class="sxs-lookup"><span data-stu-id="41ff5-110">The following are the supported switches:</span></span>

|<span data-ttu-id="41ff5-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="41ff5-111">Version</span></span>|<span data-ttu-id="41ff5-112">Przełącznik</span><span class="sxs-lookup"><span data-stu-id="41ff5-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="41ff5-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="41ff5-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="41ff5-114">"Switch. UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="41ff5-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="41ff5-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="41ff5-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="41ff5-116">"Switch. UseLegacyAccessibilityFeatures. 2"</span><span class="sxs-lookup"><span data-stu-id="41ff5-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="41ff5-117">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="41ff5-117">.NET Framework 4.8</span></span>|<span data-ttu-id="41ff5-118">"Switch. UseLegacyAccessibilityFeatures. 3"</span><span class="sxs-lookup"><span data-stu-id="41ff5-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="41ff5-119">Korzystanie z ulepszeń ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="41ff5-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="41ff5-120">Nowe funkcje ułatwień dostępu są domyślnie włączone dla aplikacji przeznaczonych .NET Framework 4.7.1 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="41ff5-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="41ff5-121">Ponadto aplikacje przeznaczone dla starszej wersji .NET Framework ale działają na .NET Framework 4.7.1 lub nowszych mogą zrezygnować ze starszych zachowań dostępności (a tym samym korzystać z ulepszeń ułatwień dostępu) poprzez dodanie przełączników do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element w sekcji [`<runtime>`](../configure-apps/file-schema/runtime/index.md) pliku konfiguracyjnego aplikacji i ustawienie ich wartości na `false`.</span><span class="sxs-lookup"><span data-stu-id="41ff5-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="41ff5-122">Poniżej pokazano, jak wybrać ulepszenia ułatwień dostępu wprowadzone w .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="41ff5-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="41ff5-123">W przypadku wybrania opcji ułatwienia dostępu w nowszej wersji .NET Framework należy również jawnie zadecydować o funkcjach wcześniejszych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41ff5-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="41ff5-124">Konfigurowanie aplikacji w celu wykorzystania ulepszeń ułatwień dostępu w systemach .NET Framework 4.7.1 i 4.7.2 wymaga następującego elementu [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) :</span><span class="sxs-lookup"><span data-stu-id="41ff5-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="41ff5-125">Konfigurowanie aplikacji w celu skorzystania z ulepszeń ułatwień dostępu w .NET Framework 4.7.1, 4.7.2 i 4,8 wymaga następującego elementu [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) :</span><span class="sxs-lookup"><span data-stu-id="41ff5-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="41ff5-126">Przywracanie starszego zachowania</span><span class="sxs-lookup"><span data-stu-id="41ff5-126">Restoring legacy behavior</span></span>

<span data-ttu-id="41ff5-127">Aplikacje, które są przeznaczone dla wersji .NET Framework zaczynających się od 4.7.1, mogą wyłączyć funkcje ułatwień dostępu, dodając przełączniki do elementu [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) w sekcji [`<runtime>`](../configure-apps/file-schema/runtime/index.md) pliku konfiguracyjnego aplikacji i ustawiając ich wartość do `true`.</span><span class="sxs-lookup"><span data-stu-id="41ff5-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="41ff5-128">Na przykład następujące czynności konfiguracyjne nie są związane z funkcjami ułatwień dostępu wprowadzonymi w .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="41ff5-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="41ff5-129">Nowości w ułatwieniach dostępu w .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="41ff5-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="41ff5-130">.NET Framework 4,8 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="41ff5-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="41ff5-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41ff5-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="41ff5-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="41ff5-133">Projektant przepływu pracy Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="41ff5-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41ff5-134">Windows Forms</span></span>

<span data-ttu-id="41ff5-135">W .NET Framework 4,8 Windows Forms dodaje obsługę LiveRegions i zdarzeń powiadomień do wielu często używanych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="41ff5-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="41ff5-136">Dodaje również obsługę etykietek narzędzi, gdy użytkownik przechodzi do formantu przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="41ff5-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="41ff5-137">**UIA LiveRegions support w etykietach i StatusStrip**</span><span class="sxs-lookup"><span data-stu-id="41ff5-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="41ff5-138">UIA LiveRegions umożliwiają deweloperom aplikacji powiadamianie czytników ekranu o zmianie tekstu w kontrolce, która znajduje się poza lokalizacją, w której pracuje użytkownik.</span><span class="sxs-lookup"><span data-stu-id="41ff5-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="41ff5-139">Jest to przydatne na przykład w przypadku kontrolki <xref:System.Windows.Forms.StatusStrip>, która wyświetla stan połączenia.</span><span class="sxs-lookup"><span data-stu-id="41ff5-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="41ff5-140">Jeśli połączenie zostanie przerwane i stan zmieni się, deweloper może chcieć powiadomić czytnik ekranu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="41ff5-141">Począwszy od .NET Framework 4,8, Windows Forms implementuje UIA LiveRegions dla formantów <xref:System.Windows.Forms.Label> i <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="41ff5-142">Na przykład poniższy kod używa LiveRegion w kontrolce <xref:System.Windows.Forms.Label> o nazwie `label1`:</span><span class="sxs-lookup"><span data-stu-id="41ff5-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="41ff5-143">Narrator ogłasza "gotowe" niezależnie od tego, gdzie użytkownik jest w stanie korzystać z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41ff5-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="41ff5-144">Możesz również zaimplementować <xref:System.Windows.Forms.UserControl> jako LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="41ff5-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="41ff5-145">**UIA zdarzenia powiadomień**</span><span class="sxs-lookup"><span data-stu-id="41ff5-145">**UIA notification events**</span></span>

<span data-ttu-id="41ff5-146">Zdarzenie powiadamiania UIA wprowadzone w ramach aktualizacji systemu Windows 10 z aktualizacją dla twórców pozwala aplikacji na zgłaszanie zdarzenia UIA, które prowadzi do Narratora w oparciu o tekst dostarczany wraz ze zdarzeniem, bez konieczności posiadania odpowiedniej kontrolki w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41ff5-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="41ff5-147">W niektórych scenariuszach jest to prosty sposób znacznie zwiększyć dostępność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41ff5-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="41ff5-148">W programie może być również przydatne powiadamianie o postępie niektórych procesów, które mogą zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="41ff5-149">Aby uzyskać więcej informacji na temat zdarzeń powiadomień UIA, zobacz [czy aplikacja klasyczna korzysta z nowego zdarzenia powiadamiania o interfejsie użytkownika?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span><span class="sxs-lookup"><span data-stu-id="41ff5-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span></span>

<span data-ttu-id="41ff5-150">Poniższy przykład podnosi [zdarzenie powiadomienia](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="41ff5-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="41ff5-151">**Etykietki narzędzi na dostępie z klawiatury**</span><span class="sxs-lookup"><span data-stu-id="41ff5-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="41ff5-152">W aplikacjach, które są przeznaczone .NET Framework 4.7.2 i starszych wersji, [etykietka narzędzia](xref:System.Windows.Forms.ToolTip) kontrolki może być wyzwalana tylko w celu przechodzenia do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="41ff5-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="41ff5-153">Począwszy od .NET Framework 4,8, użytkownik klawiatury może wyzwolić etykietkę narzędzia kontrolki za pomocą klawisza TAB lub klawiszy strzałek z klawiszami modyfikującymi lub bez.</span><span class="sxs-lookup"><span data-stu-id="41ff5-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="41ff5-154">To konkretne ulepszenie ułatwień dostępu wymaga dodatkowego [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="41ff5-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="41ff5-155">Na poniższej ilustracji przedstawiono etykietkę narzędzia, gdy użytkownik wybierze przycisk z klawiaturą.</span><span class="sxs-lookup"><span data-stu-id="41ff5-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Etykietka narzędzia, gdy użytkownik przechodzi do przycisku przy użyciu klawiatury](./media/tooltip.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="41ff5-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="41ff5-158">Począwszy od .NET Framework 4,8, WPF obejmuje wiele ulepszeń ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="41ff5-159">**Narratory ekranu nie ogłaszają już elementów z zwiniętym lub ukrytym widocznością**</span><span class="sxs-lookup"><span data-stu-id="41ff5-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="41ff5-160">Elementy z zwiniętym lub ukrytym widocznością nie są już anonsowane przez czytnik ekranu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="41ff5-161">Interfejsy użytkownika, które zawierają elementy z widocznością <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> lub <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> mogą być reprezentowane przez czytniki ekranu, jeśli są ogłoszone dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41ff5-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="41ff5-162">Począwszy od .NET Framework 4,8, WPF nie obejmuje już elementów zwiniętych lub ukrytych w widoku sterowania drzewa UIAutomation, dzięki czemu czytniki zawartości ekranu nie będą już ogłaszać tych elementów.</span><span class="sxs-lookup"><span data-stu-id="41ff5-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="41ff5-163">**Właściwość SelectionTextBrush do użycia z zaznaczonym tekstem innym niż moduł definiowania układu**</span><span class="sxs-lookup"><span data-stu-id="41ff5-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="41ff5-164">W .NET Framework 4.7.2, WPF dodaliśmy możliwość rysowania <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox> zaznaczania tekstu bez użycia warstwy modułu definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="41ff5-165">Kolor pierwszego planu zaznaczonego tekstu w tym scenariuszu został podyktowany przez <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="41ff5-166">.NET Framework 4,8 dodaje nową właściwość `SelectionTextBrush`, która umożliwia deweloperom wybranie określonego pędzla dla zaznaczonego tekstu przy użyciu zaznaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="41ff5-167">Ta właściwość działa tylko na kontrolkach pochodnych <xref:System.Windows.Controls.Primitives.TextBoxBase>i kontrolce <xref:System.Windows.Controls.PasswordBox> w aplikacjach WPF z włączonym zaznaczeniem tekstu innym niż moduł definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="41ff5-168">Nie działa on w kontrolce <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="41ff5-169">Jeśli wybór tekstu nie jest włączony, ta właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="41ff5-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="41ff5-170">Aby użyć tej właściwości, wystarczy dodać ją do kodu XAML i użyć odpowiedniego pędzla lub powiązania.</span><span class="sxs-lookup"><span data-stu-id="41ff5-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="41ff5-171">Wynikowy wybór tekstu wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="41ff5-171">The resulting text selection looks like this:</span></span>

![Etykietka narzędzia, gdy użytkownik przechodzi do przycisku przy użyciu klawiatury](./media/selectiontextbrush-property.png)

<span data-ttu-id="41ff5-173">Można połączyć użycie właściwości `SelectionBrush` i `SelectionTextBrush`, aby wygenerować wszelkie kombinacje kolorów tła i pierwszego planu, które są uważane za odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="41ff5-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="41ff5-174">**Obsługa właściwości UIAutomation ControllerFor**</span><span class="sxs-lookup"><span data-stu-id="41ff5-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="41ff5-175">Właściwość `ControllerFor` UIAutomation zwraca tablicę elementów automatyzacji, które są manipulowane przez element automatyzacji, który obsługuje tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="41ff5-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="41ff5-176">Ta właściwość jest często używana do automatycznego sugerowania ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="41ff5-177">`ControllerFor` jest używany, gdy element automatyzacji ma wpływ na jeden lub więcej segmentów interfejsu użytkownika aplikacji lub pulpitu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="41ff5-178">W przeciwnym razie trudno jest powiązać wpływ operacji sterowania z elementami interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41ff5-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="41ff5-179">Ta funkcja dodaje możliwość kontroli w celu udostępnienia wartości właściwości `ControllerFor`.</span><span class="sxs-lookup"><span data-stu-id="41ff5-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="41ff5-180">.NET Framework 4,8 dodaje nową metodę wirtualną, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41ff5-181">Aby podać wartość właściwości `ControllerFor`, wystarczy przesłonić tę metodę i zwrócić `List<AutomationPeer>` dla kontrolek manipulowanych przez tę <xref:System.Windows.Automation.Peers.AutomationPeer>:</span><span class="sxs-lookup"><span data-stu-id="41ff5-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="41ff5-182">**Etykietki narzędzi na dostępie z klawiatury**</span><span class="sxs-lookup"><span data-stu-id="41ff5-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="41ff5-183">W .NET Framework 4.7.2 i starszych wersjach etykietki narzędzi są wyświetlane tylko wtedy, gdy użytkownik umieści kursor myszy nad kontrolką.</span><span class="sxs-lookup"><span data-stu-id="41ff5-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="41ff5-184">W .NET Framework 4,8 etykietki narzędzi są również wyświetlane na nacisk klawiatury, a także za pomocą skrótu klawiaturowego.</span><span class="sxs-lookup"><span data-stu-id="41ff5-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="41ff5-185">Aby włączyć tę funkcję, aplikacja musi być ukierunkowana na .NET Framework 4,8 lub zadecydować przy użyciu `Switch.UseLegacyAccessibilityFeatures.3` i `Switch.UseLegacyToolTipDisplay` przełączników [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) .</span><span class="sxs-lookup"><span data-stu-id="41ff5-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="41ff5-186">Poniżej znajduje się przykładowy plik konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="41ff5-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="41ff5-187">Po włączeniu wszystkie kontrolki zawierające etykietkę narzędzia wyświetlają ją, gdy kontrolka odbierze fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="41ff5-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="41ff5-188">Etykietka narzędzia może zostać odrzucona z upływem czasu lub po zmianie fokusu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="41ff5-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="41ff5-189">Użytkownicy mogą również odrzucić etykietkę narzędzia ręcznie przy użyciu nowego skrótu klawiaturowego, Ctrl + Shift + F10.</span><span class="sxs-lookup"><span data-stu-id="41ff5-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="41ff5-190">Gdy etykietka narzędzia zostanie odrzucona, może być ponownie wyświetlana przy użyciu tego samego skrótu klawiaturowego.</span><span class="sxs-lookup"><span data-stu-id="41ff5-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="41ff5-191">[Etykietki narzędzi wstążki](xref:System.Windows.Controls.Ribbon.RibbonToolTip) w kontrolkach <xref:System.Windows.Controls.Ribbon.Ribbon> nie będą wyświetlane na fokus klawiatury; są one wyświetlane tylko za pomocą skrótu klawiaturowego.</span><span class="sxs-lookup"><span data-stu-id="41ff5-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="41ff5-192">**Dodano obsługę właściwości SizeOfSet i PositionInSet UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="41ff5-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="41ff5-193">System Windows 10 wprowadził dwie nowe właściwości UIAutomation, `SizeOfSet` i `PositionInSet`, które są używane przez aplikacje do opisywania liczby elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="41ff5-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="41ff5-194">UIAutomation aplikacje klienckie, takie jak czytniki zawartości ekranu, mogą następnie wysyłać zapytania do aplikacji, aby ogłosić dokładną reprezentację interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41ff5-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="41ff5-195">Począwszy od .NET Framework 4,8, WPF uwidacznia te dwie właściwości UIAutomation w aplikacjach WPF.</span><span class="sxs-lookup"><span data-stu-id="41ff5-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="41ff5-196">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="41ff5-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="41ff5-197">Przy użyciu właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="41ff5-197">By using dependency properties.</span></span>

  <span data-ttu-id="41ff5-198">WPF dodaje dwie nowe właściwości zależności, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41ff5-199">Deweloper może użyć języka XAML, aby ustawić ich wartości:</span><span class="sxs-lookup"><span data-stu-id="41ff5-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="41ff5-200">Przez zastępowanie metod wirtualnych AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="41ff5-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="41ff5-201">Metody wirtualne <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> zostały dodane do klasy AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="41ff5-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="41ff5-202">Deweloper może podać wartości `SizeOfSet` i `PositionInSet`, zastępując te metody, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="41ff5-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="41ff5-203">Ponadto elementy w <xref:System.Windows.Controls.ItemsControl> wystąpieniach udostępniają wartość tych właściwości automatycznie bez dodatkowej akcji od dewelopera.</span><span class="sxs-lookup"><span data-stu-id="41ff5-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="41ff5-204">Jeśli <xref:System.Windows.Controls.ItemsControl> jest zgrupowane, Kolekcja grup jest reprezentowana jako zestaw, a każda grupa jest traktowana jako oddzielny zestaw, przy czym każdy element wewnątrz tej grupy udostępnia swoją pozycję wewnątrz tej grupy, a także rozmiar grupy.</span><span class="sxs-lookup"><span data-stu-id="41ff5-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="41ff5-205">Wirtualizacja nie ma wpływ na wartości automatyczne.</span><span class="sxs-lookup"><span data-stu-id="41ff5-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="41ff5-206">Nawet jeśli element nie jest zrealizowany, nadal jest liczony do całkowitego rozmiaru zestawu i ma wpływ na pozycję w zestawie elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="41ff5-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="41ff5-207">Wartości automatyczne są dostępne tylko wtedy, gdy aplikacja jest docelowa .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="41ff5-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="41ff5-208">W przypadku aplikacji przeznaczonych dla starszej wersji .NET Framework można ustawić [przełącznik `Switch.UseLegacyAccessibilityFeatures.3` AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak pokazano w następującym pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="41ff5-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="41ff5-209">Projektant przepływu pracy Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="41ff5-210">Projektant przepływu pracy obejmuje następujące zmiany w .NET Framework 4,8:</span><span class="sxs-lookup"><span data-stu-id="41ff5-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="41ff5-211">Użytkownicy korzystający z programu Narrator zobaczą ulepszenia w etykietach przypadków FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="41ff5-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="41ff5-212">Użytkownicy korzystający z programu Narrator zobaczą ulepszenia w opisach przycisków.</span><span class="sxs-lookup"><span data-stu-id="41ff5-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="41ff5-213">Użytkownicy, którzy wybierają duży kontrast motywy zobaczą ulepszenia widoczności Projektant przepływu pracy i jej kontrolek, takich jak lepsze współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używane na potrzeby elementów fokusu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="41ff5-214">Jeśli aplikacja jest przeznaczona .NET Framework 4.7.2 lub starsza wersja, możesz zmienić te zmiany, ustawiając [przełącznik `Switch.UseLegacyAccessibilityFeatures.3` AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) , aby `false` w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41ff5-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="41ff5-215">Aby uzyskać więcej informacji, zobacz sekcję [Korzystanie z ulepszeń ułatwień dostępu](#taking-advantage-of-accessibility-enhancements) w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="41ff5-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="41ff5-216">Nowości w ułatwieniach dostępu w programie .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="41ff5-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="41ff5-217">Program .NET Framework 4.7.2 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="41ff5-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="41ff5-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41ff5-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="41ff5-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="41ff5-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41ff5-220">Windows Forms</span></span>

<span data-ttu-id="41ff5-221">**Kolory zdefiniowane przez system operacyjny w duży kontrast motywy**</span><span class="sxs-lookup"><span data-stu-id="41ff5-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="41ff5-222">Począwszy od .NET Framework 4.7.2, Windows Forms używa kolorów zdefiniowanych przez system operacyjny w duży kontrast motywach.</span><span class="sxs-lookup"><span data-stu-id="41ff5-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="41ff5-223">Ma to wpływ na następujące kontrolki:</span><span class="sxs-lookup"><span data-stu-id="41ff5-223">This affects the following controls:</span></span>

- <span data-ttu-id="41ff5-224">Strzałka listy rozwijanej kontrolki <xref:System.Windows.Forms.ToolStripDropDownButton>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="41ff5-225">Kontrolki <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> z <xref:System.Windows.Forms.ButtonBase.FlatStyle> ustawionym na <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41ff5-226">Wcześniej wybrane kolory tekstu i tła nie były kontrastowe i były trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="41ff5-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="41ff5-227">Kontrolki zawarte w <xref:System.Windows.Forms.GroupBox>, które mają właściwość <xref:System.Windows.Forms.Control.Enabled> ustawioną na `false`.</span><span class="sxs-lookup"><span data-stu-id="41ff5-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="41ff5-228">Kontrolki <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>i <xref:System.Windows.Forms.ToolStripDropDownButton> o zwiększonej proporcji kontrastu w trybie duży kontrast.</span><span class="sxs-lookup"><span data-stu-id="41ff5-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="41ff5-229">Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="41ff5-230">**Ulepszenia Narratora**</span><span class="sxs-lookup"><span data-stu-id="41ff5-230">**Narrator improvements**</span></span>

<span data-ttu-id="41ff5-231">Począwszy od .NET Framework 4.7.2, obsługa Narratora została ulepszona w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="41ff5-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="41ff5-232">Anonsuje wartość właściwości <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> podczas ogłaszania tekstu <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="41ff5-233">Wskazuje, kiedy <xref:System.Windows.Forms.ToolStripMenuItem> ma właściwość <xref:System.Windows.Forms.Control.Enabled> ustawioną na `false`.</span><span class="sxs-lookup"><span data-stu-id="41ff5-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="41ff5-234">Przekazuje ona informacje zwrotne o stanie pola wyboru, gdy właściwość <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="41ff5-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="41ff5-235">Kolejność fokusu trybu skanowania programu Narrator jest zgodna z kolejnością wizualizacji kontrolek w oknie dialogowym pobierania ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="41ff5-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="41ff5-236">**Usprawnienia formantu DataGridView**</span><span class="sxs-lookup"><span data-stu-id="41ff5-236">**DataGridView improvements**</span></span>

<span data-ttu-id="41ff5-237">Począwszy od .NET Framework 4.7.2, kontrolka <xref:System.Windows.Forms.DataGridView> wprowadziła następujące usprawnienia ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="41ff5-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="41ff5-238">Wiersze można sortować przy użyciu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="41ff5-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="41ff5-239">Użytkownik może użyć klawisza F3, aby posortować według bieżącej kolumny.</span><span class="sxs-lookup"><span data-stu-id="41ff5-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="41ff5-240">Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> jest ustawiona na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, nagłówek kolumny zmieni kolor, aby wskazać bieżącą kolumnę jako karty użytkownika przez komórki w bieżącym wierszu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="41ff5-241">Właściwość <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> zwraca poprawną kontrolkę nadrzędną.</span><span class="sxs-lookup"><span data-stu-id="41ff5-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="41ff5-242">**Ulepszone podpowiedzi wizualne**</span><span class="sxs-lookup"><span data-stu-id="41ff5-242">**Improved visual cues**</span></span>

- <span data-ttu-id="41ff5-243">Kontrolki <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> z pustą właściwością <xref:System.Windows.Forms.ButtonBase.Text> wyświetlają wskaźnik ostrości po otrzymaniu fokusu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="41ff5-244">**Ulepszona obsługa siatki właściwości**</span><span class="sxs-lookup"><span data-stu-id="41ff5-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="41ff5-245">Elementy podrzędne formantu <xref:System.Windows.Forms.PropertyGrid> teraz zwracają `true` właściwości <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> tylko wtedy, gdy element PropertyGrid jest włączony.</span><span class="sxs-lookup"><span data-stu-id="41ff5-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="41ff5-246">Elementy podrzędne formantu <xref:System.Windows.Forms.PropertyGrid> zwracają `false` właściwości <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> tylko wtedy, gdy użytkownik może zmienić element PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="41ff5-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="41ff5-247">**Ulepszone nawigowanie po klawiaturze**</span><span class="sxs-lookup"><span data-stu-id="41ff5-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="41ff5-248">Formant <xref:System.Windows.Forms.ToolStripButton> umożliwia fokus, gdy jest zawarty w <xref:System.Windows.Forms.ToolStripPanel>, który ma właściwość <xref:System.Windows.Forms.ToolStripPanel.TabStop> ustawioną na `true`</span><span class="sxs-lookup"><span data-stu-id="41ff5-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="41ff5-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="41ff5-250">**Zmiany w kontrolkach CheckBox i RadioButton**</span><span class="sxs-lookup"><span data-stu-id="41ff5-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="41ff5-251">W .NET Framework 4.7.1 i starszych wersjach, formanty WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> i <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> są niespójne, a w kompozycjach klasycznych i duży kontrast, nieprawidłowe wizualizacje fokusu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="41ff5-252">Te problemy występują w przypadkach, gdy kontrolki nie mają żadnego zestawu zawartości.</span><span class="sxs-lookup"><span data-stu-id="41ff5-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="41ff5-253">Może to spowodować, że przejście między motywami jest mylące i wizualizacja fokusu będzie widoczna.</span><span class="sxs-lookup"><span data-stu-id="41ff5-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="41ff5-254">W .NET Framework 4.7.2 te wizualizacje są teraz bardziej spójne w różnych motywach i łatwiej widoczne w klasycznych i duży kontrast motywach.</span><span class="sxs-lookup"><span data-stu-id="41ff5-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="41ff5-255">**Kontrolki WinForms hostowane w aplikacji WPF**</span><span class="sxs-lookup"><span data-stu-id="41ff5-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="41ff5-256">W przypadku kontrolki WinForms hostowanej w aplikacji WPF w .NET Framework 4.7.1 i starszych wersjach użytkownicy nie mogli wystawić z warstwy WinForms, jeśli pierwszy lub ostatni formant w tej warstwie jest formantem <xref:System.Windows.Forms.Integration.ElementHost> WPF.</span><span class="sxs-lookup"><span data-stu-id="41ff5-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="41ff5-257">W .NET Framework 4.7.2 Użytkownicy mogą teraz wystawić kartę z warstwy WinForms.</span><span class="sxs-lookup"><span data-stu-id="41ff5-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="41ff5-258">Jednak zautomatyzowane aplikacje, które opierają się na koncentracji, nigdy nie ucieczką warstwy WinForms, mogą przestać działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="41ff5-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="41ff5-259">Nowości w ułatwieniach dostępu w programie .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="41ff5-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="41ff5-260">Program .NET Framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="41ff5-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="41ff5-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="41ff5-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41ff5-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="41ff5-263">Kontrolki sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="41ff5-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="41ff5-264">SDK Tools .NET</span><span class="sxs-lookup"><span data-stu-id="41ff5-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="41ff5-265">Projektant przepływu pracy Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="41ff5-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="41ff5-267">**Ulepszenia czytnika ekranu**</span><span class="sxs-lookup"><span data-stu-id="41ff5-267">**Screen reader improvements**</span></span>

<span data-ttu-id="41ff5-268">W przypadku włączenia ulepszeń ułatwień dostępu .NET Framework 4.7.1 obejmuje następujące udoskonalenia, które mają wpływ na czytniki zawartości ekranu:</span><span class="sxs-lookup"><span data-stu-id="41ff5-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="41ff5-269">W .NET Framework 4,7 i wcześniejszych wersjach kontrolki <xref:System.Windows.Controls.Expander> zostały ogłoszone przez czytniki ekranu jako przyciski.</span><span class="sxs-lookup"><span data-stu-id="41ff5-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="41ff5-270">Począwszy od .NET Framework 4.7.1, są one prawidłowo anonsowane jako rozwijane/zwijane grupy.</span><span class="sxs-lookup"><span data-stu-id="41ff5-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="41ff5-271">W .NET Framework 4,7 i wcześniejszych wersjach kontrolki <xref:System.Windows.Controls.DataGridCell> zostały ogłoszone przez czytniki ekranu jako "niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="41ff5-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="41ff5-272">Począwszy od .NET Framework 4.7.1, są one teraz prawidłowo anonsowane jako komórka siatki danych (zlokalizowany).</span><span class="sxs-lookup"><span data-stu-id="41ff5-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="41ff5-273">Począwszy od .NET Framework 4.7.1, czytniki ekranu anonsują nazwę <xref:System.Windows.Controls.ComboBox>edytowalnego.</span><span class="sxs-lookup"><span data-stu-id="41ff5-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="41ff5-274">W .NET Framework 4,7 i starszych wersjach, formanty <xref:System.Windows.Controls.PasswordBox> zostały ogłoszone jako "Brak elementów w widoku" lub w inny sposób nie były prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="41ff5-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="41ff5-275">Ten problem został rozwiązany, rozpoczynając od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="41ff5-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="41ff5-276">**Obsługa LiveRegion UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="41ff5-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="41ff5-277">Czytniki ekranu, takie jak Narrator, ułatwiają osobom odczytywanie zawartości interfejsu użytkownika aplikacji, zazwyczaj przez zamianę tekstu na mowę dla zawartości interfejsu użytkownika, która ma fokus.</span><span class="sxs-lookup"><span data-stu-id="41ff5-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="41ff5-278">Jeśli jednak element interfejsu użytkownika zmieni się i nie ma fokusu, użytkownik może nie zostać powiadomiony i może pominąć ważne informacje.</span><span class="sxs-lookup"><span data-stu-id="41ff5-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="41ff5-279">Regiony na żywo mają na celu rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="41ff5-280">Programista może użyć ich do informowania czytnika ekranu lub innego klienta UIAutomation o tym, że wprowadzono ważną zmianę w elemencie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41ff5-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="41ff5-281">Czytnik ekranu może następnie zdecydować, jak i kiedy należy poinformować użytkownika o tej zmianie.</span><span class="sxs-lookup"><span data-stu-id="41ff5-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="41ff5-282">Do obsługi regionów na żywo dodano następujące interfejsy API do platformy WPF:</span><span class="sxs-lookup"><span data-stu-id="41ff5-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="41ff5-283">Pola <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, które identyfikują Właściwość **LiveSetting** i zdarzenie **LiveRegionChanged** .</span><span class="sxs-lookup"><span data-stu-id="41ff5-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="41ff5-284">Można je ustawić przy użyciu języka XAML.</span><span class="sxs-lookup"><span data-stu-id="41ff5-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="41ff5-285">Dołączona właściwość **AutomationProperties. LiveSetting** , która informuje czytnik ekranu o ważności zmiany interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41ff5-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="41ff5-286">Właściwość <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, która identyfikuje załączoną Właściwość **AutomationProperties. LiveSetting** .</span><span class="sxs-lookup"><span data-stu-id="41ff5-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="41ff5-287">Metoda <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, którą można zastąpić, aby zapewnić wartość **LiveSetting** .</span><span class="sxs-lookup"><span data-stu-id="41ff5-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="41ff5-288">Metody <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, które uzyskują i ustawiają wartość **LiveSetting** .</span><span class="sxs-lookup"><span data-stu-id="41ff5-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="41ff5-289">Wyliczenie <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, które definiuje następujące możliwe wartości **LiveSetting** :</span><span class="sxs-lookup"><span data-stu-id="41ff5-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="41ff5-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.,</span><span class="sxs-lookup"><span data-stu-id="41ff5-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41ff5-291">Element nie wysyła powiadomień, jeśli zawartość regionu aktywnego zmieniła się.</span><span class="sxs-lookup"><span data-stu-id="41ff5-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="41ff5-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.,</span><span class="sxs-lookup"><span data-stu-id="41ff5-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41ff5-293">Element wysyła powiadomienia nieprzerwane, jeśli zawartość regionu aktywnego uległa zmianie.</span><span class="sxs-lookup"><span data-stu-id="41ff5-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="41ff5-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.,</span><span class="sxs-lookup"><span data-stu-id="41ff5-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="41ff5-295">Element wysyła powiadomienia o przerwie, jeśli zawartość regionu aktywnego uległa zmianie.</span><span class="sxs-lookup"><span data-stu-id="41ff5-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="41ff5-296">Można utworzyć LiveRegion przez ustawienie właściwości **AutomationProperties. LiveSetting** dla elementu zainteresowania, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="41ff5-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="41ff5-297">Gdy dane w regionie aktywnym zmieniają się i musisz poinformować czytnik ekranu, można jawnie zgłosić zdarzenie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="41ff5-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="41ff5-298">**Duży kontrast**</span><span class="sxs-lookup"><span data-stu-id="41ff5-298">**High contrast**</span></span>

<span data-ttu-id="41ff5-299">Począwszy od .NET Framework 4.7.1, wprowadzono ulepszenia w różnych kontrolkach WPF.</span><span class="sxs-lookup"><span data-stu-id="41ff5-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="41ff5-300">Są one teraz widoczne po ustawieniu motywu <xref:System.Windows.SystemParameters.HighContrast%2A>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="41ff5-301">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="41ff5-301">These include:</span></span>

- <span data-ttu-id="41ff5-302">Kontrolka <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="41ff5-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="41ff5-303">Wizualizacja fokusu dla kontrolki <xref:System.Windows.Controls.Expander> jest teraz widoczna.</span><span class="sxs-lookup"><span data-stu-id="41ff5-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="41ff5-304">Wizualizacje klawiatury dla formantów <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>i <xref:System.Windows.Controls.RadioButton> są również widoczne.</span><span class="sxs-lookup"><span data-stu-id="41ff5-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="41ff5-305">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="41ff5-305">For example:</span></span>

  <span data-ttu-id="41ff5-306">Przed:</span><span class="sxs-lookup"><span data-stu-id="41ff5-306">Before:</span></span> 

  ![Kontrolka ekspandera z fokusem przed udoskonaleniami ułatwień dostępu](./media/expander-before.png)

  <span data-ttu-id="41ff5-308">Otrzyma</span><span class="sxs-lookup"><span data-stu-id="41ff5-308">After:</span></span> 

  ![Kontrolka ekspandera z fokusem po udoskonaleniach ułatwień dostępu](./media/expander-after.png)

- <span data-ttu-id="41ff5-310">kontrolki <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton></span><span class="sxs-lookup"><span data-stu-id="41ff5-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="41ff5-311">Tekst w kontrolkach <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> jest teraz łatwiejszy do sprawdzenia, gdy wybrane są motywy o dużym kontraście.</span><span class="sxs-lookup"><span data-stu-id="41ff5-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="41ff5-312">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="41ff5-312">For example:</span></span>

  <span data-ttu-id="41ff5-313">Przed:</span><span class="sxs-lookup"><span data-stu-id="41ff5-313">Before:</span></span> 

  ![Przycisk radiowy o dużym kontraście z fokusem przed udoskonaleniami ułatwień dostępu](./media/radio-button-before.png)

  <span data-ttu-id="41ff5-315">Otrzyma</span><span class="sxs-lookup"><span data-stu-id="41ff5-315">After:</span></span> 

  ![Przycisk radiowy o dużym kontraście z fokusem po ulepszeniach ułatwień dostępu](./media/radio-button-after.png)

- <span data-ttu-id="41ff5-317">Kontrolka <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="41ff5-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="41ff5-318">Począwszy od .NET Framework 4.7.1, obramowanie wyłączonej kontrolki <xref:System.Windows.Controls.ComboBox> ma taki sam kolor jak wyłączony tekst.</span><span class="sxs-lookup"><span data-stu-id="41ff5-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="41ff5-319">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="41ff5-319">For example:</span></span>

  <span data-ttu-id="41ff5-320">Przed:</span><span class="sxs-lookup"><span data-stu-id="41ff5-320">Before:</span></span> 

  ![Pole kombi wyłączone obramowanie i tekst przed ulepszeniem ułatwień dostępu](./media/combo-disabled-before.png)

  <span data-ttu-id="41ff5-322">Otrzyma</span><span class="sxs-lookup"><span data-stu-id="41ff5-322">After:</span></span>   

  ![Pole kombi wyłączone obramowanie i tekst po udoskonaleniach ułatwień dostępu](./media/combo-disabled-after.png)

  <span data-ttu-id="41ff5-324">Ponadto przyciski wyłączone i priorytetowe używają poprawnego koloru motywu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="41ff5-325">Przed:</span><span class="sxs-lookup"><span data-stu-id="41ff5-325">Before:</span></span>

  ![Kolory motywu przycisków przed ulepszeniami ułatwień dostępu](./media/button-themes-before.png) 

  <span data-ttu-id="41ff5-327">Otrzyma</span><span class="sxs-lookup"><span data-stu-id="41ff5-327">After:</span></span> 

  ![Kolory motywu przycisków po ulepszeniach ułatwień dostępu](./media/button-themes-after.png) 

  <span data-ttu-id="41ff5-329">Na koniec, w .NET Framework 4,7 i wcześniejszych wersjach, ustawienie stylu kontrolki <xref:System.Windows.Controls.ComboBox> na `Toolbar.ComboBoxStyleKey` spowodowało niewidzialność strzałki listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="41ff5-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="41ff5-330">Ten problem został rozwiązany, rozpoczynając od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="41ff5-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="41ff5-331">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="41ff5-331">For example:</span></span>

  <span data-ttu-id="41ff5-332">Przed:</span><span class="sxs-lookup"><span data-stu-id="41ff5-332">Before:</span></span> 

  ![Pasek narzędzi. ComboBoxStyleKey przed udoskonaleniami ułatwień dostępu](./media/comboboxstylekey-before.png) 

  <span data-ttu-id="41ff5-334">Otrzyma</span><span class="sxs-lookup"><span data-stu-id="41ff5-334">After:</span></span> 

  ![Pasek narzędzi. ComboBoxStyleKey po udoskonaleniach ułatwień dostępu](./media/comboboxstylekey-after.png) 

- <span data-ttu-id="41ff5-336">Kontrolka <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="41ff5-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="41ff5-337">Począwszy od .NET Framework 4.7.1, strzałka sortowania w <xref:System.Windows.Controls.DataGrid> kontrolki używa teraz poprawnych kolorów motywu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="41ff5-338">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="41ff5-338">For example:</span></span>

  <span data-ttu-id="41ff5-339">Przed:</span><span class="sxs-lookup"><span data-stu-id="41ff5-339">Before:</span></span> 

  ![Sortuj strzałkę wskaźnika przed ulepszeniami ułatwień dostępu](./media/sort-indicator-before.png) 

  <span data-ttu-id="41ff5-341">Otrzyma</span><span class="sxs-lookup"><span data-stu-id="41ff5-341">After:</span></span>   

  ![Sortuj strzałkę wskaźnika po udoskonaleniach ułatwień dostępu](./media/sort-indicator-after.png) 

  <span data-ttu-id="41ff5-343">Ponadto w .NET Framework 4,7 i wcześniejszych wersjach domyślny styl łącza został zmieniony na nieprawidłowy kolor na przycisku myszy nad trybem dużego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="41ff5-344">Jest to rozwiązane, rozpoczynając od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="41ff5-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="41ff5-345">Analogicznie, <xref:System.Windows.Controls.DataGrid> kolumny CheckBox używa oczekiwanych kolorów dla opinii o fokusie klawiatury, zaczynając od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="41ff5-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="41ff5-346">Przed:</span><span class="sxs-lookup"><span data-stu-id="41ff5-346">Before:</span></span> 

  ![Domyślny styl linku DataGrid przed ulepszeniami ułatwień dostępu](./media/default-link-style-before.png) 

  <span data-ttu-id="41ff5-348">Otrzyma</span><span class="sxs-lookup"><span data-stu-id="41ff5-348">After:</span></span>    

  ![Domyślny styl linku DataGrid po ulepszeniach ułatwień dostępu](./media/default-link-style-after.png) 

<span data-ttu-id="41ff5-350">Aby uzyskać więcej informacji na temat ulepszeń ułatwień dostępu WPF w .NET Framework 4.7.1, zobacz [ulepszenia ułatwień dostępu w programie WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="41ff5-350">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="41ff5-351">Ulepszenia ułatwień dostępu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41ff5-351">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="41ff5-352">W .NET Framework 4.7.1 Windows Forms (WinForms) obejmuje zmiany ułatwień dostępu w następujących obszarach.</span><span class="sxs-lookup"><span data-stu-id="41ff5-352">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="41ff5-353">**Udoskonalone wyświetlanie w trybie duży kontrast**</span><span class="sxs-lookup"><span data-stu-id="41ff5-353">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="41ff5-354">Począwszy od .NET Framework 4.7.1, różne kontrolki WinForm oferują ulepszone renderowanie w trybach HighContrast dostępnych w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="41ff5-354">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="41ff5-355">System Windows 10 zmienił wartości niektórych kolorów systemu o dużym kontraście, a Windows Forms jest oparty na strukturze Win32 systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="41ff5-355">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="41ff5-356">Aby uzyskać najlepsze środowisko, uruchom polecenie w najnowszej wersji systemu Windows i zapoznaj się z najnowszymi zmianami systemu operacyjnego przez dodanie pliku App. manifest do aplikacji testowej i odskomentuj wiersz systemu operacyjnego Windows 10, aby wyglądał następująco:</span><span class="sxs-lookup"><span data-stu-id="41ff5-356">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="41ff5-357">Niektóre przykłady zmian wysokiego kontrastu obejmują:</span><span class="sxs-lookup"><span data-stu-id="41ff5-357">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="41ff5-358">Zaznaczone elementy <xref:System.Windows.Forms.MenuStrip> są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="41ff5-358">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="41ff5-359">Po wybraniu elementy <xref:System.Windows.Forms.MenuStrip> są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="41ff5-359">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="41ff5-360">Tekst w wybranym formancie <xref:System.Windows.Forms.Button> kontrastu z kolorem zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="41ff5-360">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="41ff5-361">Wyłączony tekst jest łatwiejszy do odczytania.</span><span class="sxs-lookup"><span data-stu-id="41ff5-361">Disabled text is easier to read.</span></span> <span data-ttu-id="41ff5-362">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="41ff5-362">For example:</span></span>

  <span data-ttu-id="41ff5-363">Przed:</span><span class="sxs-lookup"><span data-stu-id="41ff5-363">Before:</span></span>

  ![Wyłączony tekst przed udoskonaleniami ułatwień dostępu](./media/wf-disabled-before.png) 

  <span data-ttu-id="41ff5-365">Otrzyma</span><span class="sxs-lookup"><span data-stu-id="41ff5-365">After:</span></span>

  ![Wyłączony tekst po udoskonaleniach ułatwień dostępu](./media/wf-disabled-after.png) 

- <span data-ttu-id="41ff5-367">Ulepszenia dużego kontrastu w oknie dialogowym wyjątku wątku.</span><span class="sxs-lookup"><span data-stu-id="41ff5-367">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="41ff5-368">**Ulepszona obsługa Narratora**</span><span class="sxs-lookup"><span data-stu-id="41ff5-368">**Improved Narrator support**</span></span>

<span data-ttu-id="41ff5-369">Windows Forms w programie .NET Framework 4.7.1 zawierają następujące ulepszenia ułatwień dostępu dla programu Narrator:</span><span class="sxs-lookup"><span data-stu-id="41ff5-369">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="41ff5-370">Dostęp do formantu <xref:System.Windows.Forms.MonthCalendar> można uzyskać za pomocą programu Narrator, a także innych narzędzi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41ff5-370">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="41ff5-371">Formant <xref:System.Windows.Forms.CheckedListBox> powiadamia program Narrator, gdy stan zaznaczenia elementu zmienił się, aby użytkownik był powiadomiony o zmianie wartości elementu listy.</span><span class="sxs-lookup"><span data-stu-id="41ff5-371">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="41ff5-372">Formant <xref:System.Windows.Forms.DataGridViewCell> raportuje prawidłowy stan tylko do odczytu w programie narrator.</span><span class="sxs-lookup"><span data-stu-id="41ff5-372">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="41ff5-373">Narrator może teraz odczytywać wyłączone <xref:System.Windows.Forms.ToolStripMenuItem> tekst, podczas gdy wcześniej mógłby pominąć wyłączone elementy menu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-373">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="41ff5-374">**Ulepszona obsługa wzorców dostępności UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="41ff5-374">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="41ff5-375">Począwszy od .NET Framework 4.7.1, deweloperzy narzędzi technologii ułatwień dostępu mogą korzystać ze wspólnych wzorców dostępności interfejsu API i właściwości dla kilku kontrolek WinForms.</span><span class="sxs-lookup"><span data-stu-id="41ff5-375">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="41ff5-376">Ulepszenia ułatwień dostępu obejmują:</span><span class="sxs-lookup"><span data-stu-id="41ff5-376">These accessibility improvements include:</span></span>

- <span data-ttu-id="41ff5-377"><xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ToolStripSplitButton> obsługują teraz [wzorzec rozwijania/zwijania](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="41ff5-377">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="41ff5-378"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> obsługuje teraz [wzorzec przełączania](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="41ff5-378">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="41ff5-379">Formant <xref:System.Windows.Forms.ToolStripItem> obsługuje Właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> i [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="41ff5-379">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="41ff5-380">Kontrolki <xref:System.Windows.Forms.NumericUpDown> i <xref:System.Windows.Forms.DomainUpDown> obsługują Właściwość <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-380">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="41ff5-381">**Ulepszone środowisko przeglądarki właściwości**</span><span class="sxs-lookup"><span data-stu-id="41ff5-381">**Improved property browser experience**</span></span>

<span data-ttu-id="41ff5-382">Począwszy od .NET Framework 4.7.1, Windows Forms obejmuje:</span><span class="sxs-lookup"><span data-stu-id="41ff5-382">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="41ff5-383">Lepsza Nawigacja przy użyciu klawiatury w różnych oknach menu rozwijanego.</span><span class="sxs-lookup"><span data-stu-id="41ff5-383">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="41ff5-384">Zmniejszenie niepotrzebnych tabulatorów.</span><span class="sxs-lookup"><span data-stu-id="41ff5-384">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="41ff5-385">Lepsze raportowanie typów kontroli.</span><span class="sxs-lookup"><span data-stu-id="41ff5-385">Better reporting of control types.</span></span>
- <span data-ttu-id="41ff5-386">Ulepszone zachowanie narratora.</span><span class="sxs-lookup"><span data-stu-id="41ff5-386">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="41ff5-387">Kontrolki sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="41ff5-387">ASP.NET web controls</span></span>

<span data-ttu-id="41ff5-388">Począwszy od .NET Framework 4.7.1 i programu Visual Studio 2017 w wersji 15,3, ASP.NET ulepsza, jak formanty sieci Web ASP.NET działają z technologią ułatwień dostępu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41ff5-388">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="41ff5-389">Zmiany obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="41ff5-389">Changes include the following:</span></span>

- <span data-ttu-id="41ff5-390">Zmiany w celu zaimplementowania brakujących wzorców dostępności interfejsu użytkownika w kontrolkach, takich jak okno dialogowe **Dodawanie pola** w kreatorze **widoku szczegółów** lub okno dialogowe **Konfiguruj widok ListView** kreatora **ListView** .</span><span class="sxs-lookup"><span data-stu-id="41ff5-390">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="41ff5-391">Zmiany w celu usprawnienia wyświetlania w trybie duży kontrast, takie jak **Edytor pól modułu stronicowania danych**.</span><span class="sxs-lookup"><span data-stu-id="41ff5-391">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="41ff5-392">Zmiany w celu ulepszenia środowiska nawigacji klawiaturowej dla kontrolek, takich jak okno dialogowe **pola** w kreatorze **Edytuj pola modułu stronicowania** kontrolki formantu DataPager, okno dialogowe **Konfigurowanie obiektu ObjectContext** lub **Konfiguracja wyboru konfiguracji** okno dialogowe kreatora **konfiguracji źródła danych** .</span><span class="sxs-lookup"><span data-stu-id="41ff5-392">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="41ff5-393">SDK Tools .NET</span><span class="sxs-lookup"><span data-stu-id="41ff5-393">.NET SDK Tools</span></span>

<span data-ttu-id="41ff5-394">[Narzędzie edytora konfiguracji (SvcConfigEditor. exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) i [narzędzie Podgląd śledzenia usługi (SvcTraceViewer. exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) zostały ulepszone, rozwiązując różne problemy z ułatwieniami dostępu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-394">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="41ff5-395">Większość z nich dotyczyła małych problemów, takich jak nazwa, która nie jest zdefiniowana lub niektóre wzorce automatyzacji interfejsu użytkownika nie są poprawnie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="41ff5-395">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="41ff5-396">Chociaż wielu użytkowników nie ma informacji o tych nieprawidłowych wartościach, klienci korzystający z technologii pomocniczych, takich jak czytniki zawartości ekranu, zobaczą więcej dostępnych narzędzi zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="41ff5-396">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="41ff5-397">Te udoskonalenia zmieniają niektóre poprzednie zachowania, na przykład kolejność fokusu klawiatury.</span><span class="sxs-lookup"><span data-stu-id="41ff5-397">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="41ff5-398">Projektant przepływu pracy Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="41ff5-398">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="41ff5-399">Zmiany ułatwień dostępu w Projektant przepływu pracy obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="41ff5-399">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="41ff5-400">Kolejność tabulacji zmieni się na od lewej do prawej i od góry do dołu w niektórych kontrolkach:</span><span class="sxs-lookup"><span data-stu-id="41ff5-400">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="41ff5-401">Okno inicjowania korelacji do ustawiania danych korelacji dla działania <xref:System.ServiceModel.Activities.InitializeCorrelation>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-401">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="41ff5-402">Okno definicji zawartości dla działań <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>i <xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-402">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="41ff5-403">Więcej funkcji jest dostępnych za pośrednictwem klawiatury:</span><span class="sxs-lookup"><span data-stu-id="41ff5-403">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="41ff5-404">Podczas edytowania właściwości działania grupy właściwości mogą być zwijane przez klawiaturę po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="41ff5-404">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="41ff5-405">Ikony ostrzeżeń są dostępne na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="41ff5-405">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="41ff5-406">Przycisk **więcej właściwości** w oknie **Właściwości** jest dostępny na klawiaturze.</span><span class="sxs-lookup"><span data-stu-id="41ff5-406">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="41ff5-407">Użytkownicy klawiatury mogą uzyskać dostęp do elementów nagłówka w okienkach **argumenty** i **zmienne** Projektant przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="41ff5-407">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="41ff5-408">Ulepszona widoczność elementów z fokusem, takich jak:</span><span class="sxs-lookup"><span data-stu-id="41ff5-408">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="41ff5-409">Dodawanie wierszy do siatek danych używanych przez Projektant przepływu pracy i projektantów działań.</span><span class="sxs-lookup"><span data-stu-id="41ff5-409">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="41ff5-410">Używanie tabulacji w polach <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply> działania.</span><span class="sxs-lookup"><span data-stu-id="41ff5-410">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="41ff5-411">Ustawianie wartości domyślnych dla zmiennych lub argumentów</span><span class="sxs-lookup"><span data-stu-id="41ff5-411">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="41ff5-412">Czytniki zawartości ekranu mogą teraz prawidłowo rozpoznać:</span><span class="sxs-lookup"><span data-stu-id="41ff5-412">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="41ff5-413">Punkty przerwania ustawione w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="41ff5-413">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="41ff5-414">Działania <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>i <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-414">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="41ff5-415">Zawartość działania <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-415">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="41ff5-416">Typ docelowy działania <xref:System.Activities.Statements.InvokeMethod>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-416">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="41ff5-417">Pole kombi wyjątku oraz sekcja finally w działaniu <xref:System.Activities.Statements.TryCatch>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-417">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="41ff5-418">Pole kombi typ komunikatu, rozdzielacz w oknie Dodaj inicjatory korelacji, okno definicji zawartości i okno definicji CorrelatesOn w działaniach obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>i <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="41ff5-418">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="41ff5-419">Przejścia komputera stanu i miejsca docelowe przejść.</span><span class="sxs-lookup"><span data-stu-id="41ff5-419">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="41ff5-420">Adnotacje i łączniki na <xref:System.Activities.Statements.FlowDecision> działaniach.</span><span class="sxs-lookup"><span data-stu-id="41ff5-420">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="41ff5-421">Menu kontekstowe (kliknij prawym przyciskiem myszy) dla działań.</span><span class="sxs-lookup"><span data-stu-id="41ff5-421">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="41ff5-422">Edytor wartości właściwości, przycisk Wyczyść wyszukiwanie, Kategoria według oraz alfabetyczne przyciski sortowania i okno dialogowe Edytor wyrażeń w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="41ff5-422">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="41ff5-423">Procent powiększenia w Projektant przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="41ff5-423">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="41ff5-424">Separator w <xref:System.Activities.Statements.Parallel> i <xref:System.Activities.Statements.Pick> działania.</span><span class="sxs-lookup"><span data-stu-id="41ff5-424">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="41ff5-425">Działanie <xref:System.Activities.Statements.InvokeDelegate>.</span><span class="sxs-lookup"><span data-stu-id="41ff5-425">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="41ff5-426">Okno wybór typów dla działań słownika (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`itp.).</span><span class="sxs-lookup"><span data-stu-id="41ff5-426">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="41ff5-427">Okno Przeglądaj i wybierz typ platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="41ff5-427">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="41ff5-428">Struktura nawigacyjna w Projektant przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="41ff5-428">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="41ff5-429">Użytkownicy, którzy wybierają duży kontrast motywy zobaczą wiele ulepszeń w zakresie widoczności Projektant przepływu pracy i jej kontrolek, takich jak lepsze współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używane do elementów fokusu.</span><span class="sxs-lookup"><span data-stu-id="41ff5-429">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="41ff5-430">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41ff5-430">See also</span></span>

- [<span data-ttu-id="41ff5-431">Co nowego w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="41ff5-431">What's new in the .NET Framework</span></span>](index.md)
