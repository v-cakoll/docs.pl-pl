---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179849"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="dbc25-102">Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów</span><span class="sxs-lookup"><span data-stu-id="dbc25-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="dbc25-103">Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="dbc25-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="dbc25-104">Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="dbc25-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="dbc25-105">Ten temat zawiera [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] informacje dotyczące obsługi standardowych [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]formantów w aplikacjach opracowanych dla frameworków formularzy Win32 i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dbc25-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="dbc25-106">Kontrolki fundacji prezentacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dbc25-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="dbc25-107">Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy sterujące, które zapewniają informacje lub [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wsparcie dla interakcji z użytkownikiem mają pełną obsługę natywną dla .</span><span class="sxs-lookup"><span data-stu-id="dbc25-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="dbc25-108">Inne elementy, takie jak panele, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nie są widoczne dla programu .</span><span class="sxs-lookup"><span data-stu-id="dbc25-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="dbc25-109">Sterowanie Win32</span><span class="sxs-lookup"><span data-stu-id="dbc25-109">Win32 Controls</span></span>  
 <span data-ttu-id="dbc25-110">Większość formantów Win32 są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawców po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="dbc25-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="dbc25-111">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dbc25-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="dbc25-112">Pełna obsługa jest dostępna tylko dla formantów z wersji 6 *comctrl32.dll*.</span><span class="sxs-lookup"><span data-stu-id="dbc25-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="dbc25-113">Obsługiwane są następujące formanty.</span><span class="sxs-lookup"><span data-stu-id="dbc25-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="dbc25-114">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="dbc25-114">Class name</span></span>|<span data-ttu-id="dbc25-115">Typ sterowania</span><span class="sxs-lookup"><span data-stu-id="dbc25-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="dbc25-116">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-116">Button</span></span>|<span data-ttu-id="dbc25-117">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-117">Button</span></span>|  
|<span data-ttu-id="dbc25-118">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-118">Button</span></span>|<span data-ttu-id="dbc25-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="dbc25-119">RadioButton</span></span>|  
|<span data-ttu-id="dbc25-120">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-120">Button</span></span>|<span data-ttu-id="dbc25-121">Grupa</span><span class="sxs-lookup"><span data-stu-id="dbc25-121">Group</span></span>|  
|<span data-ttu-id="dbc25-122">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-122">Button</span></span>|<span data-ttu-id="dbc25-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-123">CheckBox</span></span>|  
|<span data-ttu-id="dbc25-124">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-124">Button</span></span>|<span data-ttu-id="dbc25-125">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="dbc25-125">Hyperlink</span></span>|  
|<span data-ttu-id="dbc25-126">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-126">Button</span></span>|<span data-ttu-id="dbc25-127">Splitbutton</span><span class="sxs-lookup"><span data-stu-id="dbc25-127">SplitButton</span></span>|  
|<span data-ttu-id="dbc25-128">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-128">Button</span></span>|<span data-ttu-id="dbc25-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-129">CheckBox</span></span>|  
|<span data-ttu-id="dbc25-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="dbc25-130">ComboBoxEx32</span></span>|<span data-ttu-id="dbc25-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-131">ComboBox</span></span>|  
|<span data-ttu-id="dbc25-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-132">ComboBox</span></span>|<span data-ttu-id="dbc25-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-133">ComboBox</span></span>|  
|<span data-ttu-id="dbc25-134">Edytuj</span><span class="sxs-lookup"><span data-stu-id="dbc25-134">Edit</span></span>|<span data-ttu-id="dbc25-135">Dokument</span><span class="sxs-lookup"><span data-stu-id="dbc25-135">Document</span></span>|  
|<span data-ttu-id="dbc25-136">Edytuj</span><span class="sxs-lookup"><span data-stu-id="dbc25-136">Edit</span></span>|<span data-ttu-id="dbc25-137">Edytuj</span><span class="sxs-lookup"><span data-stu-id="dbc25-137">Edit</span></span>|  
|<span data-ttu-id="dbc25-138">SysLink (syslink)</span><span class="sxs-lookup"><span data-stu-id="dbc25-138">SysLink</span></span>|<span data-ttu-id="dbc25-139">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="dbc25-139">Hyperlink</span></span>|  
|<span data-ttu-id="dbc25-140">Statyczny</span><span class="sxs-lookup"><span data-stu-id="dbc25-140">Static</span></span>|<span data-ttu-id="dbc25-141">Tekst</span><span class="sxs-lookup"><span data-stu-id="dbc25-141">Text</span></span>|  
|<span data-ttu-id="dbc25-142">Statyczny</span><span class="sxs-lookup"><span data-stu-id="dbc25-142">Static</span></span>|<span data-ttu-id="dbc25-143">Image (Obraz)</span><span class="sxs-lookup"><span data-stu-id="dbc25-143">Image</span></span>|  
|<span data-ttu-id="dbc25-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="dbc25-144">SysIPAddress32</span></span>|<span data-ttu-id="dbc25-145">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="dbc25-145">Custom</span></span>|  
|<span data-ttu-id="dbc25-146">SysHeader32 (Właz głowy)</span><span class="sxs-lookup"><span data-stu-id="dbc25-146">SysHeader32</span></span>|<span data-ttu-id="dbc25-147">Nagłówek/nagłówekItem</span><span class="sxs-lookup"><span data-stu-id="dbc25-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="dbc25-148">Widok SysListView32</span><span class="sxs-lookup"><span data-stu-id="dbc25-148">SysListView32</span></span>|<span data-ttu-id="dbc25-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="dbc25-149">DataGrid</span></span>|  
|<span data-ttu-id="dbc25-150">Widok SysListView32</span><span class="sxs-lookup"><span data-stu-id="dbc25-150">SysListView32</span></span>|<span data-ttu-id="dbc25-151">List</span><span class="sxs-lookup"><span data-stu-id="dbc25-151">List</span></span>|  
|<span data-ttu-id="dbc25-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-152">ListBox</span></span>|<span data-ttu-id="dbc25-153">List</span><span class="sxs-lookup"><span data-stu-id="dbc25-153">List</span></span>|  
|<span data-ttu-id="dbc25-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-154">ListBox</span></span>|<span data-ttu-id="dbc25-155">Listitem</span><span class="sxs-lookup"><span data-stu-id="dbc25-155">ListItem</span></span>|  
|<span data-ttu-id="dbc25-156">#32768</span><span class="sxs-lookup"><span data-stu-id="dbc25-156">#32768</span></span>|<span data-ttu-id="dbc25-157">Menu</span><span class="sxs-lookup"><span data-stu-id="dbc25-157">Menu</span></span>|  
|<span data-ttu-id="dbc25-158">#32768</span><span class="sxs-lookup"><span data-stu-id="dbc25-158">#32768</span></span>|<span data-ttu-id="dbc25-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="dbc25-159">MenuItem</span></span>|  
|<span data-ttu-id="dbc25-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="dbc25-160">msctls_progress32</span></span>|<span data-ttu-id="dbc25-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="dbc25-161">ProgressBar</span></span>|  
|<span data-ttu-id="dbc25-162">Richedit</span><span class="sxs-lookup"><span data-stu-id="dbc25-162">RichEdit</span></span>|<span data-ttu-id="dbc25-163">Dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dbc25-163">Document.</span></span> <span data-ttu-id="dbc25-164">Patrz uwaga.</span><span class="sxs-lookup"><span data-stu-id="dbc25-164">See note.</span></span>|  
|<span data-ttu-id="dbc25-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="dbc25-165">RichEdit20A</span></span>|<span data-ttu-id="dbc25-166">Dokument</span><span class="sxs-lookup"><span data-stu-id="dbc25-166">Document</span></span>|  
|<span data-ttu-id="dbc25-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="dbc25-167">RichEdit20W</span></span>|<span data-ttu-id="dbc25-168">Dokument</span><span class="sxs-lookup"><span data-stu-id="dbc25-168">Document</span></span>|  
|<span data-ttu-id="dbc25-169">BogatyEdyt50W</span><span class="sxs-lookup"><span data-stu-id="dbc25-169">RichEdit50W</span></span>|<span data-ttu-id="dbc25-170">Dokument</span><span class="sxs-lookup"><span data-stu-id="dbc25-170">Document</span></span>|  
|<span data-ttu-id="dbc25-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="dbc25-171">ScrollBar</span></span>|<span data-ttu-id="dbc25-172">Suwak</span><span class="sxs-lookup"><span data-stu-id="dbc25-172">Slider</span></span>|  
|<span data-ttu-id="dbc25-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="dbc25-173">msctls_trackbar32</span></span>|<span data-ttu-id="dbc25-174">Suwak</span><span class="sxs-lookup"><span data-stu-id="dbc25-174">Slider</span></span>|  
|<span data-ttu-id="dbc25-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="dbc25-175">msctls_updown32</span></span>|<span data-ttu-id="dbc25-176">pokrętło</span><span class="sxs-lookup"><span data-stu-id="dbc25-176">Spinner</span></span>|  
|<span data-ttu-id="dbc25-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="dbc25-177">msctls_statusbar32</span></span>|<span data-ttu-id="dbc25-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="dbc25-178">StatusBar</span></span>|  
|<span data-ttu-id="dbc25-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="dbc25-179">SysTabControl32</span></span>|<span data-ttu-id="dbc25-180">Tab</span><span class="sxs-lookup"><span data-stu-id="dbc25-180">Tab</span></span>|  
|<span data-ttu-id="dbc25-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="dbc25-181">SysTabControl32</span></span>|<span data-ttu-id="dbc25-182">Tabitem</span><span class="sxs-lookup"><span data-stu-id="dbc25-182">TabItem</span></span>|  
|<span data-ttu-id="dbc25-183">Pasek narzędziWindow32</span><span class="sxs-lookup"><span data-stu-id="dbc25-183">ToolbarWindow32</span></span>|<span data-ttu-id="dbc25-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="dbc25-184">ToolBar</span></span>|  
|<span data-ttu-id="dbc25-185">Pasek narzędziWindow32</span><span class="sxs-lookup"><span data-stu-id="dbc25-185">ToolbarWindow32</span></span>|<span data-ttu-id="dbc25-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="dbc25-186">MenuItem</span></span>|  
|<span data-ttu-id="dbc25-187">Pasek narzędziWindow32</span><span class="sxs-lookup"><span data-stu-id="dbc25-187">ToolbarWindow32</span></span>|<span data-ttu-id="dbc25-188">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-188">Button</span></span>|  
|<span data-ttu-id="dbc25-189">Pasek narzędziWindow32</span><span class="sxs-lookup"><span data-stu-id="dbc25-189">ToolbarWindow32</span></span>|<span data-ttu-id="dbc25-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-190">CheckBox</span></span>|  
|<span data-ttu-id="dbc25-191">Pasek narzędziWindow32</span><span class="sxs-lookup"><span data-stu-id="dbc25-191">ToolbarWindow32</span></span>|<span data-ttu-id="dbc25-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="dbc25-192">RadioButton</span></span>|  
|<span data-ttu-id="dbc25-193">Pasek narzędziWindow32</span><span class="sxs-lookup"><span data-stu-id="dbc25-193">ToolbarWindow32</span></span>|<span data-ttu-id="dbc25-194">Separator</span><span class="sxs-lookup"><span data-stu-id="dbc25-194">Separator</span></span>|  
|<span data-ttu-id="dbc25-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="dbc25-195">tooltips_class32</span></span>|<span data-ttu-id="dbc25-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="dbc25-196">ToolTip</span></span>|  
|<span data-ttu-id="dbc25-197">#32774</span><span class="sxs-lookup"><span data-stu-id="dbc25-197">#32774</span></span>|<span data-ttu-id="dbc25-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="dbc25-198">ToolTip</span></span>|  
|<span data-ttu-id="dbc25-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="dbc25-199">ReBarWindow32</span></span>|<span data-ttu-id="dbc25-200">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="dbc25-200">Toolbar</span></span>|  
|<span data-ttu-id="dbc25-201">Widok SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="dbc25-201">SysTreeView32</span></span>|<span data-ttu-id="dbc25-202">Drzewo</span><span class="sxs-lookup"><span data-stu-id="dbc25-202">Tree</span></span>|  
|<span data-ttu-id="dbc25-203">Widok SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="dbc25-203">SysTreeView32</span></span>|<span data-ttu-id="dbc25-204">Treeitem</span><span class="sxs-lookup"><span data-stu-id="dbc25-204">TreeItem</span></span>|  
  
 <span data-ttu-id="dbc25-205">**Uwaga** Formant RichEdit jest obsługiwany tylko w wersjach dostarczanych z systemem Windows Vista (w pliku RichEd20.dll w wersji 3.1 i nowszej oraz msftEdit.dll w wersji 4.1 i nowszej).</span><span class="sxs-lookup"><span data-stu-id="dbc25-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="dbc25-206">Następujące formanty nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dbc25-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="dbc25-207">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="dbc25-207">Class name</span></span>|<span data-ttu-id="dbc25-208">Typ kontrolki</span><span class="sxs-lookup"><span data-stu-id="dbc25-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="dbc25-209">SysAnimate32 (WysAnimate32)</span><span class="sxs-lookup"><span data-stu-id="dbc25-209">SysAnimate32</span></span>|<span data-ttu-id="dbc25-210">Image (Obraz)</span><span class="sxs-lookup"><span data-stu-id="dbc25-210">Image</span></span>|  
|<span data-ttu-id="dbc25-211">SysPager (SysPager)</span><span class="sxs-lookup"><span data-stu-id="dbc25-211">SysPager</span></span>|<span data-ttu-id="dbc25-212">pokrętło</span><span class="sxs-lookup"><span data-stu-id="dbc25-212">Spinner</span></span>|  
|<span data-ttu-id="dbc25-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="dbc25-213">SysDateTimePick32</span></span>|<span data-ttu-id="dbc25-214">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="dbc25-214">Custom</span></span>|  
|<span data-ttu-id="dbc25-215">Miesiąc SysCal32</span><span class="sxs-lookup"><span data-stu-id="dbc25-215">SysMonthCal32</span></span>|<span data-ttu-id="dbc25-216">Kalendarz</span><span class="sxs-lookup"><span data-stu-id="dbc25-216">Calendar</span></span>|  
|<span data-ttu-id="dbc25-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="dbc25-217">MS_WINNOTE</span></span>|<span data-ttu-id="dbc25-218">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="dbc25-218">Tooltip</span></span>|  
|<span data-ttu-id="dbc25-219">VBBubble (VBBubble)</span><span class="sxs-lookup"><span data-stu-id="dbc25-219">VBBubble</span></span>|<span data-ttu-id="dbc25-220">Etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="dbc25-220">Tooltip</span></span>|  
|<span data-ttu-id="dbc25-221">Pasek przewijania (używany jako formant autonomiczny)</span><span class="sxs-lookup"><span data-stu-id="dbc25-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="dbc25-222">Suwak</span><span class="sxs-lookup"><span data-stu-id="dbc25-222">Slider</span></span>|  
|<span data-ttu-id="dbc25-223">SuperGrid (SuperGrid)</span><span class="sxs-lookup"><span data-stu-id="dbc25-223">SuperGrid</span></span>|<span data-ttu-id="dbc25-224">Niestandardowy</span><span class="sxs-lookup"><span data-stu-id="dbc25-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="dbc25-225">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dbc25-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="dbc25-226">Formanty formularzy [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] systemu Windows są widoczne za pośrednictwem dostawców po stronie klienta w UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="dbc25-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="dbc25-227">Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dbc25-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="dbc25-228">Zazwyczaj formanty windows forms, które są zarządzane otoki dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]win32 typowe formanty są obsługiwane przez .</span><span class="sxs-lookup"><span data-stu-id="dbc25-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="dbc25-229">Obsługiwane są następujące formanty.</span><span class="sxs-lookup"><span data-stu-id="dbc25-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="dbc25-230">Nazwa klasy</span><span class="sxs-lookup"><span data-stu-id="dbc25-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="dbc25-231">Button</span><span class="sxs-lookup"><span data-stu-id="dbc25-231">Button</span></span>|  
|<span data-ttu-id="dbc25-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-232">CheckBox</span></span>|  
|<span data-ttu-id="dbc25-233">Checkedlistbox</span><span class="sxs-lookup"><span data-stu-id="dbc25-233">CheckedListBox</span></span>|  
|<span data-ttu-id="dbc25-234">Colordialog</span><span class="sxs-lookup"><span data-stu-id="dbc25-234">ColorDialog</span></span>|  
|<span data-ttu-id="dbc25-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-235">ComboBox</span></span>|  
|<span data-ttu-id="dbc25-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="dbc25-236">FolderBrowser</span></span>|  
|<span data-ttu-id="dbc25-237">Fontdialog</span><span class="sxs-lookup"><span data-stu-id="dbc25-237">FontDialog</span></span>|  
|<span data-ttu-id="dbc25-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-238">GroupBox</span></span>|  
|<span data-ttu-id="dbc25-239">Hscrollbar</span><span class="sxs-lookup"><span data-stu-id="dbc25-239">HscrollBar</span></span>|  
|<span data-ttu-id="dbc25-240">Imagelist</span><span class="sxs-lookup"><span data-stu-id="dbc25-240">ImageList</span></span>|  
|<span data-ttu-id="dbc25-241">Label</span><span class="sxs-lookup"><span data-stu-id="dbc25-241">Label</span></span>|  
|<span data-ttu-id="dbc25-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-242">ListBox</span></span>|  
|<span data-ttu-id="dbc25-243">ListView</span><span class="sxs-lookup"><span data-stu-id="dbc25-243">ListView</span></span>|  
|<span data-ttu-id="dbc25-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="dbc25-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="dbc25-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="dbc25-245">MonthCalendar</span></span>|  
|<span data-ttu-id="dbc25-246">Notifyicon</span><span class="sxs-lookup"><span data-stu-id="dbc25-246">NotifyIcon</span></span>|  
|<span data-ttu-id="dbc25-247">Openfiledialog</span><span class="sxs-lookup"><span data-stu-id="dbc25-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="dbc25-248">Pagesetupdialog</span><span class="sxs-lookup"><span data-stu-id="dbc25-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="dbc25-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="dbc25-249">PrintDialog</span></span>|  
|<span data-ttu-id="dbc25-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="dbc25-250">ProgressBar</span></span>|  
|<span data-ttu-id="dbc25-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="dbc25-251">RadioButton</span></span>|  
|<span data-ttu-id="dbc25-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-252">RichTextBox</span></span>|  
|<span data-ttu-id="dbc25-253">Savefiledialog</span><span class="sxs-lookup"><span data-stu-id="dbc25-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="dbc25-254">Scrollablecontrol</span><span class="sxs-lookup"><span data-stu-id="dbc25-254">ScrollableControl</span></span>|  
|<span data-ttu-id="dbc25-255">Soundplayer</span><span class="sxs-lookup"><span data-stu-id="dbc25-255">SoundPlayer</span></span>|  
|<span data-ttu-id="dbc25-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="dbc25-256">StatusBar</span></span>|  
|<span data-ttu-id="dbc25-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="dbc25-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="dbc25-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="dbc25-258">TextBox</span></span>|  
|<span data-ttu-id="dbc25-259">Czasomierz</span><span class="sxs-lookup"><span data-stu-id="dbc25-259">Timer</span></span>|  
|<span data-ttu-id="dbc25-260">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="dbc25-260">Toolbar</span></span>|  
|<span data-ttu-id="dbc25-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="dbc25-261">ToolTip</span></span>|  
|<span data-ttu-id="dbc25-262">Trackbar</span><span class="sxs-lookup"><span data-stu-id="dbc25-262">TrackBar</span></span>|  
|<span data-ttu-id="dbc25-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="dbc25-263">TreeView</span></span>|  
|<span data-ttu-id="dbc25-264">Vscrollbar</span><span class="sxs-lookup"><span data-stu-id="dbc25-264">VscrollBar</span></span>|  
|<span data-ttu-id="dbc25-265">Webbrowser</span><span class="sxs-lookup"><span data-stu-id="dbc25-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="dbc25-266">Poniższe formanty [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] są widoczne tylko za pośrednictwem ich obsługi dostępności microsoft active.</span><span class="sxs-lookup"><span data-stu-id="dbc25-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="dbc25-267">Niektóre funkcje mogą być niedostępne.</span><span class="sxs-lookup"><span data-stu-id="dbc25-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="dbc25-268">Nazwa formantu</span><span class="sxs-lookup"><span data-stu-id="dbc25-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="dbc25-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="dbc25-269">BindingSource</span></span>|  
|<span data-ttu-id="dbc25-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="dbc25-270">DataGrid</span></span>|  
|<span data-ttu-id="dbc25-271">Datagridview</span><span class="sxs-lookup"><span data-stu-id="dbc25-271">DataGridView</span></span>|  
|<span data-ttu-id="dbc25-272">Nawigator danych</span><span class="sxs-lookup"><span data-stu-id="dbc25-272">DataNavigator</span></span>|  
|<span data-ttu-id="dbc25-273">Domainupdown</span><span class="sxs-lookup"><span data-stu-id="dbc25-273">DomainUpDown</span></span>|  
|<span data-ttu-id="dbc25-274">Errorprovider</span><span class="sxs-lookup"><span data-stu-id="dbc25-274">ErrorProvider</span></span>|  
|<span data-ttu-id="dbc25-275">Flowlayoutpanel</span><span class="sxs-lookup"><span data-stu-id="dbc25-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="dbc25-276">Formularz</span><span class="sxs-lookup"><span data-stu-id="dbc25-276">Form</span></span>|  
|<span data-ttu-id="dbc25-277">Linklabel</span><span class="sxs-lookup"><span data-stu-id="dbc25-277">LinkLabel</span></span>|  
|<span data-ttu-id="dbc25-278">Helpprovider</span><span class="sxs-lookup"><span data-stu-id="dbc25-278">HelpProvider</span></span>|  
|<span data-ttu-id="dbc25-279">Maskedtextbox</span><span class="sxs-lookup"><span data-stu-id="dbc25-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="dbc25-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="dbc25-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="dbc25-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="dbc25-281">NumericUpDown</span></span>|  
|<span data-ttu-id="dbc25-282">Panel</span><span class="sxs-lookup"><span data-stu-id="dbc25-282">Panel</span></span>|  
|<span data-ttu-id="dbc25-283">Picturebox</span><span class="sxs-lookup"><span data-stu-id="dbc25-283">PictureBox</span></span>|  
|<span data-ttu-id="dbc25-284">Printdocument</span><span class="sxs-lookup"><span data-stu-id="dbc25-284">PrintDocument</span></span>|  
|<span data-ttu-id="dbc25-285">PrintPreview-Sterowanie</span><span class="sxs-lookup"><span data-stu-id="dbc25-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="dbc25-286">Okno dialogowe PrintPreview</span><span class="sxs-lookup"><span data-stu-id="dbc25-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="dbc25-287">Propertygrid</span><span class="sxs-lookup"><span data-stu-id="dbc25-287">PropertyGrid</span></span>|  
|<span data-ttu-id="dbc25-288">Usercontrol</span><span class="sxs-lookup"><span data-stu-id="dbc25-288">UserControl</span></span>|  
|<span data-ttu-id="dbc25-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dbc25-289">ToolStrip</span></span>|  
|<span data-ttu-id="dbc25-290">Tablelayoutpanel</span><span class="sxs-lookup"><span data-stu-id="dbc25-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="dbc25-291">Panel SplitContainer/Splitter</span><span class="sxs-lookup"><span data-stu-id="dbc25-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="dbc25-292">Rozdzielacz</span><span class="sxs-lookup"><span data-stu-id="dbc25-292">Splitter</span></span>|  
|<span data-ttu-id="dbc25-293">SpływyKontainer</span><span class="sxs-lookup"><span data-stu-id="dbc25-293">RaftingContainer</span></span>|  
|<span data-ttu-id="dbc25-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="dbc25-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbc25-295">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbc25-295">See also</span></span>

- [<span data-ttu-id="dbc25-296">Typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="dbc25-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
