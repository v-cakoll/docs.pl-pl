---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 3fde9779205ea7d0902ddd99ed192f097a159d2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221482"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="83930-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów</span><span class="sxs-lookup"><span data-stu-id="83930-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="83930-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="83930-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="83930-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="83930-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="83930-105">Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla standardowych kontrolek w aplikacjach przeznaczonych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] struktur.</span><span class="sxs-lookup"><span data-stu-id="83930-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="83930-106">Formanty programu Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="83930-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="83930-107">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy kontroli, które zapewniają informacje lub pomocy technicznej do interakcji z użytkownikiem ma pełne natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83930-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="83930-108">Nie są widoczne dla innych elementów, takich jak paneli, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83930-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="83930-109">Kontrolki Win32</span><span class="sxs-lookup"><span data-stu-id="83930-109">Win32 Controls</span></span>  
 <span data-ttu-id="83930-110">Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="83930-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="83930-111">Ten zestaw jest automatycznie rejestrowane do użycia przy użyciu automatyzacji interfejsu użytkownika aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="83930-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="83930-112">Pełna pomoc techniczna jest dostępna tylko w przypadku kontrolek z ComCtrl32.dll w wersji 6 (udostępniono [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="83930-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="83930-113">Następujące elementy sterujące są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="83930-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="83930-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="83930-114">Class name</span></span>|<span data-ttu-id="83930-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="83930-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="83930-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-116">Button</span></span>|<span data-ttu-id="83930-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-117">Button</span></span>|  
|<span data-ttu-id="83930-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-118">Button</span></span>|<span data-ttu-id="83930-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="83930-119">RadioButton</span></span>|  
|<span data-ttu-id="83930-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-120">Button</span></span>|<span data-ttu-id="83930-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="83930-121">Group</span></span>|  
|<span data-ttu-id="83930-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-122">Button</span></span>|<span data-ttu-id="83930-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="83930-123">CheckBox</span></span>|  
|<span data-ttu-id="83930-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-124">Button</span></span>|<span data-ttu-id="83930-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="83930-125">Hyperlink</span></span>|  
|<span data-ttu-id="83930-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-126">Button</span></span>|<span data-ttu-id="83930-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="83930-127">SplitButton</span></span>|  
|<span data-ttu-id="83930-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-128">Button</span></span>|<span data-ttu-id="83930-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="83930-129">CheckBox</span></span>|  
|<span data-ttu-id="83930-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="83930-130">ComboBoxEx32</span></span>|<span data-ttu-id="83930-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="83930-131">ComboBox</span></span>|  
|<span data-ttu-id="83930-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="83930-132">ComboBox</span></span>|<span data-ttu-id="83930-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="83930-133">ComboBox</span></span>|  
|<span data-ttu-id="83930-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="83930-134">Edit</span></span>|<span data-ttu-id="83930-135">dokument</span><span class="sxs-lookup"><span data-stu-id="83930-135">Document</span></span>|  
|<span data-ttu-id="83930-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="83930-136">Edit</span></span>|<span data-ttu-id="83930-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="83930-137">Edit</span></span>|  
|<span data-ttu-id="83930-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="83930-138">SysLink</span></span>|<span data-ttu-id="83930-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="83930-139">Hyperlink</span></span>|  
|<span data-ttu-id="83930-140">Static</span><span class="sxs-lookup"><span data-stu-id="83930-140">Static</span></span>|<span data-ttu-id="83930-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="83930-141">Text</span></span>|  
|<span data-ttu-id="83930-142">Static</span><span class="sxs-lookup"><span data-stu-id="83930-142">Static</span></span>|<span data-ttu-id="83930-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="83930-143">Image</span></span>|  
|<span data-ttu-id="83930-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="83930-144">SysIPAddress32</span></span>|<span data-ttu-id="83930-145">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="83930-145">Custom</span></span>|  
|<span data-ttu-id="83930-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="83930-146">SysHeader32</span></span>|<span data-ttu-id="83930-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="83930-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="83930-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="83930-148">SysListView32</span></span>|<span data-ttu-id="83930-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="83930-149">DataGrid</span></span>|  
|<span data-ttu-id="83930-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="83930-150">SysListView32</span></span>|<span data-ttu-id="83930-151">Lista</span><span class="sxs-lookup"><span data-stu-id="83930-151">List</span></span>|  
|<span data-ttu-id="83930-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="83930-152">ListBox</span></span>|<span data-ttu-id="83930-153">Lista</span><span class="sxs-lookup"><span data-stu-id="83930-153">List</span></span>|  
|<span data-ttu-id="83930-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="83930-154">ListBox</span></span>|<span data-ttu-id="83930-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="83930-155">ListItem</span></span>|  
|<span data-ttu-id="83930-156">#32768</span><span class="sxs-lookup"><span data-stu-id="83930-156">#32768</span></span>|<span data-ttu-id="83930-157">Menu</span><span class="sxs-lookup"><span data-stu-id="83930-157">Menu</span></span>|  
|<span data-ttu-id="83930-158">#32768</span><span class="sxs-lookup"><span data-stu-id="83930-158">#32768</span></span>|<span data-ttu-id="83930-159">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="83930-159">MenuItem</span></span>|  
|<span data-ttu-id="83930-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="83930-160">msctls_progress32</span></span>|<span data-ttu-id="83930-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="83930-161">ProgressBar</span></span>|  
|<span data-ttu-id="83930-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="83930-162">RichEdit</span></span>|<span data-ttu-id="83930-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="83930-163">Document.</span></span> <span data-ttu-id="83930-164">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="83930-164">See note.</span></span>|  
|<span data-ttu-id="83930-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="83930-165">RichEdit20A</span></span>|<span data-ttu-id="83930-166">dokument</span><span class="sxs-lookup"><span data-stu-id="83930-166">Document</span></span>|  
|<span data-ttu-id="83930-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="83930-167">RichEdit20W</span></span>|<span data-ttu-id="83930-168">dokument</span><span class="sxs-lookup"><span data-stu-id="83930-168">Document</span></span>|  
|<span data-ttu-id="83930-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="83930-169">RichEdit50W</span></span>|<span data-ttu-id="83930-170">dokument</span><span class="sxs-lookup"><span data-stu-id="83930-170">Document</span></span>|  
|<span data-ttu-id="83930-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="83930-171">ScrollBar</span></span>|<span data-ttu-id="83930-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="83930-172">Slider</span></span>|  
|<span data-ttu-id="83930-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="83930-173">msctls_trackbar32</span></span>|<span data-ttu-id="83930-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="83930-174">Slider</span></span>|  
|<span data-ttu-id="83930-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="83930-175">msctls_updown32</span></span>|<span data-ttu-id="83930-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="83930-176">Spinner</span></span>|  
|<span data-ttu-id="83930-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="83930-177">msctls_statusbar32</span></span>|<span data-ttu-id="83930-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="83930-178">StatusBar</span></span>|  
|<span data-ttu-id="83930-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="83930-179">SysTabControl32</span></span>|<span data-ttu-id="83930-180">Tab</span><span class="sxs-lookup"><span data-stu-id="83930-180">Tab</span></span>|  
|<span data-ttu-id="83930-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="83930-181">SysTabControl32</span></span>|<span data-ttu-id="83930-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="83930-182">TabItem</span></span>|  
|<span data-ttu-id="83930-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="83930-183">ToolbarWindow32</span></span>|<span data-ttu-id="83930-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="83930-184">ToolBar</span></span>|  
|<span data-ttu-id="83930-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="83930-185">ToolbarWindow32</span></span>|<span data-ttu-id="83930-186">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="83930-186">MenuItem</span></span>|  
|<span data-ttu-id="83930-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="83930-187">ToolbarWindow32</span></span>|<span data-ttu-id="83930-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-188">Button</span></span>|  
|<span data-ttu-id="83930-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="83930-189">ToolbarWindow32</span></span>|<span data-ttu-id="83930-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="83930-190">CheckBox</span></span>|  
|<span data-ttu-id="83930-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="83930-191">ToolbarWindow32</span></span>|<span data-ttu-id="83930-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="83930-192">RadioButton</span></span>|  
|<span data-ttu-id="83930-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="83930-193">ToolbarWindow32</span></span>|<span data-ttu-id="83930-194">Separator</span><span class="sxs-lookup"><span data-stu-id="83930-194">Separator</span></span>|  
|<span data-ttu-id="83930-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="83930-195">tooltips_class32</span></span>|<span data-ttu-id="83930-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="83930-196">ToolTip</span></span>|  
|<span data-ttu-id="83930-197">#32774</span><span class="sxs-lookup"><span data-stu-id="83930-197">#32774</span></span>|<span data-ttu-id="83930-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="83930-198">ToolTip</span></span>|  
|<span data-ttu-id="83930-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="83930-199">ReBarWindow32</span></span>|<span data-ttu-id="83930-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="83930-200">Toolbar</span></span>|  
|<span data-ttu-id="83930-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="83930-201">SysTreeView32</span></span>|<span data-ttu-id="83930-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="83930-202">Tree</span></span>|  
|<span data-ttu-id="83930-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="83930-203">SysTreeView32</span></span>|<span data-ttu-id="83930-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="83930-204">TreeItem</span></span>|  
  
 <span data-ttu-id="83930-205">**Uwaga** kontrolki RichEdit jest obsługiwana tylko w przypadku wersji są dostarczane z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (w wersji biblioteki RichEd20.dll 3.1 lub nowszy i MsftEdit.dll w wersji 4.1 lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="83930-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="83930-206">Następujące elementy sterujące są nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="83930-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="83930-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="83930-207">Class name</span></span>|<span data-ttu-id="83930-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="83930-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="83930-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="83930-209">SysAnimate32</span></span>|<span data-ttu-id="83930-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="83930-210">Image</span></span>|  
|<span data-ttu-id="83930-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="83930-211">SysPager</span></span>|<span data-ttu-id="83930-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="83930-212">Spinner</span></span>|  
|<span data-ttu-id="83930-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="83930-213">SysDateTimePick32</span></span>|<span data-ttu-id="83930-214">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="83930-214">Custom</span></span>|  
|<span data-ttu-id="83930-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="83930-215">SysMonthCal32</span></span>|<span data-ttu-id="83930-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="83930-216">Calendar</span></span>|  
|<span data-ttu-id="83930-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="83930-217">MS_WINNOTE</span></span>|<span data-ttu-id="83930-218">Tooltip</span><span class="sxs-lookup"><span data-stu-id="83930-218">Tooltip</span></span>|  
|<span data-ttu-id="83930-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="83930-219">VBBubble</span></span>|<span data-ttu-id="83930-220">Tooltip</span><span class="sxs-lookup"><span data-stu-id="83930-220">Tooltip</span></span>|  
|<span data-ttu-id="83930-221">Pasek przewijania (jeśli jest używana jako kontrolkę autonomiczne)</span><span class="sxs-lookup"><span data-stu-id="83930-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="83930-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="83930-222">Slider</span></span>|  
|<span data-ttu-id="83930-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="83930-223">SuperGrid</span></span>|<span data-ttu-id="83930-224">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="83930-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="83930-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83930-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="83930-226">Kontrolek formularzy Windows Forms są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="83930-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="83930-227">Ten zestaw jest automatycznie rejestrowane do użycia przy użyciu automatyzacji interfejsu użytkownika aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="83930-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="83930-228">Zazwyczaj formantów Windows Forms, które są zarządzane otoki [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] wspólnych formantów są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83930-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="83930-229">Następujące elementy sterujące są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="83930-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="83930-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="83930-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="83930-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="83930-231">Button</span></span>|  
|<span data-ttu-id="83930-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="83930-232">CheckBox</span></span>|  
|<span data-ttu-id="83930-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="83930-233">CheckedListBox</span></span>|  
|<span data-ttu-id="83930-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="83930-234">ColorDialog</span></span>|  
|<span data-ttu-id="83930-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="83930-235">ComboBox</span></span>|  
|<span data-ttu-id="83930-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="83930-236">FolderBrowser</span></span>|  
|<span data-ttu-id="83930-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="83930-237">FontDialog</span></span>|  
|<span data-ttu-id="83930-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="83930-238">GroupBox</span></span>|  
|<span data-ttu-id="83930-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="83930-239">HscrollBar</span></span>|  
|<span data-ttu-id="83930-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="83930-240">ImageList</span></span>|  
|<span data-ttu-id="83930-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="83930-241">Label</span></span>|  
|<span data-ttu-id="83930-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="83930-242">ListBox</span></span>|  
|<span data-ttu-id="83930-243">ListView</span><span class="sxs-lookup"><span data-stu-id="83930-243">ListView</span></span>|  
|<span data-ttu-id="83930-244">MainMenu — informacje o/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="83930-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="83930-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="83930-245">MonthCalendar</span></span>|  
|<span data-ttu-id="83930-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="83930-246">NotifyIcon</span></span>|  
|<span data-ttu-id="83930-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="83930-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="83930-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="83930-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="83930-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="83930-249">PrintDialog</span></span>|  
|<span data-ttu-id="83930-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="83930-250">ProgressBar</span></span>|  
|<span data-ttu-id="83930-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="83930-251">RadioButton</span></span>|  
|<span data-ttu-id="83930-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="83930-252">RichTextBox</span></span>|  
|<span data-ttu-id="83930-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="83930-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="83930-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="83930-254">ScrollableControl</span></span>|  
|<span data-ttu-id="83930-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="83930-255">SoundPlayer</span></span>|  
|<span data-ttu-id="83930-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="83930-256">StatusBar</span></span>|  
|<span data-ttu-id="83930-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="83930-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="83930-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="83930-258">TextBox</span></span>|  
|<span data-ttu-id="83930-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="83930-259">Timer</span></span>|  
|<span data-ttu-id="83930-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="83930-260">Toolbar</span></span>|  
|<span data-ttu-id="83930-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="83930-261">ToolTip</span></span>|  
|<span data-ttu-id="83930-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="83930-262">TrackBar</span></span>|  
|<span data-ttu-id="83930-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="83930-263">TreeView</span></span>|  
|<span data-ttu-id="83930-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="83930-264">VscrollBar</span></span>|  
|<span data-ttu-id="83930-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="83930-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="83930-266">Następujące elementy sterujące są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] wyłącznie za pośrednictwem ich obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83930-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="83930-267">Niektóre funkcje mogą nie być dostępne.</span><span class="sxs-lookup"><span data-stu-id="83930-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="83930-268">Nazwa kontrolki</span><span class="sxs-lookup"><span data-stu-id="83930-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="83930-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="83930-269">BindingSource</span></span>|  
|<span data-ttu-id="83930-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="83930-270">DataGrid</span></span>|  
|<span data-ttu-id="83930-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="83930-271">DataGridView</span></span>|  
|<span data-ttu-id="83930-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="83930-272">DataNavigator</span></span>|  
|<span data-ttu-id="83930-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="83930-273">DomainUpDown</span></span>|  
|<span data-ttu-id="83930-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="83930-274">ErrorProvider</span></span>|  
|<span data-ttu-id="83930-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="83930-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="83930-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="83930-276">Form</span></span>|  
|<span data-ttu-id="83930-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="83930-277">LinkLabel</span></span>|  
|<span data-ttu-id="83930-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="83930-278">HelpProvider</span></span>|  
|<span data-ttu-id="83930-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="83930-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="83930-280">MenuStrip — / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="83930-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="83930-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="83930-281">NumericUpDown</span></span>|  
|<span data-ttu-id="83930-282">Panel</span><span class="sxs-lookup"><span data-stu-id="83930-282">Panel</span></span>|  
|<span data-ttu-id="83930-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="83930-283">PictureBox</span></span>|  
|<span data-ttu-id="83930-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="83930-284">PrintDocument</span></span>|  
|<span data-ttu-id="83930-285">Printpreview — formant</span><span class="sxs-lookup"><span data-stu-id="83930-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="83930-286">Okno dialogowe printpreview —</span><span class="sxs-lookup"><span data-stu-id="83930-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="83930-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="83930-287">PropertyGrid</span></span>|  
|<span data-ttu-id="83930-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="83930-288">UserControl</span></span>|  
|<span data-ttu-id="83930-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="83930-289">ToolStrip</span></span>|  
|<span data-ttu-id="83930-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="83930-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="83930-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="83930-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="83930-292">Rozdzielacz</span><span class="sxs-lookup"><span data-stu-id="83930-292">Splitter</span></span>|  
|<span data-ttu-id="83930-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="83930-293">RaftingContainer</span></span>|  
|<span data-ttu-id="83930-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="83930-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83930-295">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83930-295">See also</span></span>

- [<span data-ttu-id="83930-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="83930-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
