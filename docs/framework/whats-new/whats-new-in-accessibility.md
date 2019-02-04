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
ms.openlocfilehash: 092b1cfc9350ea398eb18199f19a8eee7ea9f218
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675442"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="e2044-102">What's new in ułatwień dostępu w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2044-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="e2044-103">Celem jest udostępnienie aplikacji dla użytkowników programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2044-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="e2044-104">Funkcje ułatwień dostępu, Zezwalaj na aplikację zapewnić odpowiednie środowisko dla użytkowników technologii pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="e2044-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="e2044-105">Począwszy od programu .NET Framework 4.7.1 .NET Framework zawiera dużą liczbę ulepszenia ułatwień dostępu, które umożliwiają deweloperom tworzyć aplikacje dostępne.</span><span class="sxs-lookup"><span data-stu-id="e2044-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

## <a name="accessibility-switches"></a><span data-ttu-id="e2044-106">Przełączniki ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="e2044-106">Accessibility switches</span></span>

<span data-ttu-id="e2044-107">Można skonfigurować aplikację, aby skorzystać z funkcji ułatwień dostępu, jeśli jest przeznaczony dla .NET Framework 4.7 lub starszej wersji, ale działa w środowisku .NET Framework 4.7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="e2044-107">You can configure your app to opt into accessibility features if it targets the .NET Framework 4.7 or an earlier version but is running on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="e2044-108">Możesz także skonfigurować aplikację do używania starszych funkcji (i nie korzystaj z funkcji ułatwień dostępu), jeśli jest ono przeznaczone dla platformy .NET Framework 4.7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="e2044-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="e2044-109">Każda wersja programu .NET Framework, która obejmuje funkcje ułatwień dostępu ma przełącznika ułatwień dostępu specyficzny dla wersji, możesz dodać do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e2044-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="e2044-110">Obsługiwane przełączniki są następujące:</span><span class="sxs-lookup"><span data-stu-id="e2044-110">The following are the supported switches:</span></span>

|<span data-ttu-id="e2044-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="e2044-111">Version</span></span>|<span data-ttu-id="e2044-112">Przełącznik</span><span class="sxs-lookup"><span data-stu-id="e2044-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="e2044-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="e2044-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="e2044-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="e2044-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="e2044-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="e2044-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="e2044-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="e2044-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="e2044-117">Korzystając z zalet udoskonalonym ułatwieniom dostępu</span><span class="sxs-lookup"><span data-stu-id="e2044-117">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="e2044-118">Nowe funkcje ułatwień dostępu są włączone domyślnie dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="e2044-118">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="e2044-119">Ponadto aplikacje, które kątem starszej wersji programu .NET Framework, ale są uruchomione w środowisku .NET Framework 4.7.1 lub później zdecydować się poza zachowania dostępności starszej wersji (i tym samym zalet ulepszenia ułatwień dostępu), dodając przełączniki [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) części pliku konfiguracyjnego aplikacji i ich wartości `false`.</span><span class="sxs-lookup"><span data-stu-id="e2044-119">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="e2044-120">Poniżej przedstawiono sposób korzystania z opcji w celu ulepszenia ułatwień dostępu, wprowadzone w programie .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="e2044-120">The following shows how to opt in to accessibility enhancements introduced in the .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="e2044-121">Jeśli zdecydujesz się zgadzaj się na funkcje ułatwień dostępu w nowszej wersji programu .NET Framework, musi również jawnie zgody na uczestnictwo w funkcje z wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2044-121">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="e2044-122">Konfigurowanie aplikacji w taki sposób, aby wykorzystać ulepszenia ułatwień dostępu w systemie zarówno programu .NET Framework 4.7.1 i 4.7.2 wymaga następujących [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:</span><span class="sxs-lookup"><span data-stu-id="e2044-122">Configuring your app to take advantage of accessibility improvements in both the .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="e2044-123">Przywracanie starsze zachowanie</span><span class="sxs-lookup"><span data-stu-id="e2044-123">Restoring legacy behavior</span></span>

<span data-ttu-id="e2044-124">Aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od 4.7.1 można wyłączyć funkcje ułatwień dostępu, dodając przełączniki [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji plik konfiguracji aplikacji i ich wartości `true`.</span><span class="sxs-lookup"><span data-stu-id="e2044-124">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="e2044-125">Na przykład następująca konfiguracja oznacza brak zgody na funkcje ułatwień dostępu, które wprowadzono w programie .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="e2044-125">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a><span data-ttu-id="e2044-126">What's new in ułatwień dostępu w programie .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="e2044-126">What's new in accessibility in the .NET Framework 4.7.2</span></span>

<span data-ttu-id="e2044-127">.NET Framework 4.7.2 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="e2044-127">The .NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="e2044-128">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2044-128">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="e2044-129">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="e2044-129">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a><span data-ttu-id="e2044-130">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2044-130">Windows Forms</span></span>

<span data-ttu-id="e2044-131">**Zdefiniowane przez system operacyjny kolory wysokiego kontrastu, motywów**</span><span class="sxs-lookup"><span data-stu-id="e2044-131">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="e2044-132">Począwszy od .NET Framework 4.7.2 formularze Windows używa kolorów zdefiniowanych przez system operacyjny w wysokiego kontrastu, motywów.</span><span class="sxs-lookup"><span data-stu-id="e2044-132">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="e2044-133">Dotyczy to następujących formantów:</span><span class="sxs-lookup"><span data-stu-id="e2044-133">This affects the following controls:</span></span>

- <span data-ttu-id="e2044-134">Strzałki listy rozwijanej z <xref:System.Windows.Forms.ToolStripDropDownButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="e2044-134">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="e2044-135"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> steruje się za pomocą <xref:System.Windows.Forms.ButtonBase.FlatStyle> równa <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2044-135">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e2044-136">Wcześniej wybranych kolorów tekstu i tła nie zostały kontrastujących i były trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="e2044-136">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="e2044-137">Kontrolek znajdujących się w obrębie <xref:System.Windows.Forms.GroupBox> zawierający jego <xref:System.Windows.Forms.Control.Enabled> właściwością `false`.</span><span class="sxs-lookup"><span data-stu-id="e2044-137">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
 
- <span data-ttu-id="e2044-138"><xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, I <xref:System.Windows.Forms.ToolStripDropDownButton> formanty, które mają większą jasność współczynnik kontrastu w trybie wysokiego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="e2044-138">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="e2044-139"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="e2044-139">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="e2044-140">**Ulepszenia Narrator**</span><span class="sxs-lookup"><span data-stu-id="e2044-140">**Narrator improvements**</span></span>

<span data-ttu-id="e2044-141">Począwszy od programu .NET Framework 4.7.2 obsługi programu Narrator został rozszerzony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e2044-141">Starting with the .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="e2044-142">Ogłasza, wartość <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> właściwości ogłoszenie tekst <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="e2044-142">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span> 

- <span data-ttu-id="e2044-143">Oznacza to, kiedy <xref:System.Windows.Forms.ToolStripMenuItem> ma jego <xref:System.Windows.Forms.Control.Enabled> właściwością `false`.</span><span class="sxs-lookup"><span data-stu-id="e2044-143">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="e2044-144">Przekazuje opinie dotyczące stanu pola wyboru gdy <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="e2044-144">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="e2044-145">Program Narrator firmy Skanuj tryb koncentracji uwagi kolejność jest zgodna z visual kolejność kontrolek w oknie dialogowym pobierania ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="e2044-145">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="e2044-146">**Ulepszenia w formancie DataGridView**</span><span class="sxs-lookup"><span data-stu-id="e2044-146">**DataGridView improvements**</span></span>

<span data-ttu-id="e2044-147">Począwszy od programu .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> kontroli ma wprowadzono następujące ulepszenia ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="e2044-147">Starting with the .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="e2044-148">Za pomocą klawiatury można sortować wiersze.</span><span class="sxs-lookup"><span data-stu-id="e2044-148">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="e2044-149">Użytkownik może używać klawisz F3, aby posortować według bieżącej kolumny.</span><span class="sxs-lookup"><span data-stu-id="e2044-149">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="e2044-150">Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ustawiono <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, nagłówek kolumny zmieni kolor, aby wskazać bieżącej kolumny jako karty użytkownika za pośrednictwem komórek w bieżącym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e2044-150">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="e2044-151"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> zwraca kontrolki nadrzędnej poprawne.</span><span class="sxs-lookup"><span data-stu-id="e2044-151">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="e2044-152">**Ulepszone podpowiedzi wizualne**</span><span class="sxs-lookup"><span data-stu-id="e2044-152">**Improved visual cues**</span></span>

- <span data-ttu-id="e2044-153"><xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> kontrolek z pustą <xref:System.Windows.Forms.ButtonBase.Text> właściwości wyświetlania wskaźnika fokus, gdy one zostać ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="e2044-153">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="e2044-154">**Obsługa siatki właściwości ulepszone**</span><span class="sxs-lookup"><span data-stu-id="e2044-154">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="e2044-155"><xref:System.Windows.Forms.PropertyGrid> Kontrolować elementy podrzędne, które teraz zwracany `true` dla <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> właściwości tylko wtedy, gdy PropertyGrid element jest włączony.</span><span class="sxs-lookup"><span data-stu-id="e2044-155">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="e2044-156"><xref:System.Windows.Forms.PropertyGrid> Kontrolować elementy podrzędne zwracany `false` dla <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> właściwości tylko wtedy, gdy PropertyGrid element mogą być zmieniane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e2044-156">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="e2044-157">**Ulepszone klawiatury**</span><span class="sxs-lookup"><span data-stu-id="e2044-157">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="e2044-158"><xref:System.Windows.Forms.ToolStripButton> Kontrolka zezwala na fokus, gdy jest zawarty w ramach <xref:System.Windows.Forms.ToolStripPanel> zawierający <xref:System.Windows.Forms.ToolStripPanel.TabStop> właściwością `true`</span><span class="sxs-lookup"><span data-stu-id="e2044-158">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="e2044-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="e2044-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="e2044-160">**Zmiany do kontrolki pola wyboru i RadioButton**</span><span class="sxs-lookup"><span data-stu-id="e2044-160">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="e2044-161">W wcześniejszych wersjach, WPF i .NET Framework 4.7.1 <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> i <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> formanty mają niespójne i, w modelu klasycznym oraz wysokiego kontrastu motywy niepoprawne koncentracji uwagi wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="e2044-161">In the .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="e2044-162">Te problemy występują w przypadkach, gdy formanty nie mają żadnych zestawu zawartości.</span><span class="sxs-lookup"><span data-stu-id="e2044-162">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="e2044-163">Dzięki temu może być przejście pomiędzy motywów mylące i element wizualny fokusu trudne do zobaczenia.</span><span class="sxs-lookup"><span data-stu-id="e2044-163">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="e2044-164">W programie .NET Framework 4.7.2 te wizualizacje są teraz bardziej spójny między motywy i widoczność w klasycznej sieci wirtualnej i wysokiego kontrastu motywów.</span><span class="sxs-lookup"><span data-stu-id="e2044-164">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="e2044-165">**Formanty formularzy WinForm hostowany w aplikacji WPF**</span><span class="sxs-lookup"><span data-stu-id="e2044-165">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="e2044-166">Kontrolki WinForms hostowaną w aplikacji WPF, .NET Framework 4.7.1 i wcześniejszych wersjach, użytkownicy nie karcie poza warstwy WinForms w przypadku pierwszej lub ostatniej kontroli w tej warstwie WPF <xref:System.Windows.Forms.Integration.ElementHost> kontroli.</span><span class="sxs-lookup"><span data-stu-id="e2044-166">For WinForms control hosted in a WPF application in the .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="e2044-167">W programie .NET Framework 4.7.2 użytkownicy mogą teraz kartę z warstwy WinForms.</span><span class="sxs-lookup"><span data-stu-id="e2044-167">In the .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="e2044-168">Jednak automatycznych aplikacji, które zależą od fokus nigdy nie anulowania zapewnianego element warstwy WinForms może przestać działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="e2044-168">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="e2044-169">What's new in ułatwień dostępu w programie .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="e2044-169">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="e2044-170">.NET Framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="e2044-170">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="e2044-171">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="e2044-171">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="e2044-172">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2044-172">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="e2044-173">Kontrolki sieci web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e2044-173">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="e2044-174">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="e2044-174">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="e2044-175">Projektanta przepływów pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="e2044-175">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="e2044-176">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="e2044-176">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="e2044-177">**Ulepszenia czytnika ekranu**</span><span class="sxs-lookup"><span data-stu-id="e2044-177">**Screen reader improvements**</span></span>

<span data-ttu-id="e2044-178">Po włączeniu ulepszenia ułatwień dostępu programu .NET Framework 4.7.1 obejmuje następujące ulepszenia, które wpływają na czytniki zawartości ekranu:</span><span class="sxs-lookup"><span data-stu-id="e2044-178">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="e2044-179">W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.Expander> formanty zostały odczytywana przez czytniki zawartości ekranu jako przyciski.</span><span class="sxs-lookup"><span data-stu-id="e2044-179">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="e2044-180">Począwszy od programu .NET Framework 4.7.1 ich obsłudze zostaną poprawnie opublikowane jako rozwijania/zwijane grupy.</span><span class="sxs-lookup"><span data-stu-id="e2044-180">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="e2044-181">W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.DataGridCell> formantów była odczytywana przez czytniki ekranu jako "niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="e2044-181">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="e2044-182">Począwszy od programu .NET Framework 4.7.1 one są teraz prawidłowo od niedawna komórce siatki danych (zlokalizowany).</span><span class="sxs-lookup"><span data-stu-id="e2044-182">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="e2044-183">Począwszy od programu .NET Framework 4.7.1 czytniki zawartości ekranu ogłaszamy nazwę można edytować <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="e2044-183">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="e2044-184">W .NET Framework 4.7 i wcześniejszymi wersjami <xref:System.Windows.Controls.PasswordBox> formanty zostały ogłaszany jako "Brak elementów w widoku" lub ma inny sposób niepoprawne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e2044-184">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="e2044-185">Ten problem jest rozwiązany, począwszy od programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="e2044-185">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>

<span data-ttu-id="e2044-186">**Obsługa biblioteki UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="e2044-186">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="e2044-187">Czytniki zawartości ekranu, np. osób pomocy Narrator odczytać zawartość interfejsu użytkownika aplikacji, zwykle zamiany tekstu na mowę dane wyjściowe zawartości interfejsu użytkownika, który ma fokus.</span><span class="sxs-lookup"><span data-stu-id="e2044-187">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="e2044-188">Jeśli jednak element interfejsu użytkownika zmiany i nie ma fokus, użytkownik nie może otrzymywać powiadomienia i może pominąć ważne informacje.</span><span class="sxs-lookup"><span data-stu-id="e2044-188">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="e2044-189">Regiony na żywo na celu rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="e2044-189">Live regions aim at solving this problem.</span></span> <span data-ttu-id="e2044-190">Projektant umożliwia ich poinformować czytnika zawartości ekranu lub inne zgłaszający istotnych zmian do elementu interfejsu użytkownika klienta biblioteki UIAutomation.</span><span class="sxs-lookup"><span data-stu-id="e2044-190">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="e2044-191">Czytnik zawartości ekranu możesz zdecydować, jak i kiedy poinformowania użytkownika o tej zmianie.</span><span class="sxs-lookup"><span data-stu-id="e2044-191">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="e2044-192">Aby zapewnić obsługę regionów na żywo, następujące interfejsy API zostały dodane do platformy WPF:</span><span class="sxs-lookup"><span data-stu-id="e2044-192">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="e2044-193"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pola, które identyfikują **LiveSetting** właściwości i **LiveRegionChanged** zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e2044-193">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="e2044-194">Można ich ustawić przy użyciu XAML.</span><span class="sxs-lookup"><span data-stu-id="e2044-194">They can be set by using XAML.</span></span>

- <span data-ttu-id="e2044-195">**AutomationProperties.LiveSetting** dołączona właściwość, która informuje o czytnika zawartości ekranu znaczenie zmiany interfejsu użytkownika dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e2044-195">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="e2044-196"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Właściwość, która identyfikuje **AutomationProperties.LiveSetting** dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="e2044-196">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="e2044-197"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metody, która może zostać zastąpiona w celu zapewnienia **LiveSetting** wartości.</span><span class="sxs-lookup"><span data-stu-id="e2044-197">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="e2044-198"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, które get i set **LiveSetting** wartości.</span><span class="sxs-lookup"><span data-stu-id="e2044-198">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="e2044-199"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Wyliczenia, który definiuje następujące możliwości **LiveSetting** wartości:</span><span class="sxs-lookup"><span data-stu-id="e2044-199">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="e2044-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2044-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e2044-201">Element nie wysyła powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="e2044-201">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="e2044-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2044-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e2044-203">Elementu wysyła-interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="e2044-203">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="e2044-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2044-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e2044-205">Elementu wysyła interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="e2044-205">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="e2044-206">Można utworzyć LiveRegion, ustawiając **AutomationProperties.LiveSetting** właściwości w elemencie zainteresowania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e2044-206">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="e2044-207">Gdy zmieniają się dane w regionie na żywo i należy poinformować czytnika ekranu, należy jawnie wywołać zdarzenie, jak pokazano w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e2044-207">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="e2044-208">**Duży kontrast**</span><span class="sxs-lookup"><span data-stu-id="e2044-208">**High contrast**</span></span>

<span data-ttu-id="e2044-209">Począwszy od programu .NET Framework 4.7.1 o wysokim kontraście wprowadzono ulepszenia do różnych formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="e2044-209">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="e2044-210">Są one teraz widoczne podczas <xref:System.Windows.SystemParameters.HighContrast%2A> ustawiono motywu.</span><span class="sxs-lookup"><span data-stu-id="e2044-210">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="e2044-211">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="e2044-211">These include:</span></span>

- <span data-ttu-id="e2044-212"><xref:System.Windows.Controls.Expander> Kontrolki</span><span class="sxs-lookup"><span data-stu-id="e2044-212"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="e2044-213">Fokus visual dla <xref:System.Windows.Controls.Expander> kontroli jest teraz widoczna.</span><span class="sxs-lookup"><span data-stu-id="e2044-213">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="e2044-214">Wizualizacje klawiatury dla <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.RadioButton> formanty są również widoczne.</span><span class="sxs-lookup"><span data-stu-id="e2044-214">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="e2044-215">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2044-215">For example:</span></span>

    <span data-ttu-id="e2044-216">Przed:</span><span class="sxs-lookup"><span data-stu-id="e2044-216">Before:</span></span> 
    
    ![Formant ekspandera fokus przed ulepszenia ułatwień dostępu](media/expander-before.png)

    <span data-ttu-id="e2044-218">Po:</span><span class="sxs-lookup"><span data-stu-id="e2044-218">After:</span></span> 

    ![Formant ekspandera fokus po ulepszenia ułatwień dostępu](media/expander-after.png)

- <span data-ttu-id="e2044-220"><xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów</span><span class="sxs-lookup"><span data-stu-id="e2044-220"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="e2044-221">Tekst w <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> kontrolki jest teraz lepiej widoczne po wybraniu w wysokiego kontrastu, motywów.</span><span class="sxs-lookup"><span data-stu-id="e2044-221">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="e2044-222">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2044-222">For example:</span></span>

    <span data-ttu-id="e2044-223">Przed:</span><span class="sxs-lookup"><span data-stu-id="e2044-223">Before:</span></span> 

    ![Przycisk radiowy o wysokim kontraście fokus przed ulepszenia ułatwień dostępu](media/radio-button-before.png)
    
    <span data-ttu-id="e2044-225">Po:</span><span class="sxs-lookup"><span data-stu-id="e2044-225">After:</span></span> 

    ![Przycisk radiowy o wysokim kontraście fokus po ulepszenia ułatwień dostępu](media/radio-button-after.png)

- <span data-ttu-id="e2044-227"><xref:System.Windows.Controls.ComboBox> Kontrolki</span><span class="sxs-lookup"><span data-stu-id="e2044-227"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="e2044-228">Począwszy od programu .NET Framework 4.7.1, obramowania wyłączone <xref:System.Windows.Controls.ComboBox> formant jest kolor wyłączonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="e2044-228">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="e2044-229">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2044-229">For example:</span></span>
    
    <span data-ttu-id="e2044-230">Przed:</span><span class="sxs-lookup"><span data-stu-id="e2044-230">Before:</span></span> 

     ![Pole kombi wyłączone obramowanie i tekst przed ulepszenia ułatwień dostępu](media/combo-disabled-before.png)

    <span data-ttu-id="e2044-232">Po:</span><span class="sxs-lookup"><span data-stu-id="e2044-232">After:</span></span>   

     ![Pole kombi wyłączony obramowanie i tekstu po ulepszenia ułatwień dostępu](media/combo-disabled-after.png)

    <span data-ttu-id="e2044-234">Ponadto wyłączone i skoncentrowany przyciski używają kolor motywu poprawne.</span><span class="sxs-lookup"><span data-stu-id="e2044-234">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="e2044-235">Przed:</span><span class="sxs-lookup"><span data-stu-id="e2044-235">Before:</span></span>

    ![Kolory motywu przycisk przed ulepszenia ułatwień dostępu](media/button-themes-before.png) 
    
    <span data-ttu-id="e2044-237">Po:</span><span class="sxs-lookup"><span data-stu-id="e2044-237">After:</span></span> 

    ![Kolory motywu przycisku po ulepszenia ułatwień dostępu](media/button-themes-after.png) 

    <span data-ttu-id="e2044-239">Na koniec w .NET Framework 4.7 i wcześniejszych wersjach, ustawienie <xref:System.Windows.Controls.ComboBox> stylu kontrolki do `Toolbar.ComboBoxStyleKey` spowodowane strzałkę listy rozwijanej, aby była niewidoczna.</span><span class="sxs-lookup"><span data-stu-id="e2044-239">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="e2044-240">Ten problem jest rozwiązany, począwszy od programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="e2044-240">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="e2044-241">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2044-241">For example:</span></span>

    <span data-ttu-id="e2044-242">Przed:</span><span class="sxs-lookup"><span data-stu-id="e2044-242">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey przed ulepszenia ułatwień dostępu](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="e2044-244">Po:</span><span class="sxs-lookup"><span data-stu-id="e2044-244">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey po ulepszenia ułatwień dostępu](media/comboboxstylekey-after.png) 

- <span data-ttu-id="e2044-246"><xref:System.Windows.Controls.DataGrid> Kontrolki</span><span class="sxs-lookup"><span data-stu-id="e2044-246"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="e2044-247">Począwszy od programu .NET Framework 4.7.1, strzałkę wskaźnika sortowania w <xref:System.Windows.Controls.DataGrid> kontroluje teraz używa Popraw kolory motywu.</span><span class="sxs-lookup"><span data-stu-id="e2044-247">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="e2044-248">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2044-248">For example:</span></span>

    <span data-ttu-id="e2044-249">Przed:</span><span class="sxs-lookup"><span data-stu-id="e2044-249">Before:</span></span> 

    ![Sortowanie strzałkę wskaźnika przed ulepszenia ułatwień dostępu](media/sort-indicator-before.png) 
    
    <span data-ttu-id="e2044-251">Po:</span><span class="sxs-lookup"><span data-stu-id="e2044-251">After:</span></span>   
 
    ![Strzałka wskaźnika sortowania po ulepszenia ułatwień dostępu](media/sort-indicator-after.png) 
    
    <span data-ttu-id="e2044-253">Ponadto w .NET Framework 4.7 i wcześniejszych wersjach, domyślnego stylu łącze zmieniony na niepoprawny kolor na myszy w trybach o wysokim kontraście.</span><span class="sxs-lookup"><span data-stu-id="e2044-253">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="e2044-254">Ten problem został rozwiązany, począwszy od programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="e2044-254">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="e2044-255">Podobnie <xref:System.Windows.Controls.DataGrid> wyboru kolumn używa oczekiwanego kolorów opinii fokus klawiatury, począwszy od programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="e2044-255">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="e2044-256">Przed:</span><span class="sxs-lookup"><span data-stu-id="e2044-256">Before:</span></span> 

    ![Styl łącza domyślne DataGrid przed ulepszenia ułatwień dostępu](media/default-link-style-before.png) 
 
    <span data-ttu-id="e2044-258">Po:</span><span class="sxs-lookup"><span data-stu-id="e2044-258">After:</span></span>    
  
    ![Styl łącza domyślne DataGrid po ulepszenia ułatwień dostępu](media/default-link-style-after.png)  

<span data-ttu-id="e2044-260">Aby uzyskać więcej informacji na temat ulepszenia ułatwień dostępu WPF w programie .NET Framework 4.7.1, zobacz [ulepszenia ułatwień dostępu w programie WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="e2044-260">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>
### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="e2044-261">Ulepszenia ułatwień dostępu w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2044-261">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="e2044-262">W .NET Framework 4.7.1 Windows Forms (WinForms) zawiera zmiany ułatwień dostępu w następujących obszarach.</span><span class="sxs-lookup"><span data-stu-id="e2044-262">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="e2044-263">**Ulepszone wyświetlaną w trybie dużego kontrastu**</span><span class="sxs-lookup"><span data-stu-id="e2044-263">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="e2044-264">Począwszy od programu .NET Framework 4.7.1 różne formanty formularzy WinForm oferuje ulepszoną renderowania w trybach HighContrast dostępne w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="e2044-264">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="e2044-265">Windows 10 została zmieniona wartości dla niektórych dużego kontrastu kolorów systemu i formularze Windows opiera się na platformę Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="e2044-265">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="e2044-266">Aby uzyskać najlepsze wyniki Uruchom w najnowszej wersji systemu Windows, a następnie Zezwól na korzystanie z najnowszych zmian systemu operacyjnego, dodając plik app.manifest w aplikacji testowej i un-comment systemu Windows 10 obsługiwanych wiersza systemu operacyjnego wyglądającą następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e2044-266">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="e2044-267">Niektóre zmiany o wysokim kontraście należą:</span><span class="sxs-lookup"><span data-stu-id="e2044-267">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="e2044-268">Zaznaczeń w <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="e2044-268">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="e2044-269">Po wybraniu wyłączone <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="e2044-269">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="e2044-270">Tekst w wybranych <xref:System.Windows.Forms.Button> kontrolować różni się od kolor wyboru.</span><span class="sxs-lookup"><span data-stu-id="e2044-270">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="e2044-271">Wyłączony tekst jest łatwiejsza do odczytania.</span><span class="sxs-lookup"><span data-stu-id="e2044-271">Disabled text is easier to read.</span></span> <span data-ttu-id="e2044-272">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e2044-272">For example:</span></span>

    <span data-ttu-id="e2044-273">Przed:</span><span class="sxs-lookup"><span data-stu-id="e2044-273">Before:</span></span>

    ![Wyłączony tekst przed ulepszenia ułatwień dostępu](media/wf-disabled-before.png) 

    <span data-ttu-id="e2044-275">Po:</span><span class="sxs-lookup"><span data-stu-id="e2044-275">After:</span></span>

    ![Wyłączony tekst po ulepszenia ułatwień dostępu](media/wf-disabled-after.png) 

- <span data-ttu-id="e2044-277">Duży kontrast ulepszenia w oknie dialogowym wyjątku wątku.</span><span class="sxs-lookup"><span data-stu-id="e2044-277">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="e2044-278">**Ulepszona obsługa Narrator**</span><span class="sxs-lookup"><span data-stu-id="e2044-278">**Improved Narrator support**</span></span>

<span data-ttu-id="e2044-279">Formularzy Windows w programie .NET Framework 4.7.1 obejmuje następujące ulepszenia ułatwień dostępu w programie Narrator:</span><span class="sxs-lookup"><span data-stu-id="e2044-279">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="e2044-280"><xref:System.Windows.Forms.MonthCalendar> Kontroli jest możliwy, Narrator, a także innymi narzędziami automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e2044-280">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="e2044-281"><xref:System.Windows.Forms.CheckedListBox> Kontroli powiadamia program Narrator, gdy stan zaznaczenia elementu została zmieniona, dzięki czemu użytkownik jest powiadamiany one zmieniono wartość elementu listy.</span><span class="sxs-lookup"><span data-stu-id="e2044-281">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="e2044-282"><xref:System.Windows.Forms.DataGridViewCell> Kontroli raporty prawidłowy stan tylko do odczytu do Narrator.</span><span class="sxs-lookup"><span data-stu-id="e2044-282">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="e2044-283">Narrator, teraz mogą odczytywać wyłączone <xref:System.Windows.Forms.ToolStripMenuItem> tekstu, należy wcześniej może pominąć elementów menu wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e2044-283">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="e2044-284">**Rozszerzona obsługa biblioteki UIAutomation ułatwień dostępu wzorców**</span><span class="sxs-lookup"><span data-stu-id="e2044-284">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="e2044-285">Począwszy od programu .NET Framework 4.7.1 deweloperów technologii ułatwień dostępu mogą korzystać z typowych wzorców ułatwień dostępu do interfejsu API i właściwości dla kilku formantów formularzy WinForm.</span><span class="sxs-lookup"><span data-stu-id="e2044-285">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="e2044-286">Te ulepszenia ułatwień dostępu, obejmują:</span><span class="sxs-lookup"><span data-stu-id="e2044-286">These accessibility improvements include:</span></span>

- <span data-ttu-id="e2044-287"><xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ToolStripSplitButton> obsługują teraz [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e2044-287">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="e2044-288"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Obsługuje teraz [wzorca przełącznika](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e2044-288">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="e2044-289"><xref:System.Windows.Forms.ToolStripItem> Kontrolować obsługuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości i [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e2044-289">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="e2044-290"><xref:System.Windows.Forms.NumericUpDown> i <xref:System.Windows.Forms.DomainUpDown> kontroluje pomocy technicznej <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e2044-290">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="e2044-291">**Ulepszone właściwość przeglądania**</span><span class="sxs-lookup"><span data-stu-id="e2044-291">**Improved property browser experience**</span></span>

<span data-ttu-id="e2044-292">Formularze Windows począwszy od programu .NET Framework 4.7.1 obejmuje:</span><span class="sxs-lookup"><span data-stu-id="e2044-292">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="e2044-293">Lepsze nawigacji za pomocą klawiatury przez różne okna wyboru z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="e2044-293">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="e2044-294">Ograniczenia niepotrzebne tabulatorów.</span><span class="sxs-lookup"><span data-stu-id="e2044-294">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="e2044-295">Lepiej raportowanie typów formantów.</span><span class="sxs-lookup"><span data-stu-id="e2044-295">Better reporting of control types.</span></span>
- <span data-ttu-id="e2044-296">Ulepszone narrator zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e2044-296">Improved narrator behavior.</span></span>
 
<a name="aspnet471"></a>
### <a name="aspnet-web-controls"></a><span data-ttu-id="e2044-297">Kontrolki sieci web platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e2044-297">ASP.NET web controls</span></span>

<span data-ttu-id="e2044-298">Począwszy od .NET Framework 4.7.1 i Visual Studio 2017 15.3, ASP.NET poprawia działanie kontrolki sieci web platformy ASP.NET przy użyciu technologii ułatwień dostępu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2044-298">Starting with the .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="e2044-299">Następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="e2044-299">Changes include the following:</span></span>

- <span data-ttu-id="e2044-300">Zmiany do zaimplementowania Brak wzorce dostępności interfejsu użytkownika w kontrolkach, takie jak **Dodaj pole** okna dialogowego w **widoku szczegółów** kreatora lub **skonfigurować ListView** okna dialogowego z **ListView** kreatora.</span><span class="sxs-lookup"><span data-stu-id="e2044-300">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="e2044-301">Zmiany w celu wyświetlania w trybie dużego kontrastu, takie jak **Edytor pola pagera danych**.</span><span class="sxs-lookup"><span data-stu-id="e2044-301">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="e2044-302">Zmiany w celu polepszenia nawigacji klawiatury napotyka formanty, takie jak **pola** okna dialogowego w **Edytuj pola pagera** kreatora formantu DataPager **konfigurowania obiektu ObjectContext**  okno dialogowe, lub **Konfigurowanie wyboru danych** dialogowego **skonfigurować źródło danych** kreatora.</span><span class="sxs-lookup"><span data-stu-id="e2044-302">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>
### <a name="net-sdk-tools"></a><span data-ttu-id="e2044-303">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="e2044-303">.NET SDK Tools</span></span>

<span data-ttu-id="e2044-304">[Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) i [narzędzie śledzenia usług (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) zostały ulepszone przez Rozwiązywanie problemów zależeć od dostępności.</span><span class="sxs-lookup"><span data-stu-id="e2044-304">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="e2044-305">Większość z nich zostały się niewielkie problemy, takie jak nazwy, nie zostały zdefiniowane lub niektóre wzorce automatyzacji interfejsu użytkownika nie jest zaimplementowana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="e2044-305">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="e2044-306">Gdy wielu użytkowników nie należy pamiętać o tych niepoprawne wartości, klienci korzystający z technologiami pomocniczymi, takich jak czytniki zawartości ekranu znajduje się tych narzędzi zestawu SDK łatwiej dostępne.</span><span class="sxs-lookup"><span data-stu-id="e2044-306">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> 

<span data-ttu-id="e2044-307">Te ulepszenia zmianę niektórych zachowań poprzedniej, takich jak kolejność fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="e2044-307">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>
### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="e2044-308">Projektanta przepływów pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="e2044-308">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="e2044-309">Następujące zmiany w ułatwienia dostępu w Projektancie przepływu pracy:</span><span class="sxs-lookup"><span data-stu-id="e2044-309">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="e2044-310">Zmienia kolejność tabulacji od lewej do prawej i od góry do dołu w niektóre kontrolki:</span><span class="sxs-lookup"><span data-stu-id="e2044-310">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="e2044-311">W oknie korelacji inicjowanie korelacji danych dla <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.</span><span class="sxs-lookup"><span data-stu-id="e2044-311">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="e2044-312">W oknie definicji zawartości <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działań.</span><span class="sxs-lookup"><span data-stu-id="e2044-312">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="e2044-313">Więcej funkcji są dostępne za pośrednictwem klawiatury:</span><span class="sxs-lookup"><span data-stu-id="e2044-313">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="e2044-314">Podczas edytowania właściwości działania, grupy właściwości można zwinąć, klawiatury są skupia się po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="e2044-314">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="e2044-315">Ikony ostrzeżenia są dostępne dla klawiatury.</span><span class="sxs-lookup"><span data-stu-id="e2044-315">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="e2044-316">**Więcej właściwości** znajdujący się w **właściwości** okno jest dostępny za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="e2044-316">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="e2044-317">Klawiatura, użytkownicy mogą uzyskiwać dostęp elementy nagłówka w **argumenty** i **zmienne** okienka projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="e2044-317">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="e2044-318">Ulepszona widoczność elementów z fokusem, takie jak czas:</span><span class="sxs-lookup"><span data-stu-id="e2044-318">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="e2044-319">Dodawanie wierszy do siatki danych używane przez projektantów projektanta przepływów pracy i działania.</span><span class="sxs-lookup"><span data-stu-id="e2044-319">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="e2044-320">TAB pól w <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply> działań.</span><span class="sxs-lookup"><span data-stu-id="e2044-320">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="e2044-321">Ustawianie wartości domyślnych dla zmiennych lub argumentów</span><span class="sxs-lookup"><span data-stu-id="e2044-321">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="e2044-322">Czytniki zawartości ekranu teraz mógł prawidłowo rozpoznać:</span><span class="sxs-lookup"><span data-stu-id="e2044-322">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="e2044-323">Punkty przerwania ustawione w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e2044-323">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="e2044-324"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, I <xref:System.ServiceModel.Activities.CorrelationScope> działań.</span><span class="sxs-lookup"><span data-stu-id="e2044-324">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="e2044-325">Zawartość <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="e2044-325">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="e2044-326">Typ docelowy dla <xref:System.Activities.Statements.InvokeMethod> działania.</span><span class="sxs-lookup"><span data-stu-id="e2044-326">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="e2044-327">Pole kombi wyjątek i na koniec sekcji <xref:System.Activities.Statements.TryCatch> działania.</span><span class="sxs-lookup"><span data-stu-id="e2044-327">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="e2044-328">Pole kombi typu komunikatu, podziału w oknie Dodaj inicjatory korelacji, okno definicji zawartości i okna definice Vlastnosti Correlateson działań dotyczących komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="e2044-328">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="e2044-329">Automat stanów przejścia i przeniesie miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="e2044-329">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="e2044-330">Adnotacje i łączników na <xref:System.Activities.Statements.FlowDecision> działań.</span><span class="sxs-lookup"><span data-stu-id="e2044-330">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="e2044-331">Menu kontekstowe (kliknij prawym przyciskiem myszy), działań.</span><span class="sxs-lookup"><span data-stu-id="e2044-331">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="e2044-332">Edytory wartości właściwości, przycisk Wyczyść wyszukiwanie, według kategorii i przyciski sortowania alfabetycznego i okno dialogowe Edytor wyrażeń w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="e2044-332">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="e2044-333">Procent powiększenia w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e2044-333">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="e2044-334">Separator w <xref:System.Activities.Statements.Parallel> i <xref:System.Activities.Statements.Pick> działań.</span><span class="sxs-lookup"><span data-stu-id="e2044-334">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="e2044-335"><xref:System.Activities.Statements.InvokeDelegate> Działania.</span><span class="sxs-lookup"><span data-stu-id="e2044-335">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="e2044-336">W oknie Wybierz typy działań słownika (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`itp.).</span><span class="sxs-lookup"><span data-stu-id="e2044-336">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="e2044-337">Przeglądanie i wybieranie typu .NET okna.</span><span class="sxs-lookup"><span data-stu-id="e2044-337">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="e2044-338">Linki do stron nadrzędnych w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e2044-338">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="e2044-339">Użytkownicy, którzy wysokiego kontrastu, motywów zobaczą wiele ulepszeń w widoczność projektanta przepływów pracy i jego formantów, takie jak lepsza współczynniki kontrastu między elementami i lepiej widoczne pola wyboru używany do elementów zespołu.</span><span class="sxs-lookup"><span data-stu-id="e2044-339">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2044-340">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2044-340">See also</span></span>

- [<span data-ttu-id="e2044-341">What's new in .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2044-341">What's new in the .NET Framework</span></span>](whats-new.md)

