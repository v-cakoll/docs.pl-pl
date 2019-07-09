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
ms.openlocfilehash: da73df97524b9e394fac795daf14a3f0fb1f4e3d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661385"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="8ced7-102">What's new in ułatwień dostępu w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8ced7-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="8ced7-103">Celem jest udostępnienie aplikacji dla użytkowników programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ced7-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="8ced7-104">Funkcje ułatwień dostępu, Zezwalaj na aplikację zapewnić odpowiednie środowisko dla użytkowników technologii pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="8ced7-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="8ced7-105">Począwszy od .NET Framework 4.7.1 .NET Framework zawiera dużą liczbę ulepszenia ułatwień dostępu, które umożliwiają deweloperom tworzyć aplikacje dostępne.</span><span class="sxs-lookup"><span data-stu-id="8ced7-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="8ced7-106">Przełączniki ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="8ced7-106">Accessibility switches</span></span>

<span data-ttu-id="8ced7-107">Można skonfigurować aplikację, aby skorzystać z funkcji ułatwień dostępu, jeśli jest przeznaczony dla .NET Framework 4.7 lub starszej wersji, ale działa w programie .NET Framework 4.7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="8ced7-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="8ced7-108">Możesz także skonfigurować aplikację do używania starszych funkcji (i nie korzystaj z funkcji ułatwień dostępu), jeśli jest ono przeznaczone dla platformy .NET Framework 4.7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="8ced7-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="8ced7-109">Każda wersja programu .NET Framework, która obejmuje funkcje ułatwień dostępu ma przełącznika ułatwień dostępu specyficzny dla wersji, możesz dodać do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ced7-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="8ced7-110">Obsługiwane przełączniki są następujące:</span><span class="sxs-lookup"><span data-stu-id="8ced7-110">The following are the supported switches:</span></span>

|<span data-ttu-id="8ced7-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="8ced7-111">Version</span></span>|<span data-ttu-id="8ced7-112">Przełącznik</span><span class="sxs-lookup"><span data-stu-id="8ced7-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="8ced7-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="8ced7-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="8ced7-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="8ced7-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="8ced7-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="8ced7-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="8ced7-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="8ced7-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="8ced7-117">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="8ced7-117">.NET Framework 4.8</span></span>|<span data-ttu-id="8ced7-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="8ced7-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="8ced7-119">Korzystając z zalet udoskonalonym ułatwieniom dostępu</span><span class="sxs-lookup"><span data-stu-id="8ced7-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="8ced7-120">Nowe funkcje ułatwień dostępu są włączone domyślnie dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="8ced7-121">Ponadto aplikacje, które kątem starszej wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.7.1 lub później zdecydować się poza zachowania dostępności starszej wersji (i ten sposób korzystać z zalet ulepszenia ułatwień dostępu), dodając przełączników do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) części pliku konfiguracyjnego aplikacji i ich wartości `false`.</span><span class="sxs-lookup"><span data-stu-id="8ced7-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="8ced7-122">Poniżej przedstawiono sposób korzystania z opcji w celu ulepszenia ułatwień dostępu, wprowadzone w programie .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="8ced7-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="8ced7-123">Jeśli zdecydujesz się zgadzaj się na funkcje ułatwień dostępu w nowszej wersji programu .NET Framework, musi również jawnie zgody na uczestnictwo w funkcje z wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ced7-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="8ced7-124">Konfigurowanie aplikacji w taki sposób, aby wykorzystać ulepszenia ułatwień dostępu w systemie zarówno .NET Framework 4.7.1 i 4.7.2 wymaga następujących [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:</span><span class="sxs-lookup"><span data-stu-id="8ced7-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="8ced7-125">Konfigurowanie aplikacji w taki sposób, aby wykorzystać ulepszenia ułatwień dostępu w programie .NET Framework 4.7.1 4.7.2 i 4.8 wymaga następujących [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:</span><span class="sxs-lookup"><span data-stu-id="8ced7-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="8ced7-126">Przywracanie starsze zachowanie</span><span class="sxs-lookup"><span data-stu-id="8ced7-126">Restoring legacy behavior</span></span>

<span data-ttu-id="8ced7-127">Aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od 4.7.1 można wyłączyć funkcje ułatwień dostępu, dodając przełączniki [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji plik konfiguracji aplikacji i ich wartości `true`.</span><span class="sxs-lookup"><span data-stu-id="8ced7-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="8ced7-128">Na przykład następująca konfiguracja oznacza brak zgody na funkcje ułatwień dostępu, które wprowadzono w programie .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="8ced7-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="8ced7-129">What's new in ułatwień dostępu w programie .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="8ced7-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="8ced7-130">.NET framework 4.8 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="8ced7-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="8ced7-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ced7-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="8ced7-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="8ced7-133">Projektant przepływu pracy Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="8ced7-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ced7-134">Windows Forms</span></span>

<span data-ttu-id="8ced7-135">W .NET Framework 4,8 Windows Forms dodaje obsługę LiveRegions i zdarzenia powiadomień do wielu najczęściej używane kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8ced7-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="8ced7-136">Dodaje również obsługę dla etykietki narzędzi, gdy użytkownik przechodzi do formantu za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8ced7-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="8ced7-137">**Obsługa LiveRegions automatyzacji interfejsu użytkownika w etykiety i StatusStrip**</span><span class="sxs-lookup"><span data-stu-id="8ced7-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="8ced7-138">LiveRegions automatyzacji interfejsu użytkownika umożliwiają deweloperom aplikacji do powiadamiania czytniki zawartości ekranu zmiany tekstu w kontrolce, która znajduje się niezależnie od lokalizacji, w którym pracuje użytkownik.</span><span class="sxs-lookup"><span data-stu-id="8ced7-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="8ced7-139">Jest to przydatne, na przykład w przypadku <xref:System.Windows.Forms.StatusStrip> kontrolka, która pokazuje stan połączenia.</span><span class="sxs-lookup"><span data-stu-id="8ced7-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="8ced7-140">Jeśli połączenie zostanie porzucone, a zmiany stanu, deweloper może chcieć Powiadom czytnika zawartości ekranu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="8ced7-141">Począwszy od programu .NET Framework 4.8 formularze Windows implementuje LiveRegions automatyzacji interfejsu użytkownika dla obu <xref:System.Windows.Forms.Label> i <xref:System.Windows.Forms.StatusStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8ced7-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="8ced7-142">Na przykład w poniższym kodzie użyto LiveRegion w <xref:System.Windows.Forms.Label> formantu o nazwie `label1`:</span><span class="sxs-lookup"><span data-stu-id="8ced7-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="8ced7-143">Narrator ogłasza "Gotowe", niezależnie od tego, gdzie użytkownik prowadzi interakcję z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="8ced7-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="8ced7-144">Możesz również wdrożyć swoje <xref:System.Windows.Forms.UserControl> jako LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="8ced7-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="8ced7-145">**Zdarzenia powiadomień automatyzacji interfejsu użytkownika**</span><span class="sxs-lookup"><span data-stu-id="8ced7-145">**UIA notification events**</span></span>

<span data-ttu-id="8ced7-146">Zdarzenia powiadomień automatyzacji interfejsu użytkownika, wprowadzone w programie Windows 10 Fall Creators Update umożliwia wywoływanie zdarzeń automatyzacji interfejsu użytkownika, który prowadzi do Narrator, po prostu co anons, na podstawie tekstu podać ze zdarzeniem, bez konieczności posiadania odpowiednią kontrolować w interfejsie użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ced7-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="8ced7-147">W niektórych przypadkach jest to prosty sposób znacznie zwiększyć dostępność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ced7-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="8ced7-148">W również może być przydatne do powiadomienia o postępie niektóre procesy, które może zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="8ced7-149">Aby uzyskać więcej informacji na temat zdarzenia powiadomień automatyzacji interfejsu użytkownika, zobacz [aplikację klasyczną mogą korzystać z nowego zdarzenia powiadomień interfejsu użytkownika?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span><span class="sxs-lookup"><span data-stu-id="8ced7-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span></span>

<span data-ttu-id="8ced7-150">Poniższy przykład wywołuje [zdarzenie powiadomienia](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="8ced7-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="8ced7-151">**Etykietki narzędzi na dostęp za pomocą klawiatury**</span><span class="sxs-lookup"><span data-stu-id="8ced7-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="8ced7-152">W aplikacjach przeznaczonych dla środowiska .NET Framework 4.7.2 i wcześniejszymi wersjami, formant [etykietki narzędzia](xref:System.Windows.Forms.ToolTip) tylko można wyzwolić do pop się przesuwając wskaźnik myszy w formancie.</span><span class="sxs-lookup"><span data-stu-id="8ced7-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="8ced7-153">Począwszy od programu .NET Framework 4.8 użytkownika klawiatury może wyzwalać formantu etykietki narzędzia, koncentrując się kontrolka, za pomocą klawisza Tab lub klawisze strzałek z lub bez klawisze modyfikujące.</span><span class="sxs-lookup"><span data-stu-id="8ced7-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="8ced7-154">To ulepszenie ułatwień dostępu w szczególności wiąże się z dodatkowymi [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="8ced7-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="8ced7-155">Na poniższej ilustracji przedstawiono etykietkę narzędzia, gdy użytkownik wybrał przycisk za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8ced7-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Etykietka narzędzia, gdy użytkownik przechodzi do przycisku za pomocą klawiatury](media/tooltip.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="8ced7-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="8ced7-158">Począwszy od programu .NET Framework 4.8 WPF zawiera szereg ulepszeń w ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="8ced7-159">**Narrators ekranu nie są już ogłaszamy elementów o widoczności zwinięte lub ukryte**</span><span class="sxs-lookup"><span data-stu-id="8ced7-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="8ced7-160">Elementy o widoczności zwinięty czy ukryty już nie są anonsowane przez czytnik zawartości ekranu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="8ced7-161">Interfejsy użytkownika, które zawierać elementów o widoczność <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> lub <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> może być podawanie fałszywych informacji przez czytniki zawartości ekranu w przypadku ich obsłudze zostaną opublikowane dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ced7-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="8ced7-162">Począwszy od programu .NET Framework 4.8 WPF nie zawiera już zwinięty lub ukryte elementy w widoku kontrolnym drzewa biblioteki UIAutomation, więc czytniki zawartości ekranu nie są już może poinformować o tych elementów.</span><span class="sxs-lookup"><span data-stu-id="8ced7-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="8ced7-163">**Właściwość SelectionTextBrush do użytku z programem — moduł definiowania układu na podstawie zaznaczenia tekstu**</span><span class="sxs-lookup"><span data-stu-id="8ced7-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="8ced7-164">W .NET Framework 4.7.2 WPF dodaje pobierające <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox> zaznaczonego tekstu bez korzystania z warstwy moduł definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="8ced7-165">Kolor pierwszego planu zaznaczony tekst w tym scenariuszu zostało podyktowanej <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8ced7-166">.NET framework 4.8 dodaje nową właściwość `SelectionTextBrush`, która umożliwia deweloperom wybrać określone Pędzel zaznaczony tekst, gdy za pomocą innego niż moduł definiowania układu na podstawie zaznaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="8ced7-167">Ta właściwość działa tylko w systemie <xref:System.Windows.Controls.Primitives.TextBoxBase>-pochodnych kontrolek i <xref:System.Windows.Controls.PasswordBox> kontrolki w aplikacji WPF przy użyciu wybór podstawie moduł definiowania układu tekstu, włączone.</span><span class="sxs-lookup"><span data-stu-id="8ced7-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="8ced7-168">Nie działa na <xref:System.Windows.Controls.RichTextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ced7-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="8ced7-169">Jeśli zaznaczenie tekstu podstawie moduł definiowania układu kodu nie jest włączona, ta właściwość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="8ced7-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="8ced7-170">Aby używać tej właściwości, dodaj go do kodu XAML i za pomocą odpowiednich pędzla lub powiązania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="8ced7-171">Wynikowy zaznaczonego tekstu wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="8ced7-171">The resulting text selection looks like this:</span></span>

![Etykietka narzędzia, gdy użytkownik przechodzi do przycisku za pomocą klawiatury](media/selectiontextbrush-property.png)

<span data-ttu-id="8ced7-173">Można połączyć użytkowania `SelectionBrush` i `SelectionTextBrush` właściwości, aby wygenerować żadnych tła i pierwszego planu kolor połączeniem, które uznasz za stosowny.</span><span class="sxs-lookup"><span data-stu-id="8ced7-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="8ced7-174">**Obsługa biblioteki UIAutomation ControllerFor właściwość**</span><span class="sxs-lookup"><span data-stu-id="8ced7-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="8ced7-175">Biblioteki firmy UIAutomation `ControllerFor` właściwość zwraca tablicę elementów automatyzacji, które są zmieniane przez element automatyzacji, który obsługuje tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ced7-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="8ced7-176">Ta właściwość jest często używana do automatycznego sugerowania ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="8ced7-177">`ControllerFor` jest używana podczas automatyzacji element ma wpływ na jeden lub więcej segmentów w interfejsie użytkownika aplikacji lub pulpitu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="8ced7-178">W przeciwnym razie jest trudny do skojarzenia wpływ operacji kontroli elementów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ced7-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="8ced7-179">Ta funkcja dodaje możliwość dla formantów podać wartość dla `ControllerFor` właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ced7-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="8ced7-180">.NET framework 4.8 dodaje nowej metody wirtualnej <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ced7-181">Aby podać wartość dla `ControllerFor` właściwość, po prostu zastąpić tę metodę i zwraca `List<AutomationPeer>` dla formantów podlegający manipulowaniu to <xref:System.Windows.Automation.Peers.AutomationPeer>:</span><span class="sxs-lookup"><span data-stu-id="8ced7-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="8ced7-182">**Etykietki narzędzi na dostęp za pomocą klawiatury**</span><span class="sxs-lookup"><span data-stu-id="8ced7-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="8ced7-183">W programie .NET Framework 4.7.2 i wcześniejszych wersjach wyświetlania w etykietkach ekranowych tylko wtedy, gdy użytkownik ustawi wskaźnik myszy nad formantem.</span><span class="sxs-lookup"><span data-stu-id="8ced7-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="8ced7-184">W .NET Framework 4,8 etykietki narzędzi także wyświetlać na klawiaturę, a także za pomocą skrótów klawiaturowych.</span><span class="sxs-lookup"><span data-stu-id="8ced7-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="8ced7-185">Aby włączyć tę funkcję, aplikacja musi platformą docelową jest program .NET Framework 4.8 lub wymaga zgody na uczestnictwo przy użyciu `Switch.UseLegacyAccessibilityFeatures.3` i `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) przełączników.</span><span class="sxs-lookup"><span data-stu-id="8ced7-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="8ced7-186">Oto przykładowy plik konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8ced7-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="8ced7-187">Po włączeniu wszystkich kontrolek, które zawierają etykietka narzędzia wyświetlić po formant uzyskuje fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8ced7-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="8ced7-188">Etykietka narzędzia może być ukryty w czasie lub podczas zmiany fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8ced7-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="8ced7-189">Użytkownicy mogą również odrzucić etykietki narzędzia ręcznie przy użyciu nowego skrótu klawiaturowego Ctrl + Shift + F10.</span><span class="sxs-lookup"><span data-stu-id="8ced7-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="8ced7-190">Gdy etykietka narzędzia został odrzucony. może być wyświetlany ponownie przy użyciu tego samego skrótu klawiaturowego.</span><span class="sxs-lookup"><span data-stu-id="8ced7-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="8ced7-191">[Wstążka etykietki narzędzi](xref:System.Windows.Controls.Ribbon.RibbonToolTip) na <xref:System.Windows.Controls.Ribbon.Ribbon> kontrolek nie zostanie wyświetlona na klawiaturę; pokazują za pomocą skrótów klawiaturowych.</span><span class="sxs-lookup"><span data-stu-id="8ced7-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="8ced7-192">**Dodano obsługę SizeOfSet i biblioteki PositionInSet UIAutomation właściwości**</span><span class="sxs-lookup"><span data-stu-id="8ced7-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="8ced7-193">Windows 10 wprowadzono dwie nowe właściwości biblioteki UIAutomation `SizeOfSet` i `PositionInSet`, które są używane przez aplikacje do opisania liczba elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="8ced7-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="8ced7-194">Biblioteki UIAutomation aplikacji klienckich, takich jak czytniki zawartości ekranu można zbadać aplikacji dla tych właściwości i ogłaszamy dokładne odzwierciedlenia Interfejsem użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ced7-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="8ced7-195">Począwszy od programu .NET Framework 4.8 WPF udostępnia te dwie właściwości do biblioteki UIAutomation w aplikacjach WPF.</span><span class="sxs-lookup"><span data-stu-id="8ced7-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="8ced7-196">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="8ced7-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="8ced7-197">Za pomocą właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="8ced7-197">By using dependency properties.</span></span>

  <span data-ttu-id="8ced7-198">WPF dodaje dwie nowe właściwości zależności <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ced7-199">Projektant umożliwia XAML ustawienia ich wartości:</span><span class="sxs-lookup"><span data-stu-id="8ced7-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="8ced7-200">Przez zastąpienie AutomationPeer metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="8ced7-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="8ced7-201"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> i <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> metody wirtualne zostały dodane do klasy AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="8ced7-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="8ced7-202">Deweloper opracowuje wartości `SizeOfSet` i `PositionInSet` przez zastąpienie tych metod, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8ced7-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="8ced7-203">Ponadto elementy w <xref:System.Windows.Controls.ItemsControl> wystąpienia oferują wartości tych właściwości, które automatycznie bez dodatkowych działań od dewelopera.</span><span class="sxs-lookup"><span data-stu-id="8ced7-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="8ced7-204">Jeśli <xref:System.Windows.Controls.ItemsControl> są grupowane, kolekcję grup jest reprezentowany jako zestaw, a każda grupa jest traktowana jako oddzielny zestaw z każdym elementem w tej grupie, podając jego pozycja w tej grupie, a także rozmiar grupy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="8ced7-205">Automatyczne wartości nie dotyczy wirtualizacji.</span><span class="sxs-lookup"><span data-stu-id="8ced7-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="8ced7-206">Nawet wtedy, gdy element nie jest wykonywane, nadal jest wliczane do łączny rozmiar zestawu i ma wpływ na położenie w zestawie z jego elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="8ced7-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="8ced7-207">Automatyczne wartości są podane tylko, jeśli aplikacja jest przeznaczony dla .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="8ced7-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="8ced7-208">W przypadku aplikacji przeznaczonych dla starszej wersji programu .NET Framework, można ustawić `Switch.UseLegacyAccessibilityFeatures.3` [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak pokazano w następującym pliku App.config:</span><span class="sxs-lookup"><span data-stu-id="8ced7-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="8ced7-209">Projektant przepływu pracy Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="8ced7-210">Projektant przepływu pracy zawiera następujące zmiany w .NET Framework 4.8:</span><span class="sxs-lookup"><span data-stu-id="8ced7-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="8ced7-211">Za pomocą programu Narrator będzie towarzyszyć poprawę FlowSwitch etykiet wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="8ced7-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="8ced7-212">Za pomocą programu Narrator będzie towarzyszyć ulepszenia w opisach przycisku.</span><span class="sxs-lookup"><span data-stu-id="8ced7-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="8ced7-213">Użytkownicy, którzy wysokiego kontrastu, motywów zobaczą poprawę widoczność projektanta przepływów pracy i jego formantów, takie jak lepsza współczynniki kontrastu między elementami i lepiej widoczne pola wyboru używany do elementów zespołu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="8ced7-214">Jeśli aplikacja jest przeznaczony dla .NET Framework 4.7.2 lub starszej wersji, możesz zdecydować się na te zmiany, ustawiając `Switch.UseLegacyAccessibilityFeatures.3` [przełącznika AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `false` w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ced7-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="8ced7-215">Aby uzyskać więcej informacji, zobacz [zalet udoskonalonym ułatwieniom dostępu](#taking-advantage-of-accessibility-enhancements) sekcję w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="8ced7-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="8ced7-216">What's new in ułatwień dostępu w programie .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="8ced7-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="8ced7-217">.NET framework 4.7.2 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="8ced7-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="8ced7-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ced7-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="8ced7-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="8ced7-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ced7-220">Windows Forms</span></span>

<span data-ttu-id="8ced7-221">**Zdefiniowane przez system operacyjny kolory wysokiego kontrastu, motywów**</span><span class="sxs-lookup"><span data-stu-id="8ced7-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="8ced7-222">Począwszy od .NET Framework 4.7.2 formularze Windows używa kolorów zdefiniowanych przez system operacyjny w wysokiego kontrastu, motywów.</span><span class="sxs-lookup"><span data-stu-id="8ced7-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="8ced7-223">Dotyczy to następujących formantów:</span><span class="sxs-lookup"><span data-stu-id="8ced7-223">This affects the following controls:</span></span>

- <span data-ttu-id="8ced7-224">Strzałki listy rozwijanej z <xref:System.Windows.Forms.ToolStripDropDownButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ced7-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="8ced7-225"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> steruje się za pomocą <xref:System.Windows.Forms.ButtonBase.FlatStyle> równa <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ced7-226">Wcześniej wybranych kolorów tekstu i tła nie zostały kontrastujących i były trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="8ced7-227">Kontrolek znajdujących się w obrębie <xref:System.Windows.Forms.GroupBox> zawierający jego <xref:System.Windows.Forms.Control.Enabled> właściwością `false`.</span><span class="sxs-lookup"><span data-stu-id="8ced7-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="8ced7-228"><xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, I <xref:System.Windows.Forms.ToolStripDropDownButton> formanty, które mają większą jasność współczynnik kontrastu w trybie wysokiego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="8ced7-229"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="8ced7-230">**Ulepszenia Narrator**</span><span class="sxs-lookup"><span data-stu-id="8ced7-230">**Narrator improvements**</span></span>

<span data-ttu-id="8ced7-231">Począwszy od .NET Framework 4.7.2 obsługi programu Narrator został rozszerzony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8ced7-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="8ced7-232">Ogłasza, wartość <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> właściwości ogłoszenie tekst <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="8ced7-233">Oznacza to, kiedy <xref:System.Windows.Forms.ToolStripMenuItem> ma jego <xref:System.Windows.Forms.Control.Enabled> właściwością `false`.</span><span class="sxs-lookup"><span data-stu-id="8ced7-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="8ced7-234">Przekazuje opinie dotyczące stanu pola wyboru gdy <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="8ced7-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="8ced7-235">Program Narrator firmy Skanuj tryb koncentracji uwagi kolejność jest zgodna z visual kolejność kontrolek w oknie dialogowym pobierania ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="8ced7-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="8ced7-236">**Ulepszenia w formancie DataGridView**</span><span class="sxs-lookup"><span data-stu-id="8ced7-236">**DataGridView improvements**</span></span>

<span data-ttu-id="8ced7-237">Począwszy od .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> kontroli ma wprowadzono następujące ulepszenia ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="8ced7-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="8ced7-238">Za pomocą klawiatury można sortować wiersze.</span><span class="sxs-lookup"><span data-stu-id="8ced7-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="8ced7-239">Użytkownik może używać klawisz F3, aby posortować według bieżącej kolumny.</span><span class="sxs-lookup"><span data-stu-id="8ced7-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="8ced7-240">Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, nagłówek kolumny zmieni kolor, aby wskazać bieżącej kolumny jako karty użytkownika za pośrednictwem komórek w bieżącym wierszu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="8ced7-241"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> zwraca kontrolki nadrzędnej poprawne.</span><span class="sxs-lookup"><span data-stu-id="8ced7-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="8ced7-242">**Ulepszone podpowiedzi wizualne**</span><span class="sxs-lookup"><span data-stu-id="8ced7-242">**Improved visual cues**</span></span>

- <span data-ttu-id="8ced7-243"><xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> kontrolek z pustą <xref:System.Windows.Forms.ButtonBase.Text> właściwości wyświetlania wskaźnika fokus, gdy one zostać ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="8ced7-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="8ced7-244">**Obsługa siatki właściwości ulepszone**</span><span class="sxs-lookup"><span data-stu-id="8ced7-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="8ced7-245"><xref:System.Windows.Forms.PropertyGrid> Kontrolować elementy podrzędne, które teraz zwracany `true` dla <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> właściwości tylko wtedy, gdy PropertyGrid element jest włączony.</span><span class="sxs-lookup"><span data-stu-id="8ced7-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="8ced7-246"><xref:System.Windows.Forms.PropertyGrid> Kontrolować elementy podrzędne zwracany `false` dla <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> właściwości tylko wtedy, gdy PropertyGrid element mogą być zmieniane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ced7-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="8ced7-247">**Ulepszone klawiatury**</span><span class="sxs-lookup"><span data-stu-id="8ced7-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="8ced7-248"><xref:System.Windows.Forms.ToolStripButton> Kontrolka zezwala na fokus, gdy jest zawarty w ramach <xref:System.Windows.Forms.ToolStripPanel> zawierający <xref:System.Windows.Forms.ToolStripPanel.TabStop> właściwością `true`</span><span class="sxs-lookup"><span data-stu-id="8ced7-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="8ced7-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="8ced7-250">**Zmiany do kontrolki pola wyboru i RadioButton**</span><span class="sxs-lookup"><span data-stu-id="8ced7-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="8ced7-251">W programie .NET Framework 4.7.1 i wcześniejszymi wersjami, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> i <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> formanty mają niespójne i, w modelu klasycznym oraz wysokiego kontrastu motywy niepoprawne koncentracji uwagi wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="8ced7-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="8ced7-252">Te problemy występują w przypadkach, gdy formanty nie mają żadnych zestawu zawartości.</span><span class="sxs-lookup"><span data-stu-id="8ced7-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="8ced7-253">Dzięki temu może być przejście pomiędzy motywów mylące i element wizualny fokusu trudne do zobaczenia.</span><span class="sxs-lookup"><span data-stu-id="8ced7-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="8ced7-254">W programie .NET Framework 4.7.2 te wizualizacje są teraz bardziej spójny między motywy i widoczność w klasycznej sieci wirtualnej i wysokiego kontrastu motywów.</span><span class="sxs-lookup"><span data-stu-id="8ced7-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="8ced7-255">**Formanty formularzy WinForm hostowany w aplikacji WPF**</span><span class="sxs-lookup"><span data-stu-id="8ced7-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="8ced7-256">Kontrolki WinForms hostowaną w aplikacji WPF, .NET Framework 4.7.1 i wcześniejszych wersjach, użytkownicy nie karcie poza warstwy WinForms w przypadku pierwszej lub ostatniej kontroli w tej warstwie WPF <xref:System.Windows.Forms.Integration.ElementHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="8ced7-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="8ced7-257">W programie .NET Framework 4.7.2 użytkownicy mogą teraz kartę z warstwy WinForms.</span><span class="sxs-lookup"><span data-stu-id="8ced7-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="8ced7-258">Jednak automatycznych aplikacji, które zależą od fokus nigdy nie anulowania zapewnianego element warstwy WinForms może przestać działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="8ced7-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="8ced7-259">What's new in ułatwień dostępu w programie .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="8ced7-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="8ced7-260">.NET framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="8ced7-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="8ced7-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="8ced7-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ced7-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="8ced7-263">Kontrolki sieci web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8ced7-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="8ced7-264">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="8ced7-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="8ced7-265">Projektanta przepływów pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="8ced7-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="8ced7-267">**Ulepszenia czytnika ekranu**</span><span class="sxs-lookup"><span data-stu-id="8ced7-267">**Screen reader improvements**</span></span>

<span data-ttu-id="8ced7-268">Jeśli ulepszenia ułatwień dostępu są włączone, .NET Framework 4.7.1 obejmuje następujące ulepszenia, które wpływają na czytniki zawartości ekranu:</span><span class="sxs-lookup"><span data-stu-id="8ced7-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="8ced7-269">W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.Expander> formanty zostały odczytywana przez czytniki zawartości ekranu jako przyciski.</span><span class="sxs-lookup"><span data-stu-id="8ced7-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="8ced7-270">Począwszy od .NET Framework 4.7.1 ich obsłudze zostaną poprawnie opublikowane jako rozwijania/zwijane grupy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="8ced7-271">W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.DataGridCell> formantów była odczytywana przez czytniki ekranu jako "niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="8ced7-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="8ced7-272">Począwszy od .NET Framework 4.7.1 one są teraz prawidłowo od niedawna komórce siatki danych (zlokalizowany).</span><span class="sxs-lookup"><span data-stu-id="8ced7-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="8ced7-273">Począwszy od .NET Framework 4.7.1 czytniki zawartości ekranu ogłaszamy nazwę można edytować <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="8ced7-274">W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.PasswordBox> formanty zostały ogłaszany jako "Brak elementów w widoku" lub ma inny sposób niepoprawne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8ced7-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="8ced7-275">Ten problem jest rozwiązany, począwszy od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="8ced7-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="8ced7-276">**Obsługa biblioteki UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="8ced7-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="8ced7-277">Czytniki zawartości ekranu, np. osób pomocy Narrator odczytać zawartość interfejsu użytkownika aplikacji, zwykle zamiany tekstu na mowę dane wyjściowe zawartości interfejsu użytkownika, który ma fokus.</span><span class="sxs-lookup"><span data-stu-id="8ced7-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="8ced7-278">Jeśli jednak element interfejsu użytkownika zmiany i nie ma fokus, użytkownik nie może otrzymywać powiadomienia i może pominąć ważne informacje.</span><span class="sxs-lookup"><span data-stu-id="8ced7-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="8ced7-279">Regiony na żywo na celu rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="8ced7-280">Projektant umożliwia ich poinformować czytnika zawartości ekranu lub inne zgłaszający istotnych zmian do elementu interfejsu użytkownika klienta biblioteki UIAutomation.</span><span class="sxs-lookup"><span data-stu-id="8ced7-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="8ced7-281">Czytnik zawartości ekranu możesz zdecydować, jak i kiedy poinformowania użytkownika o tej zmianie.</span><span class="sxs-lookup"><span data-stu-id="8ced7-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="8ced7-282">Aby zapewnić obsługę regionów na żywo, następujące interfejsy API zostały dodane do platformy WPF:</span><span class="sxs-lookup"><span data-stu-id="8ced7-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="8ced7-283"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pola, które identyfikują **LiveSetting** właściwości i **LiveRegionChanged** zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8ced7-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="8ced7-284">Można ich ustawić przy użyciu XAML.</span><span class="sxs-lookup"><span data-stu-id="8ced7-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="8ced7-285">**AutomationProperties.LiveSetting** dołączona właściwość, która informuje o czytnika zawartości ekranu znaczenie zmiany interfejsu użytkownika dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ced7-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="8ced7-286"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Właściwość, która identyfikuje **AutomationProperties.LiveSetting** dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="8ced7-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="8ced7-287"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metody, która może zostać zastąpiona w celu zapewnienia **LiveSetting** wartości.</span><span class="sxs-lookup"><span data-stu-id="8ced7-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="8ced7-288"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, które get i set **LiveSetting** wartości.</span><span class="sxs-lookup"><span data-stu-id="8ced7-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="8ced7-289"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Wyliczenia, który definiuje następujące możliwości **LiveSetting** wartości:</span><span class="sxs-lookup"><span data-stu-id="8ced7-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="8ced7-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ced7-291">Element nie wysyła powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="8ced7-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="8ced7-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ced7-293">Elementu wysyła-interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="8ced7-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="8ced7-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ced7-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ced7-295">Elementu wysyła interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="8ced7-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="8ced7-296">Można utworzyć LiveRegion, ustawiając **AutomationProperties.LiveSetting** właściwości w elemencie zainteresowania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8ced7-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="8ced7-297">Gdy zmieniają się dane w regionie na żywo i należy poinformować czytnika ekranu, należy jawnie wywołać zdarzenie, jak pokazano w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ced7-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="8ced7-298">**Duży kontrast**</span><span class="sxs-lookup"><span data-stu-id="8ced7-298">**High contrast**</span></span>

<span data-ttu-id="8ced7-299">Począwszy od .NET Framework 4.7.1 o wysokim kontraście wprowadzono ulepszenia do różnych formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="8ced7-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="8ced7-300">Są one teraz widoczne podczas <xref:System.Windows.SystemParameters.HighContrast%2A> ustawiono motywu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="8ced7-301">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="8ced7-301">These include:</span></span>

- <span data-ttu-id="8ced7-302"><xref:System.Windows.Controls.Expander> Kontrolki</span><span class="sxs-lookup"><span data-stu-id="8ced7-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="8ced7-303">Fokus visual dla <xref:System.Windows.Controls.Expander> kontroli jest teraz widoczna.</span><span class="sxs-lookup"><span data-stu-id="8ced7-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="8ced7-304">Wizualizacje klawiatury dla <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.RadioButton> formanty są również widoczne.</span><span class="sxs-lookup"><span data-stu-id="8ced7-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="8ced7-305">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8ced7-305">For example:</span></span>

  <span data-ttu-id="8ced7-306">Przed:</span><span class="sxs-lookup"><span data-stu-id="8ced7-306">Before:</span></span> 

  ![Formant ekspandera fokus przed ulepszenia ułatwień dostępu](media/expander-before.png)

  <span data-ttu-id="8ced7-308">Po:</span><span class="sxs-lookup"><span data-stu-id="8ced7-308">After:</span></span> 

  ![Formant ekspandera fokus po ulepszenia ułatwień dostępu](media/expander-after.png)

- <span data-ttu-id="8ced7-310"><xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów</span><span class="sxs-lookup"><span data-stu-id="8ced7-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="8ced7-311">Tekst w <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> kontrolki jest teraz lepiej widoczne po wybraniu w wysokiego kontrastu, motywów.</span><span class="sxs-lookup"><span data-stu-id="8ced7-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="8ced7-312">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8ced7-312">For example:</span></span>

  <span data-ttu-id="8ced7-313">Przed:</span><span class="sxs-lookup"><span data-stu-id="8ced7-313">Before:</span></span> 

  ![Przycisk radiowy o wysokim kontraście fokus przed ulepszenia ułatwień dostępu](media/radio-button-before.png)

  <span data-ttu-id="8ced7-315">Po:</span><span class="sxs-lookup"><span data-stu-id="8ced7-315">After:</span></span> 

  ![Przycisk radiowy o wysokim kontraście fokus po ulepszenia ułatwień dostępu](media/radio-button-after.png)

- <span data-ttu-id="8ced7-317"><xref:System.Windows.Controls.ComboBox> Kontrolki</span><span class="sxs-lookup"><span data-stu-id="8ced7-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="8ced7-318">Począwszy od .NET Framework 4.7.1, obramowania wyłączone <xref:System.Windows.Controls.ComboBox> formant jest kolor wyłączonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="8ced7-319">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8ced7-319">For example:</span></span>

  <span data-ttu-id="8ced7-320">Przed:</span><span class="sxs-lookup"><span data-stu-id="8ced7-320">Before:</span></span> 

  ![Pole kombi wyłączone obramowanie i tekst przed ulepszenia ułatwień dostępu](media/combo-disabled-before.png)

  <span data-ttu-id="8ced7-322">Po:</span><span class="sxs-lookup"><span data-stu-id="8ced7-322">After:</span></span>   

  ![Pole kombi wyłączony obramowanie i tekstu po ulepszenia ułatwień dostępu](media/combo-disabled-after.png)

  <span data-ttu-id="8ced7-324">Ponadto wyłączone i skoncentrowany przyciski używają kolor motywu poprawne.</span><span class="sxs-lookup"><span data-stu-id="8ced7-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="8ced7-325">Przed:</span><span class="sxs-lookup"><span data-stu-id="8ced7-325">Before:</span></span>

  ![Kolory motywu przycisk przed ulepszenia ułatwień dostępu](media/button-themes-before.png) 

  <span data-ttu-id="8ced7-327">Po:</span><span class="sxs-lookup"><span data-stu-id="8ced7-327">After:</span></span> 

  ![Kolory motywu przycisku po ulepszenia ułatwień dostępu](media/button-themes-after.png) 

  <span data-ttu-id="8ced7-329">Na koniec w .NET Framework 4.7 i wcześniejszymi wersjami, ustawienie <xref:System.Windows.Controls.ComboBox> stylu kontrolki do `Toolbar.ComboBoxStyleKey` spowodowane strzałkę listy rozwijanej, aby była niewidoczna.</span><span class="sxs-lookup"><span data-stu-id="8ced7-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="8ced7-330">Ten problem jest rozwiązany, począwszy od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="8ced7-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="8ced7-331">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8ced7-331">For example:</span></span>

  <span data-ttu-id="8ced7-332">Przed:</span><span class="sxs-lookup"><span data-stu-id="8ced7-332">Before:</span></span> 

  ![Toolbar.ComboBoxStyleKey przed ulepszenia ułatwień dostępu](media/comboboxstylekey-before.png) 

  <span data-ttu-id="8ced7-334">Po:</span><span class="sxs-lookup"><span data-stu-id="8ced7-334">After:</span></span> 

  ![Toolbar.ComboBoxStyleKey po ulepszenia ułatwień dostępu](media/comboboxstylekey-after.png) 

- <span data-ttu-id="8ced7-336"><xref:System.Windows.Controls.DataGrid> Kontrolki</span><span class="sxs-lookup"><span data-stu-id="8ced7-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="8ced7-337">Począwszy od .NET Framework 4.7.1, strzałkę wskaźnika sortowania w <xref:System.Windows.Controls.DataGrid> kontroluje teraz używa Popraw kolory motywu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="8ced7-338">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8ced7-338">For example:</span></span>

  <span data-ttu-id="8ced7-339">Przed:</span><span class="sxs-lookup"><span data-stu-id="8ced7-339">Before:</span></span> 

  ![Sortowanie strzałkę wskaźnika przed ulepszenia ułatwień dostępu](media/sort-indicator-before.png) 

  <span data-ttu-id="8ced7-341">Po:</span><span class="sxs-lookup"><span data-stu-id="8ced7-341">After:</span></span>   

  ![Strzałka wskaźnika sortowania po ulepszenia ułatwień dostępu](media/sort-indicator-after.png) 

  <span data-ttu-id="8ced7-343">Ponadto w i wcześniejszych wersji programu .NET Framework 4.7, domyślnego stylu łącze zmieniana na niepoprawny kolor na myszy w trybach o wysokim kontraście.</span><span class="sxs-lookup"><span data-stu-id="8ced7-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="8ced7-344">Ten problem został rozwiązany, począwszy od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="8ced7-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="8ced7-345">Podobnie <xref:System.Windows.Controls.DataGrid> wyboru kolumn używa oczekiwanego kolorów opinii fokus klawiatury, począwszy od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="8ced7-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="8ced7-346">Przed:</span><span class="sxs-lookup"><span data-stu-id="8ced7-346">Before:</span></span> 

  ![Styl łącza domyślne DataGrid przed ulepszenia ułatwień dostępu](media/default-link-style-before.png) 

  <span data-ttu-id="8ced7-348">Po:</span><span class="sxs-lookup"><span data-stu-id="8ced7-348">After:</span></span>    

  ![Styl łącza domyślne DataGrid po ulepszenia ułatwień dostępu](media/default-link-style-after.png) 

<span data-ttu-id="8ced7-350">Aby uzyskać więcej informacji na temat ulepszenia ułatwień dostępu programu WPF w programie .NET Framework 4.7.1, zobacz [ulepszenia ułatwień dostępu w programie WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="8ced7-350">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="8ced7-351">Ulepszenia ułatwień dostępu w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ced7-351">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="8ced7-352">W programie .NET Framework 4.7.1 Windows Forms (WinForms) zawiera zmiany ułatwień dostępu w następujących obszarach.</span><span class="sxs-lookup"><span data-stu-id="8ced7-352">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="8ced7-353">**Ulepszone wyświetlaną w trybie dużego kontrastu**</span><span class="sxs-lookup"><span data-stu-id="8ced7-353">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="8ced7-354">Począwszy od .NET Framework 4.7.1 różne formanty formularzy WinForm oferuje ulepszoną renderowania w trybach HighContrast dostępne w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="8ced7-354">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="8ced7-355">Windows 10 została zmieniona wartości dla niektórych dużego kontrastu kolorów systemu i formularze Windows opiera się na platformę Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="8ced7-355">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="8ced7-356">Aby uzyskać najlepsze wyniki Uruchom w najnowszej wersji systemu Windows, a następnie Zezwól na korzystanie z najnowszych zmian systemu operacyjnego, dodając plik app.manifest w aplikacji testowej i un-comment systemu Windows 10 obsługiwanych wiersza systemu operacyjnego wyglądającą następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8ced7-356">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="8ced7-357">Niektóre zmiany o wysokim kontraście należą:</span><span class="sxs-lookup"><span data-stu-id="8ced7-357">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="8ced7-358">Zaznaczeń w <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="8ced7-358">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="8ced7-359">Po wybraniu wyłączone <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="8ced7-359">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="8ced7-360">Tekst w wybranych <xref:System.Windows.Forms.Button> kontrolować różni się od kolor wyboru.</span><span class="sxs-lookup"><span data-stu-id="8ced7-360">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="8ced7-361">Wyłączony tekst jest łatwiejsza do odczytania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-361">Disabled text is easier to read.</span></span> <span data-ttu-id="8ced7-362">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8ced7-362">For example:</span></span>

  <span data-ttu-id="8ced7-363">Przed:</span><span class="sxs-lookup"><span data-stu-id="8ced7-363">Before:</span></span>

  ![Wyłączony tekst przed ulepszenia ułatwień dostępu](media/wf-disabled-before.png) 

  <span data-ttu-id="8ced7-365">Po:</span><span class="sxs-lookup"><span data-stu-id="8ced7-365">After:</span></span>

  ![Wyłączony tekst po ulepszenia ułatwień dostępu](media/wf-disabled-after.png) 

- <span data-ttu-id="8ced7-367">Duży kontrast ulepszenia w oknie dialogowym wyjątku wątku.</span><span class="sxs-lookup"><span data-stu-id="8ced7-367">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="8ced7-368">**Ulepszona obsługa Narrator**</span><span class="sxs-lookup"><span data-stu-id="8ced7-368">**Improved Narrator support**</span></span>

<span data-ttu-id="8ced7-369">Windows Forms w programie .NET Framework 4.7.1 obejmuje następujące ulepszenia ułatwień dostępu w programie Narrator:</span><span class="sxs-lookup"><span data-stu-id="8ced7-369">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="8ced7-370"><xref:System.Windows.Forms.MonthCalendar> Kontroli jest możliwy, Narrator, a także innymi narzędziami automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8ced7-370">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="8ced7-371"><xref:System.Windows.Forms.CheckedListBox> Kontroli powiadamia program Narrator, gdy stan zaznaczenia elementu została zmieniona, dzięki czemu użytkownik jest powiadamiany one zmieniono wartość elementu listy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-371">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="8ced7-372"><xref:System.Windows.Forms.DataGridViewCell> Kontroli raporty prawidłowy stan tylko do odczytu do Narrator.</span><span class="sxs-lookup"><span data-stu-id="8ced7-372">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="8ced7-373">Narrator, teraz mogą odczytywać wyłączone <xref:System.Windows.Forms.ToolStripMenuItem> tekstu, należy wcześniej może pominąć elementów menu wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8ced7-373">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="8ced7-374">**Rozszerzona obsługa biblioteki UIAutomation ułatwień dostępu wzorców**</span><span class="sxs-lookup"><span data-stu-id="8ced7-374">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="8ced7-375">Począwszy od .NET Framework 4.7.1 deweloperów technologii ułatwień dostępu mogą korzystać z typowych wzorców ułatwień dostępu do interfejsu API i właściwości dla kilku formantów formularzy WinForm.</span><span class="sxs-lookup"><span data-stu-id="8ced7-375">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="8ced7-376">Te ulepszenia ułatwień dostępu, obejmują:</span><span class="sxs-lookup"><span data-stu-id="8ced7-376">These accessibility improvements include:</span></span>

- <span data-ttu-id="8ced7-377"><xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ToolStripSplitButton> obsługują teraz [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8ced7-377">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="8ced7-378"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Obsługuje teraz [wzorca przełącznika](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8ced7-378">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="8ced7-379"><xref:System.Windows.Forms.ToolStripItem> Kontrolować obsługuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości i [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8ced7-379">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="8ced7-380"><xref:System.Windows.Forms.NumericUpDown> i <xref:System.Windows.Forms.DomainUpDown> kontroluje pomocy technicznej <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ced7-380">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="8ced7-381">**Ulepszone właściwość przeglądania**</span><span class="sxs-lookup"><span data-stu-id="8ced7-381">**Improved property browser experience**</span></span>

<span data-ttu-id="8ced7-382">Formularze Windows począwszy od .NET Framework 4.7.1 obejmuje:</span><span class="sxs-lookup"><span data-stu-id="8ced7-382">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="8ced7-383">Lepsze nawigacji za pomocą klawiatury przez różne okna wyboru z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="8ced7-383">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="8ced7-384">Ograniczenia niepotrzebne tabulatorów.</span><span class="sxs-lookup"><span data-stu-id="8ced7-384">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="8ced7-385">Lepiej raportowanie typów formantów.</span><span class="sxs-lookup"><span data-stu-id="8ced7-385">Better reporting of control types.</span></span>
- <span data-ttu-id="8ced7-386">Ulepszone narrator zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8ced7-386">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="8ced7-387">Kontrolki sieci web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8ced7-387">ASP.NET web controls</span></span>

<span data-ttu-id="8ced7-388">Począwszy od .NET Framework 4.7.1 i Visual Studio 2017 15.3, ASP.NET poprawia działanie kontrolki sieci web platformy ASP.NET przy użyciu technologii ułatwień dostępu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8ced7-388">Starting with .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="8ced7-389">Następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="8ced7-389">Changes include the following:</span></span>

- <span data-ttu-id="8ced7-390">Zmiany do zaimplementowania Brak wzorce dostępności interfejsu użytkownika w kontrolkach, takie jak **Dodaj pole** okna dialogowego w **widoku szczegółów** kreatora lub **skonfigurować ListView** okna dialogowego z **ListView** kreatora.</span><span class="sxs-lookup"><span data-stu-id="8ced7-390">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="8ced7-391">Zmiany w celu wyświetlania w trybie dużego kontrastu, takie jak **Edytor pola pagera danych**.</span><span class="sxs-lookup"><span data-stu-id="8ced7-391">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="8ced7-392">Zmiany w celu polepszenia nawigacji klawiatury napotyka formanty, takie jak **pola** okna dialogowego w **Edytuj pola pagera** kreatora formantu DataPager **konfigurowania obiektu ObjectContext**  okno dialogowe, lub **Konfigurowanie wyboru danych** dialogowego **skonfigurować źródło danych** kreatora.</span><span class="sxs-lookup"><span data-stu-id="8ced7-392">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="8ced7-393">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="8ced7-393">.NET SDK Tools</span></span>

<span data-ttu-id="8ced7-394">[Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) i [narzędzie śledzenia usług (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) zostały ulepszone przez Rozwiązywanie problemów zależeć od dostępności.</span><span class="sxs-lookup"><span data-stu-id="8ced7-394">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="8ced7-395">Większość z nich zostały się niewielkie problemy, takie jak nazwy, nie zostały zdefiniowane lub niektóre wzorce automatyzacji interfejsu użytkownika nie jest zaimplementowana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="8ced7-395">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="8ced7-396">Gdy wielu użytkowników nie należy pamiętać o tych niepoprawne wartości, klienci korzystający z technologiami pomocniczymi, takich jak czytniki zawartości ekranu znajduje się tych narzędzi zestawu SDK łatwiej dostępne.</span><span class="sxs-lookup"><span data-stu-id="8ced7-396">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="8ced7-397">Te ulepszenia zmianę niektórych zachowań poprzedniej, takich jak kolejność fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8ced7-397">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="8ced7-398">Projektanta przepływów pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="8ced7-398">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="8ced7-399">Następujące zmiany w ułatwienia dostępu w Projektancie przepływu pracy:</span><span class="sxs-lookup"><span data-stu-id="8ced7-399">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="8ced7-400">Zmienia kolejność tabulacji od lewej do prawej i od góry do dołu w niektóre kontrolki:</span><span class="sxs-lookup"><span data-stu-id="8ced7-400">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="8ced7-401">W oknie korelacji inicjowanie korelacji danych dla <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-401">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="8ced7-402">W oknie definicji zawartości <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działań.</span><span class="sxs-lookup"><span data-stu-id="8ced7-402">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="8ced7-403">Więcej funkcji są dostępne za pośrednictwem klawiatury:</span><span class="sxs-lookup"><span data-stu-id="8ced7-403">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="8ced7-404">Podczas edytowania właściwości działania, grupy właściwości można zwinąć, klawiatury są skupia się po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-404">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="8ced7-405">Ikony ostrzeżenia są dostępne dla klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8ced7-405">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="8ced7-406">**Więcej właściwości** znajdujący się w **właściwości** okno jest dostępny za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="8ced7-406">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="8ced7-407">Klawiatura, użytkownicy mogą uzyskiwać dostęp elementy nagłówka w **argumenty** i **zmienne** okienka projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-407">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="8ced7-408">Ulepszona widoczność elementów z fokusem, takie jak czas:</span><span class="sxs-lookup"><span data-stu-id="8ced7-408">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="8ced7-409">Dodawanie wierszy do siatki danych używane przez projektantów projektanta przepływów pracy i działania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-409">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="8ced7-410">TAB pól w <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply> działań.</span><span class="sxs-lookup"><span data-stu-id="8ced7-410">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="8ced7-411">Ustawianie wartości domyślnych dla zmiennych lub argumentów</span><span class="sxs-lookup"><span data-stu-id="8ced7-411">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="8ced7-412">Czytniki zawartości ekranu teraz mógł prawidłowo rozpoznać:</span><span class="sxs-lookup"><span data-stu-id="8ced7-412">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="8ced7-413">Punkty przerwania ustawione w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-413">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="8ced7-414"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, I <xref:System.ServiceModel.Activities.CorrelationScope> działań.</span><span class="sxs-lookup"><span data-stu-id="8ced7-414">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="8ced7-415">Zawartość <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-415">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="8ced7-416">Typ docelowy dla <xref:System.Activities.Statements.InvokeMethod> działania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-416">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="8ced7-417">Pole kombi wyjątek i na koniec sekcji <xref:System.Activities.Statements.TryCatch> działania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-417">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="8ced7-418">Pole kombi typu komunikatu, podziału w oknie Dodaj inicjatory korelacji, okno definicji zawartości i okna definice Vlastnosti Correlateson działań dotyczących komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="8ced7-418">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="8ced7-419">Automat stanów przejścia i przeniesie miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="8ced7-419">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="8ced7-420">Adnotacje i łączników na <xref:System.Activities.Statements.FlowDecision> działań.</span><span class="sxs-lookup"><span data-stu-id="8ced7-420">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="8ced7-421">Menu kontekstowe (kliknij prawym przyciskiem myszy), działań.</span><span class="sxs-lookup"><span data-stu-id="8ced7-421">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="8ced7-422">Edytory wartości właściwości, przycisk Wyczyść wyszukiwanie, według kategorii i przyciski sortowania alfabetycznego i okno dialogowe Edytor wyrażeń w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ced7-422">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="8ced7-423">Procent powiększenia w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-423">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="8ced7-424">Separator w <xref:System.Activities.Statements.Parallel> i <xref:System.Activities.Statements.Pick> działań.</span><span class="sxs-lookup"><span data-stu-id="8ced7-424">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="8ced7-425"><xref:System.Activities.Statements.InvokeDelegate> Działania.</span><span class="sxs-lookup"><span data-stu-id="8ced7-425">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="8ced7-426">W oknie Wybierz typy działań słownika (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`itp.).</span><span class="sxs-lookup"><span data-stu-id="8ced7-426">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="8ced7-427">Przeglądanie i wybieranie typu .NET okna.</span><span class="sxs-lookup"><span data-stu-id="8ced7-427">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="8ced7-428">Linki do stron nadrzędnych w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ced7-428">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="8ced7-429">Użytkownicy, którzy wysokiego kontrastu, motywów zobaczą wiele ulepszeń w widoczność projektanta przepływów pracy i jego formantów, takie jak lepsza współczynniki kontrastu między elementami i lepiej widoczne pola wyboru używany do elementów zespołu.</span><span class="sxs-lookup"><span data-stu-id="8ced7-429">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ced7-430">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ced7-430">See also</span></span>

- [<span data-ttu-id="8ced7-431">What's new in .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8ced7-431">What's new in the .NET Framework</span></span>](whats-new.md)
