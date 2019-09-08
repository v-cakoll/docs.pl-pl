---
title: 'Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: 3164656bb183e7773b098cab79d8fe5e0dc5de34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792141"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="7eb58-102">Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7eb58-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="7eb58-103">W tym instruktażu przedstawiono sposób [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] użycia *skojarzeń* do reprezentowania relacji FOREIGN KEY w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7eb58-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="7eb58-104">Ten Instruktaż został zapisany przy użyciu ustawień tworzenia Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7eb58-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7eb58-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7eb58-105">Prerequisites</span></span>  
 <span data-ttu-id="7eb58-106">Należy wykonać [następujące instrukcje: Prosty model obiektu i zapytanie (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="7eb58-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="7eb58-107">Ten przewodnik jest oparty na tym instruktażu, w tym o obecności pliku northwnd. mdf w c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="7eb58-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="7eb58-108">Omówienie</span><span class="sxs-lookup"><span data-stu-id="7eb58-108">Overview</span></span>  
 <span data-ttu-id="7eb58-109">Ten przewodnik składa się z trzech głównych zadań:</span><span class="sxs-lookup"><span data-stu-id="7eb58-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="7eb58-110">Dodawanie klasy jednostki do reprezentowania tabeli Orders w przykładowej bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7eb58-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="7eb58-111">Uzupełnianie adnotacji do `Customer` klasy w celu zwiększenia relacji `Customer` między klasami `Order` i.</span><span class="sxs-lookup"><span data-stu-id="7eb58-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="7eb58-112">Utworzenie i uruchomienie zapytania w celu przetestowania procesu uzyskiwania `Order` informacji przy `Customer` użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="7eb58-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="7eb58-113">Mapowanie relacji między tabelami</span><span class="sxs-lookup"><span data-stu-id="7eb58-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="7eb58-114">Po zdefiniowaniu `Order` `Orders.Customer` `Customers.CustomerID`klasy Utwórz definicję klasy jednostki, która zawiera następujący kod, który wskazuje, że odnosi się jako klucz obcy do. `Customer`</span><span class="sxs-lookup"><span data-stu-id="7eb58-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="7eb58-115">Aby dodać klasę Entity Order</span><span class="sxs-lookup"><span data-stu-id="7eb58-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="7eb58-116">Wpisz lub wklej następujący kod po `Customer` klasie:</span><span class="sxs-lookup"><span data-stu-id="7eb58-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="7eb58-117">Dodawanie adnotacji do klasy Customer</span><span class="sxs-lookup"><span data-stu-id="7eb58-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="7eb58-118">W tym kroku utworzysz adnotację `Customer` klasy, aby wskazać jej relację `Order` z klasą.</span><span class="sxs-lookup"><span data-stu-id="7eb58-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="7eb58-119">(To dodawanie nie jest absolutnie konieczne, ponieważ zdefiniowanie relacji w dowolnym kierunku jest wystarczające do utworzenia linku.</span><span class="sxs-lookup"><span data-stu-id="7eb58-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="7eb58-120">Jednak dodanie tej adnotacji umożliwia łatwe nawigowanie po obiektach w dowolnym kierunku.</span><span class="sxs-lookup"><span data-stu-id="7eb58-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="7eb58-121">Aby dodać adnotacje do klasy Customer</span><span class="sxs-lookup"><span data-stu-id="7eb58-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="7eb58-122">Wpisz lub wklej następujący kod do `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="7eb58-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="7eb58-123">Tworzenie i uruchamianie zapytania w ramach relacji zamówienia klienta</span><span class="sxs-lookup"><span data-stu-id="7eb58-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="7eb58-124">Teraz możesz uzyskiwać dostęp `Order` do obiektów bezpośrednio `Customer` z obiektów lub w odwrotnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="7eb58-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="7eb58-125">Nie jest potrzebne jawne *dołączenie* między klientami i zamówieniami.</span><span class="sxs-lookup"><span data-stu-id="7eb58-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="7eb58-126">Aby uzyskać dostęp do obiektów zamówienia przy użyciu obiektów klienta</span><span class="sxs-lookup"><span data-stu-id="7eb58-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="7eb58-127">`Sub Main` Zmodyfikuj metodę, wpisując lub wklejając następujący kod do metody:</span><span class="sxs-lookup"><span data-stu-id="7eb58-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="7eb58-128">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="7eb58-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="7eb58-129">W oknie komunikatu są wyświetlane dwie nazwy, a okno konsoli zawiera wygenerowany kod SQL.</span><span class="sxs-lookup"><span data-stu-id="7eb58-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3. <span data-ttu-id="7eb58-130">Zamknij okno komunikatu, aby zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="7eb58-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="7eb58-131">Tworzenie widoku bazy danych o jednoznacznie określonym typie</span><span class="sxs-lookup"><span data-stu-id="7eb58-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="7eb58-132">Znacznie łatwiej jest zacząć od jednoznacznie określonego widoku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7eb58-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="7eb58-133">Silnie wpisywanie <xref:System.Data.Linq.DataContext> obiektu nie wymaga wywołania do <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="7eb58-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="7eb58-134">Można używać tabel z jednoznacznie określonymi typami we wszystkich zapytaniach, gdy używasz obiektu <xref:System.Data.Linq.DataContext> silnie określonego typu.</span><span class="sxs-lookup"><span data-stu-id="7eb58-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="7eb58-135">W poniższych krokach `Customers` utworzysz jako tabelę o jednoznacznie określonym typie, która jest mapowana na tabelę Customers w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7eb58-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="7eb58-136">Aby silnie wpisać obiekt DataContext</span><span class="sxs-lookup"><span data-stu-id="7eb58-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="7eb58-137">Dodaj następujący kod powyżej `Customer` deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="7eb58-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. <span data-ttu-id="7eb58-138">Zmodyfikuj `Sub Main` , aby użyć silnie <xref:System.Data.Linq.DataContext> wpisanej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7eb58-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. <span data-ttu-id="7eb58-139">Naciśnij klawisz F5, aby debugować aplikację.</span><span class="sxs-lookup"><span data-stu-id="7eb58-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="7eb58-140">Dane wyjściowe okna konsoli są następujące:</span><span class="sxs-lookup"><span data-stu-id="7eb58-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="7eb58-141">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="7eb58-141">Press Enter in the Console window to close the application.</span></span>  
  
5. <span data-ttu-id="7eb58-142">W menu **plik** kliknij **Zapisz wszystko** , jeśli chcesz zapisać tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="7eb58-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7eb58-143">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7eb58-143">Next Steps</span></span>  
 <span data-ttu-id="7eb58-144">Następny Przewodnik ([Przewodnik: Manipulowanie danymi (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) demonstruje sposób manipulowania danymi.</span><span class="sxs-lookup"><span data-stu-id="7eb58-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="7eb58-145">Ten Instruktaż nie wymaga zapisania dwóch instruktaży w tej serii, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="7eb58-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb58-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7eb58-146">See also</span></span>

- [<span data-ttu-id="7eb58-147">Nauka przez przewodniki</span><span class="sxs-lookup"><span data-stu-id="7eb58-147">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
