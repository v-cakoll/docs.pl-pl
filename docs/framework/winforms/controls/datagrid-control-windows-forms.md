---
title: DataGrid, kontrolka
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: efcc8770232f657c13135cefb4027f814d4d7d19
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742515"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="9ad06-102">DataGrid — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="9ad06-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="9ad06-103">Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki `DataGrid`; Niemniej jednak kontrolka `DataGrid` jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="9ad06-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9ad06-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9ad06-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9ad06-105">Kontrolka `DataGrid` Windows Forms udostępnia interfejs użytkownika, który ADO.NET zestawy danych, wyświetlając dane tabelaryczne i włączając aktualizacje dla źródła danych.</span><span class="sxs-lookup"><span data-stu-id="9ad06-105">The Windows Forms `DataGrid` control provides a user interface to ADO.NET datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="9ad06-106">Gdy kontrolka `DataGrid` jest ustawiona na prawidłowe źródło danych, formant jest wypełniany automatycznie, tworzenie kolumn i wierszy na podstawie kształtu danych.</span><span class="sxs-lookup"><span data-stu-id="9ad06-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="9ad06-107">Kontrolka `DataGrid` może służyć do wyświetlania pojedynczej tabeli lub hierarchicznych relacji między zestawem tabel.</span><span class="sxs-lookup"><span data-stu-id="9ad06-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ad06-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9ad06-108">In This Section</span></span>  
 [<span data-ttu-id="9ad06-109">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9ad06-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="9ad06-110">Opisuje podstawowe funkcje formantu `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="9ad06-111">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9ad06-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="9ad06-112">Opisuje sposób dodawania tabel i kolumn do kontrolki `DataGrid` przy użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="9ad06-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="9ad06-113">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="9ad06-114">Zawiera opis sposobu dodawania tabel i kolumn do kontrolki `DataGrid` programowo.</span><span class="sxs-lookup"><span data-stu-id="9ad06-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="9ad06-115">Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9ad06-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="9ad06-116">Opisuje sposób powiązania zestawu danych ADO.NET z kontrolką `DataGrid` przy użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="9ad06-116">Describes how to bind an ADO.NET dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="9ad06-117">Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="9ad06-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="9ad06-118">Opisuje sposób powiązania zestawu danych ADO.NET z kontrolką `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-118">Describes how to bind an ADO.NET dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="9ad06-119">Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="9ad06-120">Opisuje sposób programistycznego zmieniania danych w kontrolce `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="9ad06-121">Instrukcje: tworzenie list wzorzec-szczegół za pomocą kontrolki DataGrid formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9ad06-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="9ad06-122">Opisuje, jak wyświetlić dwie tabele, powiązane z relacją nadrzędny/podrzędny, w dwóch oddzielnych kontrolkach `DataGrid` przy użyciu projektanta.</span><span class="sxs-lookup"><span data-stu-id="9ad06-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="9ad06-123">Instrukcje: Tworzenie list Master-Details za pomocą kontrolki DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="9ad06-124">Opisuje sposób wyświetlania dwóch tabel, powiązane z relacją nadrzędny/podrzędny, w dwóch oddzielnych kontrolkach `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="9ad06-125">Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="9ad06-126">Opisuje sposób usuwania kolumn w kontrolce `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="9ad06-127">Instrukcje: formatowanie kontrolki DataGrid formularzy Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9ad06-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="9ad06-128">Opisuje sposób zmiany właściwości związanych z wyglądem formantu `DataGrid` przy użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="9ad06-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="9ad06-129">Instrukcje: formatowanie kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="9ad06-130">Opisuje sposób zmiany właściwości związanych z wyglądem kontrolki `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="9ad06-131">Skróty klawiaturowe dla kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="9ad06-132">Wyświetla skróty do nawigowania po kontrolce `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="9ad06-133">Instrukcje: odpowiadanie na kliknięcia w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="9ad06-134">Opisuje, w jaki sposób określić, która komórka została kliknięta przez użytkownika w kontrolce `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="9ad06-135">Instrukcje: sprawdzanie poprawności danych wejściowych w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="9ad06-136">Opisuje sposób sprawdzania poprawności danych wejściowych w zestawie danych powiązanym z kontrolką `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="9ad06-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9ad06-137">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="9ad06-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="9ad06-138">Zawiera przegląd klasy <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="9ad06-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="9ad06-139">Zawiera szczegółowe informacje o używaniu tej właściwości w celu powiązania formantu <xref:System.Windows.Forms.DataGrid> z danymi.</span><span class="sxs-lookup"><span data-stu-id="9ad06-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9ad06-140">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9ad06-140">Related Sections</span></span>  
 [<span data-ttu-id="9ad06-141">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="9ad06-142">Zawiera łącza do tematów dotyczących powiązań danych w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9ad06-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad06-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ad06-143">See also</span></span>

- [<span data-ttu-id="9ad06-144">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9ad06-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="9ad06-145">Różnice między kontrolkami DataGridView i DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ad06-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
