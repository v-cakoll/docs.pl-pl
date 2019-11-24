---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: c59352f908c5f4a1fd2ca6dd631d26bb5d69f09a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441226"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="88bf9-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów</span><span class="sxs-lookup"><span data-stu-id="88bf9-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="88bf9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="88bf9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="88bf9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="88bf9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="88bf9-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span><span class="sxs-lookup"><span data-stu-id="88bf9-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="88bf9-106">Windows Presentation Foundation Controls</span><span class="sxs-lookup"><span data-stu-id="88bf9-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="88bf9-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88bf9-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="88bf9-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88bf9-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="88bf9-109">Win32 Controls</span><span class="sxs-lookup"><span data-stu-id="88bf9-109">Win32 Controls</span></span>  
 <span data-ttu-id="88bf9-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="88bf9-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="88bf9-111">This assembly is automatically registered for use with UI Automation client applications.</span><span class="sxs-lookup"><span data-stu-id="88bf9-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="88bf9-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span><span class="sxs-lookup"><span data-stu-id="88bf9-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="88bf9-113">The following controls are supported.</span><span class="sxs-lookup"><span data-stu-id="88bf9-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="88bf9-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="88bf9-114">Class name</span></span>|<span data-ttu-id="88bf9-115">Control Type</span><span class="sxs-lookup"><span data-stu-id="88bf9-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="88bf9-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-116">Button</span></span>|<span data-ttu-id="88bf9-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-117">Button</span></span>|  
|<span data-ttu-id="88bf9-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-118">Button</span></span>|<span data-ttu-id="88bf9-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="88bf9-119">RadioButton</span></span>|  
|<span data-ttu-id="88bf9-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-120">Button</span></span>|<span data-ttu-id="88bf9-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="88bf9-121">Group</span></span>|  
|<span data-ttu-id="88bf9-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-122">Button</span></span>|<span data-ttu-id="88bf9-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-123">CheckBox</span></span>|  
|<span data-ttu-id="88bf9-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-124">Button</span></span>|<span data-ttu-id="88bf9-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="88bf9-125">Hyperlink</span></span>|  
|<span data-ttu-id="88bf9-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-126">Button</span></span>|<span data-ttu-id="88bf9-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="88bf9-127">SplitButton</span></span>|  
|<span data-ttu-id="88bf9-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-128">Button</span></span>|<span data-ttu-id="88bf9-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-129">CheckBox</span></span>|  
|<span data-ttu-id="88bf9-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="88bf9-130">ComboBoxEx32</span></span>|<span data-ttu-id="88bf9-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-131">ComboBox</span></span>|  
|<span data-ttu-id="88bf9-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-132">ComboBox</span></span>|<span data-ttu-id="88bf9-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-133">ComboBox</span></span>|  
|<span data-ttu-id="88bf9-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="88bf9-134">Edit</span></span>|<span data-ttu-id="88bf9-135">dokument</span><span class="sxs-lookup"><span data-stu-id="88bf9-135">Document</span></span>|  
|<span data-ttu-id="88bf9-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="88bf9-136">Edit</span></span>|<span data-ttu-id="88bf9-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="88bf9-137">Edit</span></span>|  
|<span data-ttu-id="88bf9-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="88bf9-138">SysLink</span></span>|<span data-ttu-id="88bf9-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="88bf9-139">Hyperlink</span></span>|  
|<span data-ttu-id="88bf9-140">Static</span><span class="sxs-lookup"><span data-stu-id="88bf9-140">Static</span></span>|<span data-ttu-id="88bf9-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="88bf9-141">Text</span></span>|  
|<span data-ttu-id="88bf9-142">Static</span><span class="sxs-lookup"><span data-stu-id="88bf9-142">Static</span></span>|<span data-ttu-id="88bf9-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="88bf9-143">Image</span></span>|  
|<span data-ttu-id="88bf9-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="88bf9-144">SysIPAddress32</span></span>|<span data-ttu-id="88bf9-145">Custom</span><span class="sxs-lookup"><span data-stu-id="88bf9-145">Custom</span></span>|  
|<span data-ttu-id="88bf9-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="88bf9-146">SysHeader32</span></span>|<span data-ttu-id="88bf9-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="88bf9-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="88bf9-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="88bf9-148">SysListView32</span></span>|<span data-ttu-id="88bf9-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="88bf9-149">DataGrid</span></span>|  
|<span data-ttu-id="88bf9-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="88bf9-150">SysListView32</span></span>|<span data-ttu-id="88bf9-151">Lista</span><span class="sxs-lookup"><span data-stu-id="88bf9-151">List</span></span>|  
|<span data-ttu-id="88bf9-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-152">ListBox</span></span>|<span data-ttu-id="88bf9-153">Lista</span><span class="sxs-lookup"><span data-stu-id="88bf9-153">List</span></span>|  
|<span data-ttu-id="88bf9-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-154">ListBox</span></span>|<span data-ttu-id="88bf9-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="88bf9-155">ListItem</span></span>|  
|<span data-ttu-id="88bf9-156">#32768</span><span class="sxs-lookup"><span data-stu-id="88bf9-156">#32768</span></span>|<span data-ttu-id="88bf9-157">Menu</span><span class="sxs-lookup"><span data-stu-id="88bf9-157">Menu</span></span>|  
|<span data-ttu-id="88bf9-158">#32768</span><span class="sxs-lookup"><span data-stu-id="88bf9-158">#32768</span></span>|<span data-ttu-id="88bf9-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="88bf9-159">MenuItem</span></span>|  
|<span data-ttu-id="88bf9-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="88bf9-160">msctls_progress32</span></span>|<span data-ttu-id="88bf9-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-161">ProgressBar</span></span>|  
|<span data-ttu-id="88bf9-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="88bf9-162">RichEdit</span></span>|<span data-ttu-id="88bf9-163">Document.</span><span class="sxs-lookup"><span data-stu-id="88bf9-163">Document.</span></span> <span data-ttu-id="88bf9-164">See note.</span><span class="sxs-lookup"><span data-stu-id="88bf9-164">See note.</span></span>|  
|<span data-ttu-id="88bf9-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="88bf9-165">RichEdit20A</span></span>|<span data-ttu-id="88bf9-166">dokument</span><span class="sxs-lookup"><span data-stu-id="88bf9-166">Document</span></span>|  
|<span data-ttu-id="88bf9-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="88bf9-167">RichEdit20W</span></span>|<span data-ttu-id="88bf9-168">dokument</span><span class="sxs-lookup"><span data-stu-id="88bf9-168">Document</span></span>|  
|<span data-ttu-id="88bf9-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="88bf9-169">RichEdit50W</span></span>|<span data-ttu-id="88bf9-170">dokument</span><span class="sxs-lookup"><span data-stu-id="88bf9-170">Document</span></span>|  
|<span data-ttu-id="88bf9-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-171">ScrollBar</span></span>|<span data-ttu-id="88bf9-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="88bf9-172">Slider</span></span>|  
|<span data-ttu-id="88bf9-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="88bf9-173">msctls_trackbar32</span></span>|<span data-ttu-id="88bf9-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="88bf9-174">Slider</span></span>|  
|<span data-ttu-id="88bf9-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="88bf9-175">msctls_updown32</span></span>|<span data-ttu-id="88bf9-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="88bf9-176">Spinner</span></span>|  
|<span data-ttu-id="88bf9-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="88bf9-177">msctls_statusbar32</span></span>|<span data-ttu-id="88bf9-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-178">StatusBar</span></span>|  
|<span data-ttu-id="88bf9-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="88bf9-179">SysTabControl32</span></span>|<span data-ttu-id="88bf9-180">Tab</span><span class="sxs-lookup"><span data-stu-id="88bf9-180">Tab</span></span>|  
|<span data-ttu-id="88bf9-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="88bf9-181">SysTabControl32</span></span>|<span data-ttu-id="88bf9-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="88bf9-182">TabItem</span></span>|  
|<span data-ttu-id="88bf9-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="88bf9-183">ToolbarWindow32</span></span>|<span data-ttu-id="88bf9-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-184">ToolBar</span></span>|  
|<span data-ttu-id="88bf9-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="88bf9-185">ToolbarWindow32</span></span>|<span data-ttu-id="88bf9-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="88bf9-186">MenuItem</span></span>|  
|<span data-ttu-id="88bf9-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="88bf9-187">ToolbarWindow32</span></span>|<span data-ttu-id="88bf9-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-188">Button</span></span>|  
|<span data-ttu-id="88bf9-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="88bf9-189">ToolbarWindow32</span></span>|<span data-ttu-id="88bf9-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-190">CheckBox</span></span>|  
|<span data-ttu-id="88bf9-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="88bf9-191">ToolbarWindow32</span></span>|<span data-ttu-id="88bf9-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="88bf9-192">RadioButton</span></span>|  
|<span data-ttu-id="88bf9-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="88bf9-193">ToolbarWindow32</span></span>|<span data-ttu-id="88bf9-194">Separator</span><span class="sxs-lookup"><span data-stu-id="88bf9-194">Separator</span></span>|  
|<span data-ttu-id="88bf9-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="88bf9-195">tooltips_class32</span></span>|<span data-ttu-id="88bf9-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="88bf9-196">ToolTip</span></span>|  
|<span data-ttu-id="88bf9-197">#32774</span><span class="sxs-lookup"><span data-stu-id="88bf9-197">#32774</span></span>|<span data-ttu-id="88bf9-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="88bf9-198">ToolTip</span></span>|  
|<span data-ttu-id="88bf9-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="88bf9-199">ReBarWindow32</span></span>|<span data-ttu-id="88bf9-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="88bf9-200">Toolbar</span></span>|  
|<span data-ttu-id="88bf9-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="88bf9-201">SysTreeView32</span></span>|<span data-ttu-id="88bf9-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="88bf9-202">Tree</span></span>|  
|<span data-ttu-id="88bf9-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="88bf9-203">SysTreeView32</span></span>|<span data-ttu-id="88bf9-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="88bf9-204">TreeItem</span></span>|  
  
 <span data-ttu-id="88bf9-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span><span class="sxs-lookup"><span data-stu-id="88bf9-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="88bf9-206">The following controls are not supported.</span><span class="sxs-lookup"><span data-stu-id="88bf9-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="88bf9-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="88bf9-207">Class name</span></span>|<span data-ttu-id="88bf9-208">Control type</span><span class="sxs-lookup"><span data-stu-id="88bf9-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="88bf9-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="88bf9-209">SysAnimate32</span></span>|<span data-ttu-id="88bf9-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="88bf9-210">Image</span></span>|  
|<span data-ttu-id="88bf9-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="88bf9-211">SysPager</span></span>|<span data-ttu-id="88bf9-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="88bf9-212">Spinner</span></span>|  
|<span data-ttu-id="88bf9-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="88bf9-213">SysDateTimePick32</span></span>|<span data-ttu-id="88bf9-214">Custom</span><span class="sxs-lookup"><span data-stu-id="88bf9-214">Custom</span></span>|  
|<span data-ttu-id="88bf9-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="88bf9-215">SysMonthCal32</span></span>|<span data-ttu-id="88bf9-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="88bf9-216">Calendar</span></span>|  
|<span data-ttu-id="88bf9-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="88bf9-217">MS_WINNOTE</span></span>|<span data-ttu-id="88bf9-218">Tooltip</span><span class="sxs-lookup"><span data-stu-id="88bf9-218">Tooltip</span></span>|  
|<span data-ttu-id="88bf9-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="88bf9-219">VBBubble</span></span>|<span data-ttu-id="88bf9-220">Tooltip</span><span class="sxs-lookup"><span data-stu-id="88bf9-220">Tooltip</span></span>|  
|<span data-ttu-id="88bf9-221">ScrollBar (when used as a standalone control)</span><span class="sxs-lookup"><span data-stu-id="88bf9-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="88bf9-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="88bf9-222">Slider</span></span>|  
|<span data-ttu-id="88bf9-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="88bf9-223">SuperGrid</span></span>|<span data-ttu-id="88bf9-224">Custom</span><span class="sxs-lookup"><span data-stu-id="88bf9-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="88bf9-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="88bf9-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="88bf9-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="88bf9-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="88bf9-227">This assembly is automatically registered for use with UI Automation client applications.</span><span class="sxs-lookup"><span data-stu-id="88bf9-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="88bf9-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88bf9-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="88bf9-229">The following controls are supported.</span><span class="sxs-lookup"><span data-stu-id="88bf9-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="88bf9-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="88bf9-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="88bf9-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="88bf9-231">Button</span></span>|  
|<span data-ttu-id="88bf9-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-232">CheckBox</span></span>|  
|<span data-ttu-id="88bf9-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-233">CheckedListBox</span></span>|  
|<span data-ttu-id="88bf9-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="88bf9-234">ColorDialog</span></span>|  
|<span data-ttu-id="88bf9-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-235">ComboBox</span></span>|  
|<span data-ttu-id="88bf9-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="88bf9-236">FolderBrowser</span></span>|  
|<span data-ttu-id="88bf9-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="88bf9-237">FontDialog</span></span>|  
|<span data-ttu-id="88bf9-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-238">GroupBox</span></span>|  
|<span data-ttu-id="88bf9-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-239">HscrollBar</span></span>|  
|<span data-ttu-id="88bf9-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="88bf9-240">ImageList</span></span>|  
|<span data-ttu-id="88bf9-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="88bf9-241">Label</span></span>|  
|<span data-ttu-id="88bf9-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-242">ListBox</span></span>|  
|<span data-ttu-id="88bf9-243">ListView</span><span class="sxs-lookup"><span data-stu-id="88bf9-243">ListView</span></span>|  
|<span data-ttu-id="88bf9-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="88bf9-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="88bf9-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="88bf9-245">MonthCalendar</span></span>|  
|<span data-ttu-id="88bf9-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="88bf9-246">NotifyIcon</span></span>|  
|<span data-ttu-id="88bf9-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="88bf9-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="88bf9-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="88bf9-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="88bf9-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="88bf9-249">PrintDialog</span></span>|  
|<span data-ttu-id="88bf9-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-250">ProgressBar</span></span>|  
|<span data-ttu-id="88bf9-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="88bf9-251">RadioButton</span></span>|  
|<span data-ttu-id="88bf9-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-252">RichTextBox</span></span>|  
|<span data-ttu-id="88bf9-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="88bf9-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="88bf9-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="88bf9-254">ScrollableControl</span></span>|  
|<span data-ttu-id="88bf9-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="88bf9-255">SoundPlayer</span></span>|  
|<span data-ttu-id="88bf9-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-256">StatusBar</span></span>|  
|<span data-ttu-id="88bf9-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="88bf9-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="88bf9-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-258">TextBox</span></span>|  
|<span data-ttu-id="88bf9-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="88bf9-259">Timer</span></span>|  
|<span data-ttu-id="88bf9-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="88bf9-260">Toolbar</span></span>|  
|<span data-ttu-id="88bf9-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="88bf9-261">ToolTip</span></span>|  
|<span data-ttu-id="88bf9-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-262">TrackBar</span></span>|  
|<span data-ttu-id="88bf9-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="88bf9-263">TreeView</span></span>|  
|<span data-ttu-id="88bf9-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="88bf9-264">VscrollBar</span></span>|  
|<span data-ttu-id="88bf9-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="88bf9-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="88bf9-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="88bf9-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="88bf9-267">Some functionality may not be available.</span><span class="sxs-lookup"><span data-stu-id="88bf9-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="88bf9-268">Control Name</span><span class="sxs-lookup"><span data-stu-id="88bf9-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="88bf9-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="88bf9-269">BindingSource</span></span>|  
|<span data-ttu-id="88bf9-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="88bf9-270">DataGrid</span></span>|  
|<span data-ttu-id="88bf9-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="88bf9-271">DataGridView</span></span>|  
|<span data-ttu-id="88bf9-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="88bf9-272">DataNavigator</span></span>|  
|<span data-ttu-id="88bf9-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="88bf9-273">DomainUpDown</span></span>|  
|<span data-ttu-id="88bf9-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="88bf9-274">ErrorProvider</span></span>|  
|<span data-ttu-id="88bf9-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="88bf9-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="88bf9-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="88bf9-276">Form</span></span>|  
|<span data-ttu-id="88bf9-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="88bf9-277">LinkLabel</span></span>|  
|<span data-ttu-id="88bf9-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="88bf9-278">HelpProvider</span></span>|  
|<span data-ttu-id="88bf9-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="88bf9-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="88bf9-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="88bf9-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="88bf9-281">NumericUpDown</span></span>|  
|<span data-ttu-id="88bf9-282">Panel</span><span class="sxs-lookup"><span data-stu-id="88bf9-282">Panel</span></span>|  
|<span data-ttu-id="88bf9-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="88bf9-283">PictureBox</span></span>|  
|<span data-ttu-id="88bf9-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="88bf9-284">PrintDocument</span></span>|  
|<span data-ttu-id="88bf9-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="88bf9-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="88bf9-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="88bf9-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="88bf9-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="88bf9-287">PropertyGrid</span></span>|  
|<span data-ttu-id="88bf9-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="88bf9-288">UserControl</span></span>|  
|<span data-ttu-id="88bf9-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="88bf9-289">ToolStrip</span></span>|  
|<span data-ttu-id="88bf9-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="88bf9-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="88bf9-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="88bf9-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="88bf9-292">Splitter</span><span class="sxs-lookup"><span data-stu-id="88bf9-292">Splitter</span></span>|  
|<span data-ttu-id="88bf9-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="88bf9-293">RaftingContainer</span></span>|  
|<span data-ttu-id="88bf9-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="88bf9-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88bf9-295">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88bf9-295">See also</span></span>

- [<span data-ttu-id="88bf9-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="88bf9-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
