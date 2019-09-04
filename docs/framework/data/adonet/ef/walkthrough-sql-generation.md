---
title: 'Przewodnik: Generowanie kodu SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 09b5a3c2dea5cd0483d617ee8064b41dc19c3374
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248288"
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="b0664-102">Przewodnik: Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="b0664-102">Walkthrough: SQL Generation</span></span>

<span data-ttu-id="b0664-103">W tym temacie przedstawiono sposób generowania kodu SQL w [przykładowym dostawcy](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0).</span><span class="sxs-lookup"><span data-stu-id="b0664-103">This topic illustrates how SQL generation occurs in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0).</span></span> <span data-ttu-id="b0664-104">Poniższe zapytanie Entity SQL używa modelu dołączonego do przykładowego dostawcy:</span><span class="sxs-lookup"><span data-stu-id="b0664-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

<span data-ttu-id="b0664-105">Zapytanie generuje następujące drzewo poleceń wyjściowych, które są przekazywane do dostawcy:</span><span class="sxs-lookup"><span data-stu-id="b0664-105">The query produces the following output command tree that is passed to the provider:</span></span>

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

 <span data-ttu-id="b0664-106">W tym temacie opisano sposób tłumaczenia tego drzewa poleceń wyjściowych na następujące instrukcje języka SQL.</span><span class="sxs-lookup"><span data-stu-id="b0664-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>

```sql
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

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="b0664-107">Pierwsza faza generowania kodu SQL: Odwiedzanie drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="b0664-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="b0664-108">Na poniższej ilustracji przedstawiono początkowy pusty stan osoby odwiedzającej.</span><span class="sxs-lookup"><span data-stu-id="b0664-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="b0664-109">W tym temacie są wyświetlane tylko właściwości odpowiednie dla wyjaśnienia przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b0664-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>

<span data-ttu-id="b0664-110">![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="b0664-110">![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>

<span data-ttu-id="b0664-111">Gdy jest odwiedzany węzeł projektu, VisitInputExpression jest wywoływana nad jego danymi wejściowymi (Join4), które wyzwalają odwiedzanie Join4 przez metodę VisitJoinExpression.</span><span class="sxs-lookup"><span data-stu-id="b0664-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="b0664-112">Ponieważ jest to przyłączanie do góry, IsParentAJoin zwraca wartość false, a nowy SqlSelectStatement (SelectStatement0) jest tworzony i wypychany na stosie instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="b0664-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="b0664-113">Ponadto w tabeli symboli wprowadzono nowy zakres (scope0).</span><span class="sxs-lookup"><span data-stu-id="b0664-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="b0664-114">Przed pierwszym (lewym) wejściem sprzężenia zostanie odwiedzana wartość "prawda" jest wypychana na stosie IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="b0664-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="b0664-115">Bezpośrednio przed Join1, który jest po lewej stronie Join4, jest odwiedzany, a stan osoby odwiedzającej jest jak pokazano na następnej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="b0664-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>

<span data-ttu-id="b0664-116">![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="b0664-116">![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>

<span data-ttu-id="b0664-117">Gdy wywoływana jest metoda dołączania za pośrednictwem Join4, IsParentAJoin ma wartość true, dlatego ponownie używa bieżącej instrukcji SELECT SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="b0664-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="b0664-118">Wprowadzono nowy zakres (zakres1).</span><span class="sxs-lookup"><span data-stu-id="b0664-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="b0664-119">Przed odwiedzeniem jego lewego elementu podrzędnego Extent1, inne prawdziwe jest wypychane na stosie IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="b0664-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>

<span data-ttu-id="b0664-120">Gdy Extent1 jest odwiedzany, ponieważ IsParentAJoin zwraca wartość true, zwraca element SqlBuilder zawierający "[dbo]. [Produkty] ".</span><span class="sxs-lookup"><span data-stu-id="b0664-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="b0664-121">Kontrolka powraca do metody odwiedzającej Join4.</span><span class="sxs-lookup"><span data-stu-id="b0664-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="b0664-122">Wpis jest zdjęte z IsParentAJoin, a ProcessJoinInputResult jest wywoływany, co powoduje dołączenie wyniku odwiedzania Extent1 do klauzuli FROM elementu SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="b0664-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="b0664-123">Zostanie utworzony nowy symbol z symbol_Extent1, dla nazwy powiązania wejściowego "Extent1", dodany do FromExtents of SelectStatement0, a także "As" i symbol_Extent1, są dołączane do klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="b0664-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="b0664-124">Nowy wpis zostanie dodany do AllExtentNames dla "Extent1" z wartością 0.</span><span class="sxs-lookup"><span data-stu-id="b0664-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="b0664-125">Nowy wpis zostanie dodany do bieżącego zakresu w tabeli symboli, aby skojarzyć "Extent1" z jego symbolem symbol_Extent1.</span><span class="sxs-lookup"><span data-stu-id="b0664-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="b0664-126">Symbol_Extent1 jest również dodawany do AllJoinExtents SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b0664-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>

<span data-ttu-id="b0664-127">Przed odwiedzeniem prawego wejścia Join1 "lewe SPRZĘŻENIe zewnętrzne" jest dodawane do klauzuli FROM SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="b0664-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="b0664-128">Ponieważ prawidłowe dane wejściowe są wyrażeniu skanowania, wartość true jest ponownie wypychana do stosu IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="b0664-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="b0664-129">Przed odpisaniem właściwych danych wejściowych, jak pokazano na następnej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="b0664-129">The state before visiting the right input as shown in the next figure.</span></span>

<span data-ttu-id="b0664-130">![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="b0664-130">![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>

<span data-ttu-id="b0664-131">Prawidłowe dane wejściowe są przetwarzane w taki sam sposób, jak lewe dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b0664-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="b0664-132">Stan po odwiedzeniu prawego wejścia jest pokazywany na następnym rysunku.</span><span class="sxs-lookup"><span data-stu-id="b0664-132">The state after visiting the right input is shown in the next figure.</span></span>

<span data-ttu-id="b0664-133">![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="b0664-133">![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>

<span data-ttu-id="b0664-134">Następny "false" jest wypychany na stosie IsParentAJoin i warunku sprzężenia var (Extent1). IDKategorii = = var (Extent2). Identyfikator IDKategorii jest przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="b0664-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="b0664-135">Var (Extent1) jest rozpoznawana \<do symbol_Extent1 > Po odszukaniu w tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="b0664-135">Var(Extent1) is resolved to \<symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="b0664-136">Ponieważ wystąpienie jest rozpoznawane jako prosty symbol, w wyniku przetwarzania var (Extent1). IDKategorii, element SqlBuilder z \<symbol1 > ". IDKategorii jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="b0664-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="b0664-137">Podobnie druga Strona porównania jest przetwarzana, a wynik przeszukiwania warunku sprzężenia jest dołączany do klauzuli FROM elementu SelectStatement1, a wartość "false" jest zdjęte ze stosu IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="b0664-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>

<span data-ttu-id="b0664-138">Dzięki temu Join1 został całkowicie przetworzony i zakres jest zdjęte z tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="b0664-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>

<span data-ttu-id="b0664-139">Kontrolka powraca do przetwarzania Join4, nadrzędnego elementu Join1.</span><span class="sxs-lookup"><span data-stu-id="b0664-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="b0664-140">Ponieważ element podrzędny ponownie użył instrukcji SELECT, zakresy Join1 są zastępowane pojedynczym symbolem \<sprzężenia joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="b0664-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol \<joinSymbol_Join1>.</span></span> <span data-ttu-id="b0664-141">Ponadto do tabeli symboli zostanie dodany nowy wpis, aby skojarzyć Join1 z \<joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="b0664-141">Also a new entry is added to the symbol table to associate Join1 with \<joinSymbol_Join1>.</span></span>

<span data-ttu-id="b0664-142">Następny węzeł do przetworzenia to Join3, drugi element podrzędny Join4.</span><span class="sxs-lookup"><span data-stu-id="b0664-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="b0664-143">Ponieważ jest to prawy element podrzędny, "false" jest wypychany do stosu IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="b0664-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="b0664-144">Stan odwiedzającego w tym punkcie przedstawiono na następnej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="b0664-144">The state of the visitor at this point is illustrated in the next figure.</span></span>

<span data-ttu-id="b0664-145">![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="b0664-145">![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>

<span data-ttu-id="b0664-146">W przypadku Join3 funkcja IsParentAJoin zwraca wartość false i musi uruchomić nową SqlSelectStatement (SelectStatement1) i wypchnąć ją na stosie.</span><span class="sxs-lookup"><span data-stu-id="b0664-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="b0664-147">Przetwarzanie będzie kontynuowane, jak poprzednio poprzednie sprzężenia, nowy zakres jest wypychany na stosie, a elementy podrzędne są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="b0664-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="b0664-148">Lewy element podrzędny jest zakresem (Extent3), a prawy element podrzędny to sprzężenie (Join2), które również musi rozpocząć nową SqlSelectStatement: SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="b0664-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="b0664-149">Elementy podrzędne w Join2 są również zakresami i są agregowane w SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="b0664-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>

<span data-ttu-id="b0664-150">Stan odwiedzania po Join2 jest odwiedzany, ale przed rozpoczęciem jego przetwarzania post (ProcessJoinInputResult) pokazano na następnej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="b0664-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>

<span data-ttu-id="b0664-151">![Diagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="b0664-151">![Diagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>

<span data-ttu-id="b0664-152">Na powyższym rysunku SelectStatement2 jest pokazywany jako wolny swobodny, ponieważ został zdjęte poza stosem, ale nie został jeszcze przetworzony przez element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="b0664-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="b0664-153">Należy dodać go do elementu z częścią nadrzędnej, ale nie jest to kompletna instrukcja SQL bez klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="b0664-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="b0664-154">Dlatego w tym momencie domyślne kolumny (wszystkie kolumny utworzone przez dane wejściowe) są dodawane do listy wyboru przez metodę AddDefaultColumns.</span><span class="sxs-lookup"><span data-stu-id="b0664-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="b0664-155">AddDefaultColumns wykonuje iterację symboli w FromExtents i dla każdego symbolu dodaje wszystkie kolumny, które zostały wprowadzone do zakresu.</span><span class="sxs-lookup"><span data-stu-id="b0664-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="b0664-156">Dla prostego symbolu sprawdza typ symbolu, aby pobrać wszystkie jego właściwości do dodania.</span><span class="sxs-lookup"><span data-stu-id="b0664-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="b0664-157">Wypełnia również słownik AllColumnNames nazwami kolumn.</span><span class="sxs-lookup"><span data-stu-id="b0664-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="b0664-158">Ukończony SelectStatement2 jest dołączany do klauzuli FROM SelectStatement1.</span><span class="sxs-lookup"><span data-stu-id="b0664-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>

<span data-ttu-id="b0664-159">Następnie nowy symbol sprzężenia jest tworzony w celu reprezentowania Join2, zostanie oznaczony jako zagnieżdżone sprzężenie i dodany do AllJoinExtents SelectStatement1 i dodany do tabeli symboli.</span><span class="sxs-lookup"><span data-stu-id="b0664-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="b0664-160">Teraz warunek sprzężenia Join3, VAR (Extent3). IDZamówienia = var (Join2). Extent4. IDZamówienia, musi zostać przetworzony.</span><span class="sxs-lookup"><span data-stu-id="b0664-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="b0664-161">Przetwarzanie lewej strony jest podobne do warunku sprzężenia Join1.</span><span class="sxs-lookup"><span data-stu-id="b0664-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="b0664-162">Jednak przetwarzanie po prawej stronie "var (Join2). Extent4. IDZamówienia "różni się, ponieważ jest wymagane spłaszczanie sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="b0664-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>

<span data-ttu-id="b0664-163">Następny rysunek przedstawia stan odwiedzających bezpośrednio przed DbPropertyExpression "var (Join2). Extent4. IDZamówienia "jest przetwarzana.</span><span class="sxs-lookup"><span data-stu-id="b0664-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>

<span data-ttu-id="b0664-164">Rozważ, jak "var (Join2). Extent4. IDZamówienia "jest odwiedzana.</span><span class="sxs-lookup"><span data-stu-id="b0664-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="b0664-165">Najpierw Właściwość wystąpienia "var (Join2). Extent4 "jest odwiedzana, która jest kolejną DbPropertyExpression i najpierw odwiedza swoje wystąpienie" var (Join2) ".</span><span class="sxs-lookup"><span data-stu-id="b0664-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="b0664-166">W najbardziej najwyższym zakresie w tabeli symboli "Join2" jest rozpoznawana jako \<joinSymbol_join2 >.</span><span class="sxs-lookup"><span data-stu-id="b0664-166">In the top most scope in the symbol table, "Join2" resolves to \<joinSymbol_join2>.</span></span> <span data-ttu-id="b0664-167">W metodzie zapoznaj się z DbPropertyExpression przetwarzaniem "var (Join2). Extent4 "Zwróć uwagę, że symbol sprzężenia został zwrócony podczas odwiedzania wystąpienia i jest wymagane spłaszczonie.</span><span class="sxs-lookup"><span data-stu-id="b0664-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>

<span data-ttu-id="b0664-168">Ponieważ jest to zagnieżdżony element join, należy wyszukać Właściwość "Extent4" w słowniku NameToExtent symbolu sprzężenia, rozwiązać ją na \<symbol_Extent4 > i zwrócić nową SymbolPair (\<joinSymbol_join2 >, \<symbol_Extent4 >).</span><span class="sxs-lookup"><span data-stu-id="b0664-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to \<symbol_Extent4> and return a new SymbolPair(\<joinSymbol_join2>, \<symbol_Extent4>).</span></span> <span data-ttu-id="b0664-169">Ponieważ para symboli jest zwracana z przetwarzania wystąpienia "var (Join2). Extent4. IDZamówienia ", właściwość" IDZamówienia "jest rozpoznawana z ColumnPart tej pary symboli (\<symbol_Extent4 >), która zawiera listę kolumn w zakresie, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="b0664-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (\<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="b0664-170">Tak więc, "var (Join2). Extent4. IDZamówienia "jest rozpoznawana jako \<{joinSymbol_Join2 >,". " \<, symbol_OrderID >}.</span><span class="sxs-lookup"><span data-stu-id="b0664-170">So, "Var(Join2).Extent4.OrderID" is resolved to { \<joinSymbol_Join2>, ".", \<symbol_OrderID>}.</span></span>

<span data-ttu-id="b0664-171">Warunek sprzężenia Join4 jest przetwarzany podobnie.</span><span class="sxs-lookup"><span data-stu-id="b0664-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="b0664-172">Kontrolka powraca do metody VisitInputExpression, która przetworzyła najwyższy projekt.</span><span class="sxs-lookup"><span data-stu-id="b0664-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="b0664-173">Patrząc na FromExtents zwróconej SelectStatement0, dane wejściowe są identyfikowane jako sprzężenie i usuwają oryginalne zakresy i zastępuje je nowym zakresem, tylko symbolem sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="b0664-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="b0664-174">Tabela symboli jest również aktualizowana, a następnie zostanie przetworzona część projekcji projektu.</span><span class="sxs-lookup"><span data-stu-id="b0664-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="b0664-175">Rozpoznawanie właściwości i spłaszczenie zakresów sprzężenia jest zgodnie z wcześniejszym opisem.</span><span class="sxs-lookup"><span data-stu-id="b0664-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>

<span data-ttu-id="b0664-176">![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="b0664-176">![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>

<span data-ttu-id="b0664-177">Na koniec jest tworzony następujący SqlSelectStatement:</span><span class="sxs-lookup"><span data-stu-id="b0664-177">Finally, the following SqlSelectStatement is produced:</span></span>

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

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="b0664-178">Druga faza generowania kodu SQL: Generowanie ciągu polecenia</span><span class="sxs-lookup"><span data-stu-id="b0664-178">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="b0664-179">Druga faza tworzy rzeczywiste nazwy symboli i koncentruje się na symbolach reprezentujących kolumny o nazwie "IDZamówienia", tak jak w tym przypadku należy rozwiązać konflikt.</span><span class="sxs-lookup"><span data-stu-id="b0664-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="b0664-180">Są one wyróżnione w SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="b0664-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="b0664-181">Należy pamiętać, że sufiksy używane na rysunku są tylko podkreślenia, że są to różne wystąpienia, a nie do reprezentowania żadnych nowych nazw, tak jak na tym etapie ich ostateczne nazwy (prawdopodobnie różne w postaci oryginalnych nazw) nie zostały jeszcze przypisane.</span><span class="sxs-lookup"><span data-stu-id="b0664-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>

<span data-ttu-id="b0664-182">Pierwszy znaleziony symbol, którego nazwę należy zmienić, to \<symbol_OrderID >.</span><span class="sxs-lookup"><span data-stu-id="b0664-182">The first symbol found that needs to be renamed is \<symbol_OrderID>.</span></span> <span data-ttu-id="b0664-183">Nowa nazwa jest przypisana jako "OrderID1", 1 jest oznaczona jako ostatni używany sufiks dla "IDZamówienia" i symbol jest oznaczony jako niewymagające zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="b0664-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="b0664-184">Następnie zostanie znalezione pierwsze użycie \<symbol_OrderID_2 >.</span><span class="sxs-lookup"><span data-stu-id="b0664-184">Next, the first usage of \<symbol_OrderID_2> is found.</span></span> <span data-ttu-id="b0664-185">Nazwa zostanie zmieniona, aby użyć następnego dostępnego sufiksu ("OrderID2"), a następnie ponownie oznaczona jako niewymagające zmiany nazwy, więc przy następnym użyciu nie zostanie zmieniona nazwa.</span><span class="sxs-lookup"><span data-stu-id="b0664-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="b0664-186">Jest to wykonywane tylko \<w przypadku symbol_OrderID_3 >.</span><span class="sxs-lookup"><span data-stu-id="b0664-186">This is done for \<symbol_OrderID_3> too.</span></span>

<span data-ttu-id="b0664-187">Na końcu drugiej fazy jest generowana Ostatnia instrukcja SQL.</span><span class="sxs-lookup"><span data-stu-id="b0664-187">At the end of the second phase, the final SQL statement is generated.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0664-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0664-188">See also</span></span>

- [<span data-ttu-id="b0664-189">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="b0664-189">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
