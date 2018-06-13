---
title: Grupuj według (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 3b5edee08afef8418f19df433223818218ae909d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763189"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="58bd1-102">Grupuj według (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="58bd1-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="58bd1-103">Określa grupę, do których obiektów zwróconych przez kwerendę ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) zostaną umieszczone wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="58bd1-103">Specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58bd1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58bd1-104">Syntax</span></span>  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="58bd1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="58bd1-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="58bd1-106">Dowolne wyrażenie prawidłowe zapytanie wykonane grupowanie.</span><span class="sxs-lookup"><span data-stu-id="58bd1-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="58bd1-107">`expression` może być właściwością lub wyrażenie niedotyczących agregacji, które odwołuje się do właściwości zwrócony przez klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="58bd1-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="58bd1-108">Każde wyrażenie w klauzuli GROUP BY musi mieć typ, który można porównywać pod względem równości.</span><span class="sxs-lookup"><span data-stu-id="58bd1-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="58bd1-109">Te typy są zazwyczaj skalarne w nim elementów podstawowych, takich jak liczby, ciągi i daty.</span><span class="sxs-lookup"><span data-stu-id="58bd1-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="58bd1-110">Nie można grupować według kolekcji.</span><span class="sxs-lookup"><span data-stu-id="58bd1-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58bd1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58bd1-111">Remarks</span></span>  
 <span data-ttu-id="58bd1-112">Jeśli funkcje agregujące są uwzględnione w klauzuli SELECT \<listy wyboru >, GROUP BY oblicza wartość podsumowania dla każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="58bd1-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="58bd1-113">Gdy GROUP BY jest określona, nazwy właściwości w dowolne inne niż zbiorcze wyrażenie na liście wyboru powinny uwzględnione na liście GROUP BY lub wyrażenie GROUP BY musi dokładnie odpowiadać wyrażenie listy wyboru.</span><span class="sxs-lookup"><span data-stu-id="58bd1-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58bd1-114">Jeśli nie określono klauzuli ORDER BY, grup zwracane przez klauzulę GROUP BY nie są w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="58bd1-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="58bd1-115">Aby określić konkretnego porządkowanie danych, zaleca się zawsze używać klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="58bd1-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="58bd1-116">W przypadku klauzuli GROUP BY albo jawnie lub niejawnie (na przykład w klauzuli HAVING w zapytaniu) bieżącego zakresu jest ukryta i wprowadzono nowy zakres.</span><span class="sxs-lookup"><span data-stu-id="58bd1-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="58bd1-117">W klauzuli SELECT w klauzuli HAVING i klauzuli ORDER BY będzie już można odwoływać się do nazwy elementu określone w klauzuli FROM.</span><span class="sxs-lookup"><span data-stu-id="58bd1-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="58bd1-118">Tylko mogą odwoływać się do siebie wyrażenia grupowania.</span><span class="sxs-lookup"><span data-stu-id="58bd1-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="58bd1-119">Aby to zrobić, można przypisać nowe nazwy (aliasy) do każdego wyrażenia grupowania.</span><span class="sxs-lookup"><span data-stu-id="58bd1-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="58bd1-120">Jeśli jest określony żaden alias wyrażenia grupowania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować za pomocą reguł generowania aliasu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="58bd1-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="58bd1-121">Wyrażenia w klauzuli GROUP BY nie może odwoływać się do nazwy zdefiniowanej wcześniej w tej samej klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="58bd1-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="58bd1-122">Oprócz nazwy grupowania można również określić wartości zagregowanych w klauzuli SELECT, klauzuli HAVING i klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="58bd1-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="58bd1-123">Wartość zagregowana zawiera wyrażenie, które jest obliczane dla każdego elementu grupy.</span><span class="sxs-lookup"><span data-stu-id="58bd1-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="58bd1-124">Operator zagregowany zmniejsza wartości tych wyrażeń (zwykle, ale nie zawsze pojedynczej wartości).</span><span class="sxs-lookup"><span data-stu-id="58bd1-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="58bd1-125">Wyrażenie agregujące można odwołuje się do oryginalnej nazwy elementu widoczne w zakresie nadrzędnym lub dowolnych nowych nazw wprowadzonego w klauzuli GROUP BY samej siebie.</span><span class="sxs-lookup"><span data-stu-id="58bd1-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="58bd1-126">Chociaż zagregowanych danych występują w klauzuli SELECT, klauzuli HAVING i klauzuli ORDER BY, są one faktycznie obliczane, w tym samym zakresie co wyrażenia grupowania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="58bd1-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="58bd1-127">To zapytanie używa klauzuli GROUP BY, aby wygenerować raport koszt wszystkich produktów zamówionych, według produktu.</span><span class="sxs-lookup"><span data-stu-id="58bd1-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="58bd1-128">Zawiera nazwę `name` produktu jako część wyrażenia grupowania, a następnie odwołania, których nazwy na liście wyboru.</span><span class="sxs-lookup"><span data-stu-id="58bd1-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="58bd1-129">Określa również zagregowanej `sum` na liście wyboru wewnętrznie odwołujących się do ceny i ilość wiersza zamówienia.</span><span class="sxs-lookup"><span data-stu-id="58bd1-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="58bd1-130">Każde wyrażenie GROUP By klucza musi mieć co najmniej jedno odwołanie do zakresu wejściowego:</span><span class="sxs-lookup"><span data-stu-id="58bd1-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="58bd1-131">Na przykład przy użyciu GROUP BY, zobacz [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="58bd1-131">For an example of using GROUP BY, see [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58bd1-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="58bd1-132">Example</span></span>  
 <span data-ttu-id="58bd1-133">Następujące zapytanie SQL jednostki użyto operatora GROUP BY do określenia grup, w których obiekty są zwracane przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="58bd1-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="58bd1-134">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="58bd1-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="58bd1-135">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="58bd1-135">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="58bd1-136">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="58bd1-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="58bd1-137">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="58bd1-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="58bd1-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58bd1-138">See Also</span></span>  
 [<span data-ttu-id="58bd1-139">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="58bd1-139">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="58bd1-140">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="58bd1-140">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
