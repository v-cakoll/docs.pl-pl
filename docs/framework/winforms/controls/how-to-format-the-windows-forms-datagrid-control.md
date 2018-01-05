---
title: 'Porady: format formantu DataGrid formularzy systemu Windows'
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
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f03f65c878e72a8ec4b7f8bb447a1d6cf820690
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="4d147-102">Porady: format formantu DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4d147-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="4d147-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="4d147-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="4d147-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4d147-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="4d147-105">Stosowanie różnych kolorów do różnych części <xref:System.Windows.Forms.DataGrid> formant może pomóc udostępnia informacje w nim łatwiej odczytywać i interpretowania.</span><span class="sxs-lookup"><span data-stu-id="4d147-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="4d147-106">Kolor można zastosować do wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="4d147-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="4d147-107">Wiersze i kolumny można również ukryte lub pokazane według uznania.</span><span class="sxs-lookup"><span data-stu-id="4d147-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="4d147-108">Istnieją trzy podstawowe aspekty formatowania <xref:System.Windows.Forms.DataGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="4d147-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="4d147-109">Można ustawić właściwości, aby ustanowić domyślny styl wyświetlania danych.</span><span class="sxs-lookup"><span data-stu-id="4d147-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="4d147-110">Z tego elementu bazowego można dostosować sposób wyświetlania określonych tabel w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4d147-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="4d147-111">Na koniec można zmodyfikować kolumny, które są wyświetlane w siatce danych, a także kolory i inne formatowania, który jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="4d147-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="4d147-112">Na etapie wstępnym w formatowaniu siatkę danych, można ustawić właściwości <xref:System.Windows.Forms.DataGrid> samej siebie.</span><span class="sxs-lookup"><span data-stu-id="4d147-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="4d147-113">Te opcje kolor i format tworzą podstawowy, z którego można następnie wprowadzić zmiany w zależności od danych tabele i kolumny wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="4d147-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="4d147-114">Aby ustanowić domyślny styl formantu DataGrid</span><span class="sxs-lookup"><span data-stu-id="4d147-114">To establish a default style for the DataGrid control</span></span>  
  
1.  <span data-ttu-id="4d147-115">Ustaw następujące właściwości odpowiednio:</span><span class="sxs-lookup"><span data-stu-id="4d147-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="4d147-116">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4d147-116">Property</span></span>|<span data-ttu-id="4d147-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4d147-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="4d147-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A> Właściwość określa kolor wierszach parzystych siatki.</span><span class="sxs-lookup"><span data-stu-id="4d147-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="4d147-119">Podczas ustawiania <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwość inny kolor, każdego wiersza jest ustawiona na nowy kolor (wiersze, 1, 3, 5 i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="4d147-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="4d147-120">Kolor tła wierszy parzystych siatki (wiersze, 0, 2, 4, 6 itd.).</span><span class="sxs-lookup"><span data-stu-id="4d147-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="4d147-121">Podczas gdy <xref:System.Windows.Forms.DataGrid.BackColor%2A> i <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości określa kolor wierszy w siatce <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> właściwość określa kolor obszaru nonrow, która jest widoczna tylko siatki jest przewijane w dół lub tylko kilka wierszy są zawarte w Siatka.</span><span class="sxs-lookup"><span data-stu-id="4d147-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="4d147-122">Styl obramowania siatki, jeden z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4d147-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="4d147-123">Kolor tła tytuł okna siatki, które pojawia się powyżej siatki.</span><span class="sxs-lookup"><span data-stu-id="4d147-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="4d147-124">Czcionka podpisu w górnej części siatki.</span><span class="sxs-lookup"><span data-stu-id="4d147-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="4d147-125">Kolor tła tytuł okna siatki.</span><span class="sxs-lookup"><span data-stu-id="4d147-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="4d147-126">Czcionka używana do wyświetlania tekstu w siatce.</span><span class="sxs-lookup"><span data-stu-id="4d147-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="4d147-127">Kolor czcionki wyświetlanego przez dane w wiersze siatki danych.</span><span class="sxs-lookup"><span data-stu-id="4d147-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="4d147-128">Kolor linii siatki w siatce danych.</span><span class="sxs-lookup"><span data-stu-id="4d147-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="4d147-129">Styl linii oddzielających komórki siatki, jeden z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4d147-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="4d147-130">Kolor tła nagłówków wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="4d147-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="4d147-131">Czcionka używana dla nagłówków kolumn.</span><span class="sxs-lookup"><span data-stu-id="4d147-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="4d147-132">Kolor pierwszego planu nagłówków kolumn siatki, w tym tekst nagłówka kolumny i symboli plus/minus (do wyświetlania wielu powiązanych tabel, rozwiń węzeł wierszy).</span><span class="sxs-lookup"><span data-stu-id="4d147-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="4d147-133">Kolor tekstu wszystkich łączy w siatce danych oraz łącza do tabele podrzędne, Nazwa relacji i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="4d147-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="4d147-134">W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4d147-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="4d147-135">W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4d147-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="4d147-136">Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnego za pomocą klasy <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4d147-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="4d147-137">Domyślna szerokość (w pikselach) kolumn w siatce.</span><span class="sxs-lookup"><span data-stu-id="4d147-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="4d147-138">Ta właściwość jest ustawiana przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę), lub właściwość nie odniesie żadnego skutku.</span><span class="sxs-lookup"><span data-stu-id="4d147-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="4d147-139">Nie można ustawić właściwości na wartość mniejszą niż 0.</span><span class="sxs-lookup"><span data-stu-id="4d147-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="4d147-140">Wysokość wiersza (w pikselach) wierszy w siatce.</span><span class="sxs-lookup"><span data-stu-id="4d147-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="4d147-141">Ta właściwość jest ustawiana przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę), lub właściwość nie odniesie żadnego skutku.</span><span class="sxs-lookup"><span data-stu-id="4d147-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="4d147-142">Nie można ustawić właściwości na wartość mniejszą niż 0.</span><span class="sxs-lookup"><span data-stu-id="4d147-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="4d147-143">Szerokość nagłówków wiersza siatki.</span><span class="sxs-lookup"><span data-stu-id="4d147-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="4d147-144">Po zaznaczeniu wiersza lub komórki jest to kolor tła.</span><span class="sxs-lookup"><span data-stu-id="4d147-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="4d147-145">Po zaznaczeniu wiersza lub komórki jest to kolor pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="4d147-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="4d147-146">Należy pamiętać, gdy dostosowywanie kolorów formantów, czy jest możliwe formantu niedostępny z powodu słabej kolory do wyboru (na przykład czerwony i zielony).</span><span class="sxs-lookup"><span data-stu-id="4d147-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="4d147-147">Użyj kolorów, które są dostępne na **kolorów systemu** palety, aby uniknąć tego problemu.</span><span class="sxs-lookup"><span data-stu-id="4d147-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="4d147-148">W poniższych procedurach założono formularz zawiera <xref:System.Windows.Forms.DataGrid> formant powiązany z tabelą danych.</span><span class="sxs-lookup"><span data-stu-id="4d147-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="4d147-149">Aby uzyskać więcej informacji, zobacz [powiązanie formantu DataGrid formularzy systemu Windows ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="4d147-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="4d147-150">Aby ustawić programowo styl tabel i kolumn w tabeli danych</span><span class="sxs-lookup"><span data-stu-id="4d147-150">To set the table and column style of a data table programmatically</span></span>  
  
1.  <span data-ttu-id="4d147-151">Utwórz nowy styl tabeli i ustawienia swoich właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d147-151">Create a new table style and set its properties.</span></span>  
  
2.  <span data-ttu-id="4d147-152">Utwórz styl kolumny i ustawienia swoich właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d147-152">Create a column style and set its properties.</span></span>  
  
3.  <span data-ttu-id="4d147-153">Dodać kolumnę do Kolekcja styli kolumn styl tabeli.</span><span class="sxs-lookup"><span data-stu-id="4d147-153">Add the column style to the table style's column styles collection.</span></span>  
  
4.  <span data-ttu-id="4d147-154">Styl tabeli należy dodać do Kolekcja stylów tabeli siatki danych.</span><span class="sxs-lookup"><span data-stu-id="4d147-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5.  <span data-ttu-id="4d147-155">W poniższym przykładzie Utwórz wystąpienie nowej <xref:System.Windows.Forms.DataGridTableStyle> i ustawić jej <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d147-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6.  <span data-ttu-id="4d147-156">Utwórz nowe wystąpienie klasy **GridColumnStyle** i ustawić jej **MappingName** (i innych układu i wyświetlania właściwości).</span><span class="sxs-lookup"><span data-stu-id="4d147-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7.  <span data-ttu-id="4d147-157">Powtórz kroki od 2 do 6 dla każdego stylu kolumn, który chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="4d147-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="4d147-158">Poniższy przykład przedstawia sposób <xref:System.Windows.Forms.DataGridTextBoxColumn> jest tworzony, ponieważ jest nazwa będzie wyświetlana w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="4d147-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="4d147-159">Ponadto możesz dodać styl kolumny do <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabeli i Dodaj styl tabeli do <xref:System.Windows.Forms.GridTableStylesCollection> siatki danych.</span><span class="sxs-lookup"><span data-stu-id="4d147-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4d147-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d147-160">See Also</span></span>  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [<span data-ttu-id="4d147-161">Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4d147-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="4d147-162">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="4d147-162">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
