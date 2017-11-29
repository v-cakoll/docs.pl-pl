---
title: "Wskazówki: Wykonywanie zapytań w relacjach (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 05ae619a4d3a31c83a740572eae13fe7ef883a40
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="3113b-102">Wskazówki: Wykonywanie zapytań w relacjach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3113b-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="3113b-103">W tym przewodniku zademonstrowano użycie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *skojarzenia* do reprezentowania relacji klucza obcego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="3113b-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="3113b-104">W tym przewodniku została napisana przy użyciu ustawienia środowiska deweloperskiego Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3113b-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3113b-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3113b-105">Prerequisites</span></span>  
 <span data-ttu-id="3113b-106">Należy wykonać [wskazówki: prosty Model obiektów i zapytań (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3113b-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="3113b-107">W tym przewodniku opiera się na tym z nich w tym pliku northwnd.mdf w c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="3113b-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="3113b-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="3113b-108">Overview</span></span>  
 <span data-ttu-id="3113b-109">Ten przewodnik składa się z trzech głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="3113b-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="3113b-110">Dodawanie klasy jednostki do reprezentowania tabeli zamówienia w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="3113b-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="3113b-111">Uzupełniające adnotacje do `Customer` klasy do rozszerzania relacji między `Customer` i `Order` klasy.</span><span class="sxs-lookup"><span data-stu-id="3113b-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="3113b-112">Tworzenie i uruchamianie zapytań, aby przetestować proces uzyskiwania `Order` informacji za pomocą `Customer` klasy.</span><span class="sxs-lookup"><span data-stu-id="3113b-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="3113b-113">Mapowanie relacji między tabelami</span><span class="sxs-lookup"><span data-stu-id="3113b-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="3113b-114">Po `Customer` definicji klasy, należy utworzyć `Order` definicji klasy jednostki, która zawiera następujący kod, który wskazuje, że `Orders.Customer` odnosi się jako klucz obcy do `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="3113b-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="3113b-115">Aby dodać klasę jednostki kolejności</span><span class="sxs-lookup"><span data-stu-id="3113b-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="3113b-116">Wpisz lub wklej następujący kod po `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="3113b-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="3113b-117">Dodawanie adnotacji do klasy odbiorcy</span><span class="sxs-lookup"><span data-stu-id="3113b-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="3113b-118">W tym kroku adnotacji `Customer` klasy, aby wskazać jej relacji `Order` klasy.</span><span class="sxs-lookup"><span data-stu-id="3113b-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="3113b-119">(To dodawanie nie jest niezbędne, ponieważ Definiowanie relacji w żadnym kierunku jest wystarczające, aby utworzyć łącze.</span><span class="sxs-lookup"><span data-stu-id="3113b-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="3113b-120">Ale dodawanie Ta adnotacja umożliwiają łatwe przejście obiekty w obu kierunkach).</span><span class="sxs-lookup"><span data-stu-id="3113b-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="3113b-121">Dla adnotacji klasy klienta</span><span class="sxs-lookup"><span data-stu-id="3113b-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="3113b-122">Wpisz lub wklej następujący kod do `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="3113b-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="3113b-123">Tworzenie i uruchamianie zapytania w relacji zamówienie klienta</span><span class="sxs-lookup"><span data-stu-id="3113b-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="3113b-124">Teraz uzyskiwać dostęp do `Order` obiektów bezpośrednio z `Customer` obiektów, lub w przeciwną kolejności.</span><span class="sxs-lookup"><span data-stu-id="3113b-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="3113b-125">Nie trzeba jawnie *sprzężenia* między klientami a zleceń.</span><span class="sxs-lookup"><span data-stu-id="3113b-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="3113b-126">Dostęp do obiektów kolejności przy użyciu obiektów klienta</span><span class="sxs-lookup"><span data-stu-id="3113b-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="3113b-127">Modyfikowanie `Sub Main` metody, wpisując lub wklejając następujący kod do metody:</span><span class="sxs-lookup"><span data-stu-id="3113b-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="3113b-128">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="3113b-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="3113b-129">Dwie nazwy wyświetlane w oknie komunikatu i w oknie konsoli wyświetlane z wygenerowanego kodu SQL.</span><span class="sxs-lookup"><span data-stu-id="3113b-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="3113b-130">Zamknij okno komunikatu, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="3113b-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="3113b-131">Tworzenie silnie Typizowanego widoku bazy danych</span><span class="sxs-lookup"><span data-stu-id="3113b-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="3113b-132">Znacznie łatwiej rozpoczynać silnie typizowanego widoku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3113b-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="3113b-133">Zdecydowanie wpisując <xref:System.Data.Linq.DataContext> obiektu, nie trzeba wywołania <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="3113b-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="3113b-134">Można użyć jednoznacznie tabel wszystkie zapytania, korzystając z silnie typizowaną <xref:System.Data.Linq.DataContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3113b-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="3113b-135">W poniższych krokach utworzysz `Customers` jako tabelę jednoznacznie, który jest mapowany na tabeli Klienci w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="3113b-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="3113b-136">Do silnie typu DataContext obiektu</span><span class="sxs-lookup"><span data-stu-id="3113b-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="3113b-137">Dodaj następujący kod powyżej `Customer` deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="3113b-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  <span data-ttu-id="3113b-138">Modyfikowanie `Sub Main` do użycia w silnie typizowaną <xref:System.Data.Linq.DataContext> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3113b-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  <span data-ttu-id="3113b-139">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="3113b-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="3113b-140">Dane wyjściowe z okna konsoli jest:</span><span class="sxs-lookup"><span data-stu-id="3113b-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="3113b-141">Naciśnij klawisz Enter w oknie konsoli, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="3113b-141">Press Enter in the Console window to close the application.</span></span>  
  
5.  <span data-ttu-id="3113b-142">Na **pliku** menu, kliknij przycisk **Zapisz wszystko** Jeśli chcesz zapisać tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3113b-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3113b-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3113b-143">Next Steps</span></span>  
 <span data-ttu-id="3113b-144">Wskazówki dalej ([wskazówki: manipulowanie danych (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) pokazuje, jak można manipulować danymi.</span><span class="sxs-lookup"><span data-stu-id="3113b-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="3113b-145">Ten przewodnik nie wymaga zapisać dwóch wskazówki w tej serii, która została już ukończona.</span><span class="sxs-lookup"><span data-stu-id="3113b-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3113b-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3113b-146">See Also</span></span>  
 [<span data-ttu-id="3113b-147">Learning przez — wskazówki</span><span class="sxs-lookup"><span data-stu-id="3113b-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
