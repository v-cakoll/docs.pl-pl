---
title: 'Instrukcje: format kontrolki DataGrid formularzy systemu Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 99acef0a7b29228ddf0406352ff5a88b77294b00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966672"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="7e15e-102">Instrukcje: format kontrolki DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7e15e-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="7e15e-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="7e15e-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="7e15e-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7e15e-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="7e15e-105">Stosowanie różnych kolorów do różnych części <xref:System.Windows.Forms.DataGrid> formantu może pomóc w ułatwianiu odczytywania i interpretowania informacji.</span><span class="sxs-lookup"><span data-stu-id="7e15e-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="7e15e-106">Kolor można zastosować do wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="7e15e-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="7e15e-107">Wiersze i kolumny można także ukryć lub pokazać według własnego uznania.</span><span class="sxs-lookup"><span data-stu-id="7e15e-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="7e15e-108">Istnieją trzy podstawowe aspekty formatowania <xref:System.Windows.Forms.DataGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="7e15e-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="7e15e-109">Można ustawić właściwości, aby określić domyślny styl, w którym są wyświetlane dane.</span><span class="sxs-lookup"><span data-stu-id="7e15e-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="7e15e-110">Z tej bazy można następnie dostosować sposób wyświetlania niektórych tabel w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7e15e-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="7e15e-111">Na koniec można modyfikować, które kolumny są wyświetlane w siatce danych, a także kolory i inne wyświetlane formatowanie.</span><span class="sxs-lookup"><span data-stu-id="7e15e-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="7e15e-112">Jako pierwszy krok formatowania siatki danych można ustawić właściwości <xref:System.Windows.Forms.DataGrid> samej siebie.</span><span class="sxs-lookup"><span data-stu-id="7e15e-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="7e15e-113">Opcje tego koloru i formatu stanowią podstawę, z której można wprowadzać zmiany w zależności od wyświetlanych tabel i kolumn danych.</span><span class="sxs-lookup"><span data-stu-id="7e15e-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="7e15e-114">Aby określić styl domyślny dla kontrolki DataGrid</span><span class="sxs-lookup"><span data-stu-id="7e15e-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="7e15e-115">Ustaw odpowiednio następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7e15e-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="7e15e-116">Właściwość</span><span class="sxs-lookup"><span data-stu-id="7e15e-116">Property</span></span>|<span data-ttu-id="7e15e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7e15e-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="7e15e-118"><xref:System.Windows.Forms.DataGrid.BackColor%2A> Właściwość definiuje kolor wierszy z parzystymi numerami siatki.</span><span class="sxs-lookup"><span data-stu-id="7e15e-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="7e15e-119">Po ustawieniu <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości na inny kolor, każdy inny wiersz jest ustawiany na ten nowy kolor (wiersze 1, 3, 5 itd.).</span><span class="sxs-lookup"><span data-stu-id="7e15e-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="7e15e-120">Kolor tła wierszy z parzystymi numerami siatki (wiersze 0, 2, 4, 6 itd.).</span><span class="sxs-lookup"><span data-stu-id="7e15e-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="7e15e-121">Natomiast właściwości <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> i określają kolor wierszy w siatce, właściwość określa kolor obszaru nonrow, który jest widoczny tylko wtedy, gdy siatka jest przewijana do dołu lub w przypadku, gdy zawiera tylko kilka wierszy <xref:System.Windows.Forms.DataGrid.BackColor%2A> Siatka.</span><span class="sxs-lookup"><span data-stu-id="7e15e-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="7e15e-122">Styl obramowania siatki, jedna z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7e15e-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="7e15e-123">Kolor tła podpisu okna siatki, który pojawia się bezpośrednio nad siatką.</span><span class="sxs-lookup"><span data-stu-id="7e15e-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="7e15e-124">Czcionka napisu w górnej części siatki.</span><span class="sxs-lookup"><span data-stu-id="7e15e-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="7e15e-125">Kolor tła podpisu okna siatki.</span><span class="sxs-lookup"><span data-stu-id="7e15e-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="7e15e-126">Czcionka używana do wyświetlania tekstu w siatce.</span><span class="sxs-lookup"><span data-stu-id="7e15e-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="7e15e-127">Kolor czcionki wyświetlanej przez dane w wierszach siatki danych.</span><span class="sxs-lookup"><span data-stu-id="7e15e-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="7e15e-128">Kolor linii siatki siatki danych.</span><span class="sxs-lookup"><span data-stu-id="7e15e-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="7e15e-129">Styl linii oddzielających komórki siatki, jedną z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7e15e-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="7e15e-130">Kolor tła nagłówków wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="7e15e-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="7e15e-131">Czcionka używana w nagłówkach kolumn.</span><span class="sxs-lookup"><span data-stu-id="7e15e-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="7e15e-132">Kolor pierwszego planu nagłówka kolumny siatki, włącznie z tekstem nagłówka kolumny i symbolami plus/minus (do rozwijania wierszy w przypadku wyświetlenia wielu powiązanych tabel).</span><span class="sxs-lookup"><span data-stu-id="7e15e-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="7e15e-133">Kolor tekstu wszystkich łączy w siatce danych, w tym linki do tabel podrzędnych, nazwy relacji i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7e15e-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="7e15e-134">W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7e15e-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="7e15e-135">W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7e15e-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="7e15e-136">Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnym, za pomocą <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7e15e-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="7e15e-137">Domyślna szerokość (w pikselach) kolumn w siatce.</span><span class="sxs-lookup"><span data-stu-id="7e15e-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="7e15e-138">Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości i <xref:System.Windows.Forms.DataGrid.DataMember%2A> ( <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> oddzielnie albo za pomocą metody) lub właściwość nie będzie mieć żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="7e15e-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="7e15e-139">Właściwość nie może być ustawiona na wartość mniejszą niż 0.</span><span class="sxs-lookup"><span data-stu-id="7e15e-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="7e15e-140">Wysokość wiersza (w pikselach) wierszy w siatce.</span><span class="sxs-lookup"><span data-stu-id="7e15e-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="7e15e-141">Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości i <xref:System.Windows.Forms.DataGrid.DataMember%2A> ( <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> oddzielnie albo za pomocą metody) lub właściwość nie będzie mieć żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="7e15e-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="7e15e-142">Właściwość nie może być ustawiona na wartość mniejszą niż 0.</span><span class="sxs-lookup"><span data-stu-id="7e15e-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="7e15e-143">Szerokość nagłówków wierszy siatki.</span><span class="sxs-lookup"><span data-stu-id="7e15e-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="7e15e-144">Po wybraniu wiersza lub komórki jest to kolor tła.</span><span class="sxs-lookup"><span data-stu-id="7e15e-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="7e15e-145">Po wybraniu wiersza lub komórki jest to kolor pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="7e15e-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="7e15e-146">Należy pamiętać, że podczas dostosowywania kolorów formantów możliwe jest, że kontrolka jest niedostępna z powodu słabego wyboru koloru (na przykład czerwony i zielony).</span><span class="sxs-lookup"><span data-stu-id="7e15e-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="7e15e-147">Użyj kolorów dostępnych na palecie **kolorów systemu** , aby uniknąć tego problemu.</span><span class="sxs-lookup"><span data-stu-id="7e15e-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="7e15e-148">W poniższych procedurach przyjęto założenie <xref:System.Windows.Forms.DataGrid> , że formularz zawiera kontrolkę powiązaną z tabelą danych.</span><span class="sxs-lookup"><span data-stu-id="7e15e-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="7e15e-149">Aby uzyskać więcej informacji, zobacz [powiązywanie formantu Windows Forms DataGrid ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="7e15e-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="7e15e-150">Aby programowo ustawić styl tabeli i kolumny tabeli danych</span><span class="sxs-lookup"><span data-stu-id="7e15e-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="7e15e-151">Utwórz nowy styl tabeli i ustaw jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e15e-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="7e15e-152">Utwórz styl kolumny i ustaw jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e15e-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="7e15e-153">Dodaj styl kolumny do kolekcji Style kolumn stylu tabeli.</span><span class="sxs-lookup"><span data-stu-id="7e15e-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="7e15e-154">Dodaj styl tabeli do kolekcji Style tabeli siatki danych.</span><span class="sxs-lookup"><span data-stu-id="7e15e-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="7e15e-155">W poniższym przykładzie Utwórz wystąpienie nowego <xref:System.Windows.Forms.DataGridTableStyle> i ustaw jego <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="7e15e-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="7e15e-156">Utwórz nowe wystąpienie elementu **GridColumnStyle** i ustaw jego mapowaniename (oraz inne właściwości układu i wyświetlania).</span><span class="sxs-lookup"><span data-stu-id="7e15e-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="7e15e-157">Powtórz kroki od 2 do 6 dla każdego stylu kolumny, który chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="7e15e-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="7e15e-158">Poniższy przykład ilustruje sposób <xref:System.Windows.Forms.DataGridTextBoxColumn> tworzenia, ponieważ nazwa ma być wyświetlana w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="7e15e-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="7e15e-159">Dodatkowo należy dodać styl kolumny do <xref:System.Windows.Forms.GridColumnStylesCollection> stylu tabeli, a następnie dodać styl tabeli <xref:System.Windows.Forms.GridTableStylesCollection> do siatki danych.</span><span class="sxs-lookup"><span data-stu-id="7e15e-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e15e-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e15e-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="7e15e-161">Instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e15e-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="7e15e-162">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7e15e-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
