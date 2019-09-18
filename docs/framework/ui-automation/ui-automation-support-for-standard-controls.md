---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 6cbf31c8a1cdf6e853e56445d22f4a7513bd1859
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041997"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="ff3de-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów</span><span class="sxs-lookup"><span data-stu-id="ff3de-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="ff3de-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ff3de-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ff3de-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ff3de-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ff3de-105">Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsłudze standardowych formantów w aplikacjach utworzonych [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]dla środowisk, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ff3de-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="ff3de-106">Kontrolki Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="ff3de-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="ff3de-107">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy sterujące, które dostarczają informacji lub pomocy technicznej dla interakcji użytkownika, mają pełną [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługę natywną.</span><span class="sxs-lookup"><span data-stu-id="ff3de-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="ff3de-108">Inne elementy, takie jak panele, nie są widoczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu.</span><span class="sxs-lookup"><span data-stu-id="ff3de-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="ff3de-109">Kontrolki Win32</span><span class="sxs-lookup"><span data-stu-id="ff3de-109">Win32 Controls</span></span>  
 <span data-ttu-id="ff3de-110">Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formantów jest [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] narażonych przez dostawców po stronie klienta w UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="ff3de-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="ff3de-111">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ff3de-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="ff3de-112">Pełna pomoc techniczna jest świadczona tylko dla formantów z wersji 6 programu ComCtrl32. dll (dostępne [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] z i nowsze).</span><span class="sxs-lookup"><span data-stu-id="ff3de-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="ff3de-113">Obsługiwane są następujące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ff3de-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="ff3de-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="ff3de-114">Class name</span></span>|<span data-ttu-id="ff3de-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="ff3de-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="ff3de-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-116">Button</span></span>|<span data-ttu-id="ff3de-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-117">Button</span></span>|  
|<span data-ttu-id="ff3de-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-118">Button</span></span>|<span data-ttu-id="ff3de-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ff3de-119">RadioButton</span></span>|  
|<span data-ttu-id="ff3de-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-120">Button</span></span>|<span data-ttu-id="ff3de-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="ff3de-121">Group</span></span>|  
|<span data-ttu-id="ff3de-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-122">Button</span></span>|<span data-ttu-id="ff3de-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-123">CheckBox</span></span>|  
|<span data-ttu-id="ff3de-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-124">Button</span></span>|<span data-ttu-id="ff3de-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="ff3de-125">Hyperlink</span></span>|  
|<span data-ttu-id="ff3de-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-126">Button</span></span>|<span data-ttu-id="ff3de-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="ff3de-127">SplitButton</span></span>|  
|<span data-ttu-id="ff3de-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-128">Button</span></span>|<span data-ttu-id="ff3de-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-129">CheckBox</span></span>|  
|<span data-ttu-id="ff3de-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="ff3de-130">ComboBoxEx32</span></span>|<span data-ttu-id="ff3de-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-131">ComboBox</span></span>|  
|<span data-ttu-id="ff3de-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-132">ComboBox</span></span>|<span data-ttu-id="ff3de-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-133">ComboBox</span></span>|  
|<span data-ttu-id="ff3de-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="ff3de-134">Edit</span></span>|<span data-ttu-id="ff3de-135">dokument</span><span class="sxs-lookup"><span data-stu-id="ff3de-135">Document</span></span>|  
|<span data-ttu-id="ff3de-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="ff3de-136">Edit</span></span>|<span data-ttu-id="ff3de-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="ff3de-137">Edit</span></span>|  
|<span data-ttu-id="ff3de-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="ff3de-138">SysLink</span></span>|<span data-ttu-id="ff3de-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="ff3de-139">Hyperlink</span></span>|  
|<span data-ttu-id="ff3de-140">Static</span><span class="sxs-lookup"><span data-stu-id="ff3de-140">Static</span></span>|<span data-ttu-id="ff3de-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="ff3de-141">Text</span></span>|  
|<span data-ttu-id="ff3de-142">Static</span><span class="sxs-lookup"><span data-stu-id="ff3de-142">Static</span></span>|<span data-ttu-id="ff3de-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="ff3de-143">Image</span></span>|  
|<span data-ttu-id="ff3de-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="ff3de-144">SysIPAddress32</span></span>|<span data-ttu-id="ff3de-145">Celnej</span><span class="sxs-lookup"><span data-stu-id="ff3de-145">Custom</span></span>|  
|<span data-ttu-id="ff3de-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="ff3de-146">SysHeader32</span></span>|<span data-ttu-id="ff3de-147">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="ff3de-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="ff3de-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="ff3de-148">SysListView32</span></span>|<span data-ttu-id="ff3de-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="ff3de-149">DataGrid</span></span>|  
|<span data-ttu-id="ff3de-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="ff3de-150">SysListView32</span></span>|<span data-ttu-id="ff3de-151">Lista</span><span class="sxs-lookup"><span data-stu-id="ff3de-151">List</span></span>|  
|<span data-ttu-id="ff3de-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-152">ListBox</span></span>|<span data-ttu-id="ff3de-153">Lista</span><span class="sxs-lookup"><span data-stu-id="ff3de-153">List</span></span>|  
|<span data-ttu-id="ff3de-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-154">ListBox</span></span>|<span data-ttu-id="ff3de-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="ff3de-155">ListItem</span></span>|  
|<span data-ttu-id="ff3de-156">#32768</span><span class="sxs-lookup"><span data-stu-id="ff3de-156">#32768</span></span>|<span data-ttu-id="ff3de-157">Menu</span><span class="sxs-lookup"><span data-stu-id="ff3de-157">Menu</span></span>|  
|<span data-ttu-id="ff3de-158">#32768</span><span class="sxs-lookup"><span data-stu-id="ff3de-158">#32768</span></span>|<span data-ttu-id="ff3de-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="ff3de-159">MenuItem</span></span>|  
|<span data-ttu-id="ff3de-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="ff3de-160">msctls_progress32</span></span>|<span data-ttu-id="ff3de-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="ff3de-161">ProgressBar</span></span>|  
|<span data-ttu-id="ff3de-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="ff3de-162">RichEdit</span></span>|<span data-ttu-id="ff3de-163">dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ff3de-163">Document.</span></span> <span data-ttu-id="ff3de-164">Zobacz Uwaga.</span><span class="sxs-lookup"><span data-stu-id="ff3de-164">See note.</span></span>|  
|<span data-ttu-id="ff3de-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="ff3de-165">RichEdit20A</span></span>|<span data-ttu-id="ff3de-166">dokument</span><span class="sxs-lookup"><span data-stu-id="ff3de-166">Document</span></span>|  
|<span data-ttu-id="ff3de-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="ff3de-167">RichEdit20W</span></span>|<span data-ttu-id="ff3de-168">dokument</span><span class="sxs-lookup"><span data-stu-id="ff3de-168">Document</span></span>|  
|<span data-ttu-id="ff3de-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="ff3de-169">RichEdit50W</span></span>|<span data-ttu-id="ff3de-170">dokument</span><span class="sxs-lookup"><span data-stu-id="ff3de-170">Document</span></span>|  
|<span data-ttu-id="ff3de-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="ff3de-171">ScrollBar</span></span>|<span data-ttu-id="ff3de-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="ff3de-172">Slider</span></span>|  
|<span data-ttu-id="ff3de-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="ff3de-173">msctls_trackbar32</span></span>|<span data-ttu-id="ff3de-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="ff3de-174">Slider</span></span>|  
|<span data-ttu-id="ff3de-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="ff3de-175">msctls_updown32</span></span>|<span data-ttu-id="ff3de-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="ff3de-176">Spinner</span></span>|  
|<span data-ttu-id="ff3de-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="ff3de-177">msctls_statusbar32</span></span>|<span data-ttu-id="ff3de-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="ff3de-178">StatusBar</span></span>|  
|<span data-ttu-id="ff3de-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="ff3de-179">SysTabControl32</span></span>|<span data-ttu-id="ff3de-180">Tab</span><span class="sxs-lookup"><span data-stu-id="ff3de-180">Tab</span></span>|  
|<span data-ttu-id="ff3de-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="ff3de-181">SysTabControl32</span></span>|<span data-ttu-id="ff3de-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="ff3de-182">TabItem</span></span>|  
|<span data-ttu-id="ff3de-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ff3de-183">ToolbarWindow32</span></span>|<span data-ttu-id="ff3de-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="ff3de-184">ToolBar</span></span>|  
|<span data-ttu-id="ff3de-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ff3de-185">ToolbarWindow32</span></span>|<span data-ttu-id="ff3de-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="ff3de-186">MenuItem</span></span>|  
|<span data-ttu-id="ff3de-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ff3de-187">ToolbarWindow32</span></span>|<span data-ttu-id="ff3de-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-188">Button</span></span>|  
|<span data-ttu-id="ff3de-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ff3de-189">ToolbarWindow32</span></span>|<span data-ttu-id="ff3de-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-190">CheckBox</span></span>|  
|<span data-ttu-id="ff3de-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ff3de-191">ToolbarWindow32</span></span>|<span data-ttu-id="ff3de-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ff3de-192">RadioButton</span></span>|  
|<span data-ttu-id="ff3de-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ff3de-193">ToolbarWindow32</span></span>|<span data-ttu-id="ff3de-194">Separator</span><span class="sxs-lookup"><span data-stu-id="ff3de-194">Separator</span></span>|  
|<span data-ttu-id="ff3de-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="ff3de-195">tooltips_class32</span></span>|<span data-ttu-id="ff3de-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ff3de-196">ToolTip</span></span>|  
|<span data-ttu-id="ff3de-197">#32774</span><span class="sxs-lookup"><span data-stu-id="ff3de-197">#32774</span></span>|<span data-ttu-id="ff3de-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ff3de-198">ToolTip</span></span>|  
|<span data-ttu-id="ff3de-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="ff3de-199">ReBarWindow32</span></span>|<span data-ttu-id="ff3de-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="ff3de-200">Toolbar</span></span>|  
|<span data-ttu-id="ff3de-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="ff3de-201">SysTreeView32</span></span>|<span data-ttu-id="ff3de-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="ff3de-202">Tree</span></span>|  
|<span data-ttu-id="ff3de-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="ff3de-203">SysTreeView32</span></span>|<span data-ttu-id="ff3de-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="ff3de-204">TreeItem</span></span>|  
  
 <span data-ttu-id="ff3de-205">**Uwaga** Formant RichEdit jest obsługiwany tylko w przypadku wersji dostarczonych z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] programem (w biblioteki riched20. dll w wersji 3,1 lub nowszej oraz MsftEdit. dll w wersji 4,1 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="ff3de-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="ff3de-206">Następujące kontrolki nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ff3de-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="ff3de-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="ff3de-207">Class name</span></span>|<span data-ttu-id="ff3de-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="ff3de-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="ff3de-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="ff3de-209">SysAnimate32</span></span>|<span data-ttu-id="ff3de-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="ff3de-210">Image</span></span>|  
|<span data-ttu-id="ff3de-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="ff3de-211">SysPager</span></span>|<span data-ttu-id="ff3de-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="ff3de-212">Spinner</span></span>|  
|<span data-ttu-id="ff3de-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="ff3de-213">SysDateTimePick32</span></span>|<span data-ttu-id="ff3de-214">Celnej</span><span class="sxs-lookup"><span data-stu-id="ff3de-214">Custom</span></span>|  
|<span data-ttu-id="ff3de-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="ff3de-215">SysMonthCal32</span></span>|<span data-ttu-id="ff3de-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="ff3de-216">Calendar</span></span>|  
|<span data-ttu-id="ff3de-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="ff3de-217">MS_WINNOTE</span></span>|<span data-ttu-id="ff3de-218">Wyowietlon</span><span class="sxs-lookup"><span data-stu-id="ff3de-218">Tooltip</span></span>|  
|<span data-ttu-id="ff3de-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="ff3de-219">VBBubble</span></span>|<span data-ttu-id="ff3de-220">Wyowietlon</span><span class="sxs-lookup"><span data-stu-id="ff3de-220">Tooltip</span></span>|  
|<span data-ttu-id="ff3de-221">Pasek przewijania (używany jako formant autonomiczny)</span><span class="sxs-lookup"><span data-stu-id="ff3de-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="ff3de-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="ff3de-222">Slider</span></span>|  
|<span data-ttu-id="ff3de-223">Podsiatka</span><span class="sxs-lookup"><span data-stu-id="ff3de-223">SuperGrid</span></span>|<span data-ttu-id="ff3de-224">Celnej</span><span class="sxs-lookup"><span data-stu-id="ff3de-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="ff3de-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ff3de-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="ff3de-226">Kontrolki Windows Forms są dostępne [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dla dostawców po stronie klienta w UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="ff3de-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="ff3de-227">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ff3de-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="ff3de-228">Zazwyczaj formanty Windows Forms, które są otokami zarządzanymi [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] dla wspólnych formantów, są [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługiwane przez program.</span><span class="sxs-lookup"><span data-stu-id="ff3de-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="ff3de-229">Obsługiwane są następujące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ff3de-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="ff3de-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="ff3de-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="ff3de-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="ff3de-231">Button</span></span>|  
|<span data-ttu-id="ff3de-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-232">CheckBox</span></span>|  
|<span data-ttu-id="ff3de-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-233">CheckedListBox</span></span>|  
|<span data-ttu-id="ff3de-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="ff3de-234">ColorDialog</span></span>|  
|<span data-ttu-id="ff3de-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-235">ComboBox</span></span>|  
|<span data-ttu-id="ff3de-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="ff3de-236">FolderBrowser</span></span>|  
|<span data-ttu-id="ff3de-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="ff3de-237">FontDialog</span></span>|  
|<span data-ttu-id="ff3de-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-238">GroupBox</span></span>|  
|<span data-ttu-id="ff3de-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="ff3de-239">HscrollBar</span></span>|  
|<span data-ttu-id="ff3de-240">Obrazów</span><span class="sxs-lookup"><span data-stu-id="ff3de-240">ImageList</span></span>|  
|<span data-ttu-id="ff3de-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="ff3de-241">Label</span></span>|  
|<span data-ttu-id="ff3de-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-242">ListBox</span></span>|  
|<span data-ttu-id="ff3de-243">ListView</span><span class="sxs-lookup"><span data-stu-id="ff3de-243">ListView</span></span>|  
|<span data-ttu-id="ff3de-244">MainMenu/</span><span class="sxs-lookup"><span data-stu-id="ff3de-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="ff3de-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="ff3de-245">MonthCalendar</span></span>|  
|<span data-ttu-id="ff3de-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="ff3de-246">NotifyIcon</span></span>|  
|<span data-ttu-id="ff3de-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="ff3de-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="ff3de-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="ff3de-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="ff3de-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="ff3de-249">PrintDialog</span></span>|  
|<span data-ttu-id="ff3de-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="ff3de-250">ProgressBar</span></span>|  
|<span data-ttu-id="ff3de-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ff3de-251">RadioButton</span></span>|  
|<span data-ttu-id="ff3de-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-252">RichTextBox</span></span>|  
|<span data-ttu-id="ff3de-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="ff3de-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="ff3de-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="ff3de-254">ScrollableControl</span></span>|  
|<span data-ttu-id="ff3de-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="ff3de-255">SoundPlayer</span></span>|  
|<span data-ttu-id="ff3de-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="ff3de-256">StatusBar</span></span>|  
|<span data-ttu-id="ff3de-257">Elementy TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="ff3de-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="ff3de-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-258">TextBox</span></span>|  
|<span data-ttu-id="ff3de-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="ff3de-259">Timer</span></span>|  
|<span data-ttu-id="ff3de-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="ff3de-260">Toolbar</span></span>|  
|<span data-ttu-id="ff3de-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ff3de-261">ToolTip</span></span>|  
|<span data-ttu-id="ff3de-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="ff3de-262">TrackBar</span></span>|  
|<span data-ttu-id="ff3de-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="ff3de-263">TreeView</span></span>|  
|<span data-ttu-id="ff3de-264">VScrollBar —</span><span class="sxs-lookup"><span data-stu-id="ff3de-264">VscrollBar</span></span>|  
|<span data-ttu-id="ff3de-265">Kontrol</span><span class="sxs-lookup"><span data-stu-id="ff3de-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="ff3de-266">Następujące kontrolki są dostępne [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko w ramach obsługi usługi Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="ff3de-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="ff3de-267">Niektóre funkcje mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="ff3de-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="ff3de-268">Nazwa kontrolki</span><span class="sxs-lookup"><span data-stu-id="ff3de-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="ff3de-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="ff3de-269">BindingSource</span></span>|  
|<span data-ttu-id="ff3de-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="ff3de-270">DataGrid</span></span>|  
|<span data-ttu-id="ff3de-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="ff3de-271">DataGridView</span></span>|  
|<span data-ttu-id="ff3de-272">Nawigator datanavigator</span><span class="sxs-lookup"><span data-stu-id="ff3de-272">DataNavigator</span></span>|  
|<span data-ttu-id="ff3de-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="ff3de-273">DomainUpDown</span></span>|  
|<span data-ttu-id="ff3de-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="ff3de-274">ErrorProvider</span></span>|  
|<span data-ttu-id="ff3de-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ff3de-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="ff3de-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="ff3de-276">Form</span></span>|  
|<span data-ttu-id="ff3de-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="ff3de-277">LinkLabel</span></span>|  
|<span data-ttu-id="ff3de-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="ff3de-278">HelpProvider</span></span>|  
|<span data-ttu-id="ff3de-279">Formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="ff3de-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="ff3de-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="ff3de-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="ff3de-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="ff3de-281">NumericUpDown</span></span>|  
|<span data-ttu-id="ff3de-282">Panel</span><span class="sxs-lookup"><span data-stu-id="ff3de-282">Panel</span></span>|  
|<span data-ttu-id="ff3de-283">Elemencie</span><span class="sxs-lookup"><span data-stu-id="ff3de-283">PictureBox</span></span>|  
|<span data-ttu-id="ff3de-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="ff3de-284">PrintDocument</span></span>|  
|<span data-ttu-id="ff3de-285">PrintPreview — kontrolka</span><span class="sxs-lookup"><span data-stu-id="ff3de-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="ff3de-286">PrintPreview — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="ff3de-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="ff3de-287">Używany</span><span class="sxs-lookup"><span data-stu-id="ff3de-287">PropertyGrid</span></span>|  
|<span data-ttu-id="ff3de-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="ff3de-288">UserControl</span></span>|  
|<span data-ttu-id="ff3de-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ff3de-289">ToolStrip</span></span>|  
|<span data-ttu-id="ff3de-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ff3de-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="ff3de-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="ff3de-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="ff3de-292">Dzielnik</span><span class="sxs-lookup"><span data-stu-id="ff3de-292">Splitter</span></span>|  
|<span data-ttu-id="ff3de-293">Elemencie RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="ff3de-293">RaftingContainer</span></span>|  
|<span data-ttu-id="ff3de-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="ff3de-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff3de-295">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff3de-295">See also</span></span>

- [<span data-ttu-id="ff3de-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="ff3de-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
