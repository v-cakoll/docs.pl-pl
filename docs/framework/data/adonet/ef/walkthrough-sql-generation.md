---
title: 'Wskazówki: Generowanie kodu SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: ab08b404dc60483a39e5c6ae56d82b63932c3f3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="6ccd6-102">Wskazówki: Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="6ccd6-102">Walkthrough: SQL Generation</span></span>
<span data-ttu-id="6ccd6-103">W tym temacie przedstawiono, jak generowanie kodu SQL występuje w [dostawcy próbki](http://go.microsoft.com/fwlink/?LinkId=180616).</span><span class="sxs-lookup"><span data-stu-id="6ccd6-103">This topic illustrates how SQL generation occurs in the [Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616).</span></span> <span data-ttu-id="6ccd6-104">Następujące zapytanie SQL jednostki korzysta z modelu, który jest dołączony do dostawcy próbki:</span><span class="sxs-lookup"><span data-stu-id="6ccd6-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 <span data-ttu-id="6ccd6-105">Kwerenda zwraca następujące drzewo dane wyjściowe polecenia są przekazywane do dostawcy:</span><span class="sxs-lookup"><span data-stu-id="6ccd6-105">The query produces the following output command tree that is passed to the provider:</span></span>  
  
```  
DbQueryCommandTree  
|_Parameters  
|_Query : Collection{Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]}  
  |_Project  
    |_Input : 'Join4'  
    | |_InnerJoin  
    |   |_Left : 'Join1'  
    |   | |_LeftOuterJoin  
    |   |   |_Left : 'Extent1'  
    |   |   | |_Scan : dbo.Products  
    |   |   |_Right : 'Extent2'  
    |   |   | |_Scan : dbo.Categories  
    |   |   |_JoinCondition  
    |   |     |_  
    |   |       |_Var(Extent1).CategoryID  
    |   |       |_=  
    |   |       |_Var(Extent2).CategoryID  
    |   |_Right : 'Join3'  
    |   | |_LeftOuterJoin  
    |   |   |_Left : 'Extent3'  
    |   |   | |_Scan : dbo.OrderDetails  
    |   |   |_Right : 'Join2'  
    |   |   | |_LeftOuterJoin  
    |   |   |   |_Left : 'Extent4'  
    |   |   |   | |_Scan : dbo.Orders  
    |   |   |   |_Right : 'Extent5'  
    |   |   |   | |_Scan : dbo.InternationalOrders  
    |   |   |   |_JoinCondition  
    |   |   |     |_  
    |   |   |       |_Var(Extent4).OrderID  
    |   |   |       |_=  
    |   |   |       |_Var(Extent5).OrderID  
    |   |   |_JoinCondition  
    |   |     |_  
    |   |       |_Var(Extent3).OrderID  
    |   |       |_=  
    |   |       |_Var(Join2).Extent4.OrderID  
    |   |_JoinCondition  
    |     |_  
    |       |_Var(Join1).Extent1.ProductID  
    |       |_=  
    |       |_Var(Join3).Extent3.ProductID  
    |_Projection  
      |_NewInstance : Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]  
        |_Column : 'C1'  
        | |_1  
        |_Column : 'ProductID'  
        | |_Var(Join4).Join1.Extent1.ProductID  
        |_Column : 'ProductName'  
        | |_Var(Join4).Join1.Extent1.ProductName  
        |_Column : 'CategoryName'  
        | |_Var(Join4).Join1.Extent2.CategoryName  
        |_Column : 'ShipCountry'  
        | |_Var(Join4).Join3.Join2.Extent4.ShipCountry  
        |_Column : 'ProductID1'  
          |_Var(Join4).Join3.Extent3.ProductID  
```  
  
 <span data-ttu-id="6ccd6-106">W tym temacie opisano, jak tłumaczenie tego drzewa poleceń dane wyjściowe do następujących instrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>  
  
```  
SELECT   
1 AS [C1],   
[Extent1].[ProductID] AS [ProductID],   
[Extent1].[ProductName] AS [ProductName],   
[Extent2].[CategoryName] AS [CategoryName],   
[Join3].[ShipCountry] AS [ShipCountry],   
[Join3].[ProductID] AS [ProductID1]  
FROM   [dbo].[Products] AS [Extent1]  
LEFT OUTER JOIN [dbo].[Categories] AS [Extent2] ON [Extent1].[CategoryID] = [Extent2].[CategoryID]  
INNER JOIN    
(SELECT [Extent3].[OrderID] AS [OrderID1], [Extent3].[ProductID] AS [ProductID], [Extent3].[UnitPrice] AS [UnitPrice], [Extent3].[Quantity] AS [Quantity], [Extent3].[Discount] AS [Discount], [Join2].[OrderID2], [Join2].[CustomerID], [Join2].[EmployeeID], [Join2].[OrderDate], [Join2].[RequiredDate], [Join2].[ShippedDate], [Join2].[Freight], [Join2].[ShipName], [Join2].[ShipAddress], [Join2].[ShipCity], [Join2].[ShipRegion], [Join2].[ShipPostalCode], [Join2].[ShipCountry], [Join2].[OrderID3], [Join2].[CustomsDescription], [Join2].[ExciseTax]  
FROM  [dbo].[OrderDetails] AS [Extent3]  
LEFT OUTER JOIN    
      (SELECT [Extent4].[OrderID] AS [OrderID2], [Extent4].[CustomerID] AS [CustomerID], [Extent4].[EmployeeID] AS [EmployeeID], [Extent4].[OrderDate] AS [OrderDate], [Extent4].[RequiredDate] AS [RequiredDate], [Extent4].[ShippedDate] AS [ShippedDate], [Extent4].[Freight] AS [Freight], [Extent4].[ShipName] AS [ShipName], [Extent4].[ShipAddress] AS [ShipAddress], [Extent4].[ShipCity] AS [ShipCity], [Extent4].[ShipRegion] AS [ShipRegion], [Extent4].[ShipPostalCode] AS [ShipPostalCode], [Extent4].[ShipCountry] AS [ShipCountry], [Extent5].[OrderID] AS [OrderID3], [Extent5].[CustomsDescription] AS [CustomsDescription], [Extent5].[ExciseTax] AS [ExciseTax]  
FROM  [dbo].[Orders] AS [Extent4]  
LEFT OUTER JOIN [dbo].[InternationalOrders] AS [Extent5] ON [Extent4].[OrderID] = [Extent5].[OrderID]   
      ) AS [Join2] ON [Extent3].[OrderID] = [Join2].[OrderID2]   
   ) AS [Join3] ON [Extent1].[ProductID] = [Join3].[ProductID]  
```  
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="6ccd6-107">Pierwszą fazę generowanie kodu SQL: odwiedzający wyrażenie drzewa</span><span class="sxs-lookup"><span data-stu-id="6ccd6-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>  
 <span data-ttu-id="6ccd6-108">Na poniższym rysunku przedstawiono początkowy stan pusty obiekt odwiedzający.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="6ccd6-109">W tym temacie przedstawiono wyjaśnienie wskazówki dotyczące właściwości.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>  
  
 <span data-ttu-id="6ccd6-110">![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="6ccd6-110">![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>  
  
 <span data-ttu-id="6ccd6-111">Po odwiedzeniu węzła projektu VisitInputExpression jest wywoływana przez jego danych wejściowych (Join4), która wyzwala odwiedziny Join4 przez metodę VisitJoinExpression.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="6ccd6-112">Ponieważ jest to najwyżej sprzężenia, IsParentAJoin zwraca wartość false i nowych SqlSelectStatement (SelectStatement0) jest tworzony i wypychana na stosie instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="6ccd6-113">Ponadto nowy zakres (scope0) została wprowadzona w tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="6ccd6-114">Przed odwiedzenia pierwszy danych wejściowych (lewych) sprzężenia 'true' spoczywa na stosie IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="6ccd6-115">Tuż przed odwiedzenia Join1, czyli po lewej stronie wprowadzania Join4 stan obiektu odwiedzającego jest pokazany na rysunku dalej.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>  
  
 <span data-ttu-id="6ccd6-116">![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="6ccd6-116">![Diagram](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>  
  
 <span data-ttu-id="6ccd6-117">Gdy odwiedź sprzężenie metoda jest wywoływana przez Join4 IsParentAJoin ma wartość true, w związku z tym ponownie używa bieżącej instrukcji select SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="6ccd6-118">Nowy zakres jest wprowadzona (Zakres1).</span><span class="sxs-lookup"><span data-stu-id="6ccd6-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="6ccd6-119">Przed jego lewy element podrzędny, Extent1, odwiedzając innego true spoczywa na stosie IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>  
  
 <span data-ttu-id="6ccd6-120">Po odwiedzeniu Extent1, ponieważ IsParentAJoin zwraca wartość true, zwraca SqlBuilder, zawierający "[dbo]. [Produkty] ".</span><span class="sxs-lookup"><span data-stu-id="6ccd6-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="6ccd6-121">Zwraca formantu do metody odwiedzający Join4.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="6ccd6-122">Wpis jest zdjęte ze stosu z IsParentAJoin i ProcessJoinInputResult jest wywoływana, które dołącza odwiedzający Extent1 do klauzuli From SelectStatement0 wynik.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="6ccd6-123">Nowy z symbolu, symbol_Extent1, dla nazwy powiązania wejściowego "Extent1" został utworzony, dodane do FromExtents SelectStatement0, a także "Jako" i symbol_Extent1 są dołączane do klauzuli from.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="6ccd6-124">Nowy wpis jest dodawany do AllExtentNames do "Extent1" o wartości 0.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="6ccd6-125">Nowy wpis zostanie dodany do bieżącego zakresu w tabeli symboli do skojarzenia z jego symbol_Extent1 symbol "Extent1".</span><span class="sxs-lookup"><span data-stu-id="6ccd6-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="6ccd6-126">Symbol_Extent1 jest także dodawane do AllJoinExtents z SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>  
  
 <span data-ttu-id="6ccd6-127">Przed odwiedzenia odpowiednie dane wejściowe z Join1 "LEFT OUTER JOIN" zostanie dodany do klauzuli From SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="6ccd6-128">Ponieważ odpowiednie dane wejściowe to wyrażenie skanowania, true ponownie spoczywa na stos IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="6ccd6-129">Stan przed odwiedzający odpowiednie dane wejściowe, jak pokazano na rysunku dalej.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-129">The state before visiting the right input as shown in the next figure.</span></span>  
  
 <span data-ttu-id="6ccd6-130">![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="6ccd6-130">![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>  
  
 <span data-ttu-id="6ccd6-131">Dane wejściowe są przetwarzane w taki sam sposób jak po lewej stronie dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="6ccd6-132">Stan po odwiedzeniu odpowiednie dane wejściowe pokazano na rysunku dalej.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-132">The state after visiting the right input is shown in the next figure.</span></span>  
  
 <span data-ttu-id="6ccd6-133">![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="6ccd6-133">![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>  
  
 <span data-ttu-id="6ccd6-134">Następny "false" spoczywa na stosie IsParentAJoin i Var(Extent1) warunek sprzężenia. CategoryID == Var(Extent2). CategoryID jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="6ccd6-135">Var(Extenent1) jest rozpoznać < symbol_Extent1 > po sprawdzeniu się w tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-135">Var(Extenent1) is resolved to <symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="6ccd6-136">Ponieważ wystąpienie nie zostanie rozwiązany do symbolu proste, w wyniku przetworzenia Var(Extent1). CategoryID, SqlBuilder z \<symbol1 >. " Zwracany jest identyfikatorem kategorii".</span><span class="sxs-lookup"><span data-stu-id="6ccd6-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="6ccd6-137">Podobnie po stronie porównania jest przetwarzany i wynik odwiedzający warunek sprzężenia jest dołączany do klauzuli FROM SelectStatement1, a wartość "false" jest zdjęte ze stosu ze stosu IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>  
  
 <span data-ttu-id="6ccd6-138">O tym Join1 zostały całkowicie przetworzone, a zakres jest zdjęte ze stosu z tabelą symboli.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>  
  
 <span data-ttu-id="6ccd6-139">Zwraca sterowania do przetwarzania Join4, nadrzędny Join1.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="6ccd6-140">Ponieważ podrzędne ponownie użyć instrukcji Select, zakresy Join1 są zastępowane jeden symbol sprzężenia < joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol <joinSymbol_Join1>.</span></span> <span data-ttu-id="6ccd6-141">Także nowy wpis jest dodawany do tabeli symboli, aby skojarzyć Join1 z < joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-141">Also a new entry is added to the symbol table to associate Join1 with <joinSymbol_Join1>.</span></span>  
  
 <span data-ttu-id="6ccd6-142">Następny węzeł przetwarzania jest Join3, drugi podrzędnym Join4.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="6ccd6-143">Po wykonaniu prawy element podrzędny, "false" spoczywa na stos IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="6ccd6-144">Następny rysunek przedstawia stan osoby odwiedzającej jest możliwe w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-144">The state of the visitor at this point is illustrated in the next figure.</span></span>  
  
 <span data-ttu-id="6ccd6-145">![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="6ccd6-145">![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>  
  
 <span data-ttu-id="6ccd6-146">Dla Join3 IsParentAJoin zwraca wartość false i należy uruchomić nowe SqlSelectStatement (SelectStatement1) i wypchnąć go na stosie.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="6ccd6-147">Przetwarzanie będzie kontynuowane, jak z poprzedniej poprzedniej sprzężenia, nowego zakresu spoczywa na stosie i elementy podrzędne są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="6ccd6-148">Lewy element podrzędny jest zakres (Extent3) i prawy element podrzędny sprzężenia (Join2), którą należy uruchomić nowe SqlSelectStatement: SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="6ccd6-149">Elementy podrzędne na Join2 są również zakresy i są agregowane do SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>  
  
 <span data-ttu-id="6ccd6-150">Stan obiektu odwiedzającego prawa po odwiedzeniu Join2, ale przed jego przetwarzanie końcowe (ProcessJoinInputResult) jest wykonywane jest pokazywana w następny rysunek:</span><span class="sxs-lookup"><span data-stu-id="6ccd6-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>  
  
 <span data-ttu-id="6ccd6-151">![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="6ccd6-151">![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>  
  
 <span data-ttu-id="6ccd6-152">Na poprzedniej ilustracji SelectStatement2 jest wyświetlana jako przestawne wolnego ponieważ został zdjęte ze stosu poza stosu, ale nie została jeszcze post przetworzone przez element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="6ccd6-153">Wymaga do dodania do części od elementu nadrzędnego, ale nie jest pełną instrukcję SQL bez klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="6ccd6-154">Tak w tym momencie domyślne kolumny (wszystkie kolumny tworzone przez komponenty) są dodawane do listy wyboru przez metodę AddDefaultColumns.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="6ccd6-155">AddDefaultColumns przechodzi przez symbole w FromExtents i dla każdego symbolu dodaje wszystkie kolumny w zakresie.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="6ccd6-156">Dla symbolu proste wygląda na typ symbolu do pobrania jego właściwości mają zostać dodane.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="6ccd6-157">Wypełnia słownik AllColumnNames z nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="6ccd6-158">Ukończono SelectStatement2 jest dołączany do klauzuli FROM SelectStatement1.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>  
  
 <span data-ttu-id="6ccd6-159">Następnie jest tworzony nowy symbol sprzężenia, do reprezentowania Join2, jest oznaczony jako zagnieżdżony sprzężenia i dodane do AllJoinExtents SelectStatement1 i dodane do tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="6ccd6-160">Teraz warunek sprzężenia Join3, Var(Extent3). OrderID = Var(Join2). Extent4.OrderID, musi być przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="6ccd6-161">Przetwarzanie z lewej strony jest podobny do Join1 warunek sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="6ccd6-162">Jednak przetwarzanie prawo i po stronie "Var(Join2). Extent4.OrderID"jest inny, ponieważ spłaszczanie sprzężenia jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>  
  
 <span data-ttu-id="6ccd6-163">Następny rysunek przedstawia stan prawa odwiedzający przed DbPropertyExpression "Var(Join2). Extent4.OrderID"jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>  
  
 <span data-ttu-id="6ccd6-164">Należy rozważyć sposób "Var(Join2). Odwiedzenia Extent4.OrderID".</span><span class="sxs-lookup"><span data-stu-id="6ccd6-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="6ccd6-165">Pierwsza strona, właściwości wystąpienia "Var(Join2). Extent4 "odwiedzenia, który jest inny DbPropertyExpression i najpierw odwiedza wystąpienia"Var(Join2)".</span><span class="sxs-lookup"><span data-stu-id="6ccd6-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="6ccd6-166">W górnym większości zakresie w tabeli symboli "Join2" jest rozpoznawany jako < joinSymbol_join2 >.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-166">In the top most scope in the symbol table, "Join2" resolves to <joinSymbol_join2>.</span></span> <span data-ttu-id="6ccd6-167">W metodzie odwiedziny dla DbPropertyExpression przetwarzania "Var(Join2). Extent4 "należy zauważyć, że symbol sprzężenia został zwrócony podczas odwiedzania wystąpienie i spłaszczania jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>  
  
 <span data-ttu-id="6ccd6-168">Ponieważ jest zagnieżdżony sprzężenia, możemy wyszukiwania właściwości "Extent4" w słowniku NameToExtent symbolu sprzężenia, odpowiada < symbol_Extent4 > i zwraca nowy SymbolPair (< joinSymbol_join2 >, < symbol_Extent4 >).</span><span class="sxs-lookup"><span data-stu-id="6ccd6-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to <symbol_Extent4> and return a new SymbolPair(<joinSymbol_join2>, <symbol_Extent4>).</span></span> <span data-ttu-id="6ccd6-169">Ponieważ parę symbol jest zwracana z przetwarzanie wystąpienia "Var(Join2). Extent4.OrderID"właściwości"OrderID"jest rozwiązany z ColumnPart pary tego symbolu (< symbol_Extent4 >) z listą kolumn zakresu, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="6ccd6-170">Dlatego "Var(Join2). Extent4.OrderID"zostanie rozwiązany do {< joinSymbol_Join2 >". ", < symbol_OrderID >}.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-170">So, "Var(Join2).Extent4.OrderID" is resolved to { <joinSymbol_Join2>, ".", <symbol_OrderID>}.</span></span>  
  
 <span data-ttu-id="6ccd6-171">Warunek sprzężenia Join4 podobnie jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="6ccd6-172">Formant zwraca do metody VisitInputExpression przetwarzania górnej większości projektu.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="6ccd6-173">Patrzeć FromExtents z SelectStatement0 zwrócone, danych wejściowych jest rozpoznawany jako sprzężenia i usuwa oryginalny zakres i zastępuje je nowy zakres symbolem tylko sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="6ccd6-174">Zaktualizowano także tabeli symboli, a następne projekcji częścią projektu jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="6ccd6-175">Rozpoznawanie właściwości i spłaszczanie zakresów sprzężenia jest zgodnie z wcześniejszym opisem.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>  
  
 <span data-ttu-id="6ccd6-176">![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="6ccd6-176">![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>  
  
 <span data-ttu-id="6ccd6-177">Na koniec jest generowany SqlSelectStatement następujące:</span><span class="sxs-lookup"><span data-stu-id="6ccd6-177">Finally, the following SqlSelectStatement is produced:</span></span>  
  
```  
SELECT:   
  "1", " AS ", "[C1]",  
  <symbol_Extent1>, ".", "[ProductID]", " AS ", "[ProductID]",   
  <symbol_Extent1>, ".", "[ProductName]", " AS ", "[ProductName]",  
  <symbol_Extent2>, ".", "[CategoryName]", " AS ", "[CategoryName]",  
  <joinSymbol_Join3>, ".", <symbol_ShipCountry>, " AS ", "[ShipCountry]",   
  <joinSymbol_Join3>, ".", <symbol_ProductID>, " AS ", "[ProductID1]"  
FROM: "[dbo].[Products]", " AS ", <symbol_Extent1>,   
        "LEFT OUTER JOIN ""[dbo].[Categories]", " AS ", <symbol_Extent2>, " ON ", <symbol_Extent1>, ".", "[CategoryID]", " = ", <symbol_Extent2>, ".", "[CategoryID]",   
        "INNER JOIN ",   
        " (", SELECT:   
           <symbol_Extent3>, ".", "[OrderID]", " AS ", <symbol_OrderID>, ",   
              <symbol_Extent3>, ".", "[ProductID]", " AS ", <symbol_ProductID>, ...,  
         <joinSymbol_Join2>, ".", <symbol_OrderID_2>, ", ",   
           <joinSymbol_Join2>, ".", <symbol_CustomerID>, ....,    
        <joinSymbol_Join2>, ".", <symbol_OrderID_3>,   
<joinSymbol_Join2>, ".", <symbol_CustomsDescription>,   
<joinSymbol_Join2>, ".", <symbol_ExciseTax>  
FROM: "[dbo].[OrderDetails]", " AS ", <symbol_Extent3>,   
"LEFT OUTER JOIN ",   
" (", SELECT:   
<symbol_Extent4>, ".", "[OrderID]", " AS ", <symbol_OrderID_2>,   
<symbol_Extent4>, ".", "[CustomerID]", " AS ", <symbol_CustomerID>, ...  
<symbol_Extent5>, ".", "[OrderID]", " AS ", <symbol_OrderID_3>,  
<symbol_Extent5>, ".", "[CustomsDescription]", " AS ", <symbol_CustomsDescription>,  
<symbol_Extent5>, ".", "[ExciseTax]", " AS ", <symbol_ExciseTax>  
FROM: "[dbo].[Orders]", " AS ", <symbol_Extent4>,  
"LEFT OUTER JOIN ", , "[dbo].[InternationalOrders]", " AS ", <symbol_Extent5>,   
" ON ", <symbol_Extent4>, ".", "[OrderID]", " = ", , <symbol_Extent5>, ".", "[OrderID]"  
" )", " AS ", <joinSymbol_Join2>, " ON ", , , <symbol_Extent3>, ".", "[OrderID]", " = ", , <joinSymbol_Join2>, ".", <symbol_OrderID_2>  
" )", " AS ", <joinSymbol_Join3>, " ON ", , , <symbol_Extent1>, ".", "[ProductID]", " = ", , <joinSymbol_Join3>, ".", <symbol_ProductID>  
```  
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="6ccd6-178">Drugi etap generowanie kodu SQL: generowanie polecenie String</span><span class="sxs-lookup"><span data-stu-id="6ccd6-178">Second Phase of SQL Generation: Generating the String Command</span></span>  
 <span data-ttu-id="6ccd6-179">Na drugim etapie tworzących rzeczywiste nazwy symboli i skupimy symboli reprezentujący kolumny o nazwie "OrderID", jak w przypadku tej konflikt musi zostać rozpoznane.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="6ccd6-180">Te zostały wyróżnione SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="6ccd6-181">Należy pamiętać, że sufiksy używane na ilustracji są tylko, aby podkreślić, że są one różnych wystąpień, aby nie reprezentują wszelkie nowe nazwy, ponieważ w tej etap nazwy końcowego (być może różnymi tworzą oryginalnej nazwy) nie został jeszcze przypisany.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>  
  
 <span data-ttu-id="6ccd6-182">Symbol pierwszy znaleziony, która musi zostać zmienione jest < symbol_OrderID >.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-182">The first symbol found that needs to be renamed is <symbol_OrderID>.</span></span> <span data-ttu-id="6ccd6-183">Nie przypisano jej nową nazwę jako "OrderID1", 1 jest oznaczony jako ostatniego używać sufiksu dla "OrderID" oraz symbol jest oznaczony jako nie wymagające zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="6ccd6-184">Następnie to pierwsze użycie < symbol_OrderID_2 > zostanie znaleziony.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-184">Next, the first usage of <symbol_OrderID_2> is found.</span></span> <span data-ttu-id="6ccd6-185">Jest zmieniana na używają sufiksu dostępne dalej ("OrderID2") i ponownie oznaczony jako nie wymagające zmiany nazwy, tak, aby następnym służy on nie uzyskać zmieniona.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="6ccd6-186">Jest to realizowane dla < symbol_OrderID_3 > zbyt.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-186">This is done for <symbol_OrderID_3> too.</span></span>  
  
 <span data-ttu-id="6ccd6-187">Na koniec drugiej fazy jest generowany końcowej instrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="6ccd6-187">At the end of the second phase, the final SQL statement is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ccd6-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ccd6-188">See Also</span></span>  
 [<span data-ttu-id="6ccd6-189">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="6ccd6-189">SQL Generation in the Sample Provider</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
