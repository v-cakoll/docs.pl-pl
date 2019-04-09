---
title: 'Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
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
ms.openlocfilehash: a7b03ab5417eacf7962f2a05b674ceb45c7d558c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115734"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="580db-102">Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="580db-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="580db-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="580db-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="580db-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="580db-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="580db-105">Formularze Windows <xref:System.Windows.Forms.DataGrid> kontroli jest specjalnie przeznaczona do wyświetlania informacji ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="580db-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="580db-106">Powiązywanie formantu w czasie projektowania, ustawiając <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości, lub w czasie wykonywania przez wywołanie metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="580db-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="580db-107">Choć można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła są zestawy danych i widokami danych.</span><span class="sxs-lookup"><span data-stu-id="580db-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="580db-108">Jeśli źródło danych jest dostępna w czasie projektowania — na przykład, jeśli formularz zawiera wystąpienie zestawu danych lub widoku danych — Siatka można powiązać ze źródłem danych w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="580db-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="580db-109">Możesz przeglądać dane jak będzie wyglądał w siatce.</span><span class="sxs-lookup"><span data-stu-id="580db-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="580db-110">Możesz również powiązać siatki programowo, w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="580db-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="580db-111">Jest to przydatne, jeśli chcesz ustawić źródło danych, w oparciu o informacje, które otrzymujesz w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="580db-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="580db-112">Na przykład aplikacja może zezwolić użytkownikom na Określ nazwę tabeli, aby wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="580db-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="580db-113">Konieczne jest również w sytuacji, gdy źródło danych nie istnieje w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="580db-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="580db-114">W tym źródeł danych, takich jak tablice, kolekcje, nietypizowanych zbiorów danych oraz czytniki danych.</span><span class="sxs-lookup"><span data-stu-id="580db-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="580db-115">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGrid> kontroli.</span><span class="sxs-lookup"><span data-stu-id="580db-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="580db-116">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="580db-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="580db-117">W programie Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> formantu nie znajduje się w **przybornika** domyślnie.</span><span class="sxs-lookup"><span data-stu-id="580db-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="580db-118">Aby uzyskać informacje dotyczące dodawania go, zobacz [jak: Dodaj elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="580db-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="580db-119">Ponadto w programie Visual Studio 2005, można za pomocą **źródeł danych** okna dla powiązania danych w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="580db-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="580db-120">Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="580db-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="580db-121">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="580db-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="580db-122">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="580db-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="580db-123">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="580db-123">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="580db-124">Aby powiązanie danych kontrolki DataGrid z pojedynczej tabeli w Projektancie</span><span class="sxs-lookup"><span data-stu-id="580db-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1.  <span data-ttu-id="580db-125">Ustaw dla formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="580db-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="580db-126">Jeśli źródło danych zestawu danych, ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwość na nazwę tabeli dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="580db-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3.  <span data-ttu-id="580db-127">W przypadku zestawu danych lub widoku danych, na podstawie tabeli zestawu danych źródła danych należy dodać kod do formularza, aby wypełnić dataset.</span><span class="sxs-lookup"><span data-stu-id="580db-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="580db-128">Dokładne kod, który możesz użyć zależy od tego, gdzie zestaw danych jest wprowadzenie danych.</span><span class="sxs-lookup"><span data-stu-id="580db-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="580db-129">Jeśli trwa wypełnianie zestawu danych bezpośrednio z bazy danych, zazwyczaj wywołujesz `Fill` metody w obrębie adaptera danych, jak w poniższym przykładzie kodu, który wypełnia zestaw danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="580db-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  <span data-ttu-id="580db-130">(Opcjonalnie) Dodaj style odpowiedniej tabeli i kolumn do siatki.</span><span class="sxs-lookup"><span data-stu-id="580db-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="580db-131">Jeśli nie ma żadnych style tabeli, tabeli, zostanie wyświetlony, ale z minimalnym formatowania i widoczne dla wszystkich kolumn.</span><span class="sxs-lookup"><span data-stu-id="580db-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="580db-132">Aby powiązanie danych kontrolki DataGrid z wielu tabel w zestawie danych w Projektancie</span><span class="sxs-lookup"><span data-stu-id="580db-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1.  <span data-ttu-id="580db-133">Ustaw dla formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="580db-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="580db-134">Jeśli zestaw danych zawiera tabele powiązane (to znaczy, jeśli zawiera on obiektu relacji), ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwość na nazwę tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="580db-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3.  <span data-ttu-id="580db-135">Pisz kod, aby wypełnić dataset.</span><span class="sxs-lookup"><span data-stu-id="580db-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="580db-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="580db-136">See also</span></span>

- [<span data-ttu-id="580db-137">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="580db-137">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="580db-138">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="580db-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="580db-139">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="580db-139">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="580db-140">Powiązywanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="580db-140">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="580db-141">Uzyskiwanie dostępu do danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="580db-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
