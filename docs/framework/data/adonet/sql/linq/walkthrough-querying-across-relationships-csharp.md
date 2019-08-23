---
title: 'Przewodnik: Wykonywanie zapytań w relacjach (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: a9e0583b14c07df2b1de23ba37fa88552a4c5c7c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946948"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="a7d54-102">Przewodnik: Wykonywanie zapytań w relacjach (C#)</span><span class="sxs-lookup"><span data-stu-id="a7d54-102">Walkthrough: Querying Across Relationships (C#)</span></span>
<span data-ttu-id="a7d54-103">W tym instruktażu przedstawiono sposób [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] użycia *skojarzeń* do reprezentowania relacji FOREIGN KEY w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a7d54-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="a7d54-104">Ten Instruktaż został zapisany przy użyciu ustawień C# deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="a7d54-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a7d54-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a7d54-105">Prerequisites</span></span>  
 <span data-ttu-id="a7d54-106">Należy wykonać [następujące instrukcje: Prosty model obiektu i zapytanie (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="a7d54-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="a7d54-107">Ten przewodnik jest oparty na tym instruktażu, w tym o obecności pliku northwnd. mdf w c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="a7d54-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a7d54-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="a7d54-108">Overview</span></span>  
 <span data-ttu-id="a7d54-109">Ten przewodnik składa się z trzech głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="a7d54-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="a7d54-110">Dodawanie klasy jednostki do reprezentowania tabeli Orders w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7d54-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="a7d54-111">Uzupełnianie adnotacji do `Customer` klasy w celu zwiększenia relacji `Customer` między klasami `Order` i.</span><span class="sxs-lookup"><span data-stu-id="a7d54-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="a7d54-112">Utworzenie i uruchomienie zapytania w celu przetestowania uzyskiwania `Order` informacji przy `Customer` użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="a7d54-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="a7d54-113">Mapowanie relacji między tabelami</span><span class="sxs-lookup"><span data-stu-id="a7d54-113">Mapping Relationships Across Tables</span></span>  
 <span data-ttu-id="a7d54-114">Po zdefiniowaniu `Order` `Order.Customer` `Customer.CustomerID`klasy Utwórz definicję klasy jednostki, która zawiera następujący kod, który wskazuje, że odnosi się jako klucz obcy do. `Customer`</span><span class="sxs-lookup"><span data-stu-id="a7d54-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="a7d54-115">Aby dodać klasę Entity Order</span><span class="sxs-lookup"><span data-stu-id="a7d54-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="a7d54-116">Wpisz lub wklej następujący kod po `Customer` klasie:</span><span class="sxs-lookup"><span data-stu-id="a7d54-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="a7d54-117">Dodawanie adnotacji do klasy Customer</span><span class="sxs-lookup"><span data-stu-id="a7d54-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="a7d54-118">W tym kroku utworzysz adnotację `Customer` klasy, aby wskazać jej relację `Order` z klasą.</span><span class="sxs-lookup"><span data-stu-id="a7d54-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="a7d54-119">(To dodawanie nie jest absolutnie konieczne, ponieważ zdefiniowanie relacji w dowolnym kierunku jest wystarczające do utworzenia linku.</span><span class="sxs-lookup"><span data-stu-id="a7d54-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="a7d54-120">Jednak dodanie tej adnotacji umożliwia łatwe nawigowanie po obiektach w dowolnym kierunku.</span><span class="sxs-lookup"><span data-stu-id="a7d54-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="a7d54-121">Aby dodać adnotacje do klasy Customer</span><span class="sxs-lookup"><span data-stu-id="a7d54-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="a7d54-122">Wpisz lub wklej następujący kod do `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="a7d54-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="a7d54-123">Tworzenie i uruchamianie zapytania w ramach relacji zamówienia klienta</span><span class="sxs-lookup"><span data-stu-id="a7d54-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="a7d54-124">Teraz możesz uzyskiwać dostęp `Order` do obiektów bezpośrednio `Customer` z obiektów lub w odwrotnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="a7d54-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="a7d54-125">Nie jest potrzebne jawne dołączenie między klientami i zamówieniami.</span><span class="sxs-lookup"><span data-stu-id="a7d54-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="a7d54-126">Aby uzyskać dostęp do obiektów zamówienia przy użyciu obiektów klienta</span><span class="sxs-lookup"><span data-stu-id="a7d54-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="a7d54-127">`Main` Zmodyfikuj metodę, wpisując lub wklejając następujący kod do metody:</span><span class="sxs-lookup"><span data-stu-id="a7d54-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="a7d54-128">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="a7d54-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a7d54-129">Możesz wyeliminować kod SQL w oknie konsoli, dodając do niego komentarz `db.Log = Console.Out;`.</span><span class="sxs-lookup"><span data-stu-id="a7d54-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3. <span data-ttu-id="a7d54-130">Naciśnij klawisz ENTER w oknie konsoli, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="a7d54-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="a7d54-131">Tworzenie widoku bazy danych o jednoznacznie określonym typie</span><span class="sxs-lookup"><span data-stu-id="a7d54-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="a7d54-132">Znacznie łatwiej jest zacząć od jednoznacznie określonego widoku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a7d54-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="a7d54-133">Silnie wpisywanie <xref:System.Data.Linq.DataContext> obiektu nie wymaga wywołania do <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7d54-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="a7d54-134">Można używać tabel z jednoznacznie określonymi typami we wszystkich zapytaniach, gdy używasz obiektu <xref:System.Data.Linq.DataContext> silnie określonego typu.</span><span class="sxs-lookup"><span data-stu-id="a7d54-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="a7d54-135">W poniższych krokach `Customers` utworzysz jako tabelę o jednoznacznie określonym typie, która jest mapowana na tabelę Customers w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a7d54-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="a7d54-136">Aby silnie wpisać obiekt DataContext</span><span class="sxs-lookup"><span data-stu-id="a7d54-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="a7d54-137">Dodaj następujący kod powyżej `Customer` deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="a7d54-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. <span data-ttu-id="a7d54-138">Zmodyfikuj metodę, tak aby używała silnie wpisanej <xref:System.Data.Linq.DataContext> metody w następujący sposób: `Main`</span><span class="sxs-lookup"><span data-stu-id="a7d54-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. <span data-ttu-id="a7d54-139">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="a7d54-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="a7d54-140">Dane wyjściowe okna konsoli są następujące:</span><span class="sxs-lookup"><span data-stu-id="a7d54-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="a7d54-141">Naciśnij klawisz ENTER w oknie konsoli, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="a7d54-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a7d54-142">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a7d54-142">Next Steps</span></span>  
 <span data-ttu-id="a7d54-143">Następny Przewodnik ([Przewodnik: Manipulowanie danymi (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) demonstruje sposób manipulowania danymi.</span><span class="sxs-lookup"><span data-stu-id="a7d54-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="a7d54-144">Ten Instruktaż nie wymaga zapisania dwóch instruktaży w tej serii, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="a7d54-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d54-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7d54-145">See also</span></span>

- [<span data-ttu-id="a7d54-146">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="a7d54-146">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
