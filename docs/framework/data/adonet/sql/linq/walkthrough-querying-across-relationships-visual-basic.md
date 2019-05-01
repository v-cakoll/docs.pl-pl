---
title: 'Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: abd4941697639ec7bdda545b1ead8d57091e9e7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038444"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="e5a18-102">Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5a18-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="e5a18-103">W tym instruktażu pokazano użycie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *skojarzenia* do reprezentowania relacji klucza obcego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e5a18-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="e5a18-104">W tym przewodniku została napisana przy użyciu ustawień środowiska deweloperskiego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e5a18-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e5a18-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e5a18-105">Prerequisites</span></span>  
 <span data-ttu-id="e5a18-106">Konieczne jest ukończenie [instruktażu: Prosty Model obiektu i zapytanie (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e5a18-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="e5a18-107">W tym przewodniku opiera się na tym, co w tym pliku northwnd.mdf w c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="e5a18-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e5a18-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e5a18-108">Overview</span></span>  
 <span data-ttu-id="e5a18-109">Ten przewodnik składa się z trzech głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="e5a18-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="e5a18-110">Dodawanie klasy jednostki do reprezentowania tabeli Orders z przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="e5a18-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="e5a18-111">Uzupełniające adnotacje do `Customer` klasy w celu zwiększenia relacji między `Customer` i `Order` klasy.</span><span class="sxs-lookup"><span data-stu-id="e5a18-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="e5a18-112">Tworzenie i uruchamianie zapytań, aby przetestować proces uzyskiwania `Order` informacji przy użyciu `Customer` klasy.</span><span class="sxs-lookup"><span data-stu-id="e5a18-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="e5a18-113">Mapowanie relacji między tabelami</span><span class="sxs-lookup"><span data-stu-id="e5a18-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="e5a18-114">Po `Customer` definicji klasy, należy utworzyć `Order` jednostki definicji klasy, która zawiera następujący kod, który wskazuje, że `Orders.Customer` odnosi się jako klucz obcy, aby `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="e5a18-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="e5a18-115">Aby dodać klasę jednostki zamówienia</span><span class="sxs-lookup"><span data-stu-id="e5a18-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="e5a18-116">Wpisz lub wklej następujący kod po `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="e5a18-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="e5a18-117">Dodawanie adnotacji do klasy odbiorcy</span><span class="sxs-lookup"><span data-stu-id="e5a18-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="e5a18-118">W tym kroku możesz dodawać adnotacje do `Customer` klasy, aby wskazać jej relacji z `Order` klasy.</span><span class="sxs-lookup"><span data-stu-id="e5a18-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="e5a18-119">(To dodawanie nie jest bezwzględnie konieczne, ponieważ zdefiniowaniem relacji w dowolnym kierunku jest wystarczające, aby utworzyć łącze.</span><span class="sxs-lookup"><span data-stu-id="e5a18-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="e5a18-120">Ale dodanie tej adnotacji umożliwiają łatwe nawigowanie obiektów w dowolnym kierunku).</span><span class="sxs-lookup"><span data-stu-id="e5a18-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="e5a18-121">Dodawać adnotacje do klasy odbiorcy</span><span class="sxs-lookup"><span data-stu-id="e5a18-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="e5a18-122">Wpisz lub wklej następujący kod do `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="e5a18-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="e5a18-123">Tworzenie i uruchamianie zapytań w relacji zamówienia klienta</span><span class="sxs-lookup"><span data-stu-id="e5a18-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="e5a18-124">Teraz uzyskiwać dostęp do `Order` obiektów bezpośrednio z `Customer` obiektów, lub w kolejności przeciwnej.</span><span class="sxs-lookup"><span data-stu-id="e5a18-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="e5a18-125">Nie trzeba jawnie *sprzężenia* między klienci i zamówienia.</span><span class="sxs-lookup"><span data-stu-id="e5a18-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="e5a18-126">Dostęp do obiektów kolejności przy użyciu obiektów klienta</span><span class="sxs-lookup"><span data-stu-id="e5a18-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="e5a18-127">Modyfikowanie `Sub Main` metody, wpisując lub wklejając następujący kod do metody:</span><span class="sxs-lookup"><span data-stu-id="e5a18-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="e5a18-128">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="e5a18-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="e5a18-129">Dwie nazwy wyświetlane w oknie komunikatu, a w oknie konsoli wyświetlane wygenerowanego kodu SQL.</span><span class="sxs-lookup"><span data-stu-id="e5a18-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3. <span data-ttu-id="e5a18-130">Zamknij okno komunikatu, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="e5a18-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="e5a18-131">Tworzenie silnie Typizowanego widoku bazy danych</span><span class="sxs-lookup"><span data-stu-id="e5a18-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="e5a18-132">Jest znacznie łatwiejsze do uruchamiania w silnie typizowanym widoku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e5a18-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="e5a18-133">Zdecydowanie wpisując <xref:System.Data.Linq.DataContext> obiektu, nie trzeba wywołania <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5a18-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="e5a18-134">Silnie typizowane tabel można używać wszystkie zapytania, korzystając z silnie typizowaną <xref:System.Data.Linq.DataContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e5a18-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="e5a18-135">W poniższych krokach utworzysz `Customers` jako silnie typizowaną tabelę, która mapuje dane do tabeli Klienci w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e5a18-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="e5a18-136">Do silnie typu obiektu DataContext</span><span class="sxs-lookup"><span data-stu-id="e5a18-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="e5a18-137">Dodaj następujący kod powyżej `Customer` deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="e5a18-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. <span data-ttu-id="e5a18-138">Modyfikowanie `Sub Main` do użycia w silnie typizowany <xref:System.Data.Linq.DataContext> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e5a18-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. <span data-ttu-id="e5a18-139">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="e5a18-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="e5a18-140">Dane wyjściowe z okna konsoli jest:</span><span class="sxs-lookup"><span data-stu-id="e5a18-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="e5a18-141">Naciśnij klawisz Enter w oknie konsoli, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="e5a18-141">Press Enter in the Console window to close the application.</span></span>  
  
5. <span data-ttu-id="e5a18-142">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** Jeśli chcesz zapisać tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="e5a18-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e5a18-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e5a18-143">Next Steps</span></span>  
 <span data-ttu-id="e5a18-144">Następnym instruktażu ([instruktażu: Manipulowanie danych (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) pokazuje, jak wykonywać operacje na danych.</span><span class="sxs-lookup"><span data-stu-id="e5a18-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="e5a18-145">Ten przewodnik nie wymaga zapisania dwa przewodniki w tej serii, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="e5a18-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a18-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5a18-146">See also</span></span>

- [<span data-ttu-id="e5a18-147">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="e5a18-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
