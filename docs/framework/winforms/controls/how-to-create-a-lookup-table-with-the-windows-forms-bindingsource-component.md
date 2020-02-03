---
title: Tworzenie tabeli odnośników ze składnikiem BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: ccf2bfa6cf3f56a38b55f8c87004c42a46172891
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736816"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="ea36c-102">Porady: tworzenie tabeli wyszukiwania za pomocą składnika BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ea36c-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="ea36c-103">Tabela wyszukiwania to tabela danych, która zawiera kolumnę, która wyświetla dane z rekordów w powiązanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ea36c-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="ea36c-104">W poniższych procedurach formant <xref:System.Windows.Forms.ComboBox> służy do wyświetlania pola z relacją klucza obcego od elementu nadrzędnego do tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ea36c-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="ea36c-105">Aby ułatwić wizualizację tych dwóch tabel i tę relację, Oto przykład tabeli nadrzędnej i podrzędnej:</span><span class="sxs-lookup"><span data-stu-id="ea36c-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="ea36c-106">Customers (tabela nadrzędna)</span><span class="sxs-lookup"><span data-stu-id="ea36c-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="ea36c-107">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="ea36c-107">CustomerID</span></span>|<span data-ttu-id="ea36c-108">customerName</span><span class="sxs-lookup"><span data-stu-id="ea36c-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="ea36c-109">712</span><span class="sxs-lookup"><span data-stu-id="ea36c-109">712</span></span>|<span data-ttu-id="ea36c-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="ea36c-110">Paul Koch</span></span>|  
|<span data-ttu-id="ea36c-111">713</span><span class="sxs-lookup"><span data-stu-id="ea36c-111">713</span></span>|<span data-ttu-id="ea36c-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="ea36c-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="ea36c-113">Orders (tabela podrzędna)</span><span class="sxs-lookup"><span data-stu-id="ea36c-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="ea36c-114">Wartooć</span><span class="sxs-lookup"><span data-stu-id="ea36c-114">OrderID</span></span>|<span data-ttu-id="ea36c-115">DataZamówienia</span><span class="sxs-lookup"><span data-stu-id="ea36c-115">OrderDate</span></span>|<span data-ttu-id="ea36c-116">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="ea36c-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="ea36c-117">903</span><span class="sxs-lookup"><span data-stu-id="ea36c-117">903</span></span>|<span data-ttu-id="ea36c-118">12 lutego 2004</span><span class="sxs-lookup"><span data-stu-id="ea36c-118">February 12, 2004</span></span>|<span data-ttu-id="ea36c-119">712</span><span class="sxs-lookup"><span data-stu-id="ea36c-119">712</span></span>|  
|<span data-ttu-id="ea36c-120">904</span><span class="sxs-lookup"><span data-stu-id="ea36c-120">904</span></span>|<span data-ttu-id="ea36c-121">13 lutego 2004</span><span class="sxs-lookup"><span data-stu-id="ea36c-121">February 13, 2004</span></span>|<span data-ttu-id="ea36c-122">713</span><span class="sxs-lookup"><span data-stu-id="ea36c-122">713</span></span>|  
  
 <span data-ttu-id="ea36c-123">W tym scenariuszu jedna tabela, Customers, przechowuje rzeczywiste informacje, które mają być wyświetlane i zapisywane.</span><span class="sxs-lookup"><span data-stu-id="ea36c-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="ea36c-124">Jednak aby zaoszczędzić miejsce, tabela opuszcza dane, które zwiększają czytelność.</span><span class="sxs-lookup"><span data-stu-id="ea36c-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="ea36c-125">Druga tabela, Orders, zawiera tylko informacje dotyczące wyglądu, dla których numer IDENTYFIKACYJNy klienta jest równoważny z datą zamówienia i IDENTYFIKATORem zamówienia.</span><span class="sxs-lookup"><span data-stu-id="ea36c-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="ea36c-126">Nie ma wzmianki o nazwach klientów.</span><span class="sxs-lookup"><span data-stu-id="ea36c-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="ea36c-127">Cztery ważne właściwości są ustawiane w kontrolce [kontrolki ComboBox](combobox-control-windows-forms.md) , aby utworzyć tabelę odnośników.</span><span class="sxs-lookup"><span data-stu-id="ea36c-127">Four important properties are set on the [ComboBox Control](combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
- <span data-ttu-id="ea36c-128">Właściwość <xref:System.Windows.Forms.ComboBox.DataSource%2A> zawiera nazwę tabeli.</span><span class="sxs-lookup"><span data-stu-id="ea36c-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
- <span data-ttu-id="ea36c-129">Właściwość <xref:System.Windows.Forms.ListControl.DisplayMember%2A> zawiera kolumnę danych tej tabeli, która ma być wyświetlana dla tekstu kontrolki (Nazwa klienta).</span><span class="sxs-lookup"><span data-stu-id="ea36c-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
- <span data-ttu-id="ea36c-130">Właściwość <xref:System.Windows.Forms.ListControl.ValueMember%2A> zawiera kolumnę danych tej tabeli zawierającą przechowywane informacje (numer IDENTYFIKACYJNy w tabeli nadrzędnej).</span><span class="sxs-lookup"><span data-stu-id="ea36c-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
- <span data-ttu-id="ea36c-131">Właściwość <xref:System.Windows.Forms.ListControl.SelectedValue%2A> udostępnia wartość wyszukiwania dla tabeli podrzędnej na podstawie <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea36c-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="ea36c-132">Poniższe procedury przedstawiają sposób tworzenia układu formularza jako tabeli odnośników i powiązania danych z kontrolkami na nim.</span><span class="sxs-lookup"><span data-stu-id="ea36c-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="ea36c-133">Aby pomyślnie wykonać procedury, musisz mieć źródło danych z tabelami nadrzędnymi i podrzędnymi, które mają relację klucza obcego, jak wspomniano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ea36c-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="ea36c-134">Aby utworzyć interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="ea36c-134">To create the user interface</span></span>  
  
1. <span data-ttu-id="ea36c-135">Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.ComboBox> na formularz.</span><span class="sxs-lookup"><span data-stu-id="ea36c-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="ea36c-136">Ta kontrolka wyświetli kolumnę z tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ea36c-136">This control will display the column from parent table.</span></span>  
  
2. <span data-ttu-id="ea36c-137">Przeciągnij inne kontrolki, aby wyświetlić szczegóły z tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ea36c-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="ea36c-138">Format danych w tabeli powinien określać wybrane kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ea36c-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="ea36c-139">Aby uzyskać więcej informacji, zobacz [Windows Forms formantów według funkcji](windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="ea36c-139">For more information, see [Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span></span>  
  
3. <span data-ttu-id="ea36c-140">Przeciągnij kontrolkę <xref:System.Windows.Forms.BindingNavigator> na formularz; umożliwi to nawigowanie po danych w tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ea36c-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="ea36c-141">Aby nawiązać połączenie z danymi i powiązać je z kontrolkami</span><span class="sxs-lookup"><span data-stu-id="ea36c-141">To connect to the data and bind it to controls</span></span>  
  
1. <span data-ttu-id="ea36c-142">Wybierz <xref:System.Windows.Forms.ComboBox> i kliknij symbol panel inteligentny, aby wyświetlić okno dialogowe panel inteligentny.</span><span class="sxs-lookup"><span data-stu-id="ea36c-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2. <span data-ttu-id="ea36c-143">Wybierz pozycję **Użyj elementów powiązanych z danymi**.</span><span class="sxs-lookup"><span data-stu-id="ea36c-143">Select **Use data bound items**.</span></span>  
  
3. <span data-ttu-id="ea36c-144">Kliknij strzałkę obok pola listy rozwijanej **Źródło danych** .</span><span class="sxs-lookup"><span data-stu-id="ea36c-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="ea36c-145">Jeśli źródło danych zostało wcześniej skonfigurowane dla projektu lub formularza, zostanie wyświetlone. w przeciwnym razie wykonaj następujące czynności (w tym przykładzie są wykorzystywane tabele Customers i Orders w przykładowej bazie danych Northwind i odwołujące się do nich w nawiasach).</span><span class="sxs-lookup"><span data-stu-id="ea36c-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1. <span data-ttu-id="ea36c-146">Kliknij pozycję **Dodaj źródło danych projektu** , aby połączyć się z danymi i utworzyć źródło danych.</span><span class="sxs-lookup"><span data-stu-id="ea36c-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2. <span data-ttu-id="ea36c-147">Na stronie powitalnej **Kreatora konfiguracji źródła danych** kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="ea36c-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3. <span data-ttu-id="ea36c-148">Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** .</span><span class="sxs-lookup"><span data-stu-id="ea36c-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4. <span data-ttu-id="ea36c-149">Wybierz połączenie danych z listy dostępnych połączeń na stronie **Wybierz połączenie danych** .</span><span class="sxs-lookup"><span data-stu-id="ea36c-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="ea36c-150">Jeśli żądane połączenie danych nie jest dostępne, wybierz pozycję **nowe połączenie** , aby utworzyć nowe połączenie danych.</span><span class="sxs-lookup"><span data-stu-id="ea36c-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5. <span data-ttu-id="ea36c-151">Kliknij przycisk **tak, Zapisz połączenie,** aby zapisać parametry połączenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea36c-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6. <span data-ttu-id="ea36c-152">Wybierz obiekty bazy danych do dołączenia do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ea36c-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="ea36c-153">W takim przypadku wybierz tabelę nadrzędną i tabelę podrzędną (na przykład klienci i zamówienia) z relacją klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="ea36c-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7. <span data-ttu-id="ea36c-154">W razie potrzeby Zastąp domyślną nazwę zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="ea36c-154">Replace the default dataset name if you want.</span></span>  
  
    8. <span data-ttu-id="ea36c-155">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="ea36c-155">Click **Finish**.</span></span>  
  
4. <span data-ttu-id="ea36c-156">W polu listy rozwijanej **Wyświetl element członkowski** wybierz nazwę kolumny (na przykład ContactName), która ma być wyświetlana w polu kombi.</span><span class="sxs-lookup"><span data-stu-id="ea36c-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5. <span data-ttu-id="ea36c-157">W polu listy rozwijanej **członek wartości** wybierz kolumnę (na przykład CustomerID), aby wykonać operację wyszukiwania w tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ea36c-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6. <span data-ttu-id="ea36c-158">W polu listy rozwijanej **wybrana wartość** przejdź do **źródeł danych projektu** i utworzonego zestawu danych, który zawiera tabele nadrzędne i podrzędne.</span><span class="sxs-lookup"><span data-stu-id="ea36c-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="ea36c-159">Wybierz tę samą Właściwość tabeli podrzędnej, która jest elementem członkowskim wartości tabeli nadrzędnej (na przykład Orders. IDklienta).</span><span class="sxs-lookup"><span data-stu-id="ea36c-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="ea36c-160">Odpowiednie <xref:System.Windows.Forms.BindingSource>, zestaw danych i składniki karty tabeli zostaną utworzone i dodane do formularza.</span><span class="sxs-lookup"><span data-stu-id="ea36c-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7. <span data-ttu-id="ea36c-161">Powiąż formant <xref:System.Windows.Forms.BindingNavigator> z <xref:System.Windows.Forms.BindingSource> tabeli podrzędnej (na przykład `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="ea36c-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8. <span data-ttu-id="ea36c-162">Powiąż formanty inne niż <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.BindingNavigator> formantu z polami szczegółów w <xref:System.Windows.Forms.BindingSource> tabeli podrzędnej (na przykład `OrdersBindingSource`), które chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="ea36c-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea36c-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea36c-163">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="ea36c-164">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="ea36c-164">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="ea36c-165">ComboBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ea36c-165">ComboBox Control</span></span>](combobox-control-windows-forms.md)
- [<span data-ttu-id="ea36c-166">Wiązanie kontrolek z danymi w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ea36c-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
