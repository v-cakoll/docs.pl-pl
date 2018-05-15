---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3ccd6e1348125f5d901e0f093d2b5483b818719f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="4fcce-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek</span><span class="sxs-lookup"><span data-stu-id="4fcce-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="4fcce-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4fcce-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4fcce-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="4fcce-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4fcce-105">Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla standardowych formantów w aplikacjach przeznaczonych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] struktury.</span><span class="sxs-lookup"><span data-stu-id="4fcce-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="4fcce-106">Windows Presentation Foundation formantów</span><span class="sxs-lookup"><span data-stu-id="4fcce-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="4fcce-107">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy kontroli, które udostępniają informacje lub pomocy technicznej do interakcji z użytkownikiem mają pełną natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4fcce-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="4fcce-108">Nie są widoczne dla innych elementów, takich jak panele, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4fcce-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="4fcce-109">Formanty Win32</span><span class="sxs-lookup"><span data-stu-id="4fcce-109">Win32 Controls</span></span>  
 <span data-ttu-id="4fcce-110">Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="4fcce-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="4fcce-111">Ten zestaw jest automatycznie dodawane do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4fcce-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="4fcce-112">Pełna obsługa jest udostępniany tylko dla formantów z ComCtrl32.dll w wersji 6 (dostępnych z [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] i nowsze).</span><span class="sxs-lookup"><span data-stu-id="4fcce-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="4fcce-113">Obsługiwane są następujące formanty.</span><span class="sxs-lookup"><span data-stu-id="4fcce-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="4fcce-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="4fcce-114">Class name</span></span>|<span data-ttu-id="4fcce-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="4fcce-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="4fcce-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-116">Button</span></span>|<span data-ttu-id="4fcce-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-117">Button</span></span>|  
|<span data-ttu-id="4fcce-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-118">Button</span></span>|<span data-ttu-id="4fcce-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4fcce-119">RadioButton</span></span>|  
|<span data-ttu-id="4fcce-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-120">Button</span></span>|<span data-ttu-id="4fcce-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="4fcce-121">Group</span></span>|  
|<span data-ttu-id="4fcce-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-122">Button</span></span>|<span data-ttu-id="4fcce-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-123">CheckBox</span></span>|  
|<span data-ttu-id="4fcce-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-124">Button</span></span>|<span data-ttu-id="4fcce-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="4fcce-125">Hyperlink</span></span>|  
|<span data-ttu-id="4fcce-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-126">Button</span></span>|<span data-ttu-id="4fcce-127">Przycisk podziału</span><span class="sxs-lookup"><span data-stu-id="4fcce-127">SplitButton</span></span>|  
|<span data-ttu-id="4fcce-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-128">Button</span></span>|<span data-ttu-id="4fcce-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-129">CheckBox</span></span>|  
|<span data-ttu-id="4fcce-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="4fcce-130">ComboBoxEx32</span></span>|<span data-ttu-id="4fcce-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-131">ComboBox</span></span>|  
|<span data-ttu-id="4fcce-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-132">ComboBox</span></span>|<span data-ttu-id="4fcce-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-133">ComboBox</span></span>|  
|<span data-ttu-id="4fcce-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="4fcce-134">Edit</span></span>|<span data-ttu-id="4fcce-135">dokument</span><span class="sxs-lookup"><span data-stu-id="4fcce-135">Document</span></span>|  
|<span data-ttu-id="4fcce-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="4fcce-136">Edit</span></span>|<span data-ttu-id="4fcce-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="4fcce-137">Edit</span></span>|  
|<span data-ttu-id="4fcce-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="4fcce-138">SysLink</span></span>|<span data-ttu-id="4fcce-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="4fcce-139">Hyperlink</span></span>|  
|<span data-ttu-id="4fcce-140">Static</span><span class="sxs-lookup"><span data-stu-id="4fcce-140">Static</span></span>|<span data-ttu-id="4fcce-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="4fcce-141">Text</span></span>|  
|<span data-ttu-id="4fcce-142">Static</span><span class="sxs-lookup"><span data-stu-id="4fcce-142">Static</span></span>|<span data-ttu-id="4fcce-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="4fcce-143">Image</span></span>|  
|<span data-ttu-id="4fcce-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="4fcce-144">SysIPAddress32</span></span>|<span data-ttu-id="4fcce-145">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="4fcce-145">Custom</span></span>|  
|<span data-ttu-id="4fcce-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="4fcce-146">SysHeader32</span></span>|<span data-ttu-id="4fcce-147">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="4fcce-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="4fcce-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="4fcce-148">SysListView32</span></span>|<span data-ttu-id="4fcce-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="4fcce-149">DataGrid</span></span>|  
|<span data-ttu-id="4fcce-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="4fcce-150">SysListView32</span></span>|<span data-ttu-id="4fcce-151">Lista</span><span class="sxs-lookup"><span data-stu-id="4fcce-151">List</span></span>|  
|<span data-ttu-id="4fcce-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-152">ListBox</span></span>|<span data-ttu-id="4fcce-153">Lista</span><span class="sxs-lookup"><span data-stu-id="4fcce-153">List</span></span>|  
|<span data-ttu-id="4fcce-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-154">ListBox</span></span>|<span data-ttu-id="4fcce-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="4fcce-155">ListItem</span></span>|  
|<span data-ttu-id="4fcce-156">#32768</span><span class="sxs-lookup"><span data-stu-id="4fcce-156">#32768</span></span>|<span data-ttu-id="4fcce-157">Menu</span><span class="sxs-lookup"><span data-stu-id="4fcce-157">Menu</span></span>|  
|<span data-ttu-id="4fcce-158">#32768</span><span class="sxs-lookup"><span data-stu-id="4fcce-158">#32768</span></span>|<span data-ttu-id="4fcce-159">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="4fcce-159">MenuItem</span></span>|  
|<span data-ttu-id="4fcce-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="4fcce-160">msctls_progress32</span></span>|<span data-ttu-id="4fcce-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="4fcce-161">ProgressBar</span></span>|  
|<span data-ttu-id="4fcce-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="4fcce-162">RichEdit</span></span>|<span data-ttu-id="4fcce-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="4fcce-163">Document.</span></span> <span data-ttu-id="4fcce-164">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="4fcce-164">See note.</span></span>|  
|<span data-ttu-id="4fcce-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="4fcce-165">RichEdit20A</span></span>|<span data-ttu-id="4fcce-166">dokument</span><span class="sxs-lookup"><span data-stu-id="4fcce-166">Document</span></span>|  
|<span data-ttu-id="4fcce-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="4fcce-167">RichEdit20W</span></span>|<span data-ttu-id="4fcce-168">dokument</span><span class="sxs-lookup"><span data-stu-id="4fcce-168">Document</span></span>|  
|<span data-ttu-id="4fcce-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="4fcce-169">RichEdit50W</span></span>|<span data-ttu-id="4fcce-170">dokument</span><span class="sxs-lookup"><span data-stu-id="4fcce-170">Document</span></span>|  
|<span data-ttu-id="4fcce-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="4fcce-171">ScrollBar</span></span>|<span data-ttu-id="4fcce-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="4fcce-172">Slider</span></span>|  
|<span data-ttu-id="4fcce-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="4fcce-173">msctls_trackbar32</span></span>|<span data-ttu-id="4fcce-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="4fcce-174">Slider</span></span>|  
|<span data-ttu-id="4fcce-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="4fcce-175">msctls_updown32</span></span>|<span data-ttu-id="4fcce-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="4fcce-176">Spinner</span></span>|  
|<span data-ttu-id="4fcce-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="4fcce-177">msctls_statusbar32</span></span>|<span data-ttu-id="4fcce-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="4fcce-178">StatusBar</span></span>|  
|<span data-ttu-id="4fcce-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="4fcce-179">SysTabControl32</span></span>|<span data-ttu-id="4fcce-180">Tab</span><span class="sxs-lookup"><span data-stu-id="4fcce-180">Tab</span></span>|  
|<span data-ttu-id="4fcce-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="4fcce-181">SysTabControl32</span></span>|<span data-ttu-id="4fcce-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="4fcce-182">TabItem</span></span>|  
|<span data-ttu-id="4fcce-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4fcce-183">ToolbarWindow32</span></span>|<span data-ttu-id="4fcce-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="4fcce-184">ToolBar</span></span>|  
|<span data-ttu-id="4fcce-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4fcce-185">ToolbarWindow32</span></span>|<span data-ttu-id="4fcce-186">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="4fcce-186">MenuItem</span></span>|  
|<span data-ttu-id="4fcce-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4fcce-187">ToolbarWindow32</span></span>|<span data-ttu-id="4fcce-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-188">Button</span></span>|  
|<span data-ttu-id="4fcce-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4fcce-189">ToolbarWindow32</span></span>|<span data-ttu-id="4fcce-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-190">CheckBox</span></span>|  
|<span data-ttu-id="4fcce-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4fcce-191">ToolbarWindow32</span></span>|<span data-ttu-id="4fcce-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4fcce-192">RadioButton</span></span>|  
|<span data-ttu-id="4fcce-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="4fcce-193">ToolbarWindow32</span></span>|<span data-ttu-id="4fcce-194">Separator</span><span class="sxs-lookup"><span data-stu-id="4fcce-194">Separator</span></span>|  
|<span data-ttu-id="4fcce-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="4fcce-195">tooltips_class32</span></span>|<span data-ttu-id="4fcce-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="4fcce-196">ToolTip</span></span>|  
|<span data-ttu-id="4fcce-197">#32774</span><span class="sxs-lookup"><span data-stu-id="4fcce-197">#32774</span></span>|<span data-ttu-id="4fcce-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="4fcce-198">ToolTip</span></span>|  
|<span data-ttu-id="4fcce-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="4fcce-199">ReBarWindow32</span></span>|<span data-ttu-id="4fcce-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="4fcce-200">Toolbar</span></span>|  
|<span data-ttu-id="4fcce-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="4fcce-201">SysTreeView32</span></span>|<span data-ttu-id="4fcce-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="4fcce-202">Tree</span></span>|  
|<span data-ttu-id="4fcce-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="4fcce-203">SysTreeView32</span></span>|<span data-ttu-id="4fcce-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="4fcce-204">TreeItem</span></span>|  
  
 <span data-ttu-id="4fcce-205">**Uwaga** formantu RichEdit jest obsługiwana tylko dla wersji dostarczone z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (w wersji biblioteki RichEd20.dll 3.1 lub nowszy, a MsftEdit.dll wersji 4.1 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="4fcce-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="4fcce-206">Następujące formanty nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4fcce-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="4fcce-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="4fcce-207">Class name</span></span>|<span data-ttu-id="4fcce-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="4fcce-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="4fcce-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="4fcce-209">SysAnimate32</span></span>|<span data-ttu-id="4fcce-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="4fcce-210">Image</span></span>|  
|<span data-ttu-id="4fcce-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="4fcce-211">SysPager</span></span>|<span data-ttu-id="4fcce-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="4fcce-212">Spinner</span></span>|  
|<span data-ttu-id="4fcce-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="4fcce-213">SysDateTimePick32</span></span>|<span data-ttu-id="4fcce-214">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="4fcce-214">Custom</span></span>|  
|<span data-ttu-id="4fcce-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="4fcce-215">SysMonthCal32</span></span>|<span data-ttu-id="4fcce-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="4fcce-216">Calendar</span></span>|  
|<span data-ttu-id="4fcce-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="4fcce-217">MS_WINNOTE</span></span>|<span data-ttu-id="4fcce-218">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="4fcce-218">Tooltip</span></span>|  
|<span data-ttu-id="4fcce-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="4fcce-219">VBBubble</span></span>|<span data-ttu-id="4fcce-220">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="4fcce-220">Tooltip</span></span>|  
|<span data-ttu-id="4fcce-221">Pasek przewijania (jeśli jest używany jako formant autonomiczne)</span><span class="sxs-lookup"><span data-stu-id="4fcce-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="4fcce-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="4fcce-222">Slider</span></span>|  
|<span data-ttu-id="4fcce-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="4fcce-223">SuperGrid</span></span>|<span data-ttu-id="4fcce-224">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="4fcce-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="4fcce-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4fcce-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="4fcce-226">Formanty formularzy systemu Windows są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="4fcce-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="4fcce-227">Ten zestaw jest automatycznie dodawane do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4fcce-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="4fcce-228">Zazwyczaj formanty formularzy systemu Windows, które są zarządzane otoki [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty standardowe są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4fcce-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="4fcce-229">Obsługiwane są następujące formanty.</span><span class="sxs-lookup"><span data-stu-id="4fcce-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="4fcce-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="4fcce-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="4fcce-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="4fcce-231">Button</span></span>|  
|<span data-ttu-id="4fcce-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-232">CheckBox</span></span>|  
|<span data-ttu-id="4fcce-233">CheckedListBox —</span><span class="sxs-lookup"><span data-stu-id="4fcce-233">CheckedListBox</span></span>|  
|<span data-ttu-id="4fcce-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="4fcce-234">ColorDialog</span></span>|  
|<span data-ttu-id="4fcce-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-235">ComboBox</span></span>|  
|<span data-ttu-id="4fcce-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="4fcce-236">FolderBrowser</span></span>|  
|<span data-ttu-id="4fcce-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="4fcce-237">FontDialog</span></span>|  
|<span data-ttu-id="4fcce-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-238">GroupBox</span></span>|  
|<span data-ttu-id="4fcce-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="4fcce-239">HscrollBar</span></span>|  
|<span data-ttu-id="4fcce-240">Listy obrazów</span><span class="sxs-lookup"><span data-stu-id="4fcce-240">ImageList</span></span>|  
|<span data-ttu-id="4fcce-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="4fcce-241">Label</span></span>|  
|<span data-ttu-id="4fcce-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-242">ListBox</span></span>|  
|<span data-ttu-id="4fcce-243">ListView</span><span class="sxs-lookup"><span data-stu-id="4fcce-243">ListView</span></span>|  
|<span data-ttu-id="4fcce-244">MainMenu — / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4fcce-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="4fcce-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="4fcce-245">MonthCalendar</span></span>|  
|<span data-ttu-id="4fcce-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="4fcce-246">NotifyIcon</span></span>|  
|<span data-ttu-id="4fcce-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="4fcce-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="4fcce-248">PageSetupDialog —</span><span class="sxs-lookup"><span data-stu-id="4fcce-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="4fcce-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="4fcce-249">PrintDialog</span></span>|  
|<span data-ttu-id="4fcce-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="4fcce-250">ProgressBar</span></span>|  
|<span data-ttu-id="4fcce-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="4fcce-251">RadioButton</span></span>|  
|<span data-ttu-id="4fcce-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-252">RichTextBox</span></span>|  
|<span data-ttu-id="4fcce-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="4fcce-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="4fcce-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="4fcce-254">ScrollableControl</span></span>|  
|<span data-ttu-id="4fcce-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="4fcce-255">SoundPlayer</span></span>|  
|<span data-ttu-id="4fcce-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="4fcce-256">StatusBar</span></span>|  
|<span data-ttu-id="4fcce-257">TabControl — / TabPage</span><span class="sxs-lookup"><span data-stu-id="4fcce-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="4fcce-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-258">TextBox</span></span>|  
|<span data-ttu-id="4fcce-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="4fcce-259">Timer</span></span>|  
|<span data-ttu-id="4fcce-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="4fcce-260">Toolbar</span></span>|  
|<span data-ttu-id="4fcce-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="4fcce-261">ToolTip</span></span>|  
|<span data-ttu-id="4fcce-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="4fcce-262">TrackBar</span></span>|  
|<span data-ttu-id="4fcce-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="4fcce-263">TreeView</span></span>|  
|<span data-ttu-id="4fcce-264">Vscrollbar —</span><span class="sxs-lookup"><span data-stu-id="4fcce-264">VscrollBar</span></span>|  
|<span data-ttu-id="4fcce-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="4fcce-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="4fcce-266">Następujące sterowniki są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko za pośrednictwem ich obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4fcce-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="4fcce-267">Niektóre funkcje mogą nie być dostępne.</span><span class="sxs-lookup"><span data-stu-id="4fcce-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="4fcce-268">Nazwa formantu</span><span class="sxs-lookup"><span data-stu-id="4fcce-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="4fcce-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="4fcce-269">BindingSource</span></span>|  
|<span data-ttu-id="4fcce-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="4fcce-270">DataGrid</span></span>|  
|<span data-ttu-id="4fcce-271">Formant DataGridView</span><span class="sxs-lookup"><span data-stu-id="4fcce-271">DataGridView</span></span>|  
|<span data-ttu-id="4fcce-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="4fcce-272">DataNavigator</span></span>|  
|<span data-ttu-id="4fcce-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="4fcce-273">DomainUpDown</span></span>|  
|<span data-ttu-id="4fcce-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="4fcce-274">ErrorProvider</span></span>|  
|<span data-ttu-id="4fcce-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4fcce-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="4fcce-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="4fcce-276">Form</span></span>|  
|<span data-ttu-id="4fcce-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="4fcce-277">LinkLabel</span></span>|  
|<span data-ttu-id="4fcce-278">Helpprovider —</span><span class="sxs-lookup"><span data-stu-id="4fcce-278">HelpProvider</span></span>|  
|<span data-ttu-id="4fcce-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="4fcce-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="4fcce-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="4fcce-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="4fcce-281">NumericUpDown</span></span>|  
|<span data-ttu-id="4fcce-282">Panel</span><span class="sxs-lookup"><span data-stu-id="4fcce-282">Panel</span></span>|  
|<span data-ttu-id="4fcce-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="4fcce-283">PictureBox</span></span>|  
|<span data-ttu-id="4fcce-284">PrintDocument —</span><span class="sxs-lookup"><span data-stu-id="4fcce-284">PrintDocument</span></span>|  
|<span data-ttu-id="4fcce-285">Printpreview — formant</span><span class="sxs-lookup"><span data-stu-id="4fcce-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="4fcce-286">Printpreview — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="4fcce-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="4fcce-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="4fcce-287">PropertyGrid</span></span>|  
|<span data-ttu-id="4fcce-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="4fcce-288">UserControl</span></span>|  
|<span data-ttu-id="4fcce-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4fcce-289">ToolStrip</span></span>|  
|<span data-ttu-id="4fcce-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4fcce-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="4fcce-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="4fcce-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="4fcce-292">Podziału</span><span class="sxs-lookup"><span data-stu-id="4fcce-292">Splitter</span></span>|  
|<span data-ttu-id="4fcce-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="4fcce-293">RaftingContainer</span></span>|  
|<span data-ttu-id="4fcce-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="4fcce-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fcce-295">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fcce-295">See Also</span></span>  
 [<span data-ttu-id="4fcce-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4fcce-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
