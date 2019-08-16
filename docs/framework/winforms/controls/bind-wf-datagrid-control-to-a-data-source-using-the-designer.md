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
ms.openlocfilehash: de8b8d16f45221fbafe9f61ca634f144d8f6f6ae
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040009"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="0479a-102">Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="0479a-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="0479a-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="0479a-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="0479a-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0479a-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="0479a-105">Formant Windows Forms <xref:System.Windows.Forms.DataGrid> jest specjalnie zaprojektowany do wyświetlania informacji ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0479a-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="0479a-106">Formant można powiązać w czasie projektowania przez ustawienie <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości i <xref:System.Windows.Forms.DataGrid.DataMember%2A> lub w czasie <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> wykonywania przez wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="0479a-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="0479a-107">Mimo że można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła to zestawy danych i ich widoki.</span><span class="sxs-lookup"><span data-stu-id="0479a-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>

 <span data-ttu-id="0479a-108">Jeśli źródło danych jest dostępne w czasie projektowania — na przykład, jeśli formularz zawiera wystąpienie zestawu danych lub widok danych — można powiązać siatkę ze źródłem danych w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="0479a-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="0479a-109">Następnie możesz wyświetlić podgląd danych, które będą wyglądały jak w siatce.</span><span class="sxs-lookup"><span data-stu-id="0479a-109">You can then preview what the data will look like in the grid.</span></span>

 <span data-ttu-id="0479a-110">Możesz również programowo powiązać siatkę w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0479a-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="0479a-111">Jest to przydatne, gdy chcesz ustawić źródło danych na podstawie informacji uzyskanych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0479a-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="0479a-112">Na przykład aplikacja może pozwolić, aby użytkownik określił nazwę tabeli do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="0479a-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="0479a-113">Jest to również konieczne w sytuacjach, gdy źródło danych nie istnieje w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="0479a-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="0479a-114">Obejmuje to źródła danych, takie jak tablice, kolekcje, niewpisane zestawy danych i czytniki danych.</span><span class="sxs-lookup"><span data-stu-id="0479a-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>

 <span data-ttu-id="0479a-115">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGrid> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="0479a-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="0479a-116">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0479a-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="0479a-117">W programie Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> formant domyślnie nie znajduje się w **przyborniku** .</span><span class="sxs-lookup"><span data-stu-id="0479a-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="0479a-118">Aby uzyskać informacje o dodawaniu, [zobacz How to: Dodaj elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0479a-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="0479a-119">Ponadto w programie Visual Studio 2005 można użyć okna **źródła danych** dla powiązania danych czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="0479a-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="0479a-120">Aby uzyskać więcej informacji [, zobacz Powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="0479a-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="0479a-121">Do danych — powiązywanie formantu DataGrid z pojedynczą tabelą w projektancie</span><span class="sxs-lookup"><span data-stu-id="0479a-121">To data-bind the DataGrid control to a single table in the designer</span></span>

1. <span data-ttu-id="0479a-122">Ustaw <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwość kontrolki na obiekt zawierający elementy danych, które chcesz powiązać z.</span><span class="sxs-lookup"><span data-stu-id="0479a-122">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="0479a-123">Jeśli źródłem danych jest zestaw danych, ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwość na nazwę tabeli, z którą ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="0479a-123">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>

3. <span data-ttu-id="0479a-124">Jeśli źródłem danych jest zestaw danych lub widok danych oparty na tabeli zestawu danych, Dodaj kod do formularza, aby wypełnić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="0479a-124">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>

     <span data-ttu-id="0479a-125">Dokładny kod, którego używasz, zależy od tego, gdzie zestaw danych pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="0479a-125">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="0479a-126">Jeśli zestaw danych jest wypełniany bezpośrednio z bazy danych, zazwyczaj wywoływana jest `Fill` Metoda adaptera danych, tak jak w poniższym przykładzie kodu, który wypełnia zestaw danych o nazwie: `DsCategories1`</span><span class="sxs-lookup"><span data-stu-id="0479a-126">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. <span data-ttu-id="0479a-127">Obowiązkowe Dodaj odpowiednie style tabeli i Style kolumn do siatki.</span><span class="sxs-lookup"><span data-stu-id="0479a-127">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>

     <span data-ttu-id="0479a-128">Jeśli nie ma żadnych stylów tabeli, zostanie wyświetlona tabela, ale z minimalnym formatowaniem i wszystkimi kolumnami widocznymi.</span><span class="sxs-lookup"><span data-stu-id="0479a-128">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="0479a-129">Do danych — powiązywanie formantu DataGrid z wieloma tabelami w zestawie danych w projektancie</span><span class="sxs-lookup"><span data-stu-id="0479a-129">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>

1. <span data-ttu-id="0479a-130">Ustaw <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwość kontrolki na obiekt zawierający elementy danych, które chcesz powiązać z.</span><span class="sxs-lookup"><span data-stu-id="0479a-130">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="0479a-131">Jeśli zestaw danych zawiera powiązane tabele (czyli jeśli zawiera obiekt relacji), ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwość na nazwę tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="0479a-131">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>

3. <span data-ttu-id="0479a-132">Napisz kod, aby wypełnić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="0479a-132">Write code to fill the dataset.</span></span>

## <a name="see-also"></a><span data-ttu-id="0479a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0479a-133">See also</span></span>

- [<span data-ttu-id="0479a-134">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="0479a-134">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="0479a-135">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0479a-135">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="0479a-136">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0479a-136">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="0479a-137">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0479a-137">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="0479a-138">Uzyskiwanie dostępu do danych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0479a-138">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
