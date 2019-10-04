---
title: Grupuj według (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 711fbdc2d51177037cf349150c3431de14b11974
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833780"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="1a607-102">Grupuj według (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1a607-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="1a607-103">Określa grupy, do których obiekty zwracane przez zapytanie ([SELECT](select-entity-sql.md)) mają zostać umieszczone.</span><span class="sxs-lookup"><span data-stu-id="1a607-103">Specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a607-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a607-104">Syntax</span></span>  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1a607-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1a607-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="1a607-106">Dowolne prawidłowe wyrażenie zapytania, w którym jest wykonywane grupowanie.</span><span class="sxs-lookup"><span data-stu-id="1a607-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="1a607-107">`expression` może być właściwością lub niezagregowanym wyrażeniem, które odwołuje się do właściwości zwróconej przez klauzulę FROM.</span><span class="sxs-lookup"><span data-stu-id="1a607-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="1a607-108">Każde wyrażenie w klauzuli GROUP BY musi być szacowane do typu, który można porównać pod kątem równości.</span><span class="sxs-lookup"><span data-stu-id="1a607-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="1a607-109">Te typy są ogólnie skalarnymi typami podstawowymi, takimi jak liczby, ciągi i daty.</span><span class="sxs-lookup"><span data-stu-id="1a607-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="1a607-110">Nie można grupować według kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1a607-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a607-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a607-111">Remarks</span></span>  
 <span data-ttu-id="1a607-112">Jeśli funkcja agregująca jest uwzględniona w klauzuli SELECT \<select list >, GROUP BY oblicza wartość podsumowania dla każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="1a607-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="1a607-113">Gdy Grupuj według jest określony, każda nazwa właściwości w dowolnym niezagregowanym wyrażeniu na liście wyboru powinna być uwzględniona na liście Grupuj według lub wyrażenie GROUP BY musi być dokładnie zgodne z wyrażeniem Select list.</span><span class="sxs-lookup"><span data-stu-id="1a607-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a607-114">Jeśli klauzula ORDER BY nie jest określona, grupy zwracane przez klauzulę GROUP BY nie są w żadnej określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="1a607-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="1a607-115">Aby określić konkretną kolejność danych, zaleca się, aby zawsze używać klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="1a607-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="1a607-116">Gdy klauzula GROUP BY jest określona, jawnie lub niejawnie (na przykład przez klauzulę HAVING w zapytaniu), bieżący zakres jest ukryty i wprowadzany jest nowy zakres.</span><span class="sxs-lookup"><span data-stu-id="1a607-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="1a607-117">Klauzula SELECT, klauzula HAVING i klauzula ORDER BY nie będą już mogły odwoływać się do nazw elementów określonych w klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="1a607-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="1a607-118">Można odwoływać się tylko do samych wyrażeń grupowania.</span><span class="sxs-lookup"><span data-stu-id="1a607-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="1a607-119">W tym celu można przypisać nowe nazwy (aliasy) do każdego wyrażenia grupowania.</span><span class="sxs-lookup"><span data-stu-id="1a607-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="1a607-120">Jeśli nie określono aliasu dla wyrażenia grupowania, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować jeden przy użyciu reguł generacji aliasów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1a607-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="1a607-121">Wyrażenia w klauzuli GROUP BY nie mogą odwoływać się do nazw zdefiniowanych wcześniej w tej samej klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="1a607-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="1a607-122">Oprócz nazw grupowania można także określić wartości zagregowane w klauzuli SELECT, klauzuli HAVING i klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="1a607-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="1a607-123">Agregacja zawiera wyrażenie, które jest oceniane dla każdego elementu grupy.</span><span class="sxs-lookup"><span data-stu-id="1a607-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="1a607-124">Operator agregujący redukuje wartości wszystkich tych wyrażeń (zwykle, ale nie zawsze, do pojedynczej wartości).</span><span class="sxs-lookup"><span data-stu-id="1a607-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="1a607-125">Wyrażenie agregujące może tworzyć odwołania do oryginalnych nazw elementów widocznych w zakresie nadrzędnym lub do dowolnych nowych nazw wprowadzonych przez samą klauzulę GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="1a607-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="1a607-126">Chociaż agregacje pojawiają się w klauzuli SELECT, klauzuli HAVING i klauzuli ORDER BY, są faktycznie oceniane w tym samym zakresie co wyrażenia grupowania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1a607-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="1a607-127">To zapytanie używa klauzuli GROUP BY do tworzenia raportu o kosztach wszystkich produktów uporządkowanych według produktu.</span><span class="sxs-lookup"><span data-stu-id="1a607-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="1a607-128">Podaje nazwę `name` do produktu jako część wyrażenia grupowania, a następnie odwołuje się do tej nazwy na liście wyboru.</span><span class="sxs-lookup"><span data-stu-id="1a607-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="1a607-129">Określa również wartość zagregowaną `sum` na liście wyboru, która wewnętrznie odwołuje się do ceny i ilości wiersza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="1a607-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="1a607-130">Każde wyrażenie GROUP by key musi mieć co najmniej jedno odwołanie do zakresu wejściowego:</span><span class="sxs-lookup"><span data-stu-id="1a607-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="1a607-131">Aby zapoznać się z przykładem użycia opcji Grupuj według [, zobacz.](having-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="1a607-131">For an example of using GROUP BY, see [HAVING](having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a607-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a607-132">Example</span></span>  
 <span data-ttu-id="1a607-133">Poniższe zapytanie Entity SQL używa operatora Grupuj według, aby określić grupy, do których obiekty są zwracane przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="1a607-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="1a607-134">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1a607-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1a607-135">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1a607-135">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1a607-136">Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1a607-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="1a607-137">Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="1a607-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="1a607-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a607-138">See also</span></span>

- [<span data-ttu-id="1a607-139">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1a607-139">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="1a607-140">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="1a607-140">Query Expressions</span></span>](query-expressions-entity-sql.md)
