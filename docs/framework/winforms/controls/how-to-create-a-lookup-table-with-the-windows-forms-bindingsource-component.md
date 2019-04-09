---
title: 'Instrukcje: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: b2b588a8529983699e49531f51aae8e4225e9608
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181483"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="f42b1-102">Instrukcje: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f42b1-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="f42b1-103">Tabela odnośników znajduje się tabela danych, która zawiera kolumnę, która wyświetla dane z rekordów w powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f42b1-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="f42b1-104">W poniższych procedurach <xref:System.Windows.Forms.ComboBox> formantu służy do wyświetlania pól z relacji klucza obcego z obiektu nadrzędnego do tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f42b1-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="f42b1-105">Aby wizualizować tymi dwiema tabelami i tę relację, Oto przykład tabeli nadrzędnej i podrzędnej:</span><span class="sxs-lookup"><span data-stu-id="f42b1-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="f42b1-106">CustomersTable (tabeli nadrzędnej)</span><span class="sxs-lookup"><span data-stu-id="f42b1-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="f42b1-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="f42b1-107">CustomerID</span></span>|<span data-ttu-id="f42b1-108">CustomerName</span><span class="sxs-lookup"><span data-stu-id="f42b1-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="f42b1-109">712</span><span class="sxs-lookup"><span data-stu-id="f42b1-109">712</span></span>|<span data-ttu-id="f42b1-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="f42b1-110">Paul Koch</span></span>|  
|<span data-ttu-id="f42b1-111">713</span><span class="sxs-lookup"><span data-stu-id="f42b1-111">713</span></span>|<span data-ttu-id="f42b1-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="f42b1-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="f42b1-113">OrdersTable (tabeli podrzędnej)</span><span class="sxs-lookup"><span data-stu-id="f42b1-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="f42b1-114">OrderID</span><span class="sxs-lookup"><span data-stu-id="f42b1-114">OrderID</span></span>|<span data-ttu-id="f42b1-115">DataZamówienia.</span><span class="sxs-lookup"><span data-stu-id="f42b1-115">OrderDate</span></span>|<span data-ttu-id="f42b1-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="f42b1-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="f42b1-117">903</span><span class="sxs-lookup"><span data-stu-id="f42b1-117">903</span></span>|<span data-ttu-id="f42b1-118">12 lutego 2004</span><span class="sxs-lookup"><span data-stu-id="f42b1-118">February 12, 2004</span></span>|<span data-ttu-id="f42b1-119">712</span><span class="sxs-lookup"><span data-stu-id="f42b1-119">712</span></span>|  
|<span data-ttu-id="f42b1-120">904</span><span class="sxs-lookup"><span data-stu-id="f42b1-120">904</span></span>|<span data-ttu-id="f42b1-121">13 lutego 2004</span><span class="sxs-lookup"><span data-stu-id="f42b1-121">February 13, 2004</span></span>|<span data-ttu-id="f42b1-122">713</span><span class="sxs-lookup"><span data-stu-id="f42b1-122">713</span></span>|  
  
 <span data-ttu-id="f42b1-123">W tym scenariuszu jednej tabeli, CustomersTable, przechowuje aktualne informacje, które chcesz wyświetlić, a następnie zapisz.</span><span class="sxs-lookup"><span data-stu-id="f42b1-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="f42b1-124">Ale aby zaoszczędzić przestrzeń, tabeli powoduje, że dane, które dodaje przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="f42b1-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="f42b1-125">Drugiej tabeli OrdersTable, zawiera tylko informacje związane z wygląd, o których odbiorcy numer identyfikacyjny jest odpowiednikiem których data zamówienia i kolejność identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="f42b1-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="f42b1-126">Nie wymieniono nazwy klientów nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f42b1-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="f42b1-127">Cztery ważne właściwości są ustawione na [ComboBox, kontrolka](combobox-control-windows-forms.md) kontroli można utworzyć tabeli odnośników.</span><span class="sxs-lookup"><span data-stu-id="f42b1-127">Four important properties are set on the [ComboBox Control](combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="f42b1-128"><xref:System.Windows.Forms.ComboBox.DataSource%2A> Właściwość zawiera nazwę tabeli.</span><span class="sxs-lookup"><span data-stu-id="f42b1-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="f42b1-129"><xref:System.Windows.Forms.ListControl.DisplayMember%2A> Właściwość zawiera kolumny danych tej tabeli, którą chcesz wyświetlić tekst formantu (nazwy klienta).</span><span class="sxs-lookup"><span data-stu-id="f42b1-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="f42b1-130"><xref:System.Windows.Forms.ListControl.ValueMember%2A> Właściwość zawiera kolumny danych tej tabeli przy użyciu przechowywanych informacji (identyfikator tabeli nadrzędnej).</span><span class="sxs-lookup"><span data-stu-id="f42b1-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="f42b1-131"><xref:System.Windows.Forms.ListControl.SelectedValue%2A> Właściwość zawiera wartość wyszukiwania dla tabeli podrzędnej na podstawie <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="f42b1-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="f42b1-132">Poniższe procedury pokazują, jak określić układ formularza jako tabela odnośnika i powiązać dane z formantów na nim.</span><span class="sxs-lookup"><span data-stu-id="f42b1-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="f42b1-133">Aby pomyślnie wykonać procedury, musi mieć źródło danych o tabele nadrzędne i podrzędne, które mają relacji klucza obcego, jak wspomniano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f42b1-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="f42b1-134">Aby utworzyć interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="f42b1-134">To create the user interface</span></span>  
  
1.  <span data-ttu-id="f42b1-135">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ComboBox> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="f42b1-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="f42b1-136">Ta kontrolka będzie wyświetlać kolumny z tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f42b1-136">This control will display the column from parent table.</span></span>  
  
2.  <span data-ttu-id="f42b1-137">Przeciągnij inne kontrolki, aby wyświetlić szczegółowe informacje z tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f42b1-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="f42b1-138">Format danych w tabeli należy określić, które kontrolki, możesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="f42b1-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="f42b1-139">Aby uzyskać więcej informacji, zobacz [formantów formularzy Windows za pomocą funkcji](windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="f42b1-139">For more information, see [Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span></span>  
  
3.  <span data-ttu-id="f42b1-140">Przeciągnij <xref:System.Windows.Forms.BindingNavigator> formant na formularzu; to umożliwia nawigowanie po danych w tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f42b1-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="f42b1-141">Aby połączyć się z danymi i powiąż go z kontrolkami</span><span class="sxs-lookup"><span data-stu-id="f42b1-141">To connect to the data and bind it to controls</span></span>  
  
1.  <span data-ttu-id="f42b1-142">Wybierz <xref:System.Windows.Forms.ComboBox> i kliknij symbol inteligentne zadań, aby wyświetlić okno dialogowe inteligentne zadania.</span><span class="sxs-lookup"><span data-stu-id="f42b1-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2.  <span data-ttu-id="f42b1-143">Wybierz **elementów powiązanych danych użycia**.</span><span class="sxs-lookup"><span data-stu-id="f42b1-143">Select **Use data bound items**.</span></span>  
  
3.  <span data-ttu-id="f42b1-144">Kliknij strzałkę obok pozycji **źródła danych** pole listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="f42b1-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="f42b1-145">Jeśli wcześniej skonfigurowano źródła danych dla projektu lub formularza, pojawi się; w przeciwnym razie wykonaj następujące czynności (w tym przykładzie używa tabele Customers i Orders z przykładowej bazy danych Northwind i odwołuje się do nich w nawiasach).</span><span class="sxs-lookup"><span data-stu-id="f42b1-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="f42b1-146">Kliknij przycisk **Dodaj źródło danych projektu** do nawiązywania połączeń z danymi i Utwórz źródło danych.</span><span class="sxs-lookup"><span data-stu-id="f42b1-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="f42b1-147">Na **Kreatora konfiguracji źródła danych** strona powitalna, kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="f42b1-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="f42b1-148">Wybierz **bazy danych** na **wybierz typ źródła danych** strony.</span><span class="sxs-lookup"><span data-stu-id="f42b1-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="f42b1-149">Wybierz połączenie danych z listy dostępnych połączeń na **wybierz połączenie danych** strony.</span><span class="sxs-lookup"><span data-stu-id="f42b1-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="f42b1-150">Jeśli żądane połączenie danych nie jest dostępna, wybierz **nowe połączenie** Aby utworzyć nowe połączenie danych.</span><span class="sxs-lookup"><span data-stu-id="f42b1-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="f42b1-151">Kliknij przycisk **tak, Zapisz połączenie** można zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f42b1-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="f42b1-152">Wybierz obiekty bazy danych w celu dostosowania do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f42b1-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="f42b1-153">W takim przypadku wybierz tabelę nadrzędną i tabeli podrzędnej (na przykład klienci i zamówienia) z relacji klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="f42b1-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="f42b1-154">Zastąp domyślną nazwę zestawu danych, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="f42b1-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="f42b1-155">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="f42b1-155">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="f42b1-156">W **członkiem wyświetlania** listy rozwijanej wybierz pozycję Nazwa kolumny (na przykład nazwa kontaktu) mają być wyświetlane w polu kombi.</span><span class="sxs-lookup"><span data-stu-id="f42b1-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5.  <span data-ttu-id="f42b1-157">W **wartość elementu członkowskiego** listy rozwijanej wybierz kolumnę (na przykład identyfikator klienta) do wykonywania operacji wyszukiwania w tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f42b1-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6.  <span data-ttu-id="f42b1-158">W **wybrana wartość** listy rozwijanej, przejdź do **zdroje dat projektu** i zestaw danych został utworzony, który zawiera tabele nadrzędnymi i podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="f42b1-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="f42b1-159">Wybierz tę samą właściwość tabeli podrzędnej, który jest członkiem wartość tabeli nadrzędnej (na przykład zamówienia.IDklienta).</span><span class="sxs-lookup"><span data-stu-id="f42b1-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="f42b1-160">Odpowiednie <xref:System.Windows.Forms.BindingSource> zestawu danych i składników karty tabeli zostanie utworzona i dodany do formularza.</span><span class="sxs-lookup"><span data-stu-id="f42b1-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7.  <span data-ttu-id="f42b1-161">Powiąż <xref:System.Windows.Forms.BindingNavigator> kontrolę <xref:System.Windows.Forms.BindingSource> tabeli podrzędnej (na przykład `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="f42b1-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8.  <span data-ttu-id="f42b1-162">Powiązywanie kontrolek innych niż <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.BindingNavigator> kontrolki pola informacji z tabeli podrzędnej <xref:System.Windows.Forms.BindingSource> (na przykład `OrdersBindingSource`), którą chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="f42b1-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f42b1-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f42b1-163">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="f42b1-164">BindingSource — Składnik</span><span class="sxs-lookup"><span data-stu-id="f42b1-164">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="f42b1-165">ComboBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="f42b1-165">ComboBox Control</span></span>](combobox-control-windows-forms.md)
- [<span data-ttu-id="f42b1-166">Powiązywanie kontrolek z danymi w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f42b1-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
