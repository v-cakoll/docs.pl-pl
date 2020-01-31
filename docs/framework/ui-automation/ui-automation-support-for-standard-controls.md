---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 49277073706444fd611ae41e762442388ac50b71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789603"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="8f24f-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów</span><span class="sxs-lookup"><span data-stu-id="8f24f-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="8f24f-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="8f24f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8f24f-104">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8f24f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8f24f-105">Ten temat zawiera informacje dotyczące [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi standardowych formantów w aplikacjach opracowanych dla platform [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8f24f-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="8f24f-106">Kontrolki Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="8f24f-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="8f24f-107">Wszystkie elementy formantu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], które zapewniają informacje lub pomoc techniczną dla interakcji użytkownika, mają pełną natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f24f-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="8f24f-108">Inne elementy, takie jak panele, nie są widoczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f24f-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="8f24f-109">Kontrolki Win32</span><span class="sxs-lookup"><span data-stu-id="8f24f-109">Win32 Controls</span></span>  
 <span data-ttu-id="8f24f-110">Większość formantów Win32 jest narażonych na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za poorednictwem dostawców po stronie klienta w UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="8f24f-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="8f24f-111">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f24f-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="8f24f-112">Pełna pomoc techniczna jest świadczona tylko dla formantów z wersji 6 programu *ComCtrl32. dll*.</span><span class="sxs-lookup"><span data-stu-id="8f24f-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="8f24f-113">Obsługiwane są następujące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8f24f-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="8f24f-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="8f24f-114">Class name</span></span>|<span data-ttu-id="8f24f-115">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="8f24f-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="8f24f-116">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-116">Button</span></span>|<span data-ttu-id="8f24f-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-117">Button</span></span>|  
|<span data-ttu-id="8f24f-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-118">Button</span></span>|<span data-ttu-id="8f24f-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="8f24f-119">RadioButton</span></span>|  
|<span data-ttu-id="8f24f-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-120">Button</span></span>|<span data-ttu-id="8f24f-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="8f24f-121">Group</span></span>|  
|<span data-ttu-id="8f24f-122">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-122">Button</span></span>|<span data-ttu-id="8f24f-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-123">CheckBox</span></span>|  
|<span data-ttu-id="8f24f-124">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-124">Button</span></span>|<span data-ttu-id="8f24f-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="8f24f-125">Hyperlink</span></span>|  
|<span data-ttu-id="8f24f-126">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-126">Button</span></span>|<span data-ttu-id="8f24f-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="8f24f-127">SplitButton</span></span>|  
|<span data-ttu-id="8f24f-128">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-128">Button</span></span>|<span data-ttu-id="8f24f-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-129">CheckBox</span></span>|  
|<span data-ttu-id="8f24f-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="8f24f-130">ComboBoxEx32</span></span>|<span data-ttu-id="8f24f-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-131">ComboBox</span></span>|  
|<span data-ttu-id="8f24f-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-132">ComboBox</span></span>|<span data-ttu-id="8f24f-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-133">ComboBox</span></span>|  
|<span data-ttu-id="8f24f-134">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="8f24f-134">Edit</span></span>|<span data-ttu-id="8f24f-135">dokument</span><span class="sxs-lookup"><span data-stu-id="8f24f-135">Document</span></span>|  
|<span data-ttu-id="8f24f-136">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="8f24f-136">Edit</span></span>|<span data-ttu-id="8f24f-137">Edytowanie</span><span class="sxs-lookup"><span data-stu-id="8f24f-137">Edit</span></span>|  
|<span data-ttu-id="8f24f-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="8f24f-138">SysLink</span></span>|<span data-ttu-id="8f24f-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="8f24f-139">Hyperlink</span></span>|  
|<span data-ttu-id="8f24f-140">Static</span><span class="sxs-lookup"><span data-stu-id="8f24f-140">Static</span></span>|<span data-ttu-id="8f24f-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="8f24f-141">Text</span></span>|  
|<span data-ttu-id="8f24f-142">Static</span><span class="sxs-lookup"><span data-stu-id="8f24f-142">Static</span></span>|<span data-ttu-id="8f24f-143">Obraz</span><span class="sxs-lookup"><span data-stu-id="8f24f-143">Image</span></span>|  
|<span data-ttu-id="8f24f-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="8f24f-144">SysIPAddress32</span></span>|<span data-ttu-id="8f24f-145">Celnej</span><span class="sxs-lookup"><span data-stu-id="8f24f-145">Custom</span></span>|  
|<span data-ttu-id="8f24f-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="8f24f-146">SysHeader32</span></span>|<span data-ttu-id="8f24f-147">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="8f24f-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="8f24f-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="8f24f-148">SysListView32</span></span>|<span data-ttu-id="8f24f-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="8f24f-149">DataGrid</span></span>|  
|<span data-ttu-id="8f24f-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="8f24f-150">SysListView32</span></span>|<span data-ttu-id="8f24f-151">Lista</span><span class="sxs-lookup"><span data-stu-id="8f24f-151">List</span></span>|  
|<span data-ttu-id="8f24f-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-152">ListBox</span></span>|<span data-ttu-id="8f24f-153">Lista</span><span class="sxs-lookup"><span data-stu-id="8f24f-153">List</span></span>|  
|<span data-ttu-id="8f24f-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-154">ListBox</span></span>|<span data-ttu-id="8f24f-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="8f24f-155">ListItem</span></span>|  
|<span data-ttu-id="8f24f-156">#32768</span><span class="sxs-lookup"><span data-stu-id="8f24f-156">#32768</span></span>|<span data-ttu-id="8f24f-157">Menu</span><span class="sxs-lookup"><span data-stu-id="8f24f-157">Menu</span></span>|  
|<span data-ttu-id="8f24f-158">#32768</span><span class="sxs-lookup"><span data-stu-id="8f24f-158">#32768</span></span>|<span data-ttu-id="8f24f-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="8f24f-159">MenuItem</span></span>|  
|<span data-ttu-id="8f24f-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="8f24f-160">msctls_progress32</span></span>|<span data-ttu-id="8f24f-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="8f24f-161">ProgressBar</span></span>|  
|<span data-ttu-id="8f24f-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="8f24f-162">RichEdit</span></span>|<span data-ttu-id="8f24f-163">Dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8f24f-163">Document.</span></span> <span data-ttu-id="8f24f-164">Zobacz Uwaga.</span><span class="sxs-lookup"><span data-stu-id="8f24f-164">See note.</span></span>|  
|<span data-ttu-id="8f24f-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="8f24f-165">RichEdit20A</span></span>|<span data-ttu-id="8f24f-166">dokument</span><span class="sxs-lookup"><span data-stu-id="8f24f-166">Document</span></span>|  
|<span data-ttu-id="8f24f-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="8f24f-167">RichEdit20W</span></span>|<span data-ttu-id="8f24f-168">dokument</span><span class="sxs-lookup"><span data-stu-id="8f24f-168">Document</span></span>|  
|<span data-ttu-id="8f24f-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="8f24f-169">RichEdit50W</span></span>|<span data-ttu-id="8f24f-170">dokument</span><span class="sxs-lookup"><span data-stu-id="8f24f-170">Document</span></span>|  
|<span data-ttu-id="8f24f-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="8f24f-171">ScrollBar</span></span>|<span data-ttu-id="8f24f-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="8f24f-172">Slider</span></span>|  
|<span data-ttu-id="8f24f-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="8f24f-173">msctls_trackbar32</span></span>|<span data-ttu-id="8f24f-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="8f24f-174">Slider</span></span>|  
|<span data-ttu-id="8f24f-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="8f24f-175">msctls_updown32</span></span>|<span data-ttu-id="8f24f-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="8f24f-176">Spinner</span></span>|  
|<span data-ttu-id="8f24f-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="8f24f-177">msctls_statusbar32</span></span>|<span data-ttu-id="8f24f-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="8f24f-178">StatusBar</span></span>|  
|<span data-ttu-id="8f24f-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="8f24f-179">SysTabControl32</span></span>|<span data-ttu-id="8f24f-180">Tab</span><span class="sxs-lookup"><span data-stu-id="8f24f-180">Tab</span></span>|  
|<span data-ttu-id="8f24f-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="8f24f-181">SysTabControl32</span></span>|<span data-ttu-id="8f24f-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="8f24f-182">TabItem</span></span>|  
|<span data-ttu-id="8f24f-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="8f24f-183">ToolbarWindow32</span></span>|<span data-ttu-id="8f24f-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="8f24f-184">ToolBar</span></span>|  
|<span data-ttu-id="8f24f-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="8f24f-185">ToolbarWindow32</span></span>|<span data-ttu-id="8f24f-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="8f24f-186">MenuItem</span></span>|  
|<span data-ttu-id="8f24f-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="8f24f-187">ToolbarWindow32</span></span>|<span data-ttu-id="8f24f-188">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-188">Button</span></span>|  
|<span data-ttu-id="8f24f-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="8f24f-189">ToolbarWindow32</span></span>|<span data-ttu-id="8f24f-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-190">CheckBox</span></span>|  
|<span data-ttu-id="8f24f-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="8f24f-191">ToolbarWindow32</span></span>|<span data-ttu-id="8f24f-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="8f24f-192">RadioButton</span></span>|  
|<span data-ttu-id="8f24f-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="8f24f-193">ToolbarWindow32</span></span>|<span data-ttu-id="8f24f-194">Separator</span><span class="sxs-lookup"><span data-stu-id="8f24f-194">Separator</span></span>|  
|<span data-ttu-id="8f24f-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="8f24f-195">tooltips_class32</span></span>|<span data-ttu-id="8f24f-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="8f24f-196">ToolTip</span></span>|  
|<span data-ttu-id="8f24f-197">#32774</span><span class="sxs-lookup"><span data-stu-id="8f24f-197">#32774</span></span>|<span data-ttu-id="8f24f-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="8f24f-198">ToolTip</span></span>|  
|<span data-ttu-id="8f24f-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="8f24f-199">ReBarWindow32</span></span>|<span data-ttu-id="8f24f-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="8f24f-200">Toolbar</span></span>|  
|<span data-ttu-id="8f24f-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="8f24f-201">SysTreeView32</span></span>|<span data-ttu-id="8f24f-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="8f24f-202">Tree</span></span>|  
|<span data-ttu-id="8f24f-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="8f24f-203">SysTreeView32</span></span>|<span data-ttu-id="8f24f-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="8f24f-204">TreeItem</span></span>|  
  
 <span data-ttu-id="8f24f-205">**Uwaga** Formant RichEdit jest obsługiwany tylko w przypadku wersji dostarczonych z systemem Windows Vista (w biblioteki riched20. dll w wersji 3,1 i nowszych oraz MsftEdit. dll w wersji 4,1 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="8f24f-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="8f24f-206">Następujące kontrolki nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8f24f-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="8f24f-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="8f24f-207">Class name</span></span>|<span data-ttu-id="8f24f-208">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="8f24f-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="8f24f-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="8f24f-209">SysAnimate32</span></span>|<span data-ttu-id="8f24f-210">Obraz</span><span class="sxs-lookup"><span data-stu-id="8f24f-210">Image</span></span>|  
|<span data-ttu-id="8f24f-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="8f24f-211">SysPager</span></span>|<span data-ttu-id="8f24f-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="8f24f-212">Spinner</span></span>|  
|<span data-ttu-id="8f24f-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="8f24f-213">SysDateTimePick32</span></span>|<span data-ttu-id="8f24f-214">Celnej</span><span class="sxs-lookup"><span data-stu-id="8f24f-214">Custom</span></span>|  
|<span data-ttu-id="8f24f-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="8f24f-215">SysMonthCal32</span></span>|<span data-ttu-id="8f24f-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="8f24f-216">Calendar</span></span>|  
|<span data-ttu-id="8f24f-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="8f24f-217">MS_WINNOTE</span></span>|<span data-ttu-id="8f24f-218">wyowietlon</span><span class="sxs-lookup"><span data-stu-id="8f24f-218">Tooltip</span></span>|  
|<span data-ttu-id="8f24f-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="8f24f-219">VBBubble</span></span>|<span data-ttu-id="8f24f-220">wyowietlon</span><span class="sxs-lookup"><span data-stu-id="8f24f-220">Tooltip</span></span>|  
|<span data-ttu-id="8f24f-221">Pasek przewijania (używany jako formant autonomiczny)</span><span class="sxs-lookup"><span data-stu-id="8f24f-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="8f24f-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="8f24f-222">Slider</span></span>|  
|<span data-ttu-id="8f24f-223">Podsiatka</span><span class="sxs-lookup"><span data-stu-id="8f24f-223">SuperGrid</span></span>|<span data-ttu-id="8f24f-224">Celnej</span><span class="sxs-lookup"><span data-stu-id="8f24f-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="8f24f-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8f24f-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="8f24f-226">Kontrolki Windows Forms są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za poorednictwem dostawców po stronie klienta w UIAutomationClientsideProviders. dll.</span><span class="sxs-lookup"><span data-stu-id="8f24f-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="8f24f-227">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8f24f-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="8f24f-228">Zazwyczaj Windows Forms formantów, które są otokami zarządzanymi dla formantów standardowych Win32, są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f24f-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="8f24f-229">Obsługiwane są następujące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8f24f-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="8f24f-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="8f24f-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="8f24f-231">Przycisk</span><span class="sxs-lookup"><span data-stu-id="8f24f-231">Button</span></span>|  
|<span data-ttu-id="8f24f-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-232">CheckBox</span></span>|  
|<span data-ttu-id="8f24f-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-233">CheckedListBox</span></span>|  
|<span data-ttu-id="8f24f-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="8f24f-234">ColorDialog</span></span>|  
|<span data-ttu-id="8f24f-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-235">ComboBox</span></span>|  
|<span data-ttu-id="8f24f-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="8f24f-236">FolderBrowser</span></span>|  
|<span data-ttu-id="8f24f-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="8f24f-237">FontDialog</span></span>|  
|<span data-ttu-id="8f24f-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-238">GroupBox</span></span>|  
|<span data-ttu-id="8f24f-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="8f24f-239">HscrollBar</span></span>|  
|<span data-ttu-id="8f24f-240">Obrazów</span><span class="sxs-lookup"><span data-stu-id="8f24f-240">ImageList</span></span>|  
|<span data-ttu-id="8f24f-241">Etykieta</span><span class="sxs-lookup"><span data-stu-id="8f24f-241">Label</span></span>|  
|<span data-ttu-id="8f24f-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-242">ListBox</span></span>|  
|<span data-ttu-id="8f24f-243">ListView</span><span class="sxs-lookup"><span data-stu-id="8f24f-243">ListView</span></span>|  
|<span data-ttu-id="8f24f-244">MainMenu/</span><span class="sxs-lookup"><span data-stu-id="8f24f-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="8f24f-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="8f24f-245">MonthCalendar</span></span>|  
|<span data-ttu-id="8f24f-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="8f24f-246">NotifyIcon</span></span>|  
|<span data-ttu-id="8f24f-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="8f24f-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="8f24f-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="8f24f-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="8f24f-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="8f24f-249">PrintDialog</span></span>|  
|<span data-ttu-id="8f24f-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="8f24f-250">ProgressBar</span></span>|  
|<span data-ttu-id="8f24f-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="8f24f-251">RadioButton</span></span>|  
|<span data-ttu-id="8f24f-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-252">RichTextBox</span></span>|  
|<span data-ttu-id="8f24f-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="8f24f-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="8f24f-254">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="8f24f-254">ScrollableControl</span></span>|  
|<span data-ttu-id="8f24f-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="8f24f-255">SoundPlayer</span></span>|  
|<span data-ttu-id="8f24f-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="8f24f-256">StatusBar</span></span>|  
|<span data-ttu-id="8f24f-257">Elementy TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="8f24f-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="8f24f-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-258">TextBox</span></span>|  
|<span data-ttu-id="8f24f-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="8f24f-259">Timer</span></span>|  
|<span data-ttu-id="8f24f-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="8f24f-260">Toolbar</span></span>|  
|<span data-ttu-id="8f24f-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="8f24f-261">ToolTip</span></span>|  
|<span data-ttu-id="8f24f-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="8f24f-262">TrackBar</span></span>|  
|<span data-ttu-id="8f24f-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="8f24f-263">TreeView</span></span>|  
|<span data-ttu-id="8f24f-264">VScrollBar —</span><span class="sxs-lookup"><span data-stu-id="8f24f-264">VscrollBar</span></span>|  
|<span data-ttu-id="8f24f-265">Kontrol</span><span class="sxs-lookup"><span data-stu-id="8f24f-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="8f24f-266">Następujące kontrolki są dostępne do [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko w ramach obsługi usługi Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="8f24f-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="8f24f-267">Niektóre funkcje mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="8f24f-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="8f24f-268">Nazwa kontrolki</span><span class="sxs-lookup"><span data-stu-id="8f24f-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="8f24f-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="8f24f-269">BindingSource</span></span>|  
|<span data-ttu-id="8f24f-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="8f24f-270">DataGrid</span></span>|  
|<span data-ttu-id="8f24f-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="8f24f-271">DataGridView</span></span>|  
|<span data-ttu-id="8f24f-272">Nawigator datanavigator</span><span class="sxs-lookup"><span data-stu-id="8f24f-272">DataNavigator</span></span>|  
|<span data-ttu-id="8f24f-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="8f24f-273">DomainUpDown</span></span>|  
|<span data-ttu-id="8f24f-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="8f24f-274">ErrorProvider</span></span>|  
|<span data-ttu-id="8f24f-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8f24f-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="8f24f-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="8f24f-276">Form</span></span>|  
|<span data-ttu-id="8f24f-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="8f24f-277">LinkLabel</span></span>|  
|<span data-ttu-id="8f24f-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="8f24f-278">HelpProvider</span></span>|  
|<span data-ttu-id="8f24f-279">Formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="8f24f-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="8f24f-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="8f24f-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="8f24f-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="8f24f-281">NumericUpDown</span></span>|  
|<span data-ttu-id="8f24f-282">Panel</span><span class="sxs-lookup"><span data-stu-id="8f24f-282">Panel</span></span>|  
|<span data-ttu-id="8f24f-283">Elemencie</span><span class="sxs-lookup"><span data-stu-id="8f24f-283">PictureBox</span></span>|  
|<span data-ttu-id="8f24f-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="8f24f-284">PrintDocument</span></span>|  
|<span data-ttu-id="8f24f-285">PrintPreview — kontrolka</span><span class="sxs-lookup"><span data-stu-id="8f24f-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="8f24f-286">PrintPreview — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="8f24f-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="8f24f-287">Używany</span><span class="sxs-lookup"><span data-stu-id="8f24f-287">PropertyGrid</span></span>|  
|<span data-ttu-id="8f24f-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="8f24f-288">UserControl</span></span>|  
|<span data-ttu-id="8f24f-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="8f24f-289">ToolStrip</span></span>|  
|<span data-ttu-id="8f24f-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8f24f-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="8f24f-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="8f24f-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="8f24f-292">Dzielnik</span><span class="sxs-lookup"><span data-stu-id="8f24f-292">Splitter</span></span>|  
|<span data-ttu-id="8f24f-293">Elemencie RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="8f24f-293">RaftingContainer</span></span>|  
|<span data-ttu-id="8f24f-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="8f24f-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f24f-295">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f24f-295">See also</span></span>

- [<span data-ttu-id="8f24f-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8f24f-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
