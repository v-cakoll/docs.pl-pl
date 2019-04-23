---
title: Grupuj według (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 574d952e0183eb65c88864f2788eb7d698c9f2ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302949"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="d7ded-102">Grupuj według (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="d7ded-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="d7ded-103">Określa grupy, do których obiektów zwróconych przez zapytanie ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) wyrażenie, które mają być umieszczone.</span><span class="sxs-lookup"><span data-stu-id="d7ded-103">Specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ded-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7ded-104">Syntax</span></span>  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7ded-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d7ded-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="d7ded-106">Dowolne wyrażenie prawidłowe zapytanie, na którym odbywa się grupowania.</span><span class="sxs-lookup"><span data-stu-id="d7ded-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="d7ded-107">`expression` może być właściwością lub wyrażenie agregacji, które odwołuje się do właściwości zwrócony przez klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="d7ded-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="d7ded-108">Każde wyrażenie w klauzuli GROUP BY musi być typem, który można porównać pod kątem równości.</span><span class="sxs-lookup"><span data-stu-id="d7ded-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="d7ded-109">Te typy są zazwyczaj skalarną w nim elementów podstawowych, takich jak liczby, ciągi i daty.</span><span class="sxs-lookup"><span data-stu-id="d7ded-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="d7ded-110">Nie można grupować według kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d7ded-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7ded-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7ded-111">Remarks</span></span>  
 <span data-ttu-id="d7ded-112">Jeśli funkcje agregujące są uwzględnione w klauzuli SELECT \<listy wyboru >, GROUP BY oblicza wartość podsumowania dla każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="d7ded-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="d7ded-113">Kiedy GROUP BY jest określona, nazwy właściwości w inne niż zbiorcze dowolne wyrażenie, które są dostępne na liście wyboru powinny być objęte listy GROUP BY lub wyrażenie GROUP BY musi dokładnie odpowiadać wyrażeniu listy wyboru.</span><span class="sxs-lookup"><span data-stu-id="d7ded-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7ded-114">Jeśli nie określono klauzuli ORDER BY, grup zwracane przez klauzulę GROUP BY nie są w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d7ded-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="d7ded-115">Aby określić kolejność określoną w danych, zalecamy zawsze używać klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="d7ded-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="d7ded-116">Gdy klauzula GROUP BY jest określona, albo jawnie lub niejawnie (na przykład w klauzuli HAVING w zapytaniu) jest ukryta w bieżącym zakresie i wprowadzono nowy zakres.</span><span class="sxs-lookup"><span data-stu-id="d7ded-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="d7ded-117">Klauzuli SELECT, klauzula HAVING i ORDER BY — klauzula nie będzie już mógł odwoływać się do nazwy elementów określony w klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="d7ded-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="d7ded-118">Użytkownik może odwoływać się tylko do wyrażenia grupowania, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="d7ded-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="d7ded-119">Aby to zrobić, można przypisać nowe nazwami (aliasami) do każdego wyrażenia grupowania.</span><span class="sxs-lookup"><span data-stu-id="d7ded-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="d7ded-120">Jeśli określono Brak aliasu dla wyrażenia grupowania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje wygenerować za pomocą reguł generowania aliasu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d7ded-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="d7ded-121">Wyrażenia w klauzuli GROUP BY nie może odwoływać się do nazw zdefiniowanych wcześniej w tym samym klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="d7ded-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="d7ded-122">Oprócz nazwy grupowań można również określić wartości zagregowanych w klauzuli SELECT, klauzula HAVING i ORDER BY — klauzula.</span><span class="sxs-lookup"><span data-stu-id="d7ded-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="d7ded-123">Wartość zagregowana zawiera wyrażenie, które jest obliczane dla każdego elementu grupy.</span><span class="sxs-lookup"><span data-stu-id="d7ded-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="d7ded-124">Aggregate-operator ogranicza wartości tych wyrażeń (zwykle, ale nie zawsze w jedną wartość).</span><span class="sxs-lookup"><span data-stu-id="d7ded-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="d7ded-125">Wyrażenie agregujące można odwołuje się do oryginalnej nazwy elementów widoczne w zakresie nadrzędnym lub dowolnych nowych nazw wynikające z klauzuli GROUP BY, sam.</span><span class="sxs-lookup"><span data-stu-id="d7ded-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="d7ded-126">Chociaż zagregowanych danych występują w klauzuli SELECT, klauzula HAVING i ORDER BY — klauzula, ocenia się je faktycznie w taki sam zakres jak wyrażenia grupowania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d7ded-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="d7ded-127">To zapytanie używa klauzuli GROUP BY aby wygenerować raport kosztów wszystkie produkty, uporządkowanych według produktu.</span><span class="sxs-lookup"><span data-stu-id="d7ded-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="d7ded-128">Daje ona nazwę `name` produktu jako część wyrażenia grupowania, a następnie odwołań, które nazwy na liście wyboru.</span><span class="sxs-lookup"><span data-stu-id="d7ded-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="d7ded-129">Określa również agregacji `sum` na liście WYBIERANIA, który wewnętrznie odwołuje się do ceny i ilości wiersza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="d7ded-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="d7ded-130">Każde wyrażenie GROUP By klucza musi mieć co najmniej jedno odwołanie do zakresu wejściowego:</span><span class="sxs-lookup"><span data-stu-id="d7ded-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="d7ded-131">Na przykład przy użyciu grupy, zobacz [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d7ded-131">For an example of using GROUP BY, see [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7ded-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7ded-132">Example</span></span>  
 <span data-ttu-id="d7ded-133">Następujące zapytanie SQL jednostki używa operatora GROUP BY do określania grup, w których obiekty są zwracane przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="d7ded-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="d7ded-134">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d7ded-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7ded-135">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d7ded-135">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d7ded-136">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d7ded-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="d7ded-137">Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d7ded-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="d7ded-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7ded-138">See also</span></span>

- [<span data-ttu-id="d7ded-139">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d7ded-139">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="d7ded-140">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="d7ded-140">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
