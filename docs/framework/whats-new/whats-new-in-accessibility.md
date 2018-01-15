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
ms.openlocfilehash: e6a6759ae285f2dd101bddf71ea8e5ca792e87df
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="80285-102">What's new in ułatwień dostępu w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="80285-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="80285-103">Celem jest tworzenie aplikacji więcej accessibile dla użytkowników programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80285-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="80285-104">Funkcje ułatwień dostępu zezwala aplikacji zapewnić odpowiednie funkcje użytkowników korzystających z technologii pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="80285-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="80285-105">Począwszy od programu .NET Framework 4.7.1, .NET Framework zawiera wiele ulepszeń ułatwień dostępu, które umożliwiają deweloperom tworzenie aplikacji dostępny.</span><span class="sxs-lookup"><span data-stu-id="80285-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="80285-106">Nowe funkcje ułatwień dostępu są włączone domyślnie dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="80285-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="80285-107">Ponadto aplikacje, które są stosowane do wcześniejszej wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.7.1 lub później włączyć zachowań starszych ułatwień dostępu (i tym samym zgłosić się do poprawy ułatwień dostępu w programie .NET Framework 4.7.1) przez Dodawanie do następującego przełącznika [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80285-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="80285-108">Podobnie, aplikacji, które odnoszą się do wersji programu .NET Framework, począwszy od 4.7.1 można wyłączyć funkcje ułatwień dostępu, dodając następujący przełącznik do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80285-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="80285-109">What's new in ułatwień dostępu w programie .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="80285-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="80285-110">.NET Framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="80285-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="80285-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="80285-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="80285-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80285-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="80285-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="80285-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="80285-114">**Ulepszenia czytnika ekranu**</span><span class="sxs-lookup"><span data-stu-id="80285-114">**Screen reader improvements**</span></span>

<span data-ttu-id="80285-115">Włączenie ulepszenia ułatwień dostępu programu .NET Framework 4.7.1 obejmuje następujące rozszerzenia, które mają wpływ na czytników ekranu:</span><span class="sxs-lookup"><span data-stu-id="80285-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="80285-116">.NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.Expander> formanty ogłoszeniu czytników ekranu jako przyciski.</span><span class="sxs-lookup"><span data-stu-id="80285-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="80285-117">Począwszy od programu .NET Framework 4.7.1 ich obsłudze zostaną poprawnie opublikowane jako rozwijania/zwijanej grupy.</span><span class="sxs-lookup"><span data-stu-id="80285-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="80285-118">.NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.DataGridCell> formanty ogłoszeniu czytników ekranu jako "custom".</span><span class="sxs-lookup"><span data-stu-id="80285-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="80285-119">Począwszy od programu .NET Framework 4.7.1 one są teraz prawidłowo anonsowane jako komórki siatki danych (zlokalizowany).</span><span class="sxs-lookup"><span data-stu-id="80285-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="80285-120">Począwszy od programu .NET Framework 4.7.1 czytników ekranu ogłaszamy nazwę można edytować <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="80285-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="80285-121">.NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.PasswordBox> formanty zostały ogłoszenia jako "nie elementu w widoku" lub ma inaczej niepoprawnego zachowania.</span><span class="sxs-lookup"><span data-stu-id="80285-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="80285-122">Tego problemu w programie .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="80285-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="80285-123">**Obsługa biblioteki UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="80285-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="80285-124">Czytników ekranu, takie jak osoby pomocy Narrator odczytywać zawartość interfejsu użytkownika aplikacji, zwykle tekst na mowę dane wyjściowe zawartości interfejsu użytkownika, który ma fokus.</span><span class="sxs-lookup"><span data-stu-id="80285-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="80285-125">Jednak jeśli elementu interfejsu użytkownika zmiany i nie ma fokus, użytkownik nie może zostać zgłoszone i może pominąć ważne informacje.</span><span class="sxs-lookup"><span data-stu-id="80285-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="80285-126">Regiony na żywo na celu rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="80285-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="80285-127">Deweloper może użyć ich poinformować odczytywania zawartości ekranu lub inne klienta biblioteki UIAutomation, który wprowadzono istotne zmiany do elementu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="80285-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="80285-128">Czytnik następnie można zdecydować, jak i kiedy informują użytkownika o tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="80285-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="80285-129">Do obsługi na żywo regionów, WPF dodano następujące interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="80285-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="80285-130"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pola, które identyfikują **LiveSetting** właściwości i **LiveRegionChanged** zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="80285-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="80285-131">Można ich ustawiać przy użyciu języka XAML.</span><span class="sxs-lookup"><span data-stu-id="80285-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="80285-132">**AutomationProperties.LiveSetting** dołączona właściwość, która informuje czytnik ważne zmiany interfejsu użytkownika dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="80285-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="80285-133"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Właściwość, która identyfikuje **AutomationProperties.LiveSetting** dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="80285-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="80285-134"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metodę, która może zostać zastąpiona w celu zapewnienia **LiveSetting** wartości.</span><span class="sxs-lookup"><span data-stu-id="80285-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="80285-135"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody get i set **LiveSetting** wartości.</span><span class="sxs-lookup"><span data-stu-id="80285-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="80285-136"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Wyliczenia, który definiuje następujące możliwości **LiveSetting** wartości:</span><span class="sxs-lookup"><span data-stu-id="80285-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="80285-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80285-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80285-138">Element nie wysyła powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="80285-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="80285-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80285-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80285-140">Element wysyła powiadomienia interruptive zmiana zawartości na żywo regionu.</span><span class="sxs-lookup"><span data-stu-id="80285-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="80285-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80285-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80285-142">Element wysyła interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="80285-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="80285-143">Można utworzyć LiveRegion przez ustawienie **AutomationProperties.LiveSetting** właściwości w elemencie zainteresowań, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="80285-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="80285-144">Podczas zmiany danych w regionie na żywo i należy poinformować czytnika ekranu, należy jawnie wywołaj zdarzenie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="80285-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="80285-145">**Duży kontrast**</span><span class="sxs-lookup"><span data-stu-id="80285-145">**High contrast**</span></span>

<span data-ttu-id="80285-146">Począwszy od programu .NET Framework 4.7.1 ulepszenia duży kontrast zostały wprowadzone do różnych formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="80285-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="80285-147">Teraz są one widoczne podczas <xref:System.Windows.SystemParameters.HighContrast%2A> ustawiono motywu.</span><span class="sxs-lookup"><span data-stu-id="80285-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="80285-148">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="80285-148">These include:</span></span>

- <span data-ttu-id="80285-149"><xref:System.Windows.Controls.Expander>Formant</span><span class="sxs-lookup"><span data-stu-id="80285-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="80285-150">Fokus visual dla <xref:System.Windows.Controls.Expander> kontroli jest teraz widoczne.</span><span class="sxs-lookup"><span data-stu-id="80285-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="80285-151">Elementy wizualne klawiatury dla <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.RadioButton> formanty są również widoczne.</span><span class="sxs-lookup"><span data-stu-id="80285-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="80285-152">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="80285-152">For example:</span></span>

    <span data-ttu-id="80285-153">Przed:</span><span class="sxs-lookup"><span data-stu-id="80285-153">Before:</span></span> 
    
    ![Kontrolkę Expander z fokusem przed ulepszenia ułatwień dostępu](media/expander-before.png)

    <span data-ttu-id="80285-155">Po:</span><span class="sxs-lookup"><span data-stu-id="80285-155">After:</span></span> 

    ![Kontrolkę Expander z fokusem po ulepszenia ułatwień dostępu](media/expander-after.png)

- <span data-ttu-id="80285-157"><xref:System.Windows.Controls.CheckBox>i <xref:System.Windows.Controls.RadioButton> formantów</span><span class="sxs-lookup"><span data-stu-id="80285-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="80285-158">Tekst w <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów jest teraz lepiej widoczne po wybraniu w kompozycji dużego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="80285-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="80285-159">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="80285-159">For example:</span></span>

    <span data-ttu-id="80285-160">Przed:</span><span class="sxs-lookup"><span data-stu-id="80285-160">Before:</span></span> 

    ![Przycisk radiowy duży kontrast z fokusem przed ulepszenia ułatwień dostępu](media/radio-button-before.png)
    
    <span data-ttu-id="80285-162">Po:</span><span class="sxs-lookup"><span data-stu-id="80285-162">After:</span></span> 

    ![Przycisk radiowy duży kontrast z fokusem po ulepszenia ułatwień dostępu](media/radio-button-after.png)

- <span data-ttu-id="80285-164"><xref:System.Windows.Controls.ComboBox>Formant</span><span class="sxs-lookup"><span data-stu-id="80285-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="80285-165">Począwszy od programu .NET Framework 4.7.1, obramowania wyłączone <xref:System.Windows.Controls.ComboBox> formant jest kolor wyłączonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="80285-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="80285-166">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="80285-166">For example:</span></span>
    
    <span data-ttu-id="80285-167">Przed:</span><span class="sxs-lookup"><span data-stu-id="80285-167">Before:</span></span> 

     ![ComboBox — wyłączone obramowania i tekst przed ulepszenia ułatwień dostępu](media/combo-disabled-before.png)

    <span data-ttu-id="80285-169">Po:</span><span class="sxs-lookup"><span data-stu-id="80285-169">After:</span></span>   

     ![ComboBox — wyłączone obramowania i tekst po ulepszenia ułatwień dostępu](media/combo-disabled-after.png)

    <span data-ttu-id="80285-171">Ponadto przyciski wyłączone i skupiają się użyć kolor motywu poprawne.</span><span class="sxs-lookup"><span data-stu-id="80285-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="80285-172">Przed:</span><span class="sxs-lookup"><span data-stu-id="80285-172">Before:</span></span>

    ![Przycisk motywu kolorów przed ulepszenia ułatwień dostępu](media/button-themes-before.png) 
    
    <span data-ttu-id="80285-174">Po:</span><span class="sxs-lookup"><span data-stu-id="80285-174">After:</span></span> 

    ![Przycisk motywu kolorów po ulepszenia ułatwień dostępu](media/button-themes-after.png) 

    <span data-ttu-id="80285-176">Ponadto w .NET Framework 4.7 i wcześniejsze wersje, ustawienie <xref:System.Windows.Controls.ComboBox> stylu kontrolki do `Toolbar.ComboBoxStyleKey` spowodował strzałkę listy rozwijanej, aby była niewidoczna.</span><span class="sxs-lookup"><span data-stu-id="80285-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="80285-177">Tego problemu w programie .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="80285-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="80285-178">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="80285-178">For example:</span></span>

    <span data-ttu-id="80285-179">Przed:</span><span class="sxs-lookup"><span data-stu-id="80285-179">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey przed ulepszenia ułatwień dostępu](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="80285-181">Po:</span><span class="sxs-lookup"><span data-stu-id="80285-181">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey po ulepszenia ułatwień dostępu](media/comboboxstylekey-after.png) 

- <span data-ttu-id="80285-183"><xref:System.Windows.Controls.DataGrid>Formant</span><span class="sxs-lookup"><span data-stu-id="80285-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="80285-184">Począwszy od programu .NET Framework 4.7.1, Strzałka wskaźnika sortowania w <xref:System.Windows.Controls.DataGrid> steruje teraz używa Popraw kolorów motywu.</span><span class="sxs-lookup"><span data-stu-id="80285-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="80285-185">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="80285-185">For example:</span></span>

    <span data-ttu-id="80285-186">Przed:</span><span class="sxs-lookup"><span data-stu-id="80285-186">Before:</span></span> 

    ![Sortowanie Strzałka wskaźnika przed ulepszenia ułatwień dostępu](media/sort-indicator-before.png) 
    
    <span data-ttu-id="80285-188">Po:</span><span class="sxs-lookup"><span data-stu-id="80285-188">After:</span></span>   
 
    ![Strzałka wskaźnika sortowania po ulepszenia ułatwień dostępu](media/sort-indicator-after.png) 
    
    <span data-ttu-id="80285-190">Ponadto w programie .NET Framework 4.7 i wcześniejszych wersjach, domyślny styl łącza zmieniony na nieprawidłowy kolor na myszy za pośrednictwem w trybie dużego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="80285-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="80285-191">Ten problem został rozwiązany, począwszy od programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="80285-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="80285-192">Podobnie <xref:System.Windows.Controls.DataGrid> kolumn wyboru używa oczekiwanego kolorów w programie .NET Framework 4.7.1 opinii fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="80285-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="80285-193">Przed:</span><span class="sxs-lookup"><span data-stu-id="80285-193">Before:</span></span> 

    ![Styl łącza domyślne DataGrid przed ulepszenia ułatwień dostępu](media/default-link-style-before.png) 
 
    <span data-ttu-id="80285-195">Po:</span><span class="sxs-lookup"><span data-stu-id="80285-195">After:</span></span>    
  
    ![Styl łącza domyślne DataGrid po ulepszenia ułatwień dostępu](media/default-link-style-after.png)  

<span data-ttu-id="80285-197">Aby uzyskać więcej informacji na WPF ulepszenia ułatwień dostępu w programie .NET Framework 4.7.1, zobacz [usprawnienia dostępu na platformie WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="80285-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="80285-198">Ulepszenia dostępność formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80285-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="80285-199">W programie .NET Framework 4.7.1 formularze systemu Windows (WinForms) zawiera zmiany ułatwień dostępu w następujących obszarach.</span><span class="sxs-lookup"><span data-stu-id="80285-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="80285-200">**Ulepszone wyświetlania w trybie dużego kontrastu**</span><span class="sxs-lookup"><span data-stu-id="80285-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="80285-201">Począwszy od programu .NET Framework 4.7.1 różnych formantów WinForms oferują ulepszoną renderowania w trybach HighContrast dostępne w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="80285-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="80285-202">Windows 10 zmienił wartości dla niektórych kolorów systemu duży kontrast, i formularze systemu Windows jest oparta na platformę Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="80285-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="80285-203">Aby uzyskać najlepsze wyniki należy uruchomić na najnowszej wersji systemu Windows i korzystania z najnowszych zmian systemu operacyjnego przez dodawanie pliku app.manifest aplikacja testowa i un komentarz systemu Windows 10 obsługiwane wiersza systemu operacyjnego, aby wyglądały one następujące:</span><span class="sxs-lookup"><span data-stu-id="80285-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="80285-204">Niektóre zmiany duży kontrast należą:</span><span class="sxs-lookup"><span data-stu-id="80285-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="80285-205">Zaznaczeń w <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="80285-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="80285-206">Po wybraniu wyłączone <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="80285-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="80285-207">Tekst w wybranej <xref:System.Windows.Forms.Button> kontrolować różni się od kolor zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="80285-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="80285-208">Wyłączony tekst jest bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="80285-208">Disabled text is easier to read.</span></span> <span data-ttu-id="80285-209">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="80285-209">For example:</span></span>

    <span data-ttu-id="80285-210">Przed:</span><span class="sxs-lookup"><span data-stu-id="80285-210">Before:</span></span>

    ![Tekst wyłączone przed ulepszenia ułatwień dostępu](media/wf-disabled-before.png) 

    <span data-ttu-id="80285-212">Po:</span><span class="sxs-lookup"><span data-stu-id="80285-212">After:</span></span>

    ![Wyłączonego tekstu po ulepszenia ułatwień dostępu](media/wf-disabled-after.png) 

- <span data-ttu-id="80285-214">Ulepszenia duży kontrast w oknie dialogowym wyjątków wątku.</span><span class="sxs-lookup"><span data-stu-id="80285-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="80285-215">**Ulepszona obsługa Narrator**</span><span class="sxs-lookup"><span data-stu-id="80285-215">**Improved Narrator support**</span></span>

<span data-ttu-id="80285-216">Formularze systemu Windows w programie .NET Framework 4.7.1 obejmuje następujące ulepszenia Narrator ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="80285-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="80285-217"><xref:System.Windows.Forms.MonthCalendar> Kontroli jest dostępny program Narrator, a także innymi narzędziami automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="80285-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="80285-218"><xref:System.Windows.Forms.CheckedListBox> Kontroli powiadamia Narrator, gdy stan zaznaczenia elementu zostanie zmieniony, więc użytkownik jest powiadamiany o ich zmieniono wartość elementu listy.</span><span class="sxs-lookup"><span data-stu-id="80285-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="80285-219"><xref:System.Windows.Forms.DataGridViewCell> Kontroli zaraportuje prawidłowe stanu tylko do odczytu do Narrator.</span><span class="sxs-lookup"><span data-stu-id="80285-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="80285-220">Narrator, mogą teraz odczytywać wyłączone <xref:System.Windows.Forms.ToolStripMenuItem> tekstu, należy wcześniej może pominąć elementów menu wyłączone.</span><span class="sxs-lookup"><span data-stu-id="80285-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="80285-221">**Rozszerzona obsługa biblioteki UIAutomation wzorce ułatwień dostępu**</span><span class="sxs-lookup"><span data-stu-id="80285-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="80285-222">Deweloperzy technologii ułatwień dostępu w programie .NET Framework 4.7.1, można wykorzystać typowe wzorce ułatwień dostępu interfejsu API i właściwości dla kilku formantów WinForms.</span><span class="sxs-lookup"><span data-stu-id="80285-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="80285-223">Ułatwienia dostępu do tych udoskonaleń należą:</span><span class="sxs-lookup"><span data-stu-id="80285-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="80285-224"><xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ToolStripSplitButton> obsługują teraz [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="80285-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="80285-225"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Obsługuje teraz [toggle — wzorzec](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="80285-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="80285-226"><xref:System.Windows.Forms.ToolStripItem> Sterowanie obsługuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości i [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="80285-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="80285-227"><xref:System.Windows.Forms.NumericUpDown> i <xref:System.Windows.Forms.DomainUpDown> formanty obsługi <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości.</span><span class="sxs-lookup"><span data-stu-id="80285-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="80285-228">**Ulepszone właściwości przeglądania**</span><span class="sxs-lookup"><span data-stu-id="80285-228">**Improved property browser experience**</span></span>

<span data-ttu-id="80285-229">Formularze systemu Windows w programie .NET Framework 4.7.1, obejmują:</span><span class="sxs-lookup"><span data-stu-id="80285-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="80285-230">Lepsze nawigacji klawiatury przez różne okna wyboru z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="80285-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="80285-231">Zmniejszenie niepotrzebnych tabulatorów.</span><span class="sxs-lookup"><span data-stu-id="80285-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="80285-232">Lepiej raportowanie typy formantów.</span><span class="sxs-lookup"><span data-stu-id="80285-232">Better reporting of control types.</span></span>
- <span data-ttu-id="80285-233">Ulepszone narrator zachowanie.</span><span class="sxs-lookup"><span data-stu-id="80285-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="80285-234">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80285-234">See Also</span></span>
[<span data-ttu-id="80285-235">Co to jest nowe w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="80285-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 