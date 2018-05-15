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
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="29bf0-102">What's new in ułatwień dostępu w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="29bf0-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="29bf0-103">Celem jest udostępnienie aplikacji użytkownikom programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29bf0-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="29bf0-104">Funkcje ułatwień dostępu zezwala aplikacji zapewnić odpowiednie funkcje użytkowników korzystających z technologii pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="29bf0-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="29bf0-105">Począwszy od programu .NET Framework 4.7.1, .NET Framework zawiera wiele ulepszeń ułatwień dostępu, które umożliwiają deweloperom tworzenie aplikacji dostępny.</span><span class="sxs-lookup"><span data-stu-id="29bf0-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

## <a name="accessibility-switches"></a><span data-ttu-id="29bf0-106">Przełączniki ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="29bf0-106">Accessibility switches</span></span>

<span data-ttu-id="29bf0-107">Można skonfigurować aplikację do uczestnictwa w funkcje ułatwień dostępu, jeśli celem .NET Framework 4.7 lub starszej wersji, ale działa w programie .NET Framework 4.7.1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="29bf0-107">You can configure your app to opt into accessibility features if it targets the .NET Framework 4.7 or an earlier version but is running on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="29bf0-108">Można także skonfigurować aplikację, aby korzystać z funkcji starszej wersji (i nie korzystać z funkcji ułatwień dostępu), jeśli jest on przeznaczony dla programu .NET Framework 4.7.1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="29bf0-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="29bf0-109">Każda wersja programu .NET Framework, która obejmuje funkcje ułatwień dostępu ma przełącznika dostępności określonej wersji, który można dodać do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29bf0-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="29bf0-110">Przełączniki obsługiwane są następujące:</span><span class="sxs-lookup"><span data-stu-id="29bf0-110">The following are the supported switches:</span></span>

|<span data-ttu-id="29bf0-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="29bf0-111">Version</span></span>|<span data-ttu-id="29bf0-112">Przełącznik</span><span class="sxs-lookup"><span data-stu-id="29bf0-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="29bf0-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="29bf0-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="29bf0-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="29bf0-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="29bf0-115">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="29bf0-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="29bf0-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="29bf0-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="29bf0-117">Korzystanie z rozszerzeń ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="29bf0-117">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="29bf0-118">Nowe funkcje ułatwień dostępu są włączone domyślnie dla aplikacji przeznaczonych dla platformy .NET Framework 4.7.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="29bf0-118">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="29bf0-119">Ponadto aplikacje, które są stosowane do wcześniejszej wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.7.1 lub później włączyć zachowań starszych ułatwień dostępu (i tym samym korzystając z usprawnień ułatwień dostępu), dodając przełączników do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji pliku konfiguracji aplikacji i ustawienie ich wartości `false`.</span><span class="sxs-lookup"><span data-stu-id="29bf0-119">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="29bf0-120">Poniżej przedstawiono sposób korzystania z rozszerzeń ułatwień dostępu, które wprowadzono w programie .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="29bf0-120">The following shows how to opt in to accessibility enhancements introduced in the .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="29bf0-121">Jeśli wybierzesz opcję korzystania z funkcji ułatwień dostępu w nowszej wersji programu .NET Framework, musi również jawnie przystąpieniu do funkcji z wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29bf0-121">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="29bf0-122">Konfigurowanie aplikacji, korzystając z usprawnień ułatwień dostępu w obu programu .NET Framework 4.7.1 i 4.7.2 wymaga następujących [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu:</span><span class="sxs-lookup"><span data-stu-id="29bf0-122">Configuring your app to take advantage of accessibility improvements in both the .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="29bf0-123">Przywracanie starsze zachowanie</span><span class="sxs-lookup"><span data-stu-id="29bf0-123">Restoring legacy behavior</span></span>

<span data-ttu-id="29bf0-124">Aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od 4.7.1 można wyłączyć funkcje ułatwień dostępu, dodając przełącza do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) sekcji plik konfiguracji aplikacji i ustawienie ich wartości `true`.</span><span class="sxs-lookup"><span data-stu-id="29bf0-124">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="29bf0-125">Na przykład następująca konfiguracja zdecyduje się poza wprowadzone w programie .NET Framework 4.7.2 funkcje ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="29bf0-125">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a><span data-ttu-id="29bf0-126">What's new in ułatwień dostępu w programie .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="29bf0-126">What's new in accessibility in the .NET Framework 4.7.2</span></span>

<span data-ttu-id="29bf0-127">.NET Framework 4.7.2 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="29bf0-127">The .NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="29bf0-128">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29bf0-128">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="29bf0-129">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="29bf0-129">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a><span data-ttu-id="29bf0-130">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29bf0-130">Windows Forms</span></span>

<span data-ttu-id="29bf0-131">**Zdefiniowane przez system operacyjny kolorów w kompozycji duży kontrast**</span><span class="sxs-lookup"><span data-stu-id="29bf0-131">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="29bf0-132">W programie .NET Framework 4.7.2, formularze systemu Windows używa kolorów zdefiniowanych przez system operacyjny w duży kontrast motywów.</span><span class="sxs-lookup"><span data-stu-id="29bf0-132">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="29bf0-133">Ma to wpływ na następujące sterowniki:</span><span class="sxs-lookup"><span data-stu-id="29bf0-133">This affects the following controls:</span></span>

- <span data-ttu-id="29bf0-134">Strzałkę listy rozwijanej <xref:System.Windows.Forms.ToolStripDropDownButton> formantu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-134">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="29bf0-135"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> formanty z <xref:System.Windows.Forms.ButtonBase.FlatStyle> ustawioną <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> lub <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29bf0-135">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29bf0-136">Poprzednio wybrane kolory tła i tekstu nie zostały kontrastem i był trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="29bf0-136">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="29bf0-137">Formanty zawarte w <xref:System.Windows.Forms.GroupBox> mający jego <xref:System.Windows.Forms.Control.Enabled> ustawioną właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="29bf0-137">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
 
- <span data-ttu-id="29bf0-138"><xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, I <xref:System.Windows.Forms.ToolStripDropDownButton> formanty, które mają współczynnik kontrastu Zwiększona jasność w trybie wysokiej kontrastu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-138">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="29bf0-139"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="29bf0-139">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="29bf0-140">**Ulepszenia Narrator**</span><span class="sxs-lookup"><span data-stu-id="29bf0-140">**Narrator improvements**</span></span>

<span data-ttu-id="29bf0-141">Począwszy od programu .NET Framework 4.7.2 Narrator Obsługa została rozszerzona w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="29bf0-141">Starting with the .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="29bf0-142">Ogłasza, wartość <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> właściwość podczas anonsowania tekst <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="29bf0-142">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span> 

- <span data-ttu-id="29bf0-143">Wskazuje, kiedy <xref:System.Windows.Forms.ToolStripMenuItem> ma jego <xref:System.Windows.Forms.Control.Enabled> ustawioną właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="29bf0-143">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="29bf0-144">Udostępnia informacji zwrotnych dotyczących stanu pola wyboru po <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="29bf0-144">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="29bf0-145">Kolejność fokus tryb skanowania przez program Narrator jest zgodna z visual kolejności kontrolek w oknie dialogowym pobierania ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="29bf0-145">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="29bf0-146">**Ulepszenia DataGridView**</span><span class="sxs-lookup"><span data-stu-id="29bf0-146">**DataGridView improvements**</span></span>

<span data-ttu-id="29bf0-147">Począwszy od programu .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> formantu ma wprowadzono następujące ulepszenia dotyczące ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="29bf0-147">Starting with the .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="29bf0-148">Za pomocą klawiatury można sortować wierszy.</span><span class="sxs-lookup"><span data-stu-id="29bf0-148">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="29bf0-149">Użytkownik może używać klawisz F3, aby posortować według bieżącej kolumny.</span><span class="sxs-lookup"><span data-stu-id="29bf0-149">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="29bf0-150">Gdy <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ma ustawioną wartość <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, nagłówek kolumny zmienia kolor, aby wskazać bieżącej kolumny jako karty użytkownika za pośrednictwem komórek w bieżącym wierszu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-150">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="29bf0-151"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Właściwość <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> zwraca formantu nadrzędnego poprawne.</span><span class="sxs-lookup"><span data-stu-id="29bf0-151">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="29bf0-152">**Ulepszone podpowiedzi wizualne**</span><span class="sxs-lookup"><span data-stu-id="29bf0-152">**Improved visual cues**</span></span>

- <span data-ttu-id="29bf0-153"><xref:System.Windows.Forms.RadioButton> i <xref:System.Windows.Forms.CheckBox> formantów z pustą <xref:System.Windows.Forms.ButtonBase.Text> właściwości wyświetlania wskaźnika fokus po otrzymaniu fokus.</span><span class="sxs-lookup"><span data-stu-id="29bf0-153">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="29bf0-154">**Obsługa siatki właściwości ulepszone**</span><span class="sxs-lookup"><span data-stu-id="29bf0-154">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="29bf0-155"><xref:System.Windows.Forms.PropertyGrid> Sterowanie teraz zwracane elementy podrzędne `true` dla <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> właściwość tylko wtedy, gdy PropertyGrid element jest włączony.</span><span class="sxs-lookup"><span data-stu-id="29bf0-155">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="29bf0-156"><xref:System.Windows.Forms.PropertyGrid> Kontrolować zwracane elementy podrzędne `false` dla <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> właściwość tylko wtedy, gdy PropertyGrid element można zmienić przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="29bf0-156">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="29bf0-157">**Ulepszone klawiatury nawigacji**</span><span class="sxs-lookup"><span data-stu-id="29bf0-157">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="29bf0-158"><xref:System.Windows.Forms.ToolStripButton> Kontroli umożliwia fokus, gdy jest zawarty w <xref:System.Windows.Forms.ToolStripPanel> mający <xref:System.Windows.Forms.ToolStripPanel.TabStop> ustawioną właściwość `true`</span><span class="sxs-lookup"><span data-stu-id="29bf0-158">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="29bf0-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="29bf0-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="29bf0-160">**Zmiany do formantów wyboru i RadioButton**</span><span class="sxs-lookup"><span data-stu-id="29bf0-160">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="29bf0-161">W programie .NET Framework 4.7.1 i wcześniejszych wersjach, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> i <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> formanty mają niespójne i, w klasycznym i wysoki kontrast kompozycje fokus niepoprawne elementy wizualne.</span><span class="sxs-lookup"><span data-stu-id="29bf0-161">In the .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="29bf0-162">Te problemy występują w przypadkach, gdy kontrolki nie mają żadnych zestawu zawartości.</span><span class="sxs-lookup"><span data-stu-id="29bf0-162">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="29bf0-163">Możliwość trudno Zobacz przejścia między mylące kompozycje i visual fokus.</span><span class="sxs-lookup"><span data-stu-id="29bf0-163">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="29bf0-164">W programie .NET Framework 4.7.2 te elementy wizualne są teraz bardziej spójność w ramach kompozycje i widoczność w klasycznym i duży kontrast motywów.</span><span class="sxs-lookup"><span data-stu-id="29bf0-164">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="29bf0-165">**Formanty WinForms hostowanych w aplikacji WPF**</span><span class="sxs-lookup"><span data-stu-id="29bf0-165">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="29bf0-166">Do formant WinForms hostowanych w aplikacji WPF w programie .NET Framework 4.7.1 i wcześniejszych wersjach, użytkownicy nie karty poza warstwą WinForms, jeśli formant pierwszego lub ostatniego w tej warstwie jest WPF <xref:System.Windows.Forms.Integration.ElementHost> formantu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-166">For WinForms control hosted in a WPF application in the .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="29bf0-167">W programie .NET Framework 4.7.2 użytkownicy mogą teraz karcie poza warstwą WinForms.</span><span class="sxs-lookup"><span data-stu-id="29bf0-167">In the .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="29bf0-168">Jednak automatyczne aplikacje, które są oparte na fokus nigdy nie anulowanie warstwy WinForms może przestać działać zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="29bf0-168">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="29bf0-169">What's new in ułatwień dostępu w programie .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="29bf0-169">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="29bf0-170">.NET Framework 4.7.1 zawiera nowe funkcje ułatwień dostępu w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="29bf0-170">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="29bf0-171">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="29bf0-171">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="29bf0-172">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29bf0-172">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="29bf0-173">Formanty sieci web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="29bf0-173">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="29bf0-174">Narzędzia zestawu SDK .NET</span><span class="sxs-lookup"><span data-stu-id="29bf0-174">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="29bf0-175">Projektanta przepływów pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="29bf0-175">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="29bf0-176">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="29bf0-176">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="29bf0-177">**Ulepszenia czytnika ekranu**</span><span class="sxs-lookup"><span data-stu-id="29bf0-177">**Screen reader improvements**</span></span>

<span data-ttu-id="29bf0-178">Włączenie ulepszenia ułatwień dostępu programu .NET Framework 4.7.1 obejmuje następujące rozszerzenia, które mają wpływ na czytników ekranu:</span><span class="sxs-lookup"><span data-stu-id="29bf0-178">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="29bf0-179">.NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.Expander> formanty ogłoszeniu czytników ekranu jako przyciski.</span><span class="sxs-lookup"><span data-stu-id="29bf0-179">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="29bf0-180">Począwszy od programu .NET Framework 4.7.1 ich obsłudze zostaną poprawnie opublikowane jako rozwijania/zwijanej grupy.</span><span class="sxs-lookup"><span data-stu-id="29bf0-180">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="29bf0-181">.NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.DataGridCell> formanty ogłoszeniu czytników ekranu jako "custom".</span><span class="sxs-lookup"><span data-stu-id="29bf0-181">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="29bf0-182">Począwszy od programu .NET Framework 4.7.1 one są teraz prawidłowo anonsowane jako komórki siatki danych (zlokalizowany).</span><span class="sxs-lookup"><span data-stu-id="29bf0-182">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="29bf0-183">Począwszy od programu .NET Framework 4.7.1 czytników ekranu ogłaszamy nazwę można edytować <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="29bf0-183">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="29bf0-184">.NET Framework 4.7 i wcześniejszych wersjach <xref:System.Windows.Controls.PasswordBox> formanty zostały ogłoszenia jako "nie elementu w widoku" lub ma inaczej niepoprawnego zachowania.</span><span class="sxs-lookup"><span data-stu-id="29bf0-184">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="29bf0-185">Tego problemu w programie .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="29bf0-185">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>

<span data-ttu-id="29bf0-186">**Obsługa biblioteki UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="29bf0-186">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="29bf0-187">Czytników ekranu, takie jak osoby pomocy Narrator odczytywać zawartość interfejsu użytkownika aplikacji, zwykle tekst na mowę dane wyjściowe zawartości interfejsu użytkownika, który ma fokus.</span><span class="sxs-lookup"><span data-stu-id="29bf0-187">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="29bf0-188">Jednak jeśli elementu interfejsu użytkownika zmiany i nie ma fokus, użytkownik nie może zostać zgłoszone i może pominąć ważne informacje.</span><span class="sxs-lookup"><span data-stu-id="29bf0-188">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="29bf0-189">Regiony na żywo na celu rozwiązanie tego problemu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-189">Live regions aim at solving this problem.</span></span> <span data-ttu-id="29bf0-190">Deweloper może użyć ich poinformować odczytywania zawartości ekranu lub inne klienta biblioteki UIAutomation, który wprowadzono istotne zmiany do elementu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="29bf0-190">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="29bf0-191">Czytnik następnie można zdecydować, jak i kiedy informują użytkownika o tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="29bf0-191">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="29bf0-192">Do obsługi na żywo regionów, WPF dodano następujące interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="29bf0-192">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="29bf0-193"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pola, które identyfikują **LiveSetting** właściwości i **LiveRegionChanged** zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29bf0-193">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="29bf0-194">Można ich ustawiać przy użyciu języka XAML.</span><span class="sxs-lookup"><span data-stu-id="29bf0-194">They can be set by using XAML.</span></span>

- <span data-ttu-id="29bf0-195">**AutomationProperties.LiveSetting** dołączona właściwość, która informuje czytnik ważne zmiany interfejsu użytkownika dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="29bf0-195">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="29bf0-196"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Właściwość, która identyfikuje **AutomationProperties.LiveSetting** dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="29bf0-196">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="29bf0-197"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metodę, która może zostać zastąpiona w celu zapewnienia **LiveSetting** wartości.</span><span class="sxs-lookup"><span data-stu-id="29bf0-197">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="29bf0-198"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> i <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody get i set **LiveSetting** wartości.</span><span class="sxs-lookup"><span data-stu-id="29bf0-198">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="29bf0-199"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Wyliczenia, który definiuje następujące możliwości **LiveSetting** wartości:</span><span class="sxs-lookup"><span data-stu-id="29bf0-199">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="29bf0-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29bf0-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29bf0-201">Element nie wysyła powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="29bf0-201">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="29bf0-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29bf0-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29bf0-203">Element wysyła powiadomienia interruptive zmiana zawartości na żywo regionu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-203">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="29bf0-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29bf0-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29bf0-205">Element wysyła interruptive powiadomienia, jeśli zawartość obszaru na żywo została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="29bf0-205">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="29bf0-206">Można utworzyć LiveRegion przez ustawienie **AutomationProperties.LiveSetting** właściwości w elemencie zainteresowań, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="29bf0-206">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="29bf0-207">Podczas zmiany danych w regionie na żywo i należy poinformować czytnika ekranu, należy jawnie wywołaj zdarzenie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="29bf0-207">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="29bf0-208">**Duży kontrast**</span><span class="sxs-lookup"><span data-stu-id="29bf0-208">**High contrast**</span></span>

<span data-ttu-id="29bf0-209">Począwszy od programu .NET Framework 4.7.1 ulepszenia duży kontrast zostały wprowadzone do różnych formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="29bf0-209">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="29bf0-210">Teraz są one widoczne podczas <xref:System.Windows.SystemParameters.HighContrast%2A> ustawiono motywu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-210">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="29bf0-211">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="29bf0-211">These include:</span></span>

- <span data-ttu-id="29bf0-212"><xref:System.Windows.Controls.Expander> Formant</span><span class="sxs-lookup"><span data-stu-id="29bf0-212"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="29bf0-213">Fokus visual dla <xref:System.Windows.Controls.Expander> kontroli jest teraz widoczne.</span><span class="sxs-lookup"><span data-stu-id="29bf0-213">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="29bf0-214">Elementy wizualne klawiatury dla <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, i <xref:System.Windows.Controls.RadioButton> formanty są również widoczne.</span><span class="sxs-lookup"><span data-stu-id="29bf0-214">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="29bf0-215">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="29bf0-215">For example:</span></span>

    <span data-ttu-id="29bf0-216">Przed:</span><span class="sxs-lookup"><span data-stu-id="29bf0-216">Before:</span></span> 
    
    ![Kontrolkę Expander z fokusem przed ulepszenia ułatwień dostępu](media/expander-before.png)

    <span data-ttu-id="29bf0-218">Po:</span><span class="sxs-lookup"><span data-stu-id="29bf0-218">After:</span></span> 

    ![Kontrolkę Expander z fokusem po ulepszenia ułatwień dostępu](media/expander-after.png)

- <span data-ttu-id="29bf0-220"><xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów</span><span class="sxs-lookup"><span data-stu-id="29bf0-220"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="29bf0-221">Tekst w <xref:System.Windows.Controls.CheckBox> i <xref:System.Windows.Controls.RadioButton> formantów jest teraz lepiej widoczne po wybraniu w kompozycji dużego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-221">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="29bf0-222">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="29bf0-222">For example:</span></span>

    <span data-ttu-id="29bf0-223">Przed:</span><span class="sxs-lookup"><span data-stu-id="29bf0-223">Before:</span></span> 

    ![Przycisk radiowy duży kontrast z fokusem przed ulepszenia ułatwień dostępu](media/radio-button-before.png)
    
    <span data-ttu-id="29bf0-225">Po:</span><span class="sxs-lookup"><span data-stu-id="29bf0-225">After:</span></span> 

    ![Przycisk radiowy duży kontrast z fokusem po ulepszenia ułatwień dostępu](media/radio-button-after.png)

- <span data-ttu-id="29bf0-227"><xref:System.Windows.Controls.ComboBox> Formant</span><span class="sxs-lookup"><span data-stu-id="29bf0-227"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="29bf0-228">Począwszy od programu .NET Framework 4.7.1, obramowania wyłączone <xref:System.Windows.Controls.ComboBox> formant jest kolor wyłączonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-228">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="29bf0-229">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="29bf0-229">For example:</span></span>
    
    <span data-ttu-id="29bf0-230">Przed:</span><span class="sxs-lookup"><span data-stu-id="29bf0-230">Before:</span></span> 

     ![ComboBox — wyłączone obramowania i tekst przed ulepszenia ułatwień dostępu](media/combo-disabled-before.png)

    <span data-ttu-id="29bf0-232">Po:</span><span class="sxs-lookup"><span data-stu-id="29bf0-232">After:</span></span>   

     ![ComboBox — wyłączone obramowania i tekst po ulepszenia ułatwień dostępu](media/combo-disabled-after.png)

    <span data-ttu-id="29bf0-234">Ponadto przyciski wyłączone i skupiają się użyć kolor motywu poprawne.</span><span class="sxs-lookup"><span data-stu-id="29bf0-234">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="29bf0-235">Przed:</span><span class="sxs-lookup"><span data-stu-id="29bf0-235">Before:</span></span>

    ![Przycisk motywu kolorów przed ulepszenia ułatwień dostępu](media/button-themes-before.png) 
    
    <span data-ttu-id="29bf0-237">Po:</span><span class="sxs-lookup"><span data-stu-id="29bf0-237">After:</span></span> 

    ![Przycisk motywu kolorów po ulepszenia ułatwień dostępu](media/button-themes-after.png) 

    <span data-ttu-id="29bf0-239">Ponadto w .NET Framework 4.7 i wcześniejsze wersje, ustawienie <xref:System.Windows.Controls.ComboBox> stylu kontrolki do `Toolbar.ComboBoxStyleKey` spowodował strzałkę listy rozwijanej, aby była niewidoczna.</span><span class="sxs-lookup"><span data-stu-id="29bf0-239">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="29bf0-240">Tego problemu w programie .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="29bf0-240">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="29bf0-241">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="29bf0-241">For example:</span></span>

    <span data-ttu-id="29bf0-242">Przed:</span><span class="sxs-lookup"><span data-stu-id="29bf0-242">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey przed ulepszenia ułatwień dostępu](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="29bf0-244">Po:</span><span class="sxs-lookup"><span data-stu-id="29bf0-244">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey po ulepszenia ułatwień dostępu](media/comboboxstylekey-after.png) 

- <span data-ttu-id="29bf0-246"><xref:System.Windows.Controls.DataGrid> Formant</span><span class="sxs-lookup"><span data-stu-id="29bf0-246"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="29bf0-247">Począwszy od programu .NET Framework 4.7.1, Strzałka wskaźnika sortowania w <xref:System.Windows.Controls.DataGrid> steruje teraz używa Popraw kolorów motywu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-247">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="29bf0-248">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="29bf0-248">For example:</span></span>

    <span data-ttu-id="29bf0-249">Przed:</span><span class="sxs-lookup"><span data-stu-id="29bf0-249">Before:</span></span> 

    ![Sortowanie Strzałka wskaźnika przed ulepszenia ułatwień dostępu](media/sort-indicator-before.png) 
    
    <span data-ttu-id="29bf0-251">Po:</span><span class="sxs-lookup"><span data-stu-id="29bf0-251">After:</span></span>   
 
    ![Strzałka wskaźnika sortowania po ulepszenia ułatwień dostępu](media/sort-indicator-after.png) 
    
    <span data-ttu-id="29bf0-253">Ponadto w programie .NET Framework 4.7 i wcześniejszych wersjach, domyślny styl łącza zmieniony na nieprawidłowy kolor na myszy za pośrednictwem w trybie dużego kontrastu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-253">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="29bf0-254">Ten problem został rozwiązany, począwszy od programu .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="29bf0-254">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="29bf0-255">Podobnie <xref:System.Windows.Controls.DataGrid> kolumn wyboru używa oczekiwanego kolorów w programie .NET Framework 4.7.1 opinii fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="29bf0-255">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="29bf0-256">Przed:</span><span class="sxs-lookup"><span data-stu-id="29bf0-256">Before:</span></span> 

    ![Styl łącza domyślne DataGrid przed ulepszenia ułatwień dostępu](media/default-link-style-before.png) 
 
    <span data-ttu-id="29bf0-258">Po:</span><span class="sxs-lookup"><span data-stu-id="29bf0-258">After:</span></span>    
  
    ![Styl łącza domyślne DataGrid po ulepszenia ułatwień dostępu](media/default-link-style-after.png)  

<span data-ttu-id="29bf0-260">Aby uzyskać więcej informacji na WPF ulepszenia ułatwień dostępu w programie .NET Framework 4.7.1, zobacz [usprawnienia dostępu na platformie WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="29bf0-260">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="29bf0-261">Ulepszenia dostępność formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="29bf0-261">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="29bf0-262">W programie .NET Framework 4.7.1 formularze systemu Windows (WinForms) zawiera zmiany ułatwień dostępu w następujących obszarach.</span><span class="sxs-lookup"><span data-stu-id="29bf0-262">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="29bf0-263">**Ulepszone wyświetlania w trybie dużego kontrastu**</span><span class="sxs-lookup"><span data-stu-id="29bf0-263">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="29bf0-264">Począwszy od programu .NET Framework 4.7.1 różnych formantów WinForms oferują ulepszoną renderowania w trybach HighContrast dostępne w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="29bf0-264">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="29bf0-265">Windows 10 zmienił wartości dla niektórych kolorów systemu duży kontrast, i formularze systemu Windows jest oparta na platformę Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="29bf0-265">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="29bf0-266">Aby uzyskać najlepsze wyniki należy uruchomić na najnowszej wersji systemu Windows i korzystania z najnowszych zmian systemu operacyjnego przez dodawanie pliku app.manifest aplikacja testowa i un komentarz systemu Windows 10 obsługiwane wiersza systemu operacyjnego, aby wyglądały one następujące:</span><span class="sxs-lookup"><span data-stu-id="29bf0-266">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="29bf0-267">Niektóre zmiany duży kontrast należą:</span><span class="sxs-lookup"><span data-stu-id="29bf0-267">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="29bf0-268">Zaznaczeń w <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="29bf0-268">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="29bf0-269">Po wybraniu wyłączone <xref:System.Windows.Forms.MenuStrip> elementy są łatwiejsze do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="29bf0-269">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="29bf0-270">Tekst w wybranej <xref:System.Windows.Forms.Button> kontrolować różni się od kolor zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="29bf0-270">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="29bf0-271">Wyłączony tekst jest bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="29bf0-271">Disabled text is easier to read.</span></span> <span data-ttu-id="29bf0-272">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="29bf0-272">For example:</span></span>

    <span data-ttu-id="29bf0-273">Przed:</span><span class="sxs-lookup"><span data-stu-id="29bf0-273">Before:</span></span>

    ![Tekst wyłączone przed ulepszenia ułatwień dostępu](media/wf-disabled-before.png) 

    <span data-ttu-id="29bf0-275">Po:</span><span class="sxs-lookup"><span data-stu-id="29bf0-275">After:</span></span>

    ![Wyłączonego tekstu po ulepszenia ułatwień dostępu](media/wf-disabled-after.png) 

- <span data-ttu-id="29bf0-277">Ulepszenia duży kontrast w oknie dialogowym wyjątków wątku.</span><span class="sxs-lookup"><span data-stu-id="29bf0-277">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="29bf0-278">**Ulepszona obsługa Narrator**</span><span class="sxs-lookup"><span data-stu-id="29bf0-278">**Improved Narrator support**</span></span>

<span data-ttu-id="29bf0-279">Formularze systemu Windows w programie .NET Framework 4.7.1 obejmuje następujące ulepszenia Narrator ułatwień dostępu:</span><span class="sxs-lookup"><span data-stu-id="29bf0-279">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="29bf0-280"><xref:System.Windows.Forms.MonthCalendar> Kontroli jest dostępny program Narrator, a także innymi narzędziami automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="29bf0-280">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="29bf0-281"><xref:System.Windows.Forms.CheckedListBox> Kontroli powiadamia Narrator, gdy stan zaznaczenia elementu zostanie zmieniony, więc użytkownik jest powiadamiany o ich zmieniono wartość elementu listy.</span><span class="sxs-lookup"><span data-stu-id="29bf0-281">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="29bf0-282"><xref:System.Windows.Forms.DataGridViewCell> Kontroli zaraportuje prawidłowe stanu tylko do odczytu do Narrator.</span><span class="sxs-lookup"><span data-stu-id="29bf0-282">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="29bf0-283">Narrator, mogą teraz odczytywać wyłączone <xref:System.Windows.Forms.ToolStripMenuItem> tekstu, należy wcześniej może pominąć elementów menu wyłączone.</span><span class="sxs-lookup"><span data-stu-id="29bf0-283">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="29bf0-284">**Rozszerzona obsługa biblioteki UIAutomation wzorce ułatwień dostępu**</span><span class="sxs-lookup"><span data-stu-id="29bf0-284">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="29bf0-285">Deweloperzy technologii ułatwień dostępu w programie .NET Framework 4.7.1, można wykorzystać typowe wzorce ułatwień dostępu interfejsu API i właściwości dla kilku formantów WinForms.</span><span class="sxs-lookup"><span data-stu-id="29bf0-285">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="29bf0-286">Ułatwienia dostępu do tych udoskonaleń należą:</span><span class="sxs-lookup"><span data-stu-id="29bf0-286">These accessibility improvements include:</span></span>

- <span data-ttu-id="29bf0-287"><xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ToolStripSplitButton> obsługują teraz [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="29bf0-287">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="29bf0-288"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Obsługuje teraz [toggle — wzorzec](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="29bf0-288">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="29bf0-289"><xref:System.Windows.Forms.ToolStripItem> Sterowanie obsługuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości i [wzorzec Rozwiń/Zwiń](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="29bf0-289">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="29bf0-290"><xref:System.Windows.Forms.NumericUpDown> i <xref:System.Windows.Forms.DomainUpDown> formanty obsługi <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> właściwości.</span><span class="sxs-lookup"><span data-stu-id="29bf0-290">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="29bf0-291">**Ulepszone właściwości przeglądania**</span><span class="sxs-lookup"><span data-stu-id="29bf0-291">**Improved property browser experience**</span></span>

<span data-ttu-id="29bf0-292">Formularze systemu Windows w programie .NET Framework 4.7.1, obejmują:</span><span class="sxs-lookup"><span data-stu-id="29bf0-292">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="29bf0-293">Lepsze nawigacji klawiatury przez różne okna wyboru z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="29bf0-293">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="29bf0-294">Zmniejszenie niepotrzebnych tabulatorów.</span><span class="sxs-lookup"><span data-stu-id="29bf0-294">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="29bf0-295">Lepiej raportowanie typy formantów.</span><span class="sxs-lookup"><span data-stu-id="29bf0-295">Better reporting of control types.</span></span>
- <span data-ttu-id="29bf0-296">Ulepszone narrator zachowanie.</span><span class="sxs-lookup"><span data-stu-id="29bf0-296">Improved narrator behavior.</span></span>
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a><span data-ttu-id="29bf0-297">Formanty sieci web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="29bf0-297">ASP.NET web controls</span></span>

<span data-ttu-id="29bf0-298">Począwszy od programu .NET Framework 4.7.1 i 15 ustęp 3 programu Visual Studio 2017, ASP.NET poprawia działanie formantów sieci web ASP.NET przy użyciu technologii ułatwień dostępu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29bf0-298">Starting with the .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="29bf0-299">Następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="29bf0-299">Changes include the following:</span></span>

- <span data-ttu-id="29bf0-300">Zmiany w implementacji Brak wzorce ułatwień dostępu interfejsu użytkownika w formantach, tak samo, jak **Dodaj pole** okno dialogowe w **widoku szczegółów** kreatora lub **Konfiguruj element ListView** okna dialogowego z **ListView** kreatora.</span><span class="sxs-lookup"><span data-stu-id="29bf0-300">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="29bf0-301">Zmiany w celu polepszenia wyświetlania w trybie dużego kontrastu, takie jak **Edytor pola modułu stronicowania danych**.</span><span class="sxs-lookup"><span data-stu-id="29bf0-301">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="29bf0-302">Zmiany w celu polepszenia nawigacji klawiatury napotyka formanty, takie jak **pola** okno dialogowe w **Edytuj pola modułu stronicowania** Kreator formantu DataPager **skonfigurować ObjectContext**  okno dialogowe, lub **Konfigurowanie wyboru danych** okna dialogowego z **skonfiguruj źródło danych** kreatora.</span><span class="sxs-lookup"><span data-stu-id="29bf0-302">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>
## <a name="net-sdk-tools"></a><span data-ttu-id="29bf0-303">Narzędzia zestawu SDK .NET</span><span class="sxs-lookup"><span data-stu-id="29bf0-303">.NET SDK Tools</span></span>

<span data-ttu-id="29bf0-304">[Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) i [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ulepszono napraw problemy z dostępem zróżnicowane.</span><span class="sxs-lookup"><span data-stu-id="29bf0-304">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="29bf0-305">Większość tych były niewielkie problemy, jak nazwa nie jest zdefiniowany lub niektórych wzorce automatyzacji interfejsu użytkownika nie jest zaimplementowana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="29bf0-305">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="29bf0-306">Gdy wielu użytkowników nie należy pamiętać o tych niepoprawne wartości, klienci korzystający z ułatwieniami technologii, takich jak czytniki znajdzie te narzędzia zestawu SDK dostęp.</span><span class="sxs-lookup"><span data-stu-id="29bf0-306">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> 

<span data-ttu-id="29bf0-307">Te ulepszenia zmienić niektóre zachowania poprzedniej, takich jak kolejność fokus klawiatury.</span><span class="sxs-lookup"><span data-stu-id="29bf0-307">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="29bf0-308">Projektanta przepływów pracy programu Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="29bf0-308">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="29bf0-309">Zmiany ułatwień dostępu w Projektancie przepływów pracy są następujące:</span><span class="sxs-lookup"><span data-stu-id="29bf0-309">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="29bf0-310">Kolejność tabulacji zmiany od lewej do prawej i od góry do dołu w niektórych formantów:</span><span class="sxs-lookup"><span data-stu-id="29bf0-310">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="29bf0-311">W oknie korelacji zainicjować ustawienie dane korelacji dla <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.</span><span class="sxs-lookup"><span data-stu-id="29bf0-311">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="29bf0-312">W oknie definicję zawartości <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply> działań.</span><span class="sxs-lookup"><span data-stu-id="29bf0-312">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="29bf0-313">Więcej funkcji dostępnych za pośrednictwem klawiatury:</span><span class="sxs-lookup"><span data-stu-id="29bf0-313">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="29bf0-314">Podczas edytowania właściwości działania, grup właściwości może zostać zwinięty przy klawiatury są koncentruje się po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="29bf0-314">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="29bf0-315">Ostrzeżenie ikony są dostępny za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="29bf0-315">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="29bf0-316">**Więcej właściwości** przycisk **właściwości** okno jest dostępny za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="29bf0-316">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="29bf0-317">Klawiatura użytkownicy mogą uzyskiwać dostęp do elementy nagłówka w **argumenty** i **zmienne** okienka projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="29bf0-317">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="29bf0-318">Lepszą widoczność elementów z fokusem, takie jak czas:</span><span class="sxs-lookup"><span data-stu-id="29bf0-318">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="29bf0-319">Dodawanie wierszy do siatek danych używane przez projektantów projektanta przepływów pracy i działania.</span><span class="sxs-lookup"><span data-stu-id="29bf0-319">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="29bf0-320">TAB pól w <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply> działań.</span><span class="sxs-lookup"><span data-stu-id="29bf0-320">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="29bf0-321">Ustawianie wartości domyślnych do zmiennych lub argumentów</span><span class="sxs-lookup"><span data-stu-id="29bf0-321">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="29bf0-322">Czytniki teraz mógł prawidłowo rozpoznać:</span><span class="sxs-lookup"><span data-stu-id="29bf0-322">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="29bf0-323">Ustaw punkty przerwania w Projektancie przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="29bf0-323">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="29bf0-324"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, I <xref:System.ServiceModel.Activities.CorrelationScope> działań.</span><span class="sxs-lookup"><span data-stu-id="29bf0-324">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="29bf0-325">Zawartość <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="29bf0-325">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="29bf0-326">Typ docelowy dla <xref:System.Activities.Statements.InvokeMethod> działania.</span><span class="sxs-lookup"><span data-stu-id="29bf0-326">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="29bf0-327">Pole kombi wyjątku i na koniec sekcji <xref:System.Activities.Statements.TryCatch> działania.</span><span class="sxs-lookup"><span data-stu-id="29bf0-327">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="29bf0-328">Pole kombi typ komunikatu, podziału w oknie Dodaj inicjatorów korelacji, okno definicji zawartości i oknie CorrelatesOn definicji działania obsługi komunikatów (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, i <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="29bf0-328">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="29bf0-329">Automatu stanów przejścia i przejścia miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="29bf0-329">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="29bf0-330">Adnotacje i łącznikami <xref:System.Activities.Statements.FlowDecision> działań.</span><span class="sxs-lookup"><span data-stu-id="29bf0-330">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="29bf0-331">Menu kontekstowe (kliknij prawym przyciskiem myszy) dla działań.</span><span class="sxs-lookup"><span data-stu-id="29bf0-331">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="29bf0-332">Edytory wartość właściwości, przycisk Wyczyść wyszukiwanie według kategorii i przyciski alfabetycznej sortowania i okno dialogowe Edytor wyrażeń w siatce właściwości.</span><span class="sxs-lookup"><span data-stu-id="29bf0-332">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="29bf0-333">Procent powiększenia w Projektancie przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="29bf0-333">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="29bf0-334">Separator w <xref:System.Activities.Statements.Parallel> i <xref:System.Activities.Statements.Pick> działań.</span><span class="sxs-lookup"><span data-stu-id="29bf0-334">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="29bf0-335"><xref:System.Activities.Statements.InvokeDelegate> Działania.</span><span class="sxs-lookup"><span data-stu-id="29bf0-335">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="29bf0-336">W oknie Wybierz typy działań słownika (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`itp.).</span><span class="sxs-lookup"><span data-stu-id="29bf0-336">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="29bf0-337">Przeglądaj i wybierz typ .NET okna.</span><span class="sxs-lookup"><span data-stu-id="29bf0-337">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="29bf0-338">Obszar nawigacji w Projektancie przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="29bf0-338">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="29bf0-339">Użytkownicy, którzy wybierz motywów duży kontrast będą widzieć wiele ulepszeń w widoczność projektanta przepływów pracy i jego kontroli, jak lepiej współczynniki kontrastu między elementami i bardziej zauważalne pola wyboru używany do elementów zespołu.</span><span class="sxs-lookup"><span data-stu-id="29bf0-339">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="29bf0-340">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29bf0-340">See Also</span></span>

[<span data-ttu-id="29bf0-341">Co to jest nowe w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="29bf0-341">What's new in the .NET Framework</span></span>](whats-new.md)
 
