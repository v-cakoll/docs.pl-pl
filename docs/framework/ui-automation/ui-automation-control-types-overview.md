---
title: Typy formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 643c89e8f6c5e34aa1fb3c5c7c6c750c72046277
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179937"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="2b897-102">Typy formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="2b897-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="2b897-103">Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="2b897-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2b897-104">Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2b897-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="2b897-105">typy formantu są dobrze znane identyfikatory, które mogą służyć do wskazania, jaki rodzaj kontroli reprezentuje określonego elementu, takich jak pole kombi lub przycisk.</span><span class="sxs-lookup"><span data-stu-id="2b897-105">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="2b897-106">Posiadanie dobrze znanego identyfikatora ułatwia urządzeniom technologii ułatwionych określenie, jakie typy [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] formantów są dostępne w formancie i jak wchodzić w interakcje z formantami.</span><span class="sxs-lookup"><span data-stu-id="2b897-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="2b897-107">Wymagania typu kontroli automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="2b897-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="2b897-108">typy kontroli zapewniają zestaw warunków, które dostawcy muszą spełniać.</span><span class="sxs-lookup"><span data-stu-id="2b897-108">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="2b897-109">Po spełnieniu tych warunków formant może użyć nazwy określonego typu formantu.</span><span class="sxs-lookup"><span data-stu-id="2b897-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="2b897-110">Każdy typ formantu ma warunki dla następujących:</span><span class="sxs-lookup"><span data-stu-id="2b897-110">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="2b897-111">wzorce sterowania — które wzorce sterowania muszą być obsługiwane, które wzorce sterowania są opcjonalne i które wzorce sterowania nie mogą być obsługiwane przez formant.</span><span class="sxs-lookup"><span data-stu-id="2b897-111">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="2b897-112">wartości właściwości — które wartości właściwości są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2b897-112">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="2b897-113">struktura drzewa — [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wymagana struktura drzewa dla formantu.</span><span class="sxs-lookup"><span data-stu-id="2b897-113">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="2b897-114">Gdy formant spełnia warunki dla określonego <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> typu formantu, wartość właściwości wskazuje ten typ formantu.</span><span class="sxs-lookup"><span data-stu-id="2b897-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="2b897-115">Bieżące typy sterowania automatyzacją interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="2b897-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="2b897-116">Poniższa lista zawiera bieżący zestaw typów formantów: [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b897-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="2b897-117">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Button</span><span class="sxs-lookup"><span data-stu-id="2b897-117">UI Automation Support for the Button Control Type</span></span>](ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="2b897-118">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Calendar</span><span class="sxs-lookup"><span data-stu-id="2b897-118">UI Automation Support for the Calendar Control Type</span></span>](ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="2b897-119">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox</span><span class="sxs-lookup"><span data-stu-id="2b897-119">UI Automation Support for the CheckBox Control Type</span></span>](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="2b897-120">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox</span><span class="sxs-lookup"><span data-stu-id="2b897-120">UI Automation Support for the ComboBox Control Type</span></span>](ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="2b897-121">Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid</span><span class="sxs-lookup"><span data-stu-id="2b897-121">UI Automation Support for the DataGrid Control Type</span></span>](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="2b897-122">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem</span><span class="sxs-lookup"><span data-stu-id="2b897-122">UI Automation Support for the DataItem Control Type</span></span>](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="2b897-123">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Document</span><span class="sxs-lookup"><span data-stu-id="2b897-123">UI Automation Support for the Document Control Type</span></span>](ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="2b897-124">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Edit</span><span class="sxs-lookup"><span data-stu-id="2b897-124">UI Automation Support for the Edit Control Type</span></span>](ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="2b897-125">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Group</span><span class="sxs-lookup"><span data-stu-id="2b897-125">UI Automation Support for the Group Control Type</span></span>](ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="2b897-126">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Header</span><span class="sxs-lookup"><span data-stu-id="2b897-126">UI Automation Support for the Header Control Type</span></span>](ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="2b897-127">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu HeaderItem</span><span class="sxs-lookup"><span data-stu-id="2b897-127">UI Automation Support for the HeaderItem Control Type</span></span>](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="2b897-128">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Hyperlink</span><span class="sxs-lookup"><span data-stu-id="2b897-128">UI Automation Support for the Hyperlink Control Type</span></span>](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="2b897-129">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Image</span><span class="sxs-lookup"><span data-stu-id="2b897-129">UI Automation Support for the Image Control Type</span></span>](ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="2b897-130">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista</span><span class="sxs-lookup"><span data-stu-id="2b897-130">UI Automation Support for the List Control Type</span></span>](ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="2b897-131">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem</span><span class="sxs-lookup"><span data-stu-id="2b897-131">UI Automation Support for the ListItem Control Type</span></span>](ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="2b897-132">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Menu</span><span class="sxs-lookup"><span data-stu-id="2b897-132">UI Automation Support for the Menu Control Type</span></span>](ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="2b897-133">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuBar</span><span class="sxs-lookup"><span data-stu-id="2b897-133">UI Automation Support for the MenuBar Control Type</span></span>](ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="2b897-134">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem</span><span class="sxs-lookup"><span data-stu-id="2b897-134">UI Automation Support for the MenuItem Control Type</span></span>](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="2b897-135">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Pane</span><span class="sxs-lookup"><span data-stu-id="2b897-135">UI Automation Support for the Pane Control Type</span></span>](ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="2b897-136">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar</span><span class="sxs-lookup"><span data-stu-id="2b897-136">UI Automation Support for the ProgressBar Control Type</span></span>](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="2b897-137">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu RadioButton</span><span class="sxs-lookup"><span data-stu-id="2b897-137">UI Automation Support for the RadioButton Control Type</span></span>](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="2b897-138">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar</span><span class="sxs-lookup"><span data-stu-id="2b897-138">UI Automation Support for the ScrollBar Control Type</span></span>](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="2b897-139">Obsługa automatyzacji interfejsu użytkownika dla formantów typu separator</span><span class="sxs-lookup"><span data-stu-id="2b897-139">UI Automation Support for the Separator Control Type</span></span>](ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="2b897-140">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Suwak</span><span class="sxs-lookup"><span data-stu-id="2b897-140">UI Automation Support for the Slider Control Type</span></span>](ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="2b897-141">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Spinner</span><span class="sxs-lookup"><span data-stu-id="2b897-141">UI Automation Support for the Spinner Control Type</span></span>](ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="2b897-142">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton</span><span class="sxs-lookup"><span data-stu-id="2b897-142">UI Automation Support for the SplitButton Control Type</span></span>](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="2b897-143">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar</span><span class="sxs-lookup"><span data-stu-id="2b897-143">UI Automation Support for the StatusBar Control Type</span></span>](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="2b897-144">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tab</span><span class="sxs-lookup"><span data-stu-id="2b897-144">UI Automation Support for the Tab Control Type</span></span>](ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="2b897-145">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TabItem</span><span class="sxs-lookup"><span data-stu-id="2b897-145">UI Automation Support for the TabItem Control Type</span></span>](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="2b897-146">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Table</span><span class="sxs-lookup"><span data-stu-id="2b897-146">UI Automation Support for the Table Control Type</span></span>](ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="2b897-147">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Text</span><span class="sxs-lookup"><span data-stu-id="2b897-147">UI Automation Support for the Text Control Type</span></span>](ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="2b897-148">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Thumb</span><span class="sxs-lookup"><span data-stu-id="2b897-148">UI Automation Support for the Thumb Control Type</span></span>](ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="2b897-149">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TitleBar</span><span class="sxs-lookup"><span data-stu-id="2b897-149">UI Automation Support for the TitleBar Control Type</span></span>](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="2b897-150">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar</span><span class="sxs-lookup"><span data-stu-id="2b897-150">UI Automation Support for the ToolBar Control Type</span></span>](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="2b897-151">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolTip</span><span class="sxs-lookup"><span data-stu-id="2b897-151">UI Automation Support for the ToolTip Control Type</span></span>](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="2b897-152">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tree</span><span class="sxs-lookup"><span data-stu-id="2b897-152">UI Automation Support for the Tree Control Type</span></span>](ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="2b897-153">Obsługa automatyzacji interfejsu użytkownika dla typu kontrolki TreeItem</span><span class="sxs-lookup"><span data-stu-id="2b897-153">UI Automation Support for the TreeItem Control Type</span></span>](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="2b897-154">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Window</span><span class="sxs-lookup"><span data-stu-id="2b897-154">UI Automation Support for the Window Control Type</span></span>](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b897-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b897-155">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
