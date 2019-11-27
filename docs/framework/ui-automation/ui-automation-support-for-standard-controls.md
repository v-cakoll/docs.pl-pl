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
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="931d2-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów</span><span class="sxs-lookup"><span data-stu-id="931d2-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="931d2-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="931d2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="931d2-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="931d2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="931d2-105">Ten temat zawiera informacje na temat [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi standardowych formantów w aplikacjach opracowanych dla platform [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="931d2-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="931d2-106">Kontrolki Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="931d2-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="931d2-107">Wszystkie elementy formantu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], które zapewniają informacje lub pomoc techniczną dla interakcji użytkownika, mają pełną natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="931d2-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="931d2-108">Inne elementy, takie jak panele, nie są widoczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="931d2-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="931d2-109">Kontrolki Win32</span><span class="sxs-lookup"><span data-stu-id="931d2-109">Win32 Controls</span></span>  
 <span data-ttu-id="931d2-110">Większość formantów [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] jest narażonych na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za poorednictwem dostawców po stronie klienta w UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="931d2-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="931d2-111">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="931d2-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="931d2-112">Pełna pomoc techniczna jest świadczona tylko w przypadku formantów z wersji 6 programu ComCtrl32. dll (dostępnej w [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] i nowszych).</span><span class="sxs-lookup"><span data-stu-id="931d2-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="931d2-113">Obsługiwane są następujące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="931d2-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="931d2-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="931d2-114">Class name</span></span>|<span data-ttu-id="931d2-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="931d2-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="931d2-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-116">Button</span></span>|<span data-ttu-id="931d2-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-117">Button</span></span>|  
|<span data-ttu-id="931d2-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-118">Button</span></span>|<span data-ttu-id="931d2-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="931d2-119">RadioButton</span></span>|  
|<span data-ttu-id="931d2-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-120">Button</span></span>|<span data-ttu-id="931d2-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="931d2-121">Group</span></span>|  
|<span data-ttu-id="931d2-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-122">Button</span></span>|<span data-ttu-id="931d2-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="931d2-123">CheckBox</span></span>|  
|<span data-ttu-id="931d2-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-124">Button</span></span>|<span data-ttu-id="931d2-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="931d2-125">Hyperlink</span></span>|  
|<span data-ttu-id="931d2-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-126">Button</span></span>|<span data-ttu-id="931d2-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="931d2-127">SplitButton</span></span>|  
|<span data-ttu-id="931d2-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-128">Button</span></span>|<span data-ttu-id="931d2-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="931d2-129">CheckBox</span></span>|  
|<span data-ttu-id="931d2-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="931d2-130">ComboBoxEx32</span></span>|<span data-ttu-id="931d2-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="931d2-131">ComboBox</span></span>|  
|<span data-ttu-id="931d2-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="931d2-132">ComboBox</span></span>|<span data-ttu-id="931d2-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="931d2-133">ComboBox</span></span>|  
|<span data-ttu-id="931d2-134">Edytuj</span><span class="sxs-lookup"><span data-stu-id="931d2-134">Edit</span></span>|<span data-ttu-id="931d2-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="931d2-135">Document</span></span>|  
|<span data-ttu-id="931d2-136">Edytuj</span><span class="sxs-lookup"><span data-stu-id="931d2-136">Edit</span></span>|<span data-ttu-id="931d2-137">Edytuj</span><span class="sxs-lookup"><span data-stu-id="931d2-137">Edit</span></span>|  
|<span data-ttu-id="931d2-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="931d2-138">SysLink</span></span>|<span data-ttu-id="931d2-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="931d2-139">Hyperlink</span></span>|  
|<span data-ttu-id="931d2-140">Static</span><span class="sxs-lookup"><span data-stu-id="931d2-140">Static</span></span>|<span data-ttu-id="931d2-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="931d2-141">Text</span></span>|  
|<span data-ttu-id="931d2-142">Static</span><span class="sxs-lookup"><span data-stu-id="931d2-142">Static</span></span>|<span data-ttu-id="931d2-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="931d2-143">Image</span></span>|  
|<span data-ttu-id="931d2-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="931d2-144">SysIPAddress32</span></span>|<span data-ttu-id="931d2-145">Celnej</span><span class="sxs-lookup"><span data-stu-id="931d2-145">Custom</span></span>|  
|<span data-ttu-id="931d2-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="931d2-146">SysHeader32</span></span>|<span data-ttu-id="931d2-147">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="931d2-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="931d2-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="931d2-148">SysListView32</span></span>|<span data-ttu-id="931d2-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="931d2-149">DataGrid</span></span>|  
|<span data-ttu-id="931d2-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="931d2-150">SysListView32</span></span>|<span data-ttu-id="931d2-151">List</span><span class="sxs-lookup"><span data-stu-id="931d2-151">List</span></span>|  
|<span data-ttu-id="931d2-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="931d2-152">ListBox</span></span>|<span data-ttu-id="931d2-153">List</span><span class="sxs-lookup"><span data-stu-id="931d2-153">List</span></span>|  
|<span data-ttu-id="931d2-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="931d2-154">ListBox</span></span>|<span data-ttu-id="931d2-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="931d2-155">ListItem</span></span>|  
|<span data-ttu-id="931d2-156">#32768</span><span class="sxs-lookup"><span data-stu-id="931d2-156">#32768</span></span>|<span data-ttu-id="931d2-157">Menu</span><span class="sxs-lookup"><span data-stu-id="931d2-157">Menu</span></span>|  
|<span data-ttu-id="931d2-158">#32768</span><span class="sxs-lookup"><span data-stu-id="931d2-158">#32768</span></span>|<span data-ttu-id="931d2-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="931d2-159">MenuItem</span></span>|  
|<span data-ttu-id="931d2-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="931d2-160">msctls_progress32</span></span>|<span data-ttu-id="931d2-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="931d2-161">ProgressBar</span></span>|  
|<span data-ttu-id="931d2-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="931d2-162">RichEdit</span></span>|<span data-ttu-id="931d2-163">dokumentu.</span><span class="sxs-lookup"><span data-stu-id="931d2-163">Document.</span></span> <span data-ttu-id="931d2-164">Zobacz Uwaga.</span><span class="sxs-lookup"><span data-stu-id="931d2-164">See note.</span></span>|  
|<span data-ttu-id="931d2-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="931d2-165">RichEdit20A</span></span>|<span data-ttu-id="931d2-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="931d2-166">Document</span></span>|  
|<span data-ttu-id="931d2-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="931d2-167">RichEdit20W</span></span>|<span data-ttu-id="931d2-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="931d2-168">Document</span></span>|  
|<span data-ttu-id="931d2-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="931d2-169">RichEdit50W</span></span>|<span data-ttu-id="931d2-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="931d2-170">Document</span></span>|  
|<span data-ttu-id="931d2-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="931d2-171">ScrollBar</span></span>|<span data-ttu-id="931d2-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="931d2-172">Slider</span></span>|  
|<span data-ttu-id="931d2-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="931d2-173">msctls_trackbar32</span></span>|<span data-ttu-id="931d2-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="931d2-174">Slider</span></span>|  
|<span data-ttu-id="931d2-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="931d2-175">msctls_updown32</span></span>|<span data-ttu-id="931d2-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="931d2-176">Spinner</span></span>|  
|<span data-ttu-id="931d2-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="931d2-177">msctls_statusbar32</span></span>|<span data-ttu-id="931d2-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="931d2-178">StatusBar</span></span>|  
|<span data-ttu-id="931d2-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="931d2-179">SysTabControl32</span></span>|<span data-ttu-id="931d2-180">Tab</span><span class="sxs-lookup"><span data-stu-id="931d2-180">Tab</span></span>|  
|<span data-ttu-id="931d2-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="931d2-181">SysTabControl32</span></span>|<span data-ttu-id="931d2-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="931d2-182">TabItem</span></span>|  
|<span data-ttu-id="931d2-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="931d2-183">ToolbarWindow32</span></span>|<span data-ttu-id="931d2-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="931d2-184">ToolBar</span></span>|  
|<span data-ttu-id="931d2-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="931d2-185">ToolbarWindow32</span></span>|<span data-ttu-id="931d2-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="931d2-186">MenuItem</span></span>|  
|<span data-ttu-id="931d2-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="931d2-187">ToolbarWindow32</span></span>|<span data-ttu-id="931d2-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-188">Button</span></span>|  
|<span data-ttu-id="931d2-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="931d2-189">ToolbarWindow32</span></span>|<span data-ttu-id="931d2-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="931d2-190">CheckBox</span></span>|  
|<span data-ttu-id="931d2-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="931d2-191">ToolbarWindow32</span></span>|<span data-ttu-id="931d2-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="931d2-192">RadioButton</span></span>|  
|<span data-ttu-id="931d2-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="931d2-193">ToolbarWindow32</span></span>|<span data-ttu-id="931d2-194">Separator</span><span class="sxs-lookup"><span data-stu-id="931d2-194">Separator</span></span>|  
|<span data-ttu-id="931d2-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="931d2-195">tooltips_class32</span></span>|<span data-ttu-id="931d2-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="931d2-196">ToolTip</span></span>|  
|<span data-ttu-id="931d2-197">#32774</span><span class="sxs-lookup"><span data-stu-id="931d2-197">#32774</span></span>|<span data-ttu-id="931d2-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="931d2-198">ToolTip</span></span>|  
|<span data-ttu-id="931d2-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="931d2-199">ReBarWindow32</span></span>|<span data-ttu-id="931d2-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="931d2-200">Toolbar</span></span>|  
|<span data-ttu-id="931d2-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="931d2-201">SysTreeView32</span></span>|<span data-ttu-id="931d2-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="931d2-202">Tree</span></span>|  
|<span data-ttu-id="931d2-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="931d2-203">SysTreeView32</span></span>|<span data-ttu-id="931d2-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="931d2-204">TreeItem</span></span>|  
  
 <span data-ttu-id="931d2-205">**Uwaga** Formant RichEdit jest obsługiwany tylko w przypadku wersji dostarczonych z systemem Windows Vista (w biblioteki riched20. dll w wersji 3,1 i nowszych oraz MsftEdit. dll w wersji 4,1 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="931d2-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="931d2-206">Następujące kontrolki nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="931d2-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="931d2-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="931d2-207">Class name</span></span>|<span data-ttu-id="931d2-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="931d2-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="931d2-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="931d2-209">SysAnimate32</span></span>|<span data-ttu-id="931d2-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="931d2-210">Image</span></span>|  
|<span data-ttu-id="931d2-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="931d2-211">SysPager</span></span>|<span data-ttu-id="931d2-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="931d2-212">Spinner</span></span>|  
|<span data-ttu-id="931d2-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="931d2-213">SysDateTimePick32</span></span>|<span data-ttu-id="931d2-214">Celnej</span><span class="sxs-lookup"><span data-stu-id="931d2-214">Custom</span></span>|  
|<span data-ttu-id="931d2-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="931d2-215">SysMonthCal32</span></span>|<span data-ttu-id="931d2-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="931d2-216">Calendar</span></span>|  
|<span data-ttu-id="931d2-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="931d2-217">MS_WINNOTE</span></span>|<span data-ttu-id="931d2-218">wyowietlon</span><span class="sxs-lookup"><span data-stu-id="931d2-218">Tooltip</span></span>|  
|<span data-ttu-id="931d2-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="931d2-219">VBBubble</span></span>|<span data-ttu-id="931d2-220">wyowietlon</span><span class="sxs-lookup"><span data-stu-id="931d2-220">Tooltip</span></span>|  
|<span data-ttu-id="931d2-221">Pasek przewijania (używany jako formant autonomiczny)</span><span class="sxs-lookup"><span data-stu-id="931d2-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="931d2-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="931d2-222">Slider</span></span>|  
|<span data-ttu-id="931d2-223">Podsiatka</span><span class="sxs-lookup"><span data-stu-id="931d2-223">SuperGrid</span></span>|<span data-ttu-id="931d2-224">Celnej</span><span class="sxs-lookup"><span data-stu-id="931d2-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="931d2-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="931d2-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="931d2-226">Kontrolki Windows Forms są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za poorednictwem dostawców po stronie klienta w UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="931d2-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="931d2-227">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="931d2-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="931d2-228">Zwykle Windows Forms formanty, które są otokami zarządzanymi dla [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] wspólnych formantów, są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="931d2-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="931d2-229">Obsługiwane są następujące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="931d2-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="931d2-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="931d2-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="931d2-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="931d2-231">Button</span></span>|  
|<span data-ttu-id="931d2-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="931d2-232">CheckBox</span></span>|  
|<span data-ttu-id="931d2-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="931d2-233">CheckedListBox</span></span>|  
|<span data-ttu-id="931d2-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="931d2-234">ColorDialog</span></span>|  
|<span data-ttu-id="931d2-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="931d2-235">ComboBox</span></span>|  
|<span data-ttu-id="931d2-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="931d2-236">FolderBrowser</span></span>|  
|<span data-ttu-id="931d2-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="931d2-237">FontDialog</span></span>|  
|<span data-ttu-id="931d2-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="931d2-238">GroupBox</span></span>|  
|<span data-ttu-id="931d2-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="931d2-239">HscrollBar</span></span>|  
|<span data-ttu-id="931d2-240">Obrazów</span><span class="sxs-lookup"><span data-stu-id="931d2-240">ImageList</span></span>|  
|<span data-ttu-id="931d2-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="931d2-241">Label</span></span>|  
|<span data-ttu-id="931d2-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="931d2-242">ListBox</span></span>|  
|<span data-ttu-id="931d2-243">ListView</span><span class="sxs-lookup"><span data-stu-id="931d2-243">ListView</span></span>|  
|<span data-ttu-id="931d2-244">MainMenu/</span><span class="sxs-lookup"><span data-stu-id="931d2-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="931d2-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="931d2-245">MonthCalendar</span></span>|  
|<span data-ttu-id="931d2-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="931d2-246">NotifyIcon</span></span>|  
|<span data-ttu-id="931d2-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="931d2-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="931d2-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="931d2-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="931d2-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="931d2-249">PrintDialog</span></span>|  
|<span data-ttu-id="931d2-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="931d2-250">ProgressBar</span></span>|  
|<span data-ttu-id="931d2-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="931d2-251">RadioButton</span></span>|  
|<span data-ttu-id="931d2-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="931d2-252">RichTextBox</span></span>|  
|<span data-ttu-id="931d2-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="931d2-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="931d2-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="931d2-254">ScrollableControl</span></span>|  
|<span data-ttu-id="931d2-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="931d2-255">SoundPlayer</span></span>|  
|<span data-ttu-id="931d2-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="931d2-256">StatusBar</span></span>|  
|<span data-ttu-id="931d2-257">Elementy TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="931d2-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="931d2-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="931d2-258">TextBox</span></span>|  
|<span data-ttu-id="931d2-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="931d2-259">Timer</span></span>|  
|<span data-ttu-id="931d2-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="931d2-260">Toolbar</span></span>|  
|<span data-ttu-id="931d2-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="931d2-261">ToolTip</span></span>|  
|<span data-ttu-id="931d2-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="931d2-262">TrackBar</span></span>|  
|<span data-ttu-id="931d2-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="931d2-263">TreeView</span></span>|  
|<span data-ttu-id="931d2-264">VScrollBar —</span><span class="sxs-lookup"><span data-stu-id="931d2-264">VscrollBar</span></span>|  
|<span data-ttu-id="931d2-265">Kontrol</span><span class="sxs-lookup"><span data-stu-id="931d2-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="931d2-266">Następujące kontrolki są dostępne do [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko w ramach obsługi usługi Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="931d2-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="931d2-267">Niektóre funkcje mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="931d2-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="931d2-268">Nazwa kontrolki</span><span class="sxs-lookup"><span data-stu-id="931d2-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="931d2-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="931d2-269">BindingSource</span></span>|  
|<span data-ttu-id="931d2-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="931d2-270">DataGrid</span></span>|  
|<span data-ttu-id="931d2-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="931d2-271">DataGridView</span></span>|  
|<span data-ttu-id="931d2-272">Nawigator datanavigator</span><span class="sxs-lookup"><span data-stu-id="931d2-272">DataNavigator</span></span>|  
|<span data-ttu-id="931d2-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="931d2-273">DomainUpDown</span></span>|  
|<span data-ttu-id="931d2-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="931d2-274">ErrorProvider</span></span>|  
|<span data-ttu-id="931d2-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="931d2-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="931d2-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="931d2-276">Form</span></span>|  
|<span data-ttu-id="931d2-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="931d2-277">LinkLabel</span></span>|  
|<span data-ttu-id="931d2-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="931d2-278">HelpProvider</span></span>|  
|<span data-ttu-id="931d2-279">Formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="931d2-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="931d2-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="931d2-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="931d2-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="931d2-281">NumericUpDown</span></span>|  
|<span data-ttu-id="931d2-282">Panel</span><span class="sxs-lookup"><span data-stu-id="931d2-282">Panel</span></span>|  
|<span data-ttu-id="931d2-283">Elemencie</span><span class="sxs-lookup"><span data-stu-id="931d2-283">PictureBox</span></span>|  
|<span data-ttu-id="931d2-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="931d2-284">PrintDocument</span></span>|  
|<span data-ttu-id="931d2-285">PrintPreview — kontrolka</span><span class="sxs-lookup"><span data-stu-id="931d2-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="931d2-286">PrintPreview — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="931d2-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="931d2-287">Używany</span><span class="sxs-lookup"><span data-stu-id="931d2-287">PropertyGrid</span></span>|  
|<span data-ttu-id="931d2-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="931d2-288">UserControl</span></span>|  
|<span data-ttu-id="931d2-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="931d2-289">ToolStrip</span></span>|  
|<span data-ttu-id="931d2-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="931d2-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="931d2-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="931d2-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="931d2-292">Dzielnik</span><span class="sxs-lookup"><span data-stu-id="931d2-292">Splitter</span></span>|  
|<span data-ttu-id="931d2-293">Elemencie RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="931d2-293">RaftingContainer</span></span>|  
|<span data-ttu-id="931d2-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="931d2-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="931d2-295">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="931d2-295">See also</span></span>

- [<span data-ttu-id="931d2-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="931d2-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
