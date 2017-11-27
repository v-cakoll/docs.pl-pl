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
ms.openlocfilehash: 71a5a2e4319debf1a4d8ddd08d7f0979443682b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="d7a23-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek</span><span class="sxs-lookup"><span data-stu-id="d7a23-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="d7a23-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d7a23-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d7a23-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d7a23-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d7a23-105">Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla standardowych formantów w aplikacjach przeznaczonych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] struktury.</span><span class="sxs-lookup"><span data-stu-id="d7a23-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="d7a23-106">Windows Presentation Foundation formantów</span><span class="sxs-lookup"><span data-stu-id="d7a23-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="d7a23-107">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy kontroli, które udostępniają informacje lub pomocy technicznej do interakcji z użytkownikiem mają pełną natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7a23-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d7a23-108">Nie są widoczne dla innych elementów, takich jak panele, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7a23-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="d7a23-109">Formanty Win32</span><span class="sxs-lookup"><span data-stu-id="d7a23-109">Win32 Controls</span></span>  
 <span data-ttu-id="d7a23-110">Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="d7a23-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d7a23-111">Ten zestaw jest automatycznie dodawane do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d7a23-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d7a23-112">Pełna obsługa jest udostępniany tylko dla formantów z ComCtrl32.dll w wersji 6 (dostępnych z [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] i nowsze).</span><span class="sxs-lookup"><span data-stu-id="d7a23-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="d7a23-113">Obsługiwane są następujące formanty.</span><span class="sxs-lookup"><span data-stu-id="d7a23-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d7a23-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="d7a23-114">Class name</span></span>|<span data-ttu-id="d7a23-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="d7a23-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d7a23-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-116">Button</span></span>|<span data-ttu-id="d7a23-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-117">Button</span></span>|  
|<span data-ttu-id="d7a23-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-118">Button</span></span>|<span data-ttu-id="d7a23-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d7a23-119">RadioButton</span></span>|  
|<span data-ttu-id="d7a23-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-120">Button</span></span>|<span data-ttu-id="d7a23-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="d7a23-121">Group</span></span>|  
|<span data-ttu-id="d7a23-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-122">Button</span></span>|<span data-ttu-id="d7a23-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-123">CheckBox</span></span>|  
|<span data-ttu-id="d7a23-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-124">Button</span></span>|<span data-ttu-id="d7a23-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="d7a23-125">Hyperlink</span></span>|  
|<span data-ttu-id="d7a23-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-126">Button</span></span>|<span data-ttu-id="d7a23-127">Przycisk podziału</span><span class="sxs-lookup"><span data-stu-id="d7a23-127">SplitButton</span></span>|  
|<span data-ttu-id="d7a23-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-128">Button</span></span>|<span data-ttu-id="d7a23-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-129">CheckBox</span></span>|  
|<span data-ttu-id="d7a23-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="d7a23-130">ComboBoxEx32</span></span>|<span data-ttu-id="d7a23-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-131">ComboBox</span></span>|  
|<span data-ttu-id="d7a23-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-132">ComboBox</span></span>|<span data-ttu-id="d7a23-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-133">ComboBox</span></span>|  
|<span data-ttu-id="d7a23-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="d7a23-134">Edit</span></span>|<span data-ttu-id="d7a23-135">dokument</span><span class="sxs-lookup"><span data-stu-id="d7a23-135">Document</span></span>|  
|<span data-ttu-id="d7a23-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="d7a23-136">Edit</span></span>|<span data-ttu-id="d7a23-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="d7a23-137">Edit</span></span>|  
|<span data-ttu-id="d7a23-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="d7a23-138">SysLink</span></span>|<span data-ttu-id="d7a23-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="d7a23-139">Hyperlink</span></span>|  
|<span data-ttu-id="d7a23-140">Static</span><span class="sxs-lookup"><span data-stu-id="d7a23-140">Static</span></span>|<span data-ttu-id="d7a23-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="d7a23-141">Text</span></span>|  
|<span data-ttu-id="d7a23-142">Static</span><span class="sxs-lookup"><span data-stu-id="d7a23-142">Static</span></span>|<span data-ttu-id="d7a23-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="d7a23-143">Image</span></span>|  
|<span data-ttu-id="d7a23-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="d7a23-144">SysIPAddress32</span></span>|<span data-ttu-id="d7a23-145">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d7a23-145">Custom</span></span>|  
|<span data-ttu-id="d7a23-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="d7a23-146">SysHeader32</span></span>|<span data-ttu-id="d7a23-147">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="d7a23-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="d7a23-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d7a23-148">SysListView32</span></span>|<span data-ttu-id="d7a23-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d7a23-149">DataGrid</span></span>|  
|<span data-ttu-id="d7a23-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d7a23-150">SysListView32</span></span>|<span data-ttu-id="d7a23-151">Lista</span><span class="sxs-lookup"><span data-stu-id="d7a23-151">List</span></span>|  
|<span data-ttu-id="d7a23-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-152">ListBox</span></span>|<span data-ttu-id="d7a23-153">Lista</span><span class="sxs-lookup"><span data-stu-id="d7a23-153">List</span></span>|  
|<span data-ttu-id="d7a23-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-154">ListBox</span></span>|<span data-ttu-id="d7a23-155">Element listy</span><span class="sxs-lookup"><span data-stu-id="d7a23-155">ListItem</span></span>|  
|<span data-ttu-id="d7a23-156">#32768</span><span class="sxs-lookup"><span data-stu-id="d7a23-156">#32768</span></span>|<span data-ttu-id="d7a23-157">Menu</span><span class="sxs-lookup"><span data-stu-id="d7a23-157">Menu</span></span>|  
|<span data-ttu-id="d7a23-158">#32768</span><span class="sxs-lookup"><span data-stu-id="d7a23-158">#32768</span></span>|<span data-ttu-id="d7a23-159">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="d7a23-159">MenuItem</span></span>|  
|<span data-ttu-id="d7a23-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="d7a23-160">msctls_progress32</span></span>|<span data-ttu-id="d7a23-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d7a23-161">ProgressBar</span></span>|  
|<span data-ttu-id="d7a23-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="d7a23-162">RichEdit</span></span>|<span data-ttu-id="d7a23-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="d7a23-163">Document.</span></span> <span data-ttu-id="d7a23-164">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="d7a23-164">See note.</span></span>|  
|<span data-ttu-id="d7a23-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="d7a23-165">RichEdit20A</span></span>|<span data-ttu-id="d7a23-166">dokument</span><span class="sxs-lookup"><span data-stu-id="d7a23-166">Document</span></span>|  
|<span data-ttu-id="d7a23-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="d7a23-167">RichEdit20W</span></span>|<span data-ttu-id="d7a23-168">dokument</span><span class="sxs-lookup"><span data-stu-id="d7a23-168">Document</span></span>|  
|<span data-ttu-id="d7a23-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="d7a23-169">RichEdit50W</span></span>|<span data-ttu-id="d7a23-170">dokument</span><span class="sxs-lookup"><span data-stu-id="d7a23-170">Document</span></span>|  
|<span data-ttu-id="d7a23-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="d7a23-171">ScrollBar</span></span>|<span data-ttu-id="d7a23-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="d7a23-172">Slider</span></span>|  
|<span data-ttu-id="d7a23-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="d7a23-173">msctls_trackbar32</span></span>|<span data-ttu-id="d7a23-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="d7a23-174">Slider</span></span>|  
|<span data-ttu-id="d7a23-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="d7a23-175">msctls_updown32</span></span>|<span data-ttu-id="d7a23-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="d7a23-176">Spinner</span></span>|  
|<span data-ttu-id="d7a23-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="d7a23-177">msctls_statusbar32</span></span>|<span data-ttu-id="d7a23-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d7a23-178">StatusBar</span></span>|  
|<span data-ttu-id="d7a23-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d7a23-179">SysTabControl32</span></span>|<span data-ttu-id="d7a23-180">Tab</span><span class="sxs-lookup"><span data-stu-id="d7a23-180">Tab</span></span>|  
|<span data-ttu-id="d7a23-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d7a23-181">SysTabControl32</span></span>|<span data-ttu-id="d7a23-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="d7a23-182">TabItem</span></span>|  
|<span data-ttu-id="d7a23-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d7a23-183">ToolbarWindow32</span></span>|<span data-ttu-id="d7a23-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="d7a23-184">ToolBar</span></span>|  
|<span data-ttu-id="d7a23-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d7a23-185">ToolbarWindow32</span></span>|<span data-ttu-id="d7a23-186">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="d7a23-186">MenuItem</span></span>|  
|<span data-ttu-id="d7a23-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d7a23-187">ToolbarWindow32</span></span>|<span data-ttu-id="d7a23-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-188">Button</span></span>|  
|<span data-ttu-id="d7a23-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d7a23-189">ToolbarWindow32</span></span>|<span data-ttu-id="d7a23-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-190">CheckBox</span></span>|  
|<span data-ttu-id="d7a23-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d7a23-191">ToolbarWindow32</span></span>|<span data-ttu-id="d7a23-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d7a23-192">RadioButton</span></span>|  
|<span data-ttu-id="d7a23-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d7a23-193">ToolbarWindow32</span></span>|<span data-ttu-id="d7a23-194">Separator</span><span class="sxs-lookup"><span data-stu-id="d7a23-194">Separator</span></span>|  
|<span data-ttu-id="d7a23-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="d7a23-195">tooltips_class32</span></span>|<span data-ttu-id="d7a23-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d7a23-196">ToolTip</span></span>|  
|<span data-ttu-id="d7a23-197">#32774</span><span class="sxs-lookup"><span data-stu-id="d7a23-197">#32774</span></span>|<span data-ttu-id="d7a23-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d7a23-198">ToolTip</span></span>|  
|<span data-ttu-id="d7a23-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="d7a23-199">ReBarWindow32</span></span>|<span data-ttu-id="d7a23-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="d7a23-200">Toolbar</span></span>|  
|<span data-ttu-id="d7a23-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d7a23-201">SysTreeView32</span></span>|<span data-ttu-id="d7a23-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="d7a23-202">Tree</span></span>|  
|<span data-ttu-id="d7a23-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d7a23-203">SysTreeView32</span></span>|<span data-ttu-id="d7a23-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="d7a23-204">TreeItem</span></span>|  
  
 <span data-ttu-id="d7a23-205">**Uwaga** formantu RichEdit jest obsługiwana tylko dla wersji dostarczone z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (w wersji biblioteki RichEd20.dll 3.1 lub nowszy, a MsftEdit.dll wersji 4.1 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="d7a23-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="d7a23-206">Następujące formanty nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d7a23-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="d7a23-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="d7a23-207">Class name</span></span>|<span data-ttu-id="d7a23-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="d7a23-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d7a23-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="d7a23-209">SysAnimate32</span></span>|<span data-ttu-id="d7a23-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="d7a23-210">Image</span></span>|  
|<span data-ttu-id="d7a23-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="d7a23-211">SysPager</span></span>|<span data-ttu-id="d7a23-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="d7a23-212">Spinner</span></span>|  
|<span data-ttu-id="d7a23-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="d7a23-213">SysDateTimePick32</span></span>|<span data-ttu-id="d7a23-214">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d7a23-214">Custom</span></span>|  
|<span data-ttu-id="d7a23-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="d7a23-215">SysMonthCal32</span></span>|<span data-ttu-id="d7a23-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="d7a23-216">Calendar</span></span>|  
|<span data-ttu-id="d7a23-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="d7a23-217">MS_WINNOTE</span></span>|<span data-ttu-id="d7a23-218">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="d7a23-218">Tooltip</span></span>|  
|<span data-ttu-id="d7a23-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="d7a23-219">VBBubble</span></span>|<span data-ttu-id="d7a23-220">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="d7a23-220">Tooltip</span></span>|  
|<span data-ttu-id="d7a23-221">Pasek przewijania (jeśli jest używany jako formant autonomiczne)</span><span class="sxs-lookup"><span data-stu-id="d7a23-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="d7a23-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="d7a23-222">Slider</span></span>|  
|<span data-ttu-id="d7a23-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="d7a23-223">SuperGrid</span></span>|<span data-ttu-id="d7a23-224">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d7a23-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="d7a23-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d7a23-225">Windows Forms Controls</span></span>  
 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]<span data-ttu-id="d7a23-226">Formanty są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="d7a23-226"> controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d7a23-227">Ten zestaw jest automatycznie dodawane do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d7a23-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d7a23-228">Zazwyczaj [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] formantów, które są zarządzane otoki [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty standardowe są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7a23-228">Typically, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d7a23-229">Obsługiwane są następujące formanty.</span><span class="sxs-lookup"><span data-stu-id="d7a23-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d7a23-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="d7a23-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="d7a23-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d7a23-231">Button</span></span>|  
|<span data-ttu-id="d7a23-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-232">CheckBox</span></span>|  
|<span data-ttu-id="d7a23-233">CheckedListBox —</span><span class="sxs-lookup"><span data-stu-id="d7a23-233">CheckedListBox</span></span>|  
|<span data-ttu-id="d7a23-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="d7a23-234">ColorDialog</span></span>|  
|<span data-ttu-id="d7a23-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-235">ComboBox</span></span>|  
|<span data-ttu-id="d7a23-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="d7a23-236">FolderBrowser</span></span>|  
|<span data-ttu-id="d7a23-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="d7a23-237">FontDialog</span></span>|  
|<span data-ttu-id="d7a23-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-238">GroupBox</span></span>|  
|<span data-ttu-id="d7a23-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="d7a23-239">HscrollBar</span></span>|  
|<span data-ttu-id="d7a23-240">Listy obrazów</span><span class="sxs-lookup"><span data-stu-id="d7a23-240">ImageList</span></span>|  
|<span data-ttu-id="d7a23-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="d7a23-241">Label</span></span>|  
|<span data-ttu-id="d7a23-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-242">ListBox</span></span>|  
|<span data-ttu-id="d7a23-243">ListView</span><span class="sxs-lookup"><span data-stu-id="d7a23-243">ListView</span></span>|  
|<span data-ttu-id="d7a23-244">MainMenu — / ContextMenu</span><span class="sxs-lookup"><span data-stu-id="d7a23-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="d7a23-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d7a23-245">MonthCalendar</span></span>|  
|<span data-ttu-id="d7a23-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="d7a23-246">NotifyIcon</span></span>|  
|<span data-ttu-id="d7a23-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="d7a23-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="d7a23-248">PageSetupDialog —</span><span class="sxs-lookup"><span data-stu-id="d7a23-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="d7a23-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="d7a23-249">PrintDialog</span></span>|  
|<span data-ttu-id="d7a23-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d7a23-250">ProgressBar</span></span>|  
|<span data-ttu-id="d7a23-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d7a23-251">RadioButton</span></span>|  
|<span data-ttu-id="d7a23-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-252">RichTextBox</span></span>|  
|<span data-ttu-id="d7a23-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="d7a23-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="d7a23-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="d7a23-254">ScrollableControl</span></span>|  
|<span data-ttu-id="d7a23-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="d7a23-255">SoundPlayer</span></span>|  
|<span data-ttu-id="d7a23-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d7a23-256">StatusBar</span></span>|  
|<span data-ttu-id="d7a23-257">TabControl — / TabPage</span><span class="sxs-lookup"><span data-stu-id="d7a23-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="d7a23-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-258">TextBox</span></span>|  
|<span data-ttu-id="d7a23-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="d7a23-259">Timer</span></span>|  
|<span data-ttu-id="d7a23-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="d7a23-260">Toolbar</span></span>|  
|<span data-ttu-id="d7a23-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d7a23-261">ToolTip</span></span>|  
|<span data-ttu-id="d7a23-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="d7a23-262">TrackBar</span></span>|  
|<span data-ttu-id="d7a23-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="d7a23-263">TreeView</span></span>|  
|<span data-ttu-id="d7a23-264">Vscrollbar —</span><span class="sxs-lookup"><span data-stu-id="d7a23-264">VscrollBar</span></span>|  
|<span data-ttu-id="d7a23-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="d7a23-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="d7a23-266">Następujące sterowniki są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko za pośrednictwem ich obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7a23-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="d7a23-267">Niektóre funkcje mogą nie być dostępne.</span><span class="sxs-lookup"><span data-stu-id="d7a23-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="d7a23-268">Nazwa formantu</span><span class="sxs-lookup"><span data-stu-id="d7a23-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="d7a23-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="d7a23-269">BindingSource</span></span>|  
|<span data-ttu-id="d7a23-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d7a23-270">DataGrid</span></span>|  
|<span data-ttu-id="d7a23-271">Formant DataGridView</span><span class="sxs-lookup"><span data-stu-id="d7a23-271">DataGridView</span></span>|  
|<span data-ttu-id="d7a23-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="d7a23-272">DataNavigator</span></span>|  
|<span data-ttu-id="d7a23-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="d7a23-273">DomainUpDown</span></span>|  
|<span data-ttu-id="d7a23-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="d7a23-274">ErrorProvider</span></span>|  
|<span data-ttu-id="d7a23-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d7a23-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="d7a23-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="d7a23-276">Form</span></span>|  
|<span data-ttu-id="d7a23-277">Linklabel —</span><span class="sxs-lookup"><span data-stu-id="d7a23-277">LinkLabel</span></span>|  
|<span data-ttu-id="d7a23-278">Helpprovider —</span><span class="sxs-lookup"><span data-stu-id="d7a23-278">HelpProvider</span></span>|  
|<span data-ttu-id="d7a23-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="d7a23-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="d7a23-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="d7a23-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="d7a23-281">NumericUpDown</span></span>|  
|<span data-ttu-id="d7a23-282">Panel</span><span class="sxs-lookup"><span data-stu-id="d7a23-282">Panel</span></span>|  
|<span data-ttu-id="d7a23-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="d7a23-283">PictureBox</span></span>|  
|<span data-ttu-id="d7a23-284">PrintDocument —</span><span class="sxs-lookup"><span data-stu-id="d7a23-284">PrintDocument</span></span>|  
|<span data-ttu-id="d7a23-285">Printpreview — formant</span><span class="sxs-lookup"><span data-stu-id="d7a23-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="d7a23-286">Printpreview — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="d7a23-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="d7a23-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="d7a23-287">PropertyGrid</span></span>|  
|<span data-ttu-id="d7a23-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="d7a23-288">UserControl</span></span>|  
|<span data-ttu-id="d7a23-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d7a23-289">ToolStrip</span></span>|  
|<span data-ttu-id="d7a23-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d7a23-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="d7a23-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="d7a23-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="d7a23-292">Podziału</span><span class="sxs-lookup"><span data-stu-id="d7a23-292">Splitter</span></span>|  
|<span data-ttu-id="d7a23-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="d7a23-293">RaftingContainer</span></span>|  
|<span data-ttu-id="d7a23-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="d7a23-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7a23-295">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7a23-295">See Also</span></span>  
 [<span data-ttu-id="d7a23-296">Typy formantów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d7a23-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
