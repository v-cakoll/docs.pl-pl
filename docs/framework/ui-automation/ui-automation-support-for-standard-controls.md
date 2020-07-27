---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
description: Uzyskaj informacje na temat obsługi automatyzacji interfejsu użytkownika dla standardowych kontrolek w aplikacjach utworzonych dla Windows Presentation Foundation (WPF), Win32 i Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166117"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="d6b17-103">Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów</span><span class="sxs-lookup"><span data-stu-id="d6b17-103">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="d6b17-104">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d6b17-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d6b17-105">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="d6b17-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d6b17-106">Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsłudze standardowych formantów w aplikacjach opracowanych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] środowisk, Win32 i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d6b17-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="d6b17-107">Kontrolki Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d6b17-107">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="d6b17-108">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy sterujące, które dostarczają informacji lub pomocy technicznej dla interakcji użytkownika, mają pełną obsługę natywną [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d6b17-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d6b17-109">Inne elementy, takie jak panele, nie są widoczne dla programu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d6b17-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="d6b17-110">Kontrolki Win32</span><span class="sxs-lookup"><span data-stu-id="d6b17-110">Win32 Controls</span></span>  
 <span data-ttu-id="d6b17-111">Większość formantów Win32 jest narażonych [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przez dostawców po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="d6b17-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d6b17-112">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d6b17-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d6b17-113">Pełna pomoc techniczna jest świadczona tylko w przypadku formantów z wersji 6 programu *ComCtrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="d6b17-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="d6b17-114">Obsługiwane są następujące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d6b17-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d6b17-115">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="d6b17-115">Class name</span></span>|<span data-ttu-id="d6b17-116">Typ formantu</span><span class="sxs-lookup"><span data-stu-id="d6b17-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d6b17-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-117">Button</span></span>|<span data-ttu-id="d6b17-118">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-118">Button</span></span>|  
|<span data-ttu-id="d6b17-119">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-119">Button</span></span>|<span data-ttu-id="d6b17-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d6b17-120">RadioButton</span></span>|  
|<span data-ttu-id="d6b17-121">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-121">Button</span></span>|<span data-ttu-id="d6b17-122">Grupa</span><span class="sxs-lookup"><span data-stu-id="d6b17-122">Group</span></span>|  
|<span data-ttu-id="d6b17-123">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-123">Button</span></span>|<span data-ttu-id="d6b17-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-124">CheckBox</span></span>|  
|<span data-ttu-id="d6b17-125">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-125">Button</span></span>|<span data-ttu-id="d6b17-126">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="d6b17-126">Hyperlink</span></span>|  
|<span data-ttu-id="d6b17-127">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-127">Button</span></span>|<span data-ttu-id="d6b17-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="d6b17-128">SplitButton</span></span>|  
|<span data-ttu-id="d6b17-129">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-129">Button</span></span>|<span data-ttu-id="d6b17-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-130">CheckBox</span></span>|  
|<span data-ttu-id="d6b17-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="d6b17-131">ComboBoxEx32</span></span>|<span data-ttu-id="d6b17-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-132">ComboBox</span></span>|  
|<span data-ttu-id="d6b17-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-133">ComboBox</span></span>|<span data-ttu-id="d6b17-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-134">ComboBox</span></span>|  
|<span data-ttu-id="d6b17-135">Edytuj</span><span class="sxs-lookup"><span data-stu-id="d6b17-135">Edit</span></span>|<span data-ttu-id="d6b17-136">Dokument</span><span class="sxs-lookup"><span data-stu-id="d6b17-136">Document</span></span>|  
|<span data-ttu-id="d6b17-137">Edytuj</span><span class="sxs-lookup"><span data-stu-id="d6b17-137">Edit</span></span>|<span data-ttu-id="d6b17-138">Edytuj</span><span class="sxs-lookup"><span data-stu-id="d6b17-138">Edit</span></span>|  
|<span data-ttu-id="d6b17-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="d6b17-139">SysLink</span></span>|<span data-ttu-id="d6b17-140">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="d6b17-140">Hyperlink</span></span>|  
|<span data-ttu-id="d6b17-141">Statyczny</span><span class="sxs-lookup"><span data-stu-id="d6b17-141">Static</span></span>|<span data-ttu-id="d6b17-142">Tekst</span><span class="sxs-lookup"><span data-stu-id="d6b17-142">Text</span></span>|  
|<span data-ttu-id="d6b17-143">Statyczny</span><span class="sxs-lookup"><span data-stu-id="d6b17-143">Static</span></span>|<span data-ttu-id="d6b17-144">Image (Obraz)</span><span class="sxs-lookup"><span data-stu-id="d6b17-144">Image</span></span>|  
|<span data-ttu-id="d6b17-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="d6b17-145">SysIPAddress32</span></span>|<span data-ttu-id="d6b17-146">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="d6b17-146">Custom</span></span>|  
|<span data-ttu-id="d6b17-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="d6b17-147">SysHeader32</span></span>|<span data-ttu-id="d6b17-148">Nagłówek/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="d6b17-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="d6b17-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d6b17-149">SysListView32</span></span>|<span data-ttu-id="d6b17-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d6b17-150">DataGrid</span></span>|  
|<span data-ttu-id="d6b17-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="d6b17-151">SysListView32</span></span>|<span data-ttu-id="d6b17-152">Lista</span><span class="sxs-lookup"><span data-stu-id="d6b17-152">List</span></span>|  
|<span data-ttu-id="d6b17-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-153">ListBox</span></span>|<span data-ttu-id="d6b17-154">Lista</span><span class="sxs-lookup"><span data-stu-id="d6b17-154">List</span></span>|  
|<span data-ttu-id="d6b17-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-155">ListBox</span></span>|<span data-ttu-id="d6b17-156">Metodę</span><span class="sxs-lookup"><span data-stu-id="d6b17-156">ListItem</span></span>|  
|<span data-ttu-id="d6b17-157">#32768</span><span class="sxs-lookup"><span data-stu-id="d6b17-157">#32768</span></span>|<span data-ttu-id="d6b17-158">Menu</span><span class="sxs-lookup"><span data-stu-id="d6b17-158">Menu</span></span>|  
|<span data-ttu-id="d6b17-159">#32768</span><span class="sxs-lookup"><span data-stu-id="d6b17-159">#32768</span></span>|<span data-ttu-id="d6b17-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d6b17-160">MenuItem</span></span>|  
|<span data-ttu-id="d6b17-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="d6b17-161">msctls_progress32</span></span>|<span data-ttu-id="d6b17-162">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d6b17-162">ProgressBar</span></span>|  
|<span data-ttu-id="d6b17-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="d6b17-163">RichEdit</span></span>|<span data-ttu-id="d6b17-164">Dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d6b17-164">Document.</span></span> <span data-ttu-id="d6b17-165">Zobacz Uwaga.</span><span class="sxs-lookup"><span data-stu-id="d6b17-165">See note.</span></span>|  
|<span data-ttu-id="d6b17-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="d6b17-166">RichEdit20A</span></span>|<span data-ttu-id="d6b17-167">Dokument</span><span class="sxs-lookup"><span data-stu-id="d6b17-167">Document</span></span>|  
|<span data-ttu-id="d6b17-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="d6b17-168">RichEdit20W</span></span>|<span data-ttu-id="d6b17-169">Dokument</span><span class="sxs-lookup"><span data-stu-id="d6b17-169">Document</span></span>|  
|<span data-ttu-id="d6b17-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="d6b17-170">RichEdit50W</span></span>|<span data-ttu-id="d6b17-171">Dokument</span><span class="sxs-lookup"><span data-stu-id="d6b17-171">Document</span></span>|  
|<span data-ttu-id="d6b17-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="d6b17-172">ScrollBar</span></span>|<span data-ttu-id="d6b17-173">Slider</span><span class="sxs-lookup"><span data-stu-id="d6b17-173">Slider</span></span>|  
|<span data-ttu-id="d6b17-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="d6b17-174">msctls_trackbar32</span></span>|<span data-ttu-id="d6b17-175">Slider</span><span class="sxs-lookup"><span data-stu-id="d6b17-175">Slider</span></span>|  
|<span data-ttu-id="d6b17-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="d6b17-176">msctls_updown32</span></span>|<span data-ttu-id="d6b17-177">pokrętło</span><span class="sxs-lookup"><span data-stu-id="d6b17-177">Spinner</span></span>|  
|<span data-ttu-id="d6b17-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="d6b17-178">msctls_statusbar32</span></span>|<span data-ttu-id="d6b17-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d6b17-179">StatusBar</span></span>|  
|<span data-ttu-id="d6b17-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d6b17-180">SysTabControl32</span></span>|<span data-ttu-id="d6b17-181">Tab</span><span class="sxs-lookup"><span data-stu-id="d6b17-181">Tab</span></span>|  
|<span data-ttu-id="d6b17-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="d6b17-182">SysTabControl32</span></span>|<span data-ttu-id="d6b17-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="d6b17-183">TabItem</span></span>|  
|<span data-ttu-id="d6b17-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6b17-184">ToolbarWindow32</span></span>|<span data-ttu-id="d6b17-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="d6b17-185">ToolBar</span></span>|  
|<span data-ttu-id="d6b17-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6b17-186">ToolbarWindow32</span></span>|<span data-ttu-id="d6b17-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d6b17-187">MenuItem</span></span>|  
|<span data-ttu-id="d6b17-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6b17-188">ToolbarWindow32</span></span>|<span data-ttu-id="d6b17-189">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-189">Button</span></span>|  
|<span data-ttu-id="d6b17-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6b17-190">ToolbarWindow32</span></span>|<span data-ttu-id="d6b17-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-191">CheckBox</span></span>|  
|<span data-ttu-id="d6b17-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6b17-192">ToolbarWindow32</span></span>|<span data-ttu-id="d6b17-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d6b17-193">RadioButton</span></span>|  
|<span data-ttu-id="d6b17-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6b17-194">ToolbarWindow32</span></span>|<span data-ttu-id="d6b17-195">Separator</span><span class="sxs-lookup"><span data-stu-id="d6b17-195">Separator</span></span>|  
|<span data-ttu-id="d6b17-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="d6b17-196">tooltips_class32</span></span>|<span data-ttu-id="d6b17-197">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d6b17-197">ToolTip</span></span>|  
|<span data-ttu-id="d6b17-198">#32774</span><span class="sxs-lookup"><span data-stu-id="d6b17-198">#32774</span></span>|<span data-ttu-id="d6b17-199">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d6b17-199">ToolTip</span></span>|  
|<span data-ttu-id="d6b17-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="d6b17-200">ReBarWindow32</span></span>|<span data-ttu-id="d6b17-201">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="d6b17-201">Toolbar</span></span>|  
|<span data-ttu-id="d6b17-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d6b17-202">SysTreeView32</span></span>|<span data-ttu-id="d6b17-203">Drzewo</span><span class="sxs-lookup"><span data-stu-id="d6b17-203">Tree</span></span>|  
|<span data-ttu-id="d6b17-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="d6b17-204">SysTreeView32</span></span>|<span data-ttu-id="d6b17-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="d6b17-205">TreeItem</span></span>|  
  
 <span data-ttu-id="d6b17-206">**Uwaga** Formant RichEdit jest obsługiwany tylko w przypadku wersji dostarczonych z systemem Windows Vista (w RichEd20.dll w wersji 3,1 lub nowszej oraz MsftEdit.dll wersji 4,1 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="d6b17-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="d6b17-207">Następujące kontrolki nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d6b17-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="d6b17-208">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="d6b17-208">Class name</span></span>|<span data-ttu-id="d6b17-209">Typ kontrolki</span><span class="sxs-lookup"><span data-stu-id="d6b17-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="d6b17-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="d6b17-210">SysAnimate32</span></span>|<span data-ttu-id="d6b17-211">Image (Obraz)</span><span class="sxs-lookup"><span data-stu-id="d6b17-211">Image</span></span>|  
|<span data-ttu-id="d6b17-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="d6b17-212">SysPager</span></span>|<span data-ttu-id="d6b17-213">pokrętło</span><span class="sxs-lookup"><span data-stu-id="d6b17-213">Spinner</span></span>|  
|<span data-ttu-id="d6b17-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="d6b17-214">SysDateTimePick32</span></span>|<span data-ttu-id="d6b17-215">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="d6b17-215">Custom</span></span>|  
|<span data-ttu-id="d6b17-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="d6b17-216">SysMonthCal32</span></span>|<span data-ttu-id="d6b17-217">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="d6b17-217">Calendar</span></span>|  
|<span data-ttu-id="d6b17-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="d6b17-218">MS_WINNOTE</span></span>|<span data-ttu-id="d6b17-219">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="d6b17-219">Tooltip</span></span>|  
|<span data-ttu-id="d6b17-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="d6b17-220">VBBubble</span></span>|<span data-ttu-id="d6b17-221">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="d6b17-221">Tooltip</span></span>|  
|<span data-ttu-id="d6b17-222">Pasek przewijania (używany jako formant autonomiczny)</span><span class="sxs-lookup"><span data-stu-id="d6b17-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="d6b17-223">Slider</span><span class="sxs-lookup"><span data-stu-id="d6b17-223">Slider</span></span>|  
|<span data-ttu-id="d6b17-224">Podsiatka</span><span class="sxs-lookup"><span data-stu-id="d6b17-224">SuperGrid</span></span>|<span data-ttu-id="d6b17-225">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="d6b17-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="d6b17-226">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d6b17-226">Windows Forms Controls</span></span>  
 <span data-ttu-id="d6b17-227">Kontrolki Windows Forms są dostępne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dostawców po stronie klienta w programie UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="d6b17-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="d6b17-228">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d6b17-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="d6b17-229">Zazwyczaj formanty Windows Forms, które są otokami zarządzanymi dla formantów standardowych Win32, są obsługiwane przez program [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d6b17-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="d6b17-230">Obsługiwane są następujące kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d6b17-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="d6b17-231">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="d6b17-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="d6b17-232">Przycisk</span><span class="sxs-lookup"><span data-stu-id="d6b17-232">Button</span></span>|  
|<span data-ttu-id="d6b17-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-233">CheckBox</span></span>|  
|<span data-ttu-id="d6b17-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-234">CheckedListBox</span></span>|  
|<span data-ttu-id="d6b17-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="d6b17-235">ColorDialog</span></span>|  
|<span data-ttu-id="d6b17-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-236">ComboBox</span></span>|  
|<span data-ttu-id="d6b17-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="d6b17-237">FolderBrowser</span></span>|  
|<span data-ttu-id="d6b17-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="d6b17-238">FontDialog</span></span>|  
|<span data-ttu-id="d6b17-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-239">GroupBox</span></span>|  
|<span data-ttu-id="d6b17-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="d6b17-240">HscrollBar</span></span>|  
|<span data-ttu-id="d6b17-241">Obrazów</span><span class="sxs-lookup"><span data-stu-id="d6b17-241">ImageList</span></span>|  
|<span data-ttu-id="d6b17-242">Etykieta</span><span class="sxs-lookup"><span data-stu-id="d6b17-242">Label</span></span>|  
|<span data-ttu-id="d6b17-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-243">ListBox</span></span>|  
|<span data-ttu-id="d6b17-244">ListView</span><span class="sxs-lookup"><span data-stu-id="d6b17-244">ListView</span></span>|  
|<span data-ttu-id="d6b17-245">MainMenu/</span><span class="sxs-lookup"><span data-stu-id="d6b17-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="d6b17-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d6b17-246">MonthCalendar</span></span>|  
|<span data-ttu-id="d6b17-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="d6b17-247">NotifyIcon</span></span>|  
|<span data-ttu-id="d6b17-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="d6b17-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="d6b17-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="d6b17-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="d6b17-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="d6b17-250">PrintDialog</span></span>|  
|<span data-ttu-id="d6b17-251">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="d6b17-251">ProgressBar</span></span>|  
|<span data-ttu-id="d6b17-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d6b17-252">RadioButton</span></span>|  
|<span data-ttu-id="d6b17-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-253">RichTextBox</span></span>|  
|<span data-ttu-id="d6b17-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="d6b17-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="d6b17-255">Elementu ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="d6b17-255">ScrollableControl</span></span>|  
|<span data-ttu-id="d6b17-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="d6b17-256">SoundPlayer</span></span>|  
|<span data-ttu-id="d6b17-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="d6b17-257">StatusBar</span></span>|  
|<span data-ttu-id="d6b17-258">Elementy TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="d6b17-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="d6b17-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-259">TextBox</span></span>|  
|<span data-ttu-id="d6b17-260">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="d6b17-260">Timer</span></span>|  
|<span data-ttu-id="d6b17-261">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="d6b17-261">Toolbar</span></span>|  
|<span data-ttu-id="d6b17-262">ToolTip</span><span class="sxs-lookup"><span data-stu-id="d6b17-262">ToolTip</span></span>|  
|<span data-ttu-id="d6b17-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="d6b17-263">TrackBar</span></span>|  
|<span data-ttu-id="d6b17-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="d6b17-264">TreeView</span></span>|  
|<span data-ttu-id="d6b17-265">VScrollBar —</span><span class="sxs-lookup"><span data-stu-id="d6b17-265">VscrollBar</span></span>|  
|<span data-ttu-id="d6b17-266">Kontrol</span><span class="sxs-lookup"><span data-stu-id="d6b17-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="d6b17-267">Następujące kontrolki są dostępne [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko w ramach obsługi usługi Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="d6b17-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="d6b17-268">Niektóre funkcje mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="d6b17-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="d6b17-269">Nazwa kontrolki</span><span class="sxs-lookup"><span data-stu-id="d6b17-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="d6b17-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="d6b17-270">BindingSource</span></span>|  
|<span data-ttu-id="d6b17-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="d6b17-271">DataGrid</span></span>|  
|<span data-ttu-id="d6b17-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="d6b17-272">DataGridView</span></span>|  
|<span data-ttu-id="d6b17-273">Nawigator datanavigator</span><span class="sxs-lookup"><span data-stu-id="d6b17-273">DataNavigator</span></span>|  
|<span data-ttu-id="d6b17-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="d6b17-274">DomainUpDown</span></span>|  
|<span data-ttu-id="d6b17-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="d6b17-275">ErrorProvider</span></span>|  
|<span data-ttu-id="d6b17-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d6b17-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="d6b17-277">Formularz</span><span class="sxs-lookup"><span data-stu-id="d6b17-277">Form</span></span>|  
|<span data-ttu-id="d6b17-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="d6b17-278">LinkLabel</span></span>|  
|<span data-ttu-id="d6b17-279">HelpProvider —</span><span class="sxs-lookup"><span data-stu-id="d6b17-279">HelpProvider</span></span>|  
|<span data-ttu-id="d6b17-280">Formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="d6b17-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="d6b17-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="d6b17-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="d6b17-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="d6b17-282">NumericUpDown</span></span>|  
|<span data-ttu-id="d6b17-283">Panel</span><span class="sxs-lookup"><span data-stu-id="d6b17-283">Panel</span></span>|  
|<span data-ttu-id="d6b17-284">Elemencie</span><span class="sxs-lookup"><span data-stu-id="d6b17-284">PictureBox</span></span>|  
|<span data-ttu-id="d6b17-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="d6b17-285">PrintDocument</span></span>|  
|<span data-ttu-id="d6b17-286">PrintPreview — kontrolka</span><span class="sxs-lookup"><span data-stu-id="d6b17-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="d6b17-287">PrintPreview — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="d6b17-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="d6b17-288">Używany</span><span class="sxs-lookup"><span data-stu-id="d6b17-288">PropertyGrid</span></span>|  
|<span data-ttu-id="d6b17-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="d6b17-289">UserControl</span></span>|  
|<span data-ttu-id="d6b17-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d6b17-290">ToolStrip</span></span>|  
|<span data-ttu-id="d6b17-291">Element TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d6b17-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="d6b17-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="d6b17-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="d6b17-293">Rozdzielacz</span><span class="sxs-lookup"><span data-stu-id="d6b17-293">Splitter</span></span>|  
|<span data-ttu-id="d6b17-294">Elemencie RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="d6b17-294">RaftingContainer</span></span>|  
|<span data-ttu-id="d6b17-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="d6b17-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6b17-296">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6b17-296">See also</span></span>

- [<span data-ttu-id="d6b17-297">Typy formantów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d6b17-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
