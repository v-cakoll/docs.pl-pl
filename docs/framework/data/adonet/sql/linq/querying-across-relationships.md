---
title: "Wykonywanie zapytań w relacjach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f06297f79807a1548a6b5ac77aed45f52c8d03af
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="querying-across-relationships"></a><span data-ttu-id="2d1d2-102">Wykonywanie zapytań w relacjach</span><span class="sxs-lookup"><span data-stu-id="2d1d2-102">Querying Across Relationships</span></span>
<span data-ttu-id="2d1d2-103">Odwołania do innych obiektów lub kolekcje innych obiektów w definicji klasy bezpośrednio odpowiadają relacje klucza obcego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-103">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="2d1d2-104">Te relacje można użyć w przypadku zapytania według używając zapisu kropkowego dostępu do właściwości relacji i przejść z jednego obiektu do innego.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-104">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="2d1d2-105">Wykonuje te operacje związane z dostępem do bardziej złożonych sprzężeń ani podzapytań skorelowane równoważne SQL.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-105">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="2d1d2-106">Na przykład następujące zapytanie powoduje przejście zleceń klientom sposób, aby ograniczyć wyniki do tylko zamówień dla klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-106">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="2d1d2-107">Jeśli właściwości relacji nie istnieje. należy zapisać je ręcznie jako *sprzężenia*, tak jak w zapytaniu SQL, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="2d1d2-107">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="2d1d2-108">Można użyć *relacji* właściwość, aby zdefiniować tego konkretnego relacji jeden raz.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-108">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="2d1d2-109">Następnie można użyć wygodniejsze składni z kropkami.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-109">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="2d1d2-110">Ale właściwości relacji ważniejsze istnieje ponieważ modele obiektów specyficznego dla domeny są zazwyczaj definiowane jako hierarchii lub wykresy.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-110">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="2d1d2-111">Obiekty, które program względem odwołują się do innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-111">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="2d1d2-112">Jest tylko wszystkiego zbieżność odpowiadające relacji obiektu do obiektu obcego wstawiony klucza relacje w bazach danych.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-112">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="2d1d2-113">Dostęp do właściwości następnie oferuje wygodny sposób zapisu sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-113">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="2d1d2-114">W odniesieniu do tego właściwości relacji są ważniejsze po stronie wyników zapytania niż jako część samą kwerendę.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-114">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="2d1d2-115">Po pobraniu zapytanie dane dotyczące określonego klienta definicji klasy oznacza, że klienci mają zleceń.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-115">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="2d1d2-116">Innymi słowy, planujesz `Orders` właściwości określonego klienta jako kolekcja, która jest wypełniana wszystkich zamówień z tego klienta.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-116">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="2d1d2-117">W rzeczywistości to kontrakt, który jest zadeklarowany przez definiowanie klas w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-117">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="2d1d2-118">Powinny być widoczne zamówienia istnieje, nawet wtedy, gdy zapytanie nie żądał zleceń.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-118">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="2d1d2-119">Spodziewasz się modelu obiektu do obsługi iluzji jest rozszerzenie bazy danych z powiązanych obiektów natychmiast dostępna w pamięci.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-119">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="2d1d2-120">Teraz, gdy masz relacje możesz pisać zapytania, odwołując się do właściwości relacji zdefiniowanych w klas.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-120">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="2d1d2-121">Te odwołania relacji odpowiadają relacje klucza obcego w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-121">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="2d1d2-122">Tłumaczenie operacji korzystających z tych relacji do bardziej złożonych sprzężeń równoważne SQL.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-122">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="2d1d2-123">Tak długo, jak zdefiniowano relacji (przy użyciu <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybut), nie masz kodu jawne sprzężenia w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d1d2-123">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="2d1d2-124">Pomagających zapewnić tym wrażenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technika wywołuje implementuje *odroczonego ładowania*.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-124">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="2d1d2-125">Aby uzyskać więcej informacji, zobacz [odroczone i ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="2d1d2-125">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="2d1d2-126">Należy wziąć pod uwagę następujące zapytanie SQL, aby wyświetlić listę `CustomerID` - `OrderID` pary:</span><span class="sxs-lookup"><span data-stu-id="2d1d2-126">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="2d1d2-127">Aby uzyskać takie same wyniki za pomocą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć `Orders` właściwości odwołania już istniejącego w `Customer` klasy.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-127">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="2d1d2-128">`Orders` Zawiera informacje niezbędne do wykonywania zapytań i projektu `CustomerID` - `OrderID` pary, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="2d1d2-128">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="2d1d2-129">Można także utworzyć odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-129">You can also do the reverse.</span></span> <span data-ttu-id="2d1d2-130">Oznacza to, że można zbadać `Orders` i używać jej `Customer` relacji odwołania do dostępu do informacji o skojarzony `Customer` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-130">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="2d1d2-131">Poniższy kod projektów takie same `CustomerID` - `OrderID` pary jak poprzednio, ale tym razem badając `Orders` zamiast `Customers`.</span><span class="sxs-lookup"><span data-stu-id="2d1d2-131">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2d1d2-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d1d2-132">See Also</span></span>  
 [<span data-ttu-id="2d1d2-133">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="2d1d2-133">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
