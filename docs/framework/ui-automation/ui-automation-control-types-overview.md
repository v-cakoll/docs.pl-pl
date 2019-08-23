---
title: Typy formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 5274a2a090669a9c51c5247b68d2b0460625a494
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911568"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="9f4ef-102">Typy formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="9f4ef-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="9f4ef-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9f4ef-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="9f4ef-105">Typy formantów to dobrze znane identyfikatory, których można użyć do wskazania rodzaju kontrolki, która reprezentuje określony element, na przykład pole kombi lub przycisk.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-105">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="9f4ef-106">Dobrze znany identyfikator ułatwia urządzeniom technologii pomocniczych Określanie, jakie typy formantów są dostępne w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i jak korzystać z formantów.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="9f4ef-107">Wymagania dotyczące typów formantów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9f4ef-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="9f4ef-108">Typy formantów zapewniają zestaw warunków, które muszą spełniać dostawcy.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-108">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="9f4ef-109">Po spełnieniu tych warunków formant może używać konkretnej nazwy typu formantu.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="9f4ef-110">Każdy typ formantu ma następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="9f4ef-110">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="9f4ef-111">Wzorce formantów — które wzorce kontroli muszą być obsługiwane, które wzorce kontroli są opcjonalne i które wzorce kontroli nie mogą być obsługiwane przez formant.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-111">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="9f4ef-112">wartości właściwości — wartości właściwości są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-112">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="9f4ef-113">Struktura drzewa — wymagana [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktura drzewa dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-113">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="9f4ef-114">Gdy kontrolka spełnia warunki określonego typu formantu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> wartość właściwości będzie wskazywać ten typ formantu.</span><span class="sxs-lookup"><span data-stu-id="9f4ef-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="9f4ef-115">Bieżące typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="9f4ef-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="9f4ef-116">Poniższa lista zawiera bieżący zestaw [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typów formantów:</span><span class="sxs-lookup"><span data-stu-id="9f4ef-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="9f4ef-117">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Button</span><span class="sxs-lookup"><span data-stu-id="9f4ef-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="9f4ef-118">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Calendar</span><span class="sxs-lookup"><span data-stu-id="9f4ef-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="9f4ef-119">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox</span><span class="sxs-lookup"><span data-stu-id="9f4ef-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="9f4ef-120">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox</span><span class="sxs-lookup"><span data-stu-id="9f4ef-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="9f4ef-121">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataGrid</span><span class="sxs-lookup"><span data-stu-id="9f4ef-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="9f4ef-122">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem</span><span class="sxs-lookup"><span data-stu-id="9f4ef-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="9f4ef-123">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Document</span><span class="sxs-lookup"><span data-stu-id="9f4ef-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="9f4ef-124">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Edit</span><span class="sxs-lookup"><span data-stu-id="9f4ef-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="9f4ef-125">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Group</span><span class="sxs-lookup"><span data-stu-id="9f4ef-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="9f4ef-126">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Header</span><span class="sxs-lookup"><span data-stu-id="9f4ef-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="9f4ef-127">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu HeaderItem</span><span class="sxs-lookup"><span data-stu-id="9f4ef-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="9f4ef-128">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Hyperlink</span><span class="sxs-lookup"><span data-stu-id="9f4ef-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="9f4ef-129">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Image</span><span class="sxs-lookup"><span data-stu-id="9f4ef-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="9f4ef-130">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu List</span><span class="sxs-lookup"><span data-stu-id="9f4ef-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="9f4ef-131">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ListItem</span><span class="sxs-lookup"><span data-stu-id="9f4ef-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="9f4ef-132">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Menu</span><span class="sxs-lookup"><span data-stu-id="9f4ef-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="9f4ef-133">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuBar</span><span class="sxs-lookup"><span data-stu-id="9f4ef-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="9f4ef-134">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem</span><span class="sxs-lookup"><span data-stu-id="9f4ef-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="9f4ef-135">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Pane</span><span class="sxs-lookup"><span data-stu-id="9f4ef-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="9f4ef-136">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar</span><span class="sxs-lookup"><span data-stu-id="9f4ef-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="9f4ef-137">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu RadioButton</span><span class="sxs-lookup"><span data-stu-id="9f4ef-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="9f4ef-138">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar</span><span class="sxs-lookup"><span data-stu-id="9f4ef-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="9f4ef-139">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Separator</span><span class="sxs-lookup"><span data-stu-id="9f4ef-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="9f4ef-140">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Suwak</span><span class="sxs-lookup"><span data-stu-id="9f4ef-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="9f4ef-141">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Spinner</span><span class="sxs-lookup"><span data-stu-id="9f4ef-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="9f4ef-142">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton</span><span class="sxs-lookup"><span data-stu-id="9f4ef-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="9f4ef-143">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar</span><span class="sxs-lookup"><span data-stu-id="9f4ef-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="9f4ef-144">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tab</span><span class="sxs-lookup"><span data-stu-id="9f4ef-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="9f4ef-145">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TabItem</span><span class="sxs-lookup"><span data-stu-id="9f4ef-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="9f4ef-146">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Table</span><span class="sxs-lookup"><span data-stu-id="9f4ef-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="9f4ef-147">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Text</span><span class="sxs-lookup"><span data-stu-id="9f4ef-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="9f4ef-148">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Thumb</span><span class="sxs-lookup"><span data-stu-id="9f4ef-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="9f4ef-149">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TitleBar</span><span class="sxs-lookup"><span data-stu-id="9f4ef-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="9f4ef-150">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar</span><span class="sxs-lookup"><span data-stu-id="9f4ef-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="9f4ef-151">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolTip</span><span class="sxs-lookup"><span data-stu-id="9f4ef-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="9f4ef-152">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tree</span><span class="sxs-lookup"><span data-stu-id="9f4ef-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="9f4ef-153">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TreeItem</span><span class="sxs-lookup"><span data-stu-id="9f4ef-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="9f4ef-154">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Window</span><span class="sxs-lookup"><span data-stu-id="9f4ef-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="9f4ef-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f4ef-155">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
