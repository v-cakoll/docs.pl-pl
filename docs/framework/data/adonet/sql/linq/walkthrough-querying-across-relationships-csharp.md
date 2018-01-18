---
title: "Wskazówki: Wykonywanie zapytań w relacjach (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3357fa598cb00b5fa0146540f676d7463a05f146
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="0a65d-102">Wskazówki: Wykonywanie zapytań w relacjach (C#)</span><span class="sxs-lookup"><span data-stu-id="0a65d-102">Walkthrough: Querying Across Relationships (C#)</span></span>
<span data-ttu-id="0a65d-103">W tym przewodniku zademonstrowano użycie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *skojarzenia* do reprezentowania relacji klucza obcego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0a65d-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="0a65d-104">W tym przewodniku została napisana przy użyciu programu Visual C# programowanie ustawienia.</span><span class="sxs-lookup"><span data-stu-id="0a65d-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0a65d-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0a65d-105">Prerequisites</span></span>  
 <span data-ttu-id="0a65d-106">Należy wykonać [wskazówki: proste modelu obiektów i kwerendy (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="0a65d-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="0a65d-107">W tym przewodniku opiera się na tym z nich w tym pliku northwnd.mdf w c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="0a65d-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="0a65d-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="0a65d-108">Overview</span></span>  
 <span data-ttu-id="0a65d-109">Ten przewodnik składa się z trzech głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="0a65d-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="0a65d-110">Dodawanie klasy jednostki do reprezentowania tabeli zamówienia w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a65d-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="0a65d-111">Uzupełniające adnotacje do `Customer` klasy do rozszerzania relacji między `Customer` i `Order` klasy.</span><span class="sxs-lookup"><span data-stu-id="0a65d-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="0a65d-112">Tworzenie i uruchamianie zapytań, aby przetestować uzyskiwanie `Order` informacji za pomocą `Customer` klasy.</span><span class="sxs-lookup"><span data-stu-id="0a65d-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="0a65d-113">Mapowanie relacji między tabelami</span><span class="sxs-lookup"><span data-stu-id="0a65d-113">Mapping Relationships Across Tables</span></span>  
 <span data-ttu-id="0a65d-114">Po `Customer` definicji klasy, należy utworzyć `Order` definicji klasy jednostki, która zawiera następujący kod, który wskazuje, że `Order.Customer` odnosi się jako klucz obcy do `Customer.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="0a65d-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="0a65d-115">Aby dodać klasę jednostki kolejności</span><span class="sxs-lookup"><span data-stu-id="0a65d-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="0a65d-116">Wpisz lub wklej następujący kod po `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="0a65d-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="0a65d-117">Dodawanie adnotacji do klasy odbiorcy</span><span class="sxs-lookup"><span data-stu-id="0a65d-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="0a65d-118">W tym kroku adnotacji `Customer` klasy, aby wskazać jej relacji `Order` klasy.</span><span class="sxs-lookup"><span data-stu-id="0a65d-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="0a65d-119">(To dodawanie nie jest niezbędne, ponieważ Definiowanie relacji w żadnym kierunku jest wystarczające, aby utworzyć łącze.</span><span class="sxs-lookup"><span data-stu-id="0a65d-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="0a65d-120">Ale dodawanie Ta adnotacja umożliwiają łatwe przejście obiekty w obu kierunkach).</span><span class="sxs-lookup"><span data-stu-id="0a65d-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="0a65d-121">Dla adnotacji klasy klienta</span><span class="sxs-lookup"><span data-stu-id="0a65d-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="0a65d-122">Wpisz lub wklej następujący kod do `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="0a65d-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="0a65d-123">Tworzenie i uruchamianie zapytania w relacji zamówienie klienta</span><span class="sxs-lookup"><span data-stu-id="0a65d-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="0a65d-124">Teraz uzyskiwać dostęp do `Order` obiektów bezpośrednio z `Customer` obiektów, lub w przeciwną kolejności.</span><span class="sxs-lookup"><span data-stu-id="0a65d-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="0a65d-125">Nie trzeba jawnie *sprzężenia* między klientami a zleceń.</span><span class="sxs-lookup"><span data-stu-id="0a65d-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="0a65d-126">Dostęp do obiektów kolejności przy użyciu obiektów klienta</span><span class="sxs-lookup"><span data-stu-id="0a65d-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="0a65d-127">Modyfikowanie `Main` metody, wpisując lub wklejając następujący kod do metody:</span><span class="sxs-lookup"><span data-stu-id="0a65d-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="0a65d-128">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="0a65d-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a65d-129">Kod SQL w oknie konsoli można wyeliminować przez komentowania limit `db.Log = Console.Out;`.</span><span class="sxs-lookup"><span data-stu-id="0a65d-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3.  <span data-ttu-id="0a65d-130">Naciśnij klawisz Enter w oknie konsoli, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="0a65d-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="0a65d-131">Tworzenie silnie Typizowanego widoku bazy danych</span><span class="sxs-lookup"><span data-stu-id="0a65d-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="0a65d-132">Znacznie łatwiej rozpoczynać silnie typizowanego widoku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0a65d-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="0a65d-133">Zdecydowanie wpisując <xref:System.Data.Linq.DataContext> obiektu, nie trzeba wywołania <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a65d-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="0a65d-134">Można użyć jednoznacznie tabel wszystkie zapytania, korzystając z silnie typizowaną <xref:System.Data.Linq.DataContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0a65d-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="0a65d-135">W poniższych krokach utworzysz `Customers` jako tabelę jednoznacznie, który jest mapowany na tabeli Klienci w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0a65d-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="0a65d-136">Do silnie typu DataContext obiektu</span><span class="sxs-lookup"><span data-stu-id="0a65d-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="0a65d-137">Dodaj następujący kod powyżej `Customer` deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="0a65d-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  <span data-ttu-id="0a65d-138">Modyfikowanie `Main` metoda do użycia w silnie typizowaną <xref:System.Data.Linq.DataContext> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0a65d-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  <span data-ttu-id="0a65d-139">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="0a65d-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="0a65d-140">Dane wyjściowe z okna konsoli jest:</span><span class="sxs-lookup"><span data-stu-id="0a65d-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="0a65d-141">Naciśnij klawisz Enter w oknie konsoli, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="0a65d-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0a65d-142">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0a65d-142">Next Steps</span></span>  
 <span data-ttu-id="0a65d-143">Wskazówki dalej ([wskazówki: manipulowanie danych (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) pokazuje, jak można manipulować danymi.</span><span class="sxs-lookup"><span data-stu-id="0a65d-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="0a65d-144">Ten przewodnik nie wymaga zapisać dwóch wskazówki w tej serii, która została już ukończona.</span><span class="sxs-lookup"><span data-stu-id="0a65d-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a65d-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a65d-145">See Also</span></span>  
 [<span data-ttu-id="0a65d-146">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="0a65d-146">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
