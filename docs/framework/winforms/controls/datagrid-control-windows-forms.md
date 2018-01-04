---
title: "DataGrid — Formant (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0ad5ba4bdd283e411c746906adfed53282c55b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="5de00-102">DataGrid — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="5de00-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="5de00-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do `DataGrid` kontrolować; jednak `DataGrid` formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="5de00-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="5de00-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5de00-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="5de00-105">Formularze systemu Windows `DataGrid` kontroli udostępnia interfejs użytkownika do [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zestawów danych, wyświetlanie danych tabelarycznych i włączenie aktualizacji do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5de00-105">The Windows Forms `DataGrid` control provides a user interface to [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="5de00-106">Gdy `DataGrid` formantu ma ustawioną wartość poprawnego źródła danych, kontroli jest automatycznie wypełniania, tworzenie kolumn i wierszy na podstawie kształtu danych.</span><span class="sxs-lookup"><span data-stu-id="5de00-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="5de00-107">`DataGrid` Formant może służyć do wyświetlania pojedynczej tabeli lub hierarchicznych relacji pomiędzy tabelami.</span><span class="sxs-lookup"><span data-stu-id="5de00-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5de00-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5de00-108">In This Section</span></span>  
 [<span data-ttu-id="5de00-109">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="5de00-109">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="5de00-110">Zawiera opis podstawowych funkcji `DataGrid` formantu.</span><span class="sxs-lookup"><span data-stu-id="5de00-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5de00-111">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="5de00-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="5de00-112">Opisuje sposób dodawania tabel i kolumn do `DataGrid` kontrolować za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="5de00-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="5de00-113">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5de00-114">Opisuje sposób dodawania tabel i kolumn do `DataGrid` kontrolować programowo.</span><span class="sxs-lookup"><span data-stu-id="5de00-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="5de00-115">Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="5de00-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="5de00-116">Opisuje sposób wiązania [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zestawu danych na `DataGrid` kontrolować za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="5de00-116">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="5de00-117">Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="5de00-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="5de00-118">Opisuje sposób wiązania [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zestawu danych na `DataGrid` formantu.</span><span class="sxs-lookup"><span data-stu-id="5de00-118">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5de00-119">Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="5de00-120">Zawiera opis sposobu zmiany danych programowo w `DataGrid` formantu.</span><span class="sxs-lookup"><span data-stu-id="5de00-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5de00-121">Instrukcje: tworzenie list wzorzec-szczegół za pomocą kontrolki DataGrid formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="5de00-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="5de00-122">Opisuje sposób wyświetlania dwóch tabel, powiązane z relacji nadrzędny/podrzędny w dwóch oddzielnych `DataGrid` formanty za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="5de00-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="5de00-123">Porady: Tworzenie listy danych głównych za pomocą formantu DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5de00-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="5de00-124">Opisuje sposób wyświetlania dwóch tabel, powiązane z relacji nadrzędny/podrzędny w dwóch oddzielnych `DataGrid` kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5de00-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="5de00-125">Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5de00-126">Opisuje sposób usuwania kolumny w `DataGrid` formantu.</span><span class="sxs-lookup"><span data-stu-id="5de00-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5de00-127">Instrukcje: formatowanie kontrolki DataGrid formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="5de00-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="5de00-128">Zawiera opis sposobu zmiany właściwości związanych z wygląd `DataGrid` kontrolować za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="5de00-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="5de00-129">Instrukcje: formatowanie kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-129">How to: Format the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5de00-130">Zawiera opis sposobu zmiany właściwości związanych z wygląd `DataGrid` formantu.</span><span class="sxs-lookup"><span data-stu-id="5de00-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5de00-131">Skróty klawiaturowe dla kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5de00-132">Wyświetla skróty do przechodzenia między `DataGrid` formantu.</span><span class="sxs-lookup"><span data-stu-id="5de00-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5de00-133">Instrukcje: odpowiadanie na kliknięcia w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5de00-134">Opisuje sposób określania, które komórki, a użytkownik kliknął przycisk w `DataGrid` formantu.</span><span class="sxs-lookup"><span data-stu-id="5de00-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5de00-135">Instrukcje: sprawdzanie poprawności danych wejściowych w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5de00-136">Opisuje sposób sprawdzania poprawności danych wejściowych w zestawie danych powiązany `DataGrid` formantu.</span><span class="sxs-lookup"><span data-stu-id="5de00-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5de00-137">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="5de00-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="5de00-138">Zawiera omówienie <xref:System.Windows.Forms.DataGrid> klasy.</span><span class="sxs-lookup"><span data-stu-id="5de00-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="5de00-139">Zawiera szczegółowe informacje o użyciu tej właściwości można powiązać <xref:System.Windows.Forms.DataGrid> formantu danych.</span><span class="sxs-lookup"><span data-stu-id="5de00-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5de00-140">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5de00-140">Related Sections</span></span>  
 [<span data-ttu-id="5de00-141">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-141">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="5de00-142">Zawiera łącza do tematów w powiązaniu danych w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5de00-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5de00-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5de00-143">See Also</span></span>  
 [<span data-ttu-id="5de00-144">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5de00-144">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="5de00-145">Różnice między kontrolkami DataGridView i DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5de00-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
