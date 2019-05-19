---
title: DataGrid — Formant (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: 5a69605901eef7366c7a9ff9930e5f4ec6cece23
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878775"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="642f0-102">DataGrid — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="642f0-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="642f0-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do `DataGrid` kontrolować; jednak `DataGrid` kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="642f0-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="642f0-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="642f0-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="642f0-105">Formularze Windows `DataGrid` kontroli udostępnia interfejs użytkownika z zestawami danych ADO.NET, wyświetlając dane tabelaryczne i włączenie aktualizacji do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="642f0-105">The Windows Forms `DataGrid` control provides a user interface to ADO.NET datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="642f0-106">Gdy `DataGrid` kontrolki jest ustawiona na poprawnego źródła danych, kontrolka zostanie wypełniona automatycznie, tworzenie kolumn i wierszy, oparte na kształt danych.</span><span class="sxs-lookup"><span data-stu-id="642f0-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="642f0-107">`DataGrid` Kontroli może służyć do wyświetlania pojedynczej tabeli lub hierarchicznych relacji między tabelami.</span><span class="sxs-lookup"><span data-stu-id="642f0-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="642f0-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="642f0-108">In This Section</span></span>  
 [<span data-ttu-id="642f0-109">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="642f0-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="642f0-110">W tym artykule opisano podstawowe funkcje `DataGrid` kontroli.</span><span class="sxs-lookup"><span data-stu-id="642f0-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="642f0-111">Instrukcje: Dodawanie tabel i kolumn do formantu DataGrid formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="642f0-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="642f0-112">Zawiera opis sposobu dodawania tabel i kolumn do `DataGrid` kontrolować za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="642f0-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="642f0-113">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="642f0-114">Zawiera opis sposobu dodawania tabel i kolumn do `DataGrid` programistycznie sterować.</span><span class="sxs-lookup"><span data-stu-id="642f0-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="642f0-115">Instrukcje: Powiązywanie formantu DataGrid formularzy Windows ze źródłem danych przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="642f0-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="642f0-116">Opis sposobu tworzenia powiązania zestawu danych programu ADO.NET, aby `DataGrid` kontrolować za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="642f0-116">Describes how to bind an ADO.NET dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="642f0-117">Instrukcje: Powiązywanie formantu DataGrid formularzy Windows ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="642f0-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="642f0-118">Opis sposobu tworzenia powiązania zestawu danych programu ADO.NET, aby `DataGrid` kontroli.</span><span class="sxs-lookup"><span data-stu-id="642f0-118">Describes how to bind an ADO.NET dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="642f0-119">Instrukcje: Zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="642f0-120">W tym artykule opisano sposób zmiany danych, Programując `DataGrid` kontroli.</span><span class="sxs-lookup"><span data-stu-id="642f0-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="642f0-121">Instrukcje: Tworzenie list wzorzec szczegół za pomocą formantu DataGrid formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="642f0-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="642f0-122">W tym artykule opisano sposób wyświetlania tabel, powiązane z relacją nadrzędny/podrzędny w dwóch oddzielnych `DataGrid` kontrolki za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="642f0-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="642f0-123">Instrukcje: Tworzenie list wzorzec szczegół za pomocą kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="642f0-124">W tym artykule opisano sposób wyświetlania tabel, powiązane z relacją nadrzędny/podrzędny w dwóch oddzielnych `DataGrid` kontrolki.</span><span class="sxs-lookup"><span data-stu-id="642f0-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="642f0-125">Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="642f0-126">Opisuje sposób usuwania kolumny w `DataGrid` kontroli.</span><span class="sxs-lookup"><span data-stu-id="642f0-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="642f0-127">Instrukcje: Formatowanie kontrolki DataGrid formularzy Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="642f0-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="642f0-128">Zawiera opis sposobu zmiany właściwości powiązane z wyglądem `DataGrid` kontrolować za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="642f0-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="642f0-129">Instrukcje: Formatowanie kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="642f0-130">Zawiera opis sposobu zmiany właściwości powiązane z wyglądem `DataGrid` kontroli.</span><span class="sxs-lookup"><span data-stu-id="642f0-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="642f0-131">Skróty klawiaturowe dla kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="642f0-132">Wyświetla skróty do przechodzenia między `DataGrid` kontroli.</span><span class="sxs-lookup"><span data-stu-id="642f0-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="642f0-133">Instrukcje: Odpowiadanie na kliknięcia w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="642f0-134">Opisuje sposób określenia komórki, która użytkownika został kliknięty w `DataGrid` kontroli.</span><span class="sxs-lookup"><span data-stu-id="642f0-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="642f0-135">Instrukcje: Sprawdzanie poprawności danych wejściowych za pomocą kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="642f0-136">W tym artykule opisano sposób sprawdzania poprawności danych wejściowych w zestawie danych powiązany z `DataGrid` kontroli.</span><span class="sxs-lookup"><span data-stu-id="642f0-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="642f0-137">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="642f0-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="642f0-138">Zawiera omówienie <xref:System.Windows.Forms.DataGrid> klasy.</span><span class="sxs-lookup"><span data-stu-id="642f0-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="642f0-139">Zawiera szczegółowe informacje o korzystaniu z tej właściwości można powiązać <xref:System.Windows.Forms.DataGrid> kontrolki z danymi.</span><span class="sxs-lookup"><span data-stu-id="642f0-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="642f0-140">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="642f0-140">Related Sections</span></span>  
 [<span data-ttu-id="642f0-141">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="642f0-142">Zawiera łącza do tematów w powiązaniu danych w formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="642f0-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="642f0-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="642f0-143">See also</span></span>

- [<span data-ttu-id="642f0-144">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="642f0-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="642f0-145">Różnice między kontrolkami DataGridView i DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="642f0-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
