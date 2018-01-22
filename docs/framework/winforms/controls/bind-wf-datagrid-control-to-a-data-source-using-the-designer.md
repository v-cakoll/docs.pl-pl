---
title: "Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3913ffe046bb55e31d8be223061af61371a47418
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="05616-102">Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="05616-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="05616-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="05616-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="05616-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="05616-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="05616-105">Formularze systemu Windows <xref:System.Windows.Forms.DataGrid> kontrolki przeznaczone do wyświetlania informacji ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="05616-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="05616-106">Powiązywanie formantu w czasie projektowania, ustawiając <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości, lub w czasie wykonywania, wywołując <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="05616-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="05616-107">Choć można wyświetlać danych z różnych źródeł danych, najbardziej typowe źródła są widoków danych i zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="05616-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="05616-108">Jeśli źródło danych jest dostępne w czasie projektowania — na przykład, jeśli formularz zawiera wystąpienia wartość dataset lub widok danych — siatki można powiązać źródła danych w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="05616-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="05616-109">Następnie możesz przeglądać dane wyglądu w siatce.</span><span class="sxs-lookup"><span data-stu-id="05616-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="05616-110">Siatka może także powiązać programowo, w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05616-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="05616-111">Jest to przydatne, jeśli chcesz ustawić źródło danych na podstawie informacji, które pojawia się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="05616-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="05616-112">Na przykład aplikacja może pozwolić użytkownika, określ nazwę tabeli, aby wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="05616-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="05616-113">Konieczne jest również w sytuacji, gdy źródło danych nie istnieje w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="05616-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="05616-114">W tym źródeł danych, takich jak tablic, kolekcje nietypizowane zbiory danych i czytniki danych.</span><span class="sxs-lookup"><span data-stu-id="05616-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="05616-115">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="05616-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="05616-116">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="05616-116">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="05616-117">W [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> formant nie ma na liście **przybornika** domyślnie.</span><span class="sxs-lookup"><span data-stu-id="05616-117">In [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="05616-118">Uzyskać informacje dotyczące dodawania go, zobacz [porady: Dodawanie elementów do przybornika](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).</span><span class="sxs-lookup"><span data-stu-id="05616-118">For information about adding it, see [How to: Add Items to the Toolbox](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span> <span data-ttu-id="05616-119">Ponadto w [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], można użyć **źródeł danych** okna dla powiązania danych czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="05616-119">Additionally in [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="05616-120">Aby uzyskać więcej informacji, zobacz [powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="05616-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05616-121">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="05616-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="05616-122">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="05616-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="05616-123">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="05616-123">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="05616-124">Do wiązania danych formantu DataGrid do pojedynczej tabeli w Projektancie</span><span class="sxs-lookup"><span data-stu-id="05616-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1.  <span data-ttu-id="05616-125">Ustawianie formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="05616-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="05616-126">Jeśli źródło danych jest zestawu danych, ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości do nazwy tabeli, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="05616-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3.  <span data-ttu-id="05616-127">Jeśli źródło danych jest wartość dataset lub widok danych na podstawie tabeli zestawu danych, należy dodać kodu do formularza, aby wypełnić dataset.</span><span class="sxs-lookup"><span data-stu-id="05616-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="05616-128">Dokładnego kodu, używanego zależy od tego, gdzie zestawu danych jest pobieranie danych.</span><span class="sxs-lookup"><span data-stu-id="05616-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="05616-129">Jeśli jest on wypełnione zestawu danych bezpośrednio z bazy danych, należy zwykle wywołują `Fill` metody adapter danych, jak w poniższym przykładzie kodu, który wypełnia zestawu danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="05616-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  <span data-ttu-id="05616-130">(Opcjonalnie) Dodaj style właściwe tabeli i Style kolumn do tabeli.</span><span class="sxs-lookup"><span data-stu-id="05616-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="05616-131">Jeśli nie ma żadnych stylów tabeli, zobaczysz tabeli, ale z minimalnym formatowanie i widoczne wszystkie kolumny.</span><span class="sxs-lookup"><span data-stu-id="05616-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="05616-132">Do wiązania danych formantu DataGrid z wieloma tabelami w zestawie danych w Projektancie</span><span class="sxs-lookup"><span data-stu-id="05616-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1.  <span data-ttu-id="05616-133">Ustawianie formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="05616-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="05616-134">Jeśli zestaw danych zawiera tabele powiązane (to znaczy, jeśli zawiera obiekt relacji), ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości do nazwy tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="05616-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3.  <span data-ttu-id="05616-135">Napisać kod, aby wypełnić dataset.</span><span class="sxs-lookup"><span data-stu-id="05616-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05616-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05616-136">See Also</span></span>  
 [<span data-ttu-id="05616-137">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="05616-137">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="05616-138">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05616-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="05616-139">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="05616-139">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="05616-140">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05616-140">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="05616-141">Uzyskiwanie dostępu do danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="05616-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
