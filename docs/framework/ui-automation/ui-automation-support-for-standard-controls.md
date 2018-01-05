---
title: "Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f7529c68e96f93ebbba9fc5e750e09331bda9699
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="18fd5-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek</span><span class="sxs-lookup"><span data-stu-id="18fd5-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="18fd5-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="18fd5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="18fd5-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="18fd5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="18fd5-105">Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla standardowych formantów w aplikacjach przeznaczonych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] struktury.</span><span class="sxs-lookup"><span data-stu-id="18fd5-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="18fd5-106">Windows Presentation Foundation formantów</span><span class="sxs-lookup"><span data-stu-id="18fd5-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="18fd5-107">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy kontroli, które udostępniają informacje lub pomocy technicznej do interakcji z użytkownikiem mają pełną natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18fd5-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="18fd5-108">Nie są widoczne dla innych elementów, takich jak panele, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18fd5-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="18fd5-109">Formanty Win32</span><span class="sxs-lookup"><span data-stu-id="18fd5-109">Win32 Controls</span></span>  
 <span data-ttu-id="18fd5-110">Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="18fd5-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="18fd5-111">Ten zestaw jest automatycznie dodawane do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18fd5-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="18fd5-112">Pełna obsługa jest udostępniany tylko dla formantów z ComCtrl32.dll w wersji 6 (dostępnych z [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] i nowsze).</span><span class="sxs-lookup"><span data-stu-id="18fd5-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="18fd5-113">Obsługiwane są następujące formanty.</span><span class="sxs-lookup"><span data-stu-id="18fd5-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="18fd5-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="18fd5-114">Class name</span></span>|<span data-ttu-id="18fd5-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="18fd5-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="18fd5-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-116">Button</span></span>|<span data-ttu-id="18fd5-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-117">Button</span></span>|  
|<span data-ttu-id="18fd5-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-118">Button</span></span>|<span data-ttu-id="18fd5-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="18fd5-119">RadioButton</span></span>|  
|<span data-ttu-id="18fd5-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-120">Button</span></span>|<span data-ttu-id="18fd5-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="18fd5-121">Group</span></span>|  
|<span data-ttu-id="18fd5-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-122">Button</span></span>|<span data-ttu-id="18fd5-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-123">CheckBox</span></span>|  
|<span data-ttu-id="18fd5-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-124">Button</span></span>|<span data-ttu-id="18fd5-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="18fd5-125">Hyperlink</span></span>|  
|<span data-ttu-id="18fd5-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-126">Button</span></span>|<span data-ttu-id="18fd5-127">Przycisk podziału</span><span class="sxs-lookup"><span data-stu-id="18fd5-127">SplitButton</span></span>|  
|<span data-ttu-id="18fd5-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-128">Button</span></span>|<span data-ttu-id="18fd5-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-129">CheckBox</span></span>|  
|<span data-ttu-id="18fd5-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="18fd5-130">ComboBoxEx32</span></span>|<span data-ttu-id="18fd5-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-131">ComboBox</span></span>|  
|<span data-ttu-id="18fd5-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-132">ComboBox</span></span>|<span data-ttu-id="18fd5-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-133">ComboBox</span></span>|  
|<span data-ttu-id="18fd5-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="18fd5-134">Edit</span></span>|<span data-ttu-id="18fd5-135">dokument</span><span class="sxs-lookup"><span data-stu-id="18fd5-135">Document</span></span>|  
|<span data-ttu-id="18fd5-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="18fd5-136">Edit</span></span>|<span data-ttu-id="18fd5-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="18fd5-137">Edit</span></span>|  
|<span data-ttu-id="18fd5-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="18fd5-138">SysLink</span></span>|<span data-ttu-id="18fd5-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="18fd5-139">Hyperlink</span></span>|  
|<span data-ttu-id="18fd5-140">Static</span><span class="sxs-lookup"><span data-stu-id="18fd5-140">Static</span></span>|<span data-ttu-id="18fd5-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="18fd5-141">Text</span></span>|  
|<span data-ttu-id="18fd5-142">Static</span><span class="sxs-lookup"><span data-stu-id="18fd5-142">Static</span></span>|<span data-ttu-id="18fd5-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="18fd5-143">Image</span></span>|  
|<span data-ttu-id="18fd5-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="18fd5-144">SysIPAddress32</span></span>|<span data-ttu-id="18fd5-145">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="18fd5-145">Custom</span></span>|  
|<span data-ttu-id="18fd5-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="18fd5-146">SysHeader32</span></span>|<span data-ttu-id="18fd5-147">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="18fd5-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="18fd5-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="18fd5-148">SysListView32</span></span>|<span data-ttu-id="18fd5-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="18fd5-149">DataGrid</span></span>|  
|<span data-ttu-id="18fd5-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="18fd5-150">SysListView32</span></span>|<span data-ttu-id="18fd5-151">Lista</span><span class="sxs-lookup"><span data-stu-id="18fd5-151">List</span></span>|  
|<span data-ttu-id="18fd5-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-152">ListBox</span></span>|<span data-ttu-id="18fd5-153">Lista</span><span class="sxs-lookup"><span data-stu-id="18fd5-153">List</span></span>|  
|<span data-ttu-id="18fd5-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-154">ListBox</span></span>|<span data-ttu-id="18fd5-155">Element listy</span><span class="sxs-lookup"><span data-stu-id="18fd5-155">ListItem</span></span>|  
|<span data-ttu-id="18fd5-156">#32768</span><span class="sxs-lookup"><span data-stu-id="18fd5-156">#32768</span></span>|<span data-ttu-id="18fd5-157">Menu</span><span class="sxs-lookup"><span data-stu-id="18fd5-157">Menu</span></span>|  
|<span data-ttu-id="18fd5-158">#32768</span><span class="sxs-lookup"><span data-stu-id="18fd5-158">#32768</span></span>|<span data-ttu-id="18fd5-159">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="18fd5-159">MenuItem</span></span>|  
|<span data-ttu-id="18fd5-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="18fd5-160">msctls_progress32</span></span>|<span data-ttu-id="18fd5-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="18fd5-161">ProgressBar</span></span>|  
|<span data-ttu-id="18fd5-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="18fd5-162">RichEdit</span></span>|<span data-ttu-id="18fd5-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="18fd5-163">Document.</span></span> <span data-ttu-id="18fd5-164">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="18fd5-164">See note.</span></span>|  
|<span data-ttu-id="18fd5-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="18fd5-165">RichEdit20A</span></span>|<span data-ttu-id="18fd5-166">dokument</span><span class="sxs-lookup"><span data-stu-id="18fd5-166">Document</span></span>|  
|<span data-ttu-id="18fd5-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="18fd5-167">RichEdit20W</span></span>|<span data-ttu-id="18fd5-168">dokument</span><span class="sxs-lookup"><span data-stu-id="18fd5-168">Document</span></span>|  
|<span data-ttu-id="18fd5-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="18fd5-169">RichEdit50W</span></span>|<span data-ttu-id="18fd5-170">dokument</span><span class="sxs-lookup"><span data-stu-id="18fd5-170">Document</span></span>|  
|<span data-ttu-id="18fd5-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="18fd5-171">ScrollBar</span></span>|<span data-ttu-id="18fd5-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="18fd5-172">Slider</span></span>|  
|<span data-ttu-id="18fd5-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="18fd5-173">msctls_trackbar32</span></span>|<span data-ttu-id="18fd5-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="18fd5-174">Slider</span></span>|  
|<span data-ttu-id="18fd5-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="18fd5-175">msctls_updown32</span></span>|<span data-ttu-id="18fd5-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="18fd5-176">Spinner</span></span>|  
|<span data-ttu-id="18fd5-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="18fd5-177">msctls_statusbar32</span></span>|<span data-ttu-id="18fd5-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="18fd5-178">StatusBar</span></span>|  
|<span data-ttu-id="18fd5-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="18fd5-179">SysTabControl32</span></span>|<span data-ttu-id="18fd5-180">Tab</span><span class="sxs-lookup"><span data-stu-id="18fd5-180">Tab</span></span>|  
|<span data-ttu-id="18fd5-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="18fd5-181">SysTabControl32</span></span>|<span data-ttu-id="18fd5-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="18fd5-182">TabItem</span></span>|  
|<span data-ttu-id="18fd5-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="18fd5-183">ToolbarWindow32</span></span>|<span data-ttu-id="18fd5-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="18fd5-184">ToolBar</span></span>|  
|<span data-ttu-id="18fd5-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="18fd5-185">ToolbarWindow32</span></span>|<span data-ttu-id="18fd5-186">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="18fd5-186">MenuItem</span></span>|  
|<span data-ttu-id="18fd5-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="18fd5-187">ToolbarWindow32</span></span>|<span data-ttu-id="18fd5-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-188">Button</span></span>|  
|<span data-ttu-id="18fd5-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="18fd5-189">ToolbarWindow32</span></span>|<span data-ttu-id="18fd5-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-190">CheckBox</span></span>|  
|<span data-ttu-id="18fd5-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="18fd5-191">ToolbarWindow32</span></span>|<span data-ttu-id="18fd5-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="18fd5-192">RadioButton</span></span>|  
|<span data-ttu-id="18fd5-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="18fd5-193">ToolbarWindow32</span></span>|<span data-ttu-id="18fd5-194">Separator</span><span class="sxs-lookup"><span data-stu-id="18fd5-194">Separator</span></span>|  
|<span data-ttu-id="18fd5-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="18fd5-195">tooltips_class32</span></span>|<span data-ttu-id="18fd5-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="18fd5-196">ToolTip</span></span>|  
|<span data-ttu-id="18fd5-197">#32774</span><span class="sxs-lookup"><span data-stu-id="18fd5-197">#32774</span></span>|<span data-ttu-id="18fd5-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="18fd5-198">ToolTip</span></span>|  
|<span data-ttu-id="18fd5-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="18fd5-199">ReBarWindow32</span></span>|<span data-ttu-id="18fd5-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="18fd5-200">Toolbar</span></span>|  
|<span data-ttu-id="18fd5-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="18fd5-201">SysTreeView32</span></span>|<span data-ttu-id="18fd5-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="18fd5-202">Tree</span></span>|  
|<span data-ttu-id="18fd5-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="18fd5-203">SysTreeView32</span></span>|<span data-ttu-id="18fd5-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="18fd5-204">TreeItem</span></span>|  
  
 <span data-ttu-id="18fd5-205">**Uwaga** formantu RichEdit jest obsługiwana tylko dla wersji dostarczone z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (w wersji biblioteki RichEd20.dll 3.1 lub nowszy, a MsftEdit.dll wersji 4.1 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="18fd5-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="18fd5-206">Następujące formanty nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="18fd5-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="18fd5-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="18fd5-207">Class name</span></span>|<span data-ttu-id="18fd5-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="18fd5-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="18fd5-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="18fd5-209">SysAnimate32</span></span>|<span data-ttu-id="18fd5-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="18fd5-210">Image</span></span>|  
|<span data-ttu-id="18fd5-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="18fd5-211">SysPager</span></span>|<span data-ttu-id="18fd5-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="18fd5-212">Spinner</span></span>|  
|<span data-ttu-id="18fd5-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="18fd5-213">SysDateTimePick32</span></span>|<span data-ttu-id="18fd5-214">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="18fd5-214">Custom</span></span>|  
|<span data-ttu-id="18fd5-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="18fd5-215">SysMonthCal32</span></span>|<span data-ttu-id="18fd5-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="18fd5-216">Calendar</span></span>|  
|<span data-ttu-id="18fd5-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="18fd5-217">MS_WINNOTE</span></span>|<span data-ttu-id="18fd5-218">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="18fd5-218">Tooltip</span></span>|  
|<span data-ttu-id="18fd5-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="18fd5-219">VBBubble</span></span>|<span data-ttu-id="18fd5-220">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="18fd5-220">Tooltip</span></span>|  
|<span data-ttu-id="18fd5-221">Pasek przewijania (jeśli jest używany jako formant autonomiczne)</span><span class="sxs-lookup"><span data-stu-id="18fd5-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="18fd5-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="18fd5-222">Slider</span></span>|  
|<span data-ttu-id="18fd5-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="18fd5-223">SuperGrid</span></span>|<span data-ttu-id="18fd5-224">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="18fd5-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="18fd5-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="18fd5-225">Windows Forms Controls</span></span>  
 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]<span data-ttu-id="18fd5-226">Formanty są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="18fd5-226"> controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="18fd5-227">Ten zestaw jest automatycznie dodawane do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18fd5-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="18fd5-228">Zazwyczaj [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] formantów, które są zarządzane otoki [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty standardowe są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18fd5-228">Typically, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="18fd5-229">Obsługiwane są następujące formanty.</span><span class="sxs-lookup"><span data-stu-id="18fd5-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="18fd5-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="18fd5-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="18fd5-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="18fd5-231">Button</span></span>|  
|<span data-ttu-id="18fd5-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-232">CheckBox</span></span>|  
|<span data-ttu-id="18fd5-233">CheckedListBox —</span><span class="sxs-lookup"><span data-stu-id="18fd5-233">CheckedListBox</span></span>|  
|<span data-ttu-id="18fd5-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="18fd5-234">ColorDialog</span></span>|  
|<span data-ttu-id="18fd5-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-235">ComboBox</span></span>|  
|<span data-ttu-id="18fd5-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="18fd5-236">FolderBrowser</span></span>|  
|<span data-ttu-id="18fd5-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="18fd5-237">FontDialog</span></span>|  
|<span data-ttu-id="18fd5-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-238">GroupBox</span></span>|  
|<span data-ttu-id="18fd5-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="18fd5-239">HscrollBar</span></span>|  
|<span data-ttu-id="18fd5-240">Listy obrazów</span><span class="sxs-lookup"><span data-stu-id="18fd5-240">ImageList</span></span>|  
|<span data-ttu-id="18fd5-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="18fd5-241">Label</span></span>|  
|<span data-ttu-id="18fd5-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-242">ListBox</span></span>|  
|<span data-ttu-id="18fd5-243">ListView</span><span class="sxs-lookup"><span data-stu-id="18fd5-243">ListView</span></span>|  
|<span data-ttu-id="18fd5-244">MainMenu — / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="18fd5-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="18fd5-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="18fd5-245">MonthCalendar</span></span>|  
|<span data-ttu-id="18fd5-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="18fd5-246">NotifyIcon</span></span>|  
|<span data-ttu-id="18fd5-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="18fd5-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="18fd5-248">PageSetupDialog —</span><span class="sxs-lookup"><span data-stu-id="18fd5-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="18fd5-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="18fd5-249">PrintDialog</span></span>|  
|<span data-ttu-id="18fd5-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="18fd5-250">ProgressBar</span></span>|  
|<span data-ttu-id="18fd5-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="18fd5-251">RadioButton</span></span>|  
|<span data-ttu-id="18fd5-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-252">RichTextBox</span></span>|  
|<span data-ttu-id="18fd5-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="18fd5-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="18fd5-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="18fd5-254">ScrollableControl</span></span>|  
|<span data-ttu-id="18fd5-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="18fd5-255">SoundPlayer</span></span>|  
|<span data-ttu-id="18fd5-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="18fd5-256">StatusBar</span></span>|  
|<span data-ttu-id="18fd5-257">TabControl — / TabPage</span><span class="sxs-lookup"><span data-stu-id="18fd5-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="18fd5-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-258">TextBox</span></span>|  
|<span data-ttu-id="18fd5-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="18fd5-259">Timer</span></span>|  
|<span data-ttu-id="18fd5-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="18fd5-260">Toolbar</span></span>|  
|<span data-ttu-id="18fd5-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="18fd5-261">ToolTip</span></span>|  
|<span data-ttu-id="18fd5-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="18fd5-262">TrackBar</span></span>|  
|<span data-ttu-id="18fd5-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="18fd5-263">TreeView</span></span>|  
|<span data-ttu-id="18fd5-264">Vscrollbar —</span><span class="sxs-lookup"><span data-stu-id="18fd5-264">VscrollBar</span></span>|  
|<span data-ttu-id="18fd5-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="18fd5-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="18fd5-266">Następujące sterowniki są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko za pośrednictwem ich obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18fd5-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="18fd5-267">Niektóre funkcje mogą nie być dostępne.</span><span class="sxs-lookup"><span data-stu-id="18fd5-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="18fd5-268">Nazwa formantu</span><span class="sxs-lookup"><span data-stu-id="18fd5-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="18fd5-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="18fd5-269">BindingSource</span></span>|  
|<span data-ttu-id="18fd5-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="18fd5-270">DataGrid</span></span>|  
|<span data-ttu-id="18fd5-271">Formant DataGridView</span><span class="sxs-lookup"><span data-stu-id="18fd5-271">DataGridView</span></span>|  
|<span data-ttu-id="18fd5-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="18fd5-272">DataNavigator</span></span>|  
|<span data-ttu-id="18fd5-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="18fd5-273">DomainUpDown</span></span>|  
|<span data-ttu-id="18fd5-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="18fd5-274">ErrorProvider</span></span>|  
|<span data-ttu-id="18fd5-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="18fd5-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="18fd5-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="18fd5-276">Form</span></span>|  
|<span data-ttu-id="18fd5-277">Linklabel —</span><span class="sxs-lookup"><span data-stu-id="18fd5-277">LinkLabel</span></span>|  
|<span data-ttu-id="18fd5-278">Helpprovider —</span><span class="sxs-lookup"><span data-stu-id="18fd5-278">HelpProvider</span></span>|  
|<span data-ttu-id="18fd5-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="18fd5-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="18fd5-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="18fd5-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="18fd5-281">NumericUpDown</span></span>|  
|<span data-ttu-id="18fd5-282">Panel</span><span class="sxs-lookup"><span data-stu-id="18fd5-282">Panel</span></span>|  
|<span data-ttu-id="18fd5-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="18fd5-283">PictureBox</span></span>|  
|<span data-ttu-id="18fd5-284">PrintDocument —</span><span class="sxs-lookup"><span data-stu-id="18fd5-284">PrintDocument</span></span>|  
|<span data-ttu-id="18fd5-285">Printpreview — formant</span><span class="sxs-lookup"><span data-stu-id="18fd5-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="18fd5-286">Printpreview — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="18fd5-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="18fd5-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="18fd5-287">PropertyGrid</span></span>|  
|<span data-ttu-id="18fd5-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="18fd5-288">UserControl</span></span>|  
|<span data-ttu-id="18fd5-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="18fd5-289">ToolStrip</span></span>|  
|<span data-ttu-id="18fd5-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="18fd5-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="18fd5-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="18fd5-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="18fd5-292">Podziału</span><span class="sxs-lookup"><span data-stu-id="18fd5-292">Splitter</span></span>|  
|<span data-ttu-id="18fd5-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="18fd5-293">RaftingContainer</span></span>|  
|<span data-ttu-id="18fd5-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="18fd5-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18fd5-295">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18fd5-295">See Also</span></span>  
 [<span data-ttu-id="18fd5-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="18fd5-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
