---
title: 'Porady: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 83a34c9d1a4b3d1c2e9950d3c5427567022326b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="8e25f-102">Porady: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8e25f-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="8e25f-103">Tabela odnośników jest tabelą danych, która zawiera kolumnę wyświetlającą z rekordów w powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8e25f-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="8e25f-104">W poniższych procedurach <xref:System.Windows.Forms.ComboBox> formantu służy do wyświetlania pola z relacji klucza obcego z elementu nadrzędnego z tabelą podrzędną.</span><span class="sxs-lookup"><span data-stu-id="8e25f-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="8e25f-105">Aby wizualizacji tych dwóch tabel i tę relację, Oto przykład tabeli nadrzędnej i podrzędnej:</span><span class="sxs-lookup"><span data-stu-id="8e25f-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="8e25f-106">CustomersTable (Tabela nadrzędna)</span><span class="sxs-lookup"><span data-stu-id="8e25f-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="8e25f-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="8e25f-107">CustomerID</span></span>|<span data-ttu-id="8e25f-108">CustomerName</span><span class="sxs-lookup"><span data-stu-id="8e25f-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="8e25f-109">712</span><span class="sxs-lookup"><span data-stu-id="8e25f-109">712</span></span>|<span data-ttu-id="8e25f-110">Koch Pawła</span><span class="sxs-lookup"><span data-stu-id="8e25f-110">Paul Koch</span></span>|  
|<span data-ttu-id="8e25f-111">713</span><span class="sxs-lookup"><span data-stu-id="8e25f-111">713</span></span>|<span data-ttu-id="8e25f-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="8e25f-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="8e25f-113">OrdersTable (tabeli podrzędnej)</span><span class="sxs-lookup"><span data-stu-id="8e25f-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="8e25f-114">OrderID</span><span class="sxs-lookup"><span data-stu-id="8e25f-114">OrderID</span></span>|<span data-ttu-id="8e25f-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="8e25f-115">OrderDate</span></span>|<span data-ttu-id="8e25f-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="8e25f-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="8e25f-117">903</span><span class="sxs-lookup"><span data-stu-id="8e25f-117">903</span></span>|<span data-ttu-id="8e25f-118">12 lutego 2004</span><span class="sxs-lookup"><span data-stu-id="8e25f-118">February 12, 2004</span></span>|<span data-ttu-id="8e25f-119">712</span><span class="sxs-lookup"><span data-stu-id="8e25f-119">712</span></span>|  
|<span data-ttu-id="8e25f-120">904</span><span class="sxs-lookup"><span data-stu-id="8e25f-120">904</span></span>|<span data-ttu-id="8e25f-121">13 lutego 2004</span><span class="sxs-lookup"><span data-stu-id="8e25f-121">February 13, 2004</span></span>|<span data-ttu-id="8e25f-122">713</span><span class="sxs-lookup"><span data-stu-id="8e25f-122">713</span></span>|  
  
 <span data-ttu-id="8e25f-123">W tym scenariuszu jednej tabeli, CustomersTable, przechowuje aktualne informacje, które chcesz wyświetlić, a następnie zapisz.</span><span class="sxs-lookup"><span data-stu-id="8e25f-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="8e25f-124">Ale aby zaoszczędzić miejsce, tabeli powoduje, że dane, które dodaje przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="8e25f-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="8e25f-125">Drugiej tabeli OrdersTable, zawiera tylko informacje związane z wygląd, o których odbiorcy numer identyfikacyjny jest odpowiednikiem które Data zamówienia i kolejność identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="8e25f-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="8e25f-126">Nie ma nie wymieniono nazwy klientów.</span><span class="sxs-lookup"><span data-stu-id="8e25f-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="8e25f-127">Cztery ważne właściwości są ustawione na [formantu ComboBox](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) formantu można utworzyć tabeli odnośników.</span><span class="sxs-lookup"><span data-stu-id="8e25f-127">Four important properties are set on the [ComboBox Control](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="8e25f-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> Właściwość zawiera nazwę tabeli.</span><span class="sxs-lookup"><span data-stu-id="8e25f-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="8e25f-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> Właściwość zawiera kolumny danych tej tabeli, które mają być wyświetlane dla tekstu formantu (nazwy klienta).</span><span class="sxs-lookup"><span data-stu-id="8e25f-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="8e25f-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> Właściwość zawiera kolumny danych tej tabeli z przechowywanych informacji (identyfikator tabeli nadrzędnej).</span><span class="sxs-lookup"><span data-stu-id="8e25f-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="8e25f-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> Właściwość zawiera wartość wyszukiwania dla tabeli podrzędnej, na podstawie <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e25f-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="8e25f-132">W poniższej procedurze pokazano, jak określenie układu formularza jako tabela odnośnika i powiązanie formantów na nim danych.</span><span class="sxs-lookup"><span data-stu-id="8e25f-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="8e25f-133">Aby pomyślnie wykonać procedury, musi mieć źródło danych z tabelą nadrzędną i podrzędną, które mają relację klucza obcego, jak wspomniano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="8e25f-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="8e25f-134">Aby utworzyć interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="8e25f-134">To create the user interface</span></span>  
  
1.  <span data-ttu-id="8e25f-135">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ComboBox> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="8e25f-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="8e25f-136">Ten formant wyświetli kolumny z tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="8e25f-136">This control will display the column from parent table.</span></span>  
  
2.  <span data-ttu-id="8e25f-137">Przeciągnij inne formanty, aby wyświetlić szczegóły z tabelą podrzędną.</span><span class="sxs-lookup"><span data-stu-id="8e25f-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="8e25f-138">Format danych w tabeli należy określić, które kontrolki, możesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="8e25f-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="8e25f-139">Aby uzyskać więcej informacji, zobacz [formantów formularzy systemu Windows przez funkcję](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="8e25f-139">For more information, see [Windows Forms Controls by Function](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span></span>  
  
3.  <span data-ttu-id="8e25f-140">Przeciągnij <xref:System.Windows.Forms.BindingNavigator> sterowania do formularza; to umożliwia nawigowanie w danych w tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="8e25f-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="8e25f-141">Aby połączyć się z danymi i powiąż go z formantami</span><span class="sxs-lookup"><span data-stu-id="8e25f-141">To connect to the data and bind it to controls</span></span>  
  
1.  <span data-ttu-id="8e25f-142">Wybierz <xref:System.Windows.Forms.ComboBox> i kliknij przycisk symbolu inteligentne zadań, aby wyświetlić okno dialogowe inteligentne zadań.</span><span class="sxs-lookup"><span data-stu-id="8e25f-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2.  <span data-ttu-id="8e25f-143">Wybierz **powiązanych elementów danych użycia**.</span><span class="sxs-lookup"><span data-stu-id="8e25f-143">Select **Use data bound items**.</span></span>  
  
3.  <span data-ttu-id="8e25f-144">Kliknij strzałkę obok pozycji **źródła danych** pole listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="8e25f-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="8e25f-145">Jeśli wcześniej została skonfigurowana dla projektu lub formularza źródła danych, zostanie ona wyświetlona; w przeciwnym razie wykonaj następujące czynności (w tym przykładzie używa tabel Klienci i zamówienia przykładowej bazy danych Northwind i odwołuje się do nich w nawiasach).</span><span class="sxs-lookup"><span data-stu-id="8e25f-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="8e25f-146">Kliknij przycisk **Dodaj źródło danych projektu** Aby podłączyć się do danych i Utwórz źródło danych.</span><span class="sxs-lookup"><span data-stu-id="8e25f-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="8e25f-147">Na **Kreator konfiguracji źródła danych** stronie powitalnej kliknij **dalej**.</span><span class="sxs-lookup"><span data-stu-id="8e25f-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="8e25f-148">Wybierz **bazy danych** na **wybierz typ źródła danych** strony.</span><span class="sxs-lookup"><span data-stu-id="8e25f-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="8e25f-149">Wybierz połączenie danych z listy dostępnych połączeń na **wybierz połączenie danych** strony.</span><span class="sxs-lookup"><span data-stu-id="8e25f-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="8e25f-150">Jeśli połączenie żądanych danych nie jest dostępna, zaznacz **nowe połączenie** można utworzyć nowego połączenia danych.</span><span class="sxs-lookup"><span data-stu-id="8e25f-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="8e25f-151">Kliknij przycisk **tak, Zapisz połączenie** Aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e25f-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="8e25f-152">Wybierz obiekty bazy danych do wprowadzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8e25f-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="8e25f-153">W takim przypadku wybierz tabelą nadrzędną a tabelą podrzędną (na przykład klienci i zamówienia) z relacji klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="8e25f-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="8e25f-154">Zastąp domyślną nazwę zestawu danych, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="8e25f-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="8e25f-155">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="8e25f-155">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="8e25f-156">W **członkiem wyświetlania** listy rozwijanej wybierz pozycję Nazwa kolumny (na przykład nazwa kontaktu), który będzie wyświetlany w polu kombi.</span><span class="sxs-lookup"><span data-stu-id="8e25f-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5.  <span data-ttu-id="8e25f-157">W **wartość elementu członkowskiego** listy rozwijanej wybierz kolumny (na przykład identyfikator klienta) do wykonania operacji wyszukiwania w tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="8e25f-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6.  <span data-ttu-id="8e25f-158">W **wybrana wartość** listy rozwijanej wybierz opcję **źródła danych projektu** i zestawie danych właśnie utworzony, który zawiera tabelą nadrzędną i podrzędną.</span><span class="sxs-lookup"><span data-stu-id="8e25f-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="8e25f-159">Wybierz tę samą właściwość tabeli podrzędnej, który jest członkiem wartości w tabeli nadrzędnej (na przykład zamówienia.IDklienta).</span><span class="sxs-lookup"><span data-stu-id="8e25f-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="8e25f-160">Odpowiednie <xref:System.Windows.Forms.BindingSource> zestawu danych i składników karty tabeli zostanie utworzona i dodany do formularza.</span><span class="sxs-lookup"><span data-stu-id="8e25f-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7.  <span data-ttu-id="8e25f-161">Powiąż <xref:System.Windows.Forms.BindingNavigator> formant <xref:System.Windows.Forms.BindingSource> tabeli podrzędnej (na przykład `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="8e25f-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8.  <span data-ttu-id="8e25f-162">Inne niż powiązanie formantów <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.BindingNavigator> formantu do pól szczegółów z tabelą podrzędną <xref:System.Windows.Forms.BindingSource> (na przykład `OrdersBindingSource`), który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="8e25f-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e25f-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e25f-163">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="8e25f-164">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="8e25f-164">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="8e25f-165">ComboBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8e25f-165">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [<span data-ttu-id="8e25f-166">Powiązywanie formantów z danymi w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8e25f-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
