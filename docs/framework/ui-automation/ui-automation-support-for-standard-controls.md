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
ms.openlocfilehash: cbfb640a068a2c1178d321480ee3a112db07b6ac
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463895"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="6f933-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek</span><span class="sxs-lookup"><span data-stu-id="6f933-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="6f933-103">Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6f933-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6f933-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="6f933-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6f933-105">Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla standardowych kontrolek w aplikacjach przeznaczonych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] struktur.</span><span class="sxs-lookup"><span data-stu-id="6f933-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="6f933-106">Formanty programu Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="6f933-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="6f933-107">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy kontroli, które zapewniają informacje lub pomocy technicznej do interakcji z użytkownikiem ma pełne natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f933-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="6f933-108">Nie są widoczne dla innych elementów, takich jak paneli, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f933-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="6f933-109">Kontrolki Win32</span><span class="sxs-lookup"><span data-stu-id="6f933-109">Win32 Controls</span></span>  
 <span data-ttu-id="6f933-110">Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="6f933-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="6f933-111">Ten zestaw jest automatycznie rejestrowane do użycia przy użyciu automatyzacji interfejsu użytkownika aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="6f933-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="6f933-112">Pełna pomoc techniczna jest dostępna tylko w przypadku kontrolek z ComCtrl32.dll w wersji 6 (udostępniono [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="6f933-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="6f933-113">Następujące elementy sterujące są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6f933-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="6f933-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="6f933-114">Class name</span></span>|<span data-ttu-id="6f933-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="6f933-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="6f933-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-116">Button</span></span>|<span data-ttu-id="6f933-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-117">Button</span></span>|  
|<span data-ttu-id="6f933-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-118">Button</span></span>|<span data-ttu-id="6f933-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6f933-119">RadioButton</span></span>|  
|<span data-ttu-id="6f933-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-120">Button</span></span>|<span data-ttu-id="6f933-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="6f933-121">Group</span></span>|  
|<span data-ttu-id="6f933-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-122">Button</span></span>|<span data-ttu-id="6f933-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6f933-123">CheckBox</span></span>|  
|<span data-ttu-id="6f933-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-124">Button</span></span>|<span data-ttu-id="6f933-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="6f933-125">Hyperlink</span></span>|  
|<span data-ttu-id="6f933-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-126">Button</span></span>|<span data-ttu-id="6f933-127">Przycisk podziału</span><span class="sxs-lookup"><span data-stu-id="6f933-127">SplitButton</span></span>|  
|<span data-ttu-id="6f933-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-128">Button</span></span>|<span data-ttu-id="6f933-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6f933-129">CheckBox</span></span>|  
|<span data-ttu-id="6f933-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="6f933-130">ComboBoxEx32</span></span>|<span data-ttu-id="6f933-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6f933-131">ComboBox</span></span>|  
|<span data-ttu-id="6f933-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6f933-132">ComboBox</span></span>|<span data-ttu-id="6f933-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6f933-133">ComboBox</span></span>|  
|<span data-ttu-id="6f933-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="6f933-134">Edit</span></span>|<span data-ttu-id="6f933-135">dokument</span><span class="sxs-lookup"><span data-stu-id="6f933-135">Document</span></span>|  
|<span data-ttu-id="6f933-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="6f933-136">Edit</span></span>|<span data-ttu-id="6f933-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="6f933-137">Edit</span></span>|  
|<span data-ttu-id="6f933-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="6f933-138">SysLink</span></span>|<span data-ttu-id="6f933-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="6f933-139">Hyperlink</span></span>|  
|<span data-ttu-id="6f933-140">Static</span><span class="sxs-lookup"><span data-stu-id="6f933-140">Static</span></span>|<span data-ttu-id="6f933-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="6f933-141">Text</span></span>|  
|<span data-ttu-id="6f933-142">Static</span><span class="sxs-lookup"><span data-stu-id="6f933-142">Static</span></span>|<span data-ttu-id="6f933-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="6f933-143">Image</span></span>|  
|<span data-ttu-id="6f933-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="6f933-144">SysIPAddress32</span></span>|<span data-ttu-id="6f933-145">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6f933-145">Custom</span></span>|  
|<span data-ttu-id="6f933-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="6f933-146">SysHeader32</span></span>|<span data-ttu-id="6f933-147">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="6f933-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="6f933-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="6f933-148">SysListView32</span></span>|<span data-ttu-id="6f933-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="6f933-149">DataGrid</span></span>|  
|<span data-ttu-id="6f933-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="6f933-150">SysListView32</span></span>|<span data-ttu-id="6f933-151">Lista</span><span class="sxs-lookup"><span data-stu-id="6f933-151">List</span></span>|  
|<span data-ttu-id="6f933-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="6f933-152">ListBox</span></span>|<span data-ttu-id="6f933-153">Lista</span><span class="sxs-lookup"><span data-stu-id="6f933-153">List</span></span>|  
|<span data-ttu-id="6f933-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="6f933-154">ListBox</span></span>|<span data-ttu-id="6f933-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="6f933-155">ListItem</span></span>|  
|<span data-ttu-id="6f933-156">#32768</span><span class="sxs-lookup"><span data-stu-id="6f933-156">#32768</span></span>|<span data-ttu-id="6f933-157">Menu</span><span class="sxs-lookup"><span data-stu-id="6f933-157">Menu</span></span>|  
|<span data-ttu-id="6f933-158">#32768</span><span class="sxs-lookup"><span data-stu-id="6f933-158">#32768</span></span>|<span data-ttu-id="6f933-159">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="6f933-159">MenuItem</span></span>|  
|<span data-ttu-id="6f933-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="6f933-160">msctls_progress32</span></span>|<span data-ttu-id="6f933-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6f933-161">ProgressBar</span></span>|  
|<span data-ttu-id="6f933-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="6f933-162">RichEdit</span></span>|<span data-ttu-id="6f933-163">dokument.</span><span class="sxs-lookup"><span data-stu-id="6f933-163">Document.</span></span> <span data-ttu-id="6f933-164">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="6f933-164">See note.</span></span>|  
|<span data-ttu-id="6f933-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="6f933-165">RichEdit20A</span></span>|<span data-ttu-id="6f933-166">dokument</span><span class="sxs-lookup"><span data-stu-id="6f933-166">Document</span></span>|  
|<span data-ttu-id="6f933-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="6f933-167">RichEdit20W</span></span>|<span data-ttu-id="6f933-168">dokument</span><span class="sxs-lookup"><span data-stu-id="6f933-168">Document</span></span>|  
|<span data-ttu-id="6f933-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="6f933-169">RichEdit50W</span></span>|<span data-ttu-id="6f933-170">dokument</span><span class="sxs-lookup"><span data-stu-id="6f933-170">Document</span></span>|  
|<span data-ttu-id="6f933-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="6f933-171">ScrollBar</span></span>|<span data-ttu-id="6f933-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="6f933-172">Slider</span></span>|  
|<span data-ttu-id="6f933-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="6f933-173">msctls_trackbar32</span></span>|<span data-ttu-id="6f933-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="6f933-174">Slider</span></span>|  
|<span data-ttu-id="6f933-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="6f933-175">msctls_updown32</span></span>|<span data-ttu-id="6f933-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="6f933-176">Spinner</span></span>|  
|<span data-ttu-id="6f933-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="6f933-177">msctls_statusbar32</span></span>|<span data-ttu-id="6f933-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="6f933-178">StatusBar</span></span>|  
|<span data-ttu-id="6f933-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="6f933-179">SysTabControl32</span></span>|<span data-ttu-id="6f933-180">Tab</span><span class="sxs-lookup"><span data-stu-id="6f933-180">Tab</span></span>|  
|<span data-ttu-id="6f933-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="6f933-181">SysTabControl32</span></span>|<span data-ttu-id="6f933-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="6f933-182">TabItem</span></span>|  
|<span data-ttu-id="6f933-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6f933-183">ToolbarWindow32</span></span>|<span data-ttu-id="6f933-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="6f933-184">ToolBar</span></span>|  
|<span data-ttu-id="6f933-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6f933-185">ToolbarWindow32</span></span>|<span data-ttu-id="6f933-186">Element MenuItem</span><span class="sxs-lookup"><span data-stu-id="6f933-186">MenuItem</span></span>|  
|<span data-ttu-id="6f933-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6f933-187">ToolbarWindow32</span></span>|<span data-ttu-id="6f933-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-188">Button</span></span>|  
|<span data-ttu-id="6f933-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6f933-189">ToolbarWindow32</span></span>|<span data-ttu-id="6f933-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6f933-190">CheckBox</span></span>|  
|<span data-ttu-id="6f933-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6f933-191">ToolbarWindow32</span></span>|<span data-ttu-id="6f933-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6f933-192">RadioButton</span></span>|  
|<span data-ttu-id="6f933-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6f933-193">ToolbarWindow32</span></span>|<span data-ttu-id="6f933-194">Separator</span><span class="sxs-lookup"><span data-stu-id="6f933-194">Separator</span></span>|  
|<span data-ttu-id="6f933-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="6f933-195">tooltips_class32</span></span>|<span data-ttu-id="6f933-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6f933-196">ToolTip</span></span>|  
|<span data-ttu-id="6f933-197">#32774</span><span class="sxs-lookup"><span data-stu-id="6f933-197">#32774</span></span>|<span data-ttu-id="6f933-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6f933-198">ToolTip</span></span>|  
|<span data-ttu-id="6f933-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="6f933-199">ReBarWindow32</span></span>|<span data-ttu-id="6f933-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="6f933-200">Toolbar</span></span>|  
|<span data-ttu-id="6f933-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="6f933-201">SysTreeView32</span></span>|<span data-ttu-id="6f933-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="6f933-202">Tree</span></span>|  
|<span data-ttu-id="6f933-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="6f933-203">SysTreeView32</span></span>|<span data-ttu-id="6f933-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="6f933-204">TreeItem</span></span>|  
  
 <span data-ttu-id="6f933-205">**Uwaga** kontrolki RichEdit jest obsługiwana tylko w przypadku wersji są dostarczane z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (w wersji biblioteki RichEd20.dll 3.1 lub nowszy i MsftEdit.dll w wersji 4.1 lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="6f933-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="6f933-206">Następujące elementy sterujące są nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6f933-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="6f933-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="6f933-207">Class name</span></span>|<span data-ttu-id="6f933-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="6f933-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="6f933-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="6f933-209">SysAnimate32</span></span>|<span data-ttu-id="6f933-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="6f933-210">Image</span></span>|  
|<span data-ttu-id="6f933-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="6f933-211">SysPager</span></span>|<span data-ttu-id="6f933-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="6f933-212">Spinner</span></span>|  
|<span data-ttu-id="6f933-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="6f933-213">SysDateTimePick32</span></span>|<span data-ttu-id="6f933-214">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6f933-214">Custom</span></span>|  
|<span data-ttu-id="6f933-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="6f933-215">SysMonthCal32</span></span>|<span data-ttu-id="6f933-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="6f933-216">Calendar</span></span>|  
|<span data-ttu-id="6f933-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="6f933-217">MS_WINNOTE</span></span>|<span data-ttu-id="6f933-218">Etykietki narzędzi</span><span class="sxs-lookup"><span data-stu-id="6f933-218">Tooltip</span></span>|  
|<span data-ttu-id="6f933-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="6f933-219">VBBubble</span></span>|<span data-ttu-id="6f933-220">Etykietki narzędzi</span><span class="sxs-lookup"><span data-stu-id="6f933-220">Tooltip</span></span>|  
|<span data-ttu-id="6f933-221">Pasek przewijania (jeśli jest używana jako kontrolkę autonomiczne)</span><span class="sxs-lookup"><span data-stu-id="6f933-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="6f933-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="6f933-222">Slider</span></span>|  
|<span data-ttu-id="6f933-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="6f933-223">SuperGrid</span></span>|<span data-ttu-id="6f933-224">Niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6f933-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="6f933-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6f933-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="6f933-226">Kontrolek formularzy Windows Forms są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="6f933-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="6f933-227">Ten zestaw jest automatycznie rejestrowane do użycia przy użyciu automatyzacji interfejsu użytkownika aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="6f933-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="6f933-228">Zazwyczaj formantów Windows Forms, które są zarządzane otoki [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] wspólnych formantów są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f933-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="6f933-229">Następujące elementy sterujące są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6f933-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="6f933-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="6f933-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="6f933-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="6f933-231">Button</span></span>|  
|<span data-ttu-id="6f933-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6f933-232">CheckBox</span></span>|  
|<span data-ttu-id="6f933-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="6f933-233">CheckedListBox</span></span>|  
|<span data-ttu-id="6f933-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="6f933-234">ColorDialog</span></span>|  
|<span data-ttu-id="6f933-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6f933-235">ComboBox</span></span>|  
|<span data-ttu-id="6f933-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="6f933-236">FolderBrowser</span></span>|  
|<span data-ttu-id="6f933-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="6f933-237">FontDialog</span></span>|  
|<span data-ttu-id="6f933-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="6f933-238">GroupBox</span></span>|  
|<span data-ttu-id="6f933-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="6f933-239">HscrollBar</span></span>|  
|<span data-ttu-id="6f933-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="6f933-240">ImageList</span></span>|  
|<span data-ttu-id="6f933-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="6f933-241">Label</span></span>|  
|<span data-ttu-id="6f933-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="6f933-242">ListBox</span></span>|  
|<span data-ttu-id="6f933-243">ListView</span><span class="sxs-lookup"><span data-stu-id="6f933-243">ListView</span></span>|  
|<span data-ttu-id="6f933-244">MainMenu — informacje o/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="6f933-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="6f933-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="6f933-245">MonthCalendar</span></span>|  
|<span data-ttu-id="6f933-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="6f933-246">NotifyIcon</span></span>|  
|<span data-ttu-id="6f933-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="6f933-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="6f933-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="6f933-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="6f933-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="6f933-249">PrintDialog</span></span>|  
|<span data-ttu-id="6f933-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6f933-250">ProgressBar</span></span>|  
|<span data-ttu-id="6f933-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6f933-251">RadioButton</span></span>|  
|<span data-ttu-id="6f933-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="6f933-252">RichTextBox</span></span>|  
|<span data-ttu-id="6f933-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="6f933-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="6f933-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="6f933-254">ScrollableControl</span></span>|  
|<span data-ttu-id="6f933-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="6f933-255">SoundPlayer</span></span>|  
|<span data-ttu-id="6f933-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="6f933-256">StatusBar</span></span>|  
|<span data-ttu-id="6f933-257">TabControl — / TabPage —</span><span class="sxs-lookup"><span data-stu-id="6f933-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="6f933-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="6f933-258">TextBox</span></span>|  
|<span data-ttu-id="6f933-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="6f933-259">Timer</span></span>|  
|<span data-ttu-id="6f933-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="6f933-260">Toolbar</span></span>|  
|<span data-ttu-id="6f933-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6f933-261">ToolTip</span></span>|  
|<span data-ttu-id="6f933-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="6f933-262">TrackBar</span></span>|  
|<span data-ttu-id="6f933-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="6f933-263">TreeView</span></span>|  
|<span data-ttu-id="6f933-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="6f933-264">VscrollBar</span></span>|  
|<span data-ttu-id="6f933-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="6f933-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="6f933-266">Następujące elementy sterujące są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] wyłącznie za pośrednictwem ich obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f933-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="6f933-267">Niektóre funkcje mogą nie być dostępne.</span><span class="sxs-lookup"><span data-stu-id="6f933-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="6f933-268">Nazwa kontrolki</span><span class="sxs-lookup"><span data-stu-id="6f933-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="6f933-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="6f933-269">BindingSource</span></span>|  
|<span data-ttu-id="6f933-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="6f933-270">DataGrid</span></span>|  
|<span data-ttu-id="6f933-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="6f933-271">DataGridView</span></span>|  
|<span data-ttu-id="6f933-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="6f933-272">DataNavigator</span></span>|  
|<span data-ttu-id="6f933-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="6f933-273">DomainUpDown</span></span>|  
|<span data-ttu-id="6f933-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="6f933-274">ErrorProvider</span></span>|  
|<span data-ttu-id="6f933-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6f933-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="6f933-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="6f933-276">Form</span></span>|  
|<span data-ttu-id="6f933-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6f933-277">LinkLabel</span></span>|  
|<span data-ttu-id="6f933-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="6f933-278">HelpProvider</span></span>|  
|<span data-ttu-id="6f933-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="6f933-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="6f933-280">MenuStrip — / ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="6f933-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="6f933-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="6f933-281">NumericUpDown</span></span>|  
|<span data-ttu-id="6f933-282">Panel</span><span class="sxs-lookup"><span data-stu-id="6f933-282">Panel</span></span>|  
|<span data-ttu-id="6f933-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="6f933-283">PictureBox</span></span>|  
|<span data-ttu-id="6f933-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="6f933-284">PrintDocument</span></span>|  
|<span data-ttu-id="6f933-285">Printpreview — formant</span><span class="sxs-lookup"><span data-stu-id="6f933-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="6f933-286">Okno dialogowe printpreview —</span><span class="sxs-lookup"><span data-stu-id="6f933-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="6f933-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="6f933-287">PropertyGrid</span></span>|  
|<span data-ttu-id="6f933-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="6f933-288">UserControl</span></span>|  
|<span data-ttu-id="6f933-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="6f933-289">ToolStrip</span></span>|  
|<span data-ttu-id="6f933-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6f933-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="6f933-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="6f933-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="6f933-292">Rozdzielacz</span><span class="sxs-lookup"><span data-stu-id="6f933-292">Splitter</span></span>|  
|<span data-ttu-id="6f933-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="6f933-293">RaftingContainer</span></span>|  
|<span data-ttu-id="6f933-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="6f933-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f933-295">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f933-295">See Also</span></span>  
 [<span data-ttu-id="6f933-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="6f933-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
