---
title: "Typy formantów automatyzacji interfejsu użytkownika — omówienie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c1a424f05f2d57f773e8367e102f553d69b7dc22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="809bb-102">Typy kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="809bb-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="809bb-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="809bb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="809bb-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="809bb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="809bb-105">typy formantów są dobrze znane identyfikatory, których można użyć w celu wskazania, jakiego rodzaju kontroli reprezentuje dany element, takich jak pole kombi lub przycisku.</span><span class="sxs-lookup"><span data-stu-id="809bb-105"> control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="809bb-106">Posiadanie dobrze znany identyfikator ułatwia ułatwianiem urządzeń ustalić, jakie typy formantów są dostępne w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] oraz sposoby interakcji z formantami.</span><span class="sxs-lookup"><span data-stu-id="809bb-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="809bb-107">Wymagania typu formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="809bb-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="809bb-108">typy formantów udostępniają zestaw warunków, które muszą spełniać dostawców.</span><span class="sxs-lookup"><span data-stu-id="809bb-108"> control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="809bb-109">Gdy te warunki są spełnione, formantu można używać nazwy typu określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="809bb-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="809bb-110">Każdy typ formantu ma następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="809bb-110">Each control type has conditions for the following:</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="809bb-111">kontrolowanie wzorców — wzorce formantów, które muszą być obsługiwane, kontroli wzorce są opcjonalne i które wzorców formantu nie muszą być obsługiwane przez formant.</span><span class="sxs-lookup"><span data-stu-id="809bb-111"> control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="809bb-112">wartości właściwości — wartości właściwości, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="809bb-112"> property values—which property values are supported.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="809bb-113">Struktura drzewa — wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury formantu drzewa.</span><span class="sxs-lookup"><span data-stu-id="809bb-113"> tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="809bb-114">Jeśli formant spełnia warunki dla określonego typu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> wartość właściwości wskaże, że formant typu.</span><span class="sxs-lookup"><span data-stu-id="809bb-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="809bb-115">Bieżące typy formantów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="809bb-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="809bb-116">Poniższa lista zawiera bieżący zestaw [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolowanie typów:</span><span class="sxs-lookup"><span data-stu-id="809bb-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
-   [<span data-ttu-id="809bb-117">Obsługa automatyzacji interfejsu użytkownika dla formantów typu przycisk</span><span class="sxs-lookup"><span data-stu-id="809bb-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [<span data-ttu-id="809bb-118">Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz</span><span class="sxs-lookup"><span data-stu-id="809bb-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [<span data-ttu-id="809bb-119">Obsługa automatyzacji interfejsu użytkownika dla typu formantu CheckBox</span><span class="sxs-lookup"><span data-stu-id="809bb-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [<span data-ttu-id="809bb-120">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox</span><span class="sxs-lookup"><span data-stu-id="809bb-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [<span data-ttu-id="809bb-121">Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid</span><span class="sxs-lookup"><span data-stu-id="809bb-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [<span data-ttu-id="809bb-122">Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataItem</span><span class="sxs-lookup"><span data-stu-id="809bb-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [<span data-ttu-id="809bb-123">Obsługa automatyzacji interfejsu użytkownika dla formantów typu dokument</span><span class="sxs-lookup"><span data-stu-id="809bb-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [<span data-ttu-id="809bb-124">Obsługa automatyzacji interfejsu użytkownika dla formantów typu Edycja</span><span class="sxs-lookup"><span data-stu-id="809bb-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [<span data-ttu-id="809bb-125">Obsługa automatyzacji interfejsu użytkownika dla formantów typu Grupa</span><span class="sxs-lookup"><span data-stu-id="809bb-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [<span data-ttu-id="809bb-126">Obsługa automatyzacji interfejsu użytkownika dla formantów typu Nagłówek</span><span class="sxs-lookup"><span data-stu-id="809bb-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [<span data-ttu-id="809bb-127">Obsługa automatyzacji interfejsu użytkownika dla typu formantu HeaderItem</span><span class="sxs-lookup"><span data-stu-id="809bb-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [<span data-ttu-id="809bb-128">Obsługa automatyzacji interfejsu użytkownika dla formantów typu hiperłącze</span><span class="sxs-lookup"><span data-stu-id="809bb-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [<span data-ttu-id="809bb-129">Obsługa automatyzacji interfejsu użytkownika dla formantów typu obraz</span><span class="sxs-lookup"><span data-stu-id="809bb-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [<span data-ttu-id="809bb-130">Obsługa automatyzacji interfejsu użytkownika dla formantów typu Lista</span><span class="sxs-lookup"><span data-stu-id="809bb-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [<span data-ttu-id="809bb-131">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem</span><span class="sxs-lookup"><span data-stu-id="809bb-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [<span data-ttu-id="809bb-132">Obsługa automatyzacji interfejsu użytkownika dla formantów typu Menu</span><span class="sxs-lookup"><span data-stu-id="809bb-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [<span data-ttu-id="809bb-133">Obsługa automatyzacji interfejsu użytkownika dla typu formantu MenuBar</span><span class="sxs-lookup"><span data-stu-id="809bb-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [<span data-ttu-id="809bb-134">Obsługa automatyzacji interfejsu użytkownika dla typu formantu MenuItem</span><span class="sxs-lookup"><span data-stu-id="809bb-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [<span data-ttu-id="809bb-135">Obsługa automatyzacji interfejsu użytkownika dla formantów typu okienko</span><span class="sxs-lookup"><span data-stu-id="809bb-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [<span data-ttu-id="809bb-136">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ProgressBar</span><span class="sxs-lookup"><span data-stu-id="809bb-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [<span data-ttu-id="809bb-137">Obsługa automatyzacji interfejsu użytkownika dla typu formantu RadioButton</span><span class="sxs-lookup"><span data-stu-id="809bb-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [<span data-ttu-id="809bb-138">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ScrollBar</span><span class="sxs-lookup"><span data-stu-id="809bb-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [<span data-ttu-id="809bb-139">Obsługa automatyzacji interfejsu użytkownika dla formantów typu Separator</span><span class="sxs-lookup"><span data-stu-id="809bb-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [<span data-ttu-id="809bb-140">Obsługa automatyzacji interfejsu użytkownika dla formantów typu suwak</span><span class="sxs-lookup"><span data-stu-id="809bb-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [<span data-ttu-id="809bb-141">Obsługa automatyzacji interfejsu użytkownika dla formantów typu pokrętło</span><span class="sxs-lookup"><span data-stu-id="809bb-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [<span data-ttu-id="809bb-142">Obsługa automatyzacji interfejsu użytkownika dla typu formantu SplitButton</span><span class="sxs-lookup"><span data-stu-id="809bb-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [<span data-ttu-id="809bb-143">Obsługa automatyzacji interfejsu użytkownika dla typu formantu StatusBar</span><span class="sxs-lookup"><span data-stu-id="809bb-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [<span data-ttu-id="809bb-144">Obsługa automatyzacji interfejsu użytkownika dla formantów typu karta</span><span class="sxs-lookup"><span data-stu-id="809bb-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [<span data-ttu-id="809bb-145">Obsługa automatyzacji interfejsu użytkownika dla typu formantu TabItem</span><span class="sxs-lookup"><span data-stu-id="809bb-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [<span data-ttu-id="809bb-146">Obsługa automatyzacji interfejsu użytkownika dla formantów typu Tabela</span><span class="sxs-lookup"><span data-stu-id="809bb-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [<span data-ttu-id="809bb-147">Obsługa automatyzacji interfejsu użytkownika dla formantów typu tekst</span><span class="sxs-lookup"><span data-stu-id="809bb-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [<span data-ttu-id="809bb-148">Obsługa automatyzacji interfejsu użytkownika dla formantów typu Miniatura</span><span class="sxs-lookup"><span data-stu-id="809bb-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [<span data-ttu-id="809bb-149">Obsługa automatyzacji interfejsu użytkownika dla typu formantu TitleBar</span><span class="sxs-lookup"><span data-stu-id="809bb-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [<span data-ttu-id="809bb-150">Obsługa automatyzacji interfejsu użytkownika dla typu formantu paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="809bb-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [<span data-ttu-id="809bb-151">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ToolTip</span><span class="sxs-lookup"><span data-stu-id="809bb-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [<span data-ttu-id="809bb-152">Obsługa automatyzacji interfejsu użytkownika dla typu formantu drzewa</span><span class="sxs-lookup"><span data-stu-id="809bb-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [<span data-ttu-id="809bb-153">Obsługa automatyzacji interfejsu użytkownika dla typu formantu TreeItem</span><span class="sxs-lookup"><span data-stu-id="809bb-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [<span data-ttu-id="809bb-154">Obsługa automatyzacji interfejsu użytkownika dla formantów typu okno</span><span class="sxs-lookup"><span data-stu-id="809bb-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="809bb-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="809bb-155">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType>
