---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 68fa7753be76b0681c40e540e86b11c89e7a8ca1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157028"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="bb029-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek</span><span class="sxs-lookup"><span data-stu-id="bb029-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="bb029-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bb029-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bb029-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bb029-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bb029-105">Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla standardowych kontrolek w aplikacjach przeznaczonych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] struktur.</span><span class="sxs-lookup"><span data-stu-id="bb029-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="bb029-106">Formanty programu Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="bb029-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="bb029-107">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy kontroli, które zapewniają informacje lub pomocy technicznej do interakcji z użytkownikiem ma pełne natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb029-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="bb029-108">Nie są widoczne dla innych elementów, takich jak paneli, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb029-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="bb029-109">Kontrolki Win32</span><span class="sxs-lookup"><span data-stu-id="bb029-109">Win32 Controls</span></span>  
 <span data-ttu-id="bb029-110">Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="bb029-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="bb029-111">Ten zestaw jest automatycznie rejestrowane do użycia przy użyciu automatyzacji interfejsu użytkownika aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="bb029-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="bb029-112">Pełna pomoc techniczna jest dostępna tylko w przypadku kontrolek z ComCtrl32.dll w wersji 6 (udostępniono [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="bb029-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="bb029-113">Następujące elementy sterujące są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bb029-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="bb029-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="bb029-114">Class name</span></span>|<span data-ttu-id="bb029-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="bb029-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="bb029-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-116">Button</span></span>|<span data-ttu-id="bb029-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-117">Button</span></span>|  
|<span data-ttu-id="bb029-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-118">Button</span></span>|<span data-ttu-id="bb029-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bb029-119">RadioButton</span></span>|  
|<span data-ttu-id="bb029-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-120">Button</span></span>|<span data-ttu-id="bb029-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="bb029-121">Group</span></span>|  
|<span data-ttu-id="bb029-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-122">Button</span></span>|<span data-ttu-id="bb029-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb029-123">CheckBox</span></span>|  
|<span data-ttu-id="bb029-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-124">Button</span></span>|<span data-ttu-id="bb029-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="bb029-125">Hyperlink</span></span>|  
|<span data-ttu-id="bb029-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-126">Button</span></span>|<span data-ttu-id="bb029-127">Przycisk podziału</span><span class="sxs-lookup"><span data-stu-id="bb029-127">SplitButton</span></span>|  
|<span data-ttu-id="bb029-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-128">Button</span></span>|<span data-ttu-id="bb029-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb029-129">CheckBox</span></span>|  
|<span data-ttu-id="bb029-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="bb029-130">ComboBoxEx32</span></span>|<span data-ttu-id="bb029-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bb029-131">ComboBox</span></span>|  
|<span data-ttu-id="bb029-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bb029-132">ComboBox</span></span>|<span data-ttu-id="bb029-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bb029-133">ComboBox</span></span>|  
|<span data-ttu-id="bb029-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="bb029-134">Edit</span></span>|<span data-ttu-id="bb029-135">dokument</span><span class="sxs-lookup"><span data-stu-id="bb029-135">Document</span></span>|  
|<span data-ttu-id="bb029-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="bb029-136">Edit</span></span>|<span data-ttu-id="bb029-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="bb029-137">Edit</span></span>|  
|<span data-ttu-id="bb029-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="bb029-138">SysLink</span></span>|<span data-ttu-id="bb029-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="bb029-139">Hyperlink</span></span>|  
|<span data-ttu-id="bb029-140">Static</span><span class="sxs-lookup"><span data-stu-id="bb029-140">Static</span></span>|<span data-ttu-id="bb029-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="bb029-141">Text</span></span>|  
|<span data-ttu-id="bb029-142">Static</span><span class="sxs-lookup"><span data-stu-id="bb029-142">Static</span></span>|<span data-ttu-id="bb029-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="bb029-143">Image</span></span>|  
|<span data-ttu-id="bb029-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="bb029-144">SysIPAddress32</span></span>|<span data-ttu-id="bb029-145">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="bb029-145">Custom</span></span>|  
|<span data-ttu-id="bb029-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="bb029-146">SysHeader32</span></span>|<span data-ttu-id="bb029-147">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="bb029-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="bb029-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="bb029-148">SysListView32</span></span>|<span data-ttu-id="bb029-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="bb029-149">DataGrid</span></span>|  
|<span data-ttu-id="bb029-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="bb029-150">SysListView32</span></span>|<span data-ttu-id="bb029-151">Lista</span><span class="sxs-lookup"><span data-stu-id="bb029-151">List</span></span>|  
|<span data-ttu-id="bb029-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="bb029-152">ListBox</span></span>|<span data-ttu-id="bb029-153">Lista</span><span class="sxs-lookup"><span data-stu-id="bb029-153">List</span></span>|  
|<span data-ttu-id="bb029-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="bb029-154">ListBox</span></span>|<span data-ttu-id="bb029-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="bb029-155">ListItem</span></span>|  
|<span data-ttu-id="bb029-156">#32768</span><span class="sxs-lookup"><span data-stu-id="bb029-156">#32768</span></span>|<span data-ttu-id="bb029-157">Menu</span><span class="sxs-lookup"><span data-stu-id="bb029-157">Menu</span></span>|  
|<span data-ttu-id="bb029-158">#32768</span><span class="sxs-lookup"><span data-stu-id="bb029-158">#32768</span></span>|<span data-ttu-id="bb029-159">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="bb029-159">MenuItem</span></span>|  
|<span data-ttu-id="bb029-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="bb029-160">msctls_progress32</span></span>|<span data-ttu-id="bb029-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="bb029-161">ProgressBar</span></span>|  
|<span data-ttu-id="bb029-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="bb029-162">RichEdit</span></span>|<span data-ttu-id="bb029-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="bb029-163">Document.</span></span> <span data-ttu-id="bb029-164">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="bb029-164">See note.</span></span>|  
|<span data-ttu-id="bb029-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="bb029-165">RichEdit20A</span></span>|<span data-ttu-id="bb029-166">dokument</span><span class="sxs-lookup"><span data-stu-id="bb029-166">Document</span></span>|  
|<span data-ttu-id="bb029-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="bb029-167">RichEdit20W</span></span>|<span data-ttu-id="bb029-168">dokument</span><span class="sxs-lookup"><span data-stu-id="bb029-168">Document</span></span>|  
|<span data-ttu-id="bb029-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="bb029-169">RichEdit50W</span></span>|<span data-ttu-id="bb029-170">dokument</span><span class="sxs-lookup"><span data-stu-id="bb029-170">Document</span></span>|  
|<span data-ttu-id="bb029-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="bb029-171">ScrollBar</span></span>|<span data-ttu-id="bb029-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="bb029-172">Slider</span></span>|  
|<span data-ttu-id="bb029-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="bb029-173">msctls_trackbar32</span></span>|<span data-ttu-id="bb029-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="bb029-174">Slider</span></span>|  
|<span data-ttu-id="bb029-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="bb029-175">msctls_updown32</span></span>|<span data-ttu-id="bb029-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="bb029-176">Spinner</span></span>|  
|<span data-ttu-id="bb029-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="bb029-177">msctls_statusbar32</span></span>|<span data-ttu-id="bb029-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="bb029-178">StatusBar</span></span>|  
|<span data-ttu-id="bb029-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="bb029-179">SysTabControl32</span></span>|<span data-ttu-id="bb029-180">Tab</span><span class="sxs-lookup"><span data-stu-id="bb029-180">Tab</span></span>|  
|<span data-ttu-id="bb029-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="bb029-181">SysTabControl32</span></span>|<span data-ttu-id="bb029-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="bb029-182">TabItem</span></span>|  
|<span data-ttu-id="bb029-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb029-183">ToolbarWindow32</span></span>|<span data-ttu-id="bb029-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="bb029-184">ToolBar</span></span>|  
|<span data-ttu-id="bb029-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb029-185">ToolbarWindow32</span></span>|<span data-ttu-id="bb029-186">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="bb029-186">MenuItem</span></span>|  
|<span data-ttu-id="bb029-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb029-187">ToolbarWindow32</span></span>|<span data-ttu-id="bb029-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-188">Button</span></span>|  
|<span data-ttu-id="bb029-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb029-189">ToolbarWindow32</span></span>|<span data-ttu-id="bb029-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb029-190">CheckBox</span></span>|  
|<span data-ttu-id="bb029-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb029-191">ToolbarWindow32</span></span>|<span data-ttu-id="bb029-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bb029-192">RadioButton</span></span>|  
|<span data-ttu-id="bb029-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb029-193">ToolbarWindow32</span></span>|<span data-ttu-id="bb029-194">Separator</span><span class="sxs-lookup"><span data-stu-id="bb029-194">Separator</span></span>|  
|<span data-ttu-id="bb029-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="bb029-195">tooltips_class32</span></span>|<span data-ttu-id="bb029-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bb029-196">ToolTip</span></span>|  
|<span data-ttu-id="bb029-197">#32774</span><span class="sxs-lookup"><span data-stu-id="bb029-197">#32774</span></span>|<span data-ttu-id="bb029-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bb029-198">ToolTip</span></span>|  
|<span data-ttu-id="bb029-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb029-199">ReBarWindow32</span></span>|<span data-ttu-id="bb029-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="bb029-200">Toolbar</span></span>|  
|<span data-ttu-id="bb029-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="bb029-201">SysTreeView32</span></span>|<span data-ttu-id="bb029-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="bb029-202">Tree</span></span>|  
|<span data-ttu-id="bb029-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="bb029-203">SysTreeView32</span></span>|<span data-ttu-id="bb029-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="bb029-204">TreeItem</span></span>|  
  
 <span data-ttu-id="bb029-205">**Uwaga** kontrolki RichEdit jest obsługiwana tylko w przypadku wersji są dostarczane z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (w wersji biblioteki RichEd20.dll 3.1 lub nowszy i MsftEdit.dll w wersji 4.1 lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="bb029-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="bb029-206">Następujące elementy sterujące są nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bb029-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="bb029-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="bb029-207">Class name</span></span>|<span data-ttu-id="bb029-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="bb029-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="bb029-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="bb029-209">SysAnimate32</span></span>|<span data-ttu-id="bb029-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="bb029-210">Image</span></span>|  
|<span data-ttu-id="bb029-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="bb029-211">SysPager</span></span>|<span data-ttu-id="bb029-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="bb029-212">Spinner</span></span>|  
|<span data-ttu-id="bb029-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="bb029-213">SysDateTimePick32</span></span>|<span data-ttu-id="bb029-214">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="bb029-214">Custom</span></span>|  
|<span data-ttu-id="bb029-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="bb029-215">SysMonthCal32</span></span>|<span data-ttu-id="bb029-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="bb029-216">Calendar</span></span>|  
|<span data-ttu-id="bb029-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="bb029-217">MS_WINNOTE</span></span>|<span data-ttu-id="bb029-218">Etykietki narzędzi</span><span class="sxs-lookup"><span data-stu-id="bb029-218">Tooltip</span></span>|  
|<span data-ttu-id="bb029-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="bb029-219">VBBubble</span></span>|<span data-ttu-id="bb029-220">Etykietki narzędzi</span><span class="sxs-lookup"><span data-stu-id="bb029-220">Tooltip</span></span>|  
|<span data-ttu-id="bb029-221">Pasek przewijania (jeśli jest używana jako kontrolkę autonomiczne)</span><span class="sxs-lookup"><span data-stu-id="bb029-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="bb029-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="bb029-222">Slider</span></span>|  
|<span data-ttu-id="bb029-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="bb029-223">SuperGrid</span></span>|<span data-ttu-id="bb029-224">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="bb029-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="bb029-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bb029-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="bb029-226">Kontrolek formularzy Windows Forms są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="bb029-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="bb029-227">Ten zestaw jest automatycznie rejestrowane do użycia przy użyciu automatyzacji interfejsu użytkownika aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="bb029-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="bb029-228">Zazwyczaj formantów Windows Forms, które są zarządzane otoki [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] wspólnych formantów są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb029-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="bb029-229">Następujące elementy sterujące są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bb029-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="bb029-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="bb029-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="bb029-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="bb029-231">Button</span></span>|  
|<span data-ttu-id="bb029-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb029-232">CheckBox</span></span>|  
|<span data-ttu-id="bb029-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="bb029-233">CheckedListBox</span></span>|  
|<span data-ttu-id="bb029-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="bb029-234">ColorDialog</span></span>|  
|<span data-ttu-id="bb029-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bb029-235">ComboBox</span></span>|  
|<span data-ttu-id="bb029-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="bb029-236">FolderBrowser</span></span>|  
|<span data-ttu-id="bb029-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="bb029-237">FontDialog</span></span>|  
|<span data-ttu-id="bb029-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="bb029-238">GroupBox</span></span>|  
|<span data-ttu-id="bb029-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="bb029-239">HscrollBar</span></span>|  
|<span data-ttu-id="bb029-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="bb029-240">ImageList</span></span>|  
|<span data-ttu-id="bb029-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="bb029-241">Label</span></span>|  
|<span data-ttu-id="bb029-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="bb029-242">ListBox</span></span>|  
|<span data-ttu-id="bb029-243">ListView</span><span class="sxs-lookup"><span data-stu-id="bb029-243">ListView</span></span>|  
|<span data-ttu-id="bb029-244">MainMenu — informacje o/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="bb029-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="bb029-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="bb029-245">MonthCalendar</span></span>|  
|<span data-ttu-id="bb029-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="bb029-246">NotifyIcon</span></span>|  
|<span data-ttu-id="bb029-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="bb029-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="bb029-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="bb029-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="bb029-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="bb029-249">PrintDialog</span></span>|  
|<span data-ttu-id="bb029-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="bb029-250">ProgressBar</span></span>|  
|<span data-ttu-id="bb029-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bb029-251">RadioButton</span></span>|  
|<span data-ttu-id="bb029-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="bb029-252">RichTextBox</span></span>|  
|<span data-ttu-id="bb029-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="bb029-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="bb029-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="bb029-254">ScrollableControl</span></span>|  
|<span data-ttu-id="bb029-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="bb029-255">SoundPlayer</span></span>|  
|<span data-ttu-id="bb029-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="bb029-256">StatusBar</span></span>|  
|<span data-ttu-id="bb029-257">TabControl — / TabPage —</span><span class="sxs-lookup"><span data-stu-id="bb029-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="bb029-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="bb029-258">TextBox</span></span>|  
|<span data-ttu-id="bb029-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="bb029-259">Timer</span></span>|  
|<span data-ttu-id="bb029-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="bb029-260">Toolbar</span></span>|  
|<span data-ttu-id="bb029-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bb029-261">ToolTip</span></span>|  
|<span data-ttu-id="bb029-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="bb029-262">TrackBar</span></span>|  
|<span data-ttu-id="bb029-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="bb029-263">TreeView</span></span>|  
|<span data-ttu-id="bb029-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="bb029-264">VscrollBar</span></span>|  
|<span data-ttu-id="bb029-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="bb029-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="bb029-266">Następujące elementy sterujące są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] wyłącznie za pośrednictwem ich obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb029-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="bb029-267">Niektóre funkcje mogą nie być dostępne.</span><span class="sxs-lookup"><span data-stu-id="bb029-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="bb029-268">Nazwa kontrolki</span><span class="sxs-lookup"><span data-stu-id="bb029-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="bb029-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="bb029-269">BindingSource</span></span>|  
|<span data-ttu-id="bb029-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="bb029-270">DataGrid</span></span>|  
|<span data-ttu-id="bb029-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="bb029-271">DataGridView</span></span>|  
|<span data-ttu-id="bb029-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="bb029-272">DataNavigator</span></span>|  
|<span data-ttu-id="bb029-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="bb029-273">DomainUpDown</span></span>|  
|<span data-ttu-id="bb029-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="bb029-274">ErrorProvider</span></span>|  
|<span data-ttu-id="bb029-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bb029-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="bb029-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="bb029-276">Form</span></span>|  
|<span data-ttu-id="bb029-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="bb029-277">LinkLabel</span></span>|  
|<span data-ttu-id="bb029-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="bb029-278">HelpProvider</span></span>|  
|<span data-ttu-id="bb029-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="bb029-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="bb029-280">MenuStrip — / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="bb029-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="bb029-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="bb029-281">NumericUpDown</span></span>|  
|<span data-ttu-id="bb029-282">Panel</span><span class="sxs-lookup"><span data-stu-id="bb029-282">Panel</span></span>|  
|<span data-ttu-id="bb029-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="bb029-283">PictureBox</span></span>|  
|<span data-ttu-id="bb029-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="bb029-284">PrintDocument</span></span>|  
|<span data-ttu-id="bb029-285">Printpreview — formant</span><span class="sxs-lookup"><span data-stu-id="bb029-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="bb029-286">Okno dialogowe printpreview —</span><span class="sxs-lookup"><span data-stu-id="bb029-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="bb029-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="bb029-287">PropertyGrid</span></span>|  
|<span data-ttu-id="bb029-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="bb029-288">UserControl</span></span>|  
|<span data-ttu-id="bb029-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bb029-289">ToolStrip</span></span>|  
|<span data-ttu-id="bb029-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bb029-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="bb029-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="bb029-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="bb029-292">Rozdzielacz</span><span class="sxs-lookup"><span data-stu-id="bb029-292">Splitter</span></span>|  
|<span data-ttu-id="bb029-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="bb029-293">RaftingContainer</span></span>|  
|<span data-ttu-id="bb029-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="bb029-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb029-295">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb029-295">See Also</span></span>  
 [<span data-ttu-id="bb029-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="bb029-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
