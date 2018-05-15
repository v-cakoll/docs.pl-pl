---
title: Generowanie SQL na podstawie drzew poleceń — najlepsze praktyki
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 0087c67b12b4b6ea36cabd5800b7be0a72fc4a90
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="7a076-102">Generowanie SQL na podstawie drzew poleceń — najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="7a076-102">Generating SQL from Command Trees - Best Practices</span></span>
<span data-ttu-id="7a076-103">Drzew poleceń w danych wyjściowych zapytania modelu ściśle zapytania można wyrazić w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="7a076-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="7a076-104">Istnieją pewne wyzwania autorzy dostawcy podczas generowania SQL z poziomu drzewa poleceń danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="7a076-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="7a076-105">W tym temacie omówiono te problemy.</span><span class="sxs-lookup"><span data-stu-id="7a076-105">This topic discusses these challenges.</span></span> <span data-ttu-id="7a076-106">W następnym temacie dostawcy przykładowych pokazano, jak rozwiązać te problemy.</span><span class="sxs-lookup"><span data-stu-id="7a076-106">In the next topic, the sample provider shows how to address these challenges.</span></span>  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="7a076-107">Węzły DbExpression grup w instrukcji SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="7a076-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="7a076-108">Typowy instrukcja SQL zawiera zagnieżdżone struktury następujących kształt:</span><span class="sxs-lookup"><span data-stu-id="7a076-108">A typical SQL statement has a nested structure of the following shape:</span></span>  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 <span data-ttu-id="7a076-109">Co najmniej jedną klauzulę może być pusta.</span><span class="sxs-lookup"><span data-stu-id="7a076-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="7a076-110">Zagnieżdżona instrukcja SELECT może wystąpić w każdym wierszy.</span><span class="sxs-lookup"><span data-stu-id="7a076-110">A nested SELECT statement could occur in any of the lines.</span></span>  
  
 <span data-ttu-id="7a076-111">Tłumaczenie możliwe z poziomu drzewa poleceń zapytania na instrukcję SQL SELECT dałby w efekcie podzapytania jednej dla każdego operator relacyjny.</span><span class="sxs-lookup"><span data-stu-id="7a076-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="7a076-112">Jednak, która może spowodować niepotrzebne zagnieżdżonych podzapytań, które mogą być trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="7a076-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="7a076-113">Na niektóre sklepy danych zapytania mogą działać nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="7a076-113">On some data stores, the query may perform poorly.</span></span>  
  
 <span data-ttu-id="7a076-114">Na przykład należy wziąć pod uwagę następujące drzewo poleceń zapytania</span><span class="sxs-lookup"><span data-stu-id="7a076-114">As an example, consider the following query command tree</span></span>  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 <span data-ttu-id="7a076-115">Tłumaczenie nieefektywne dałby w efekcie:</span><span class="sxs-lookup"><span data-stu-id="7a076-115">An inefficient translation would produce:</span></span>  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 <span data-ttu-id="7a076-116">Należy pamiętać, że każdy węzeł wyrażenie relacyjne staje się nowych instrukcję SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="7a076-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>  
  
 <span data-ttu-id="7a076-117">W związku z tym należy do agregacji tyle węzły wyrażenia jak to możliwe w jednej instrukcji SQL SELECT przy zachowaniu poprawności.</span><span class="sxs-lookup"><span data-stu-id="7a076-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>  
  
 <span data-ttu-id="7a076-118">Wynikiem tych agregacji, na przykład przedstawionych powyżej byłby:</span><span class="sxs-lookup"><span data-stu-id="7a076-118">The result of such aggregation for the example presented above would be:</span></span>  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="7a076-119">Spłaszczanie sprzężenia w instrukcji SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="7a076-119">Flatten Joins in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="7a076-120">Jeden przypadek sumowania wiele węzłów w jednej instrukcji SQL SELECT jest agregowanie wiele wyrażeń sprzężenia w jednej instrukcji SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="7a076-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="7a076-121">DbJoinExpression reprezentuje pojedynczy sprzężenie dwóch parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="7a076-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="7a076-122">Jednak w ramach jednej instrukcji SQL SELECT, można określić więcej niż jedno połączenie.</span><span class="sxs-lookup"><span data-stu-id="7a076-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="7a076-123">W takim przypadku sprzężeń są wykonywane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="7a076-123">In that case the joins are performed in the order specified.</span></span>  
  
 <span data-ttu-id="7a076-124">Pozostanie kręgosłupa sprzężenia, (sprzężenia, które są wyświetlane jako element podrzędny lewego sprzężenia innego) może być łatwiej jako spłaszczone do jednej instrukcji SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="7a076-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="7a076-125">Rozważmy na przykład drzewo poleceń następujące zapytania:</span><span class="sxs-lookup"><span data-stu-id="7a076-125">For example, consider the following query command tree:</span></span>  
  
```  
InnerJoin(  
   a = LeftOuterJoin(  
   b = Extent("TableA")  
   c = Extent("TableB")  
   ON b.y = c.x ),  
   d = Extent("TableC")   
   ON a.b.y = d.z  
)  
```  
  
 <span data-ttu-id="7a076-126">Może zostać poprawnie przetłumaczony na:</span><span class="sxs-lookup"><span data-stu-id="7a076-126">This can be correctly translated into:</span></span>  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 <span data-ttu-id="7a076-127">Nie można łatwo spłaszczenia sprzężenia kręgosłupa lewego górnego i nie należy próbować spłaszczanie je.</span><span class="sxs-lookup"><span data-stu-id="7a076-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="7a076-128">Na przykład sprzężenia w następującym zapytaniu polecenie drzewa:</span><span class="sxs-lookup"><span data-stu-id="7a076-128">For example, the joins in the following query command tree:</span></span>  
  
```  
InnerJoin(  
   a = Extent("TableA")   
   b = LeftOuterJoin(  
   c = Extent("TableB")  
   d = Extent("TableC")  
   ON c.y = d.x),  
   ON a.z = b.c.y  
)  
```  
  
 <span data-ttu-id="7a076-129">Może być przekonwertowana na instrukcję SQL SELECT z podzapytania.</span><span class="sxs-lookup"><span data-stu-id="7a076-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a><span data-ttu-id="7a076-130">Wprowadź Alias przekierowania folderu</span><span class="sxs-lookup"><span data-stu-id="7a076-130">Input Alias Redirecting</span></span>  
 <span data-ttu-id="7a076-131">Wyjaśnienie, przekierowywanie alias wejściowy, należy wziąć pod uwagę struktury relacyjne wyrażeń, takie jak DbFilterExpression DbProjectExpression, obiekt DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, metody DbApplyExpression, i DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="7a076-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>  
  
 <span data-ttu-id="7a076-132">Każdego z tych typów ma co najmniej jednej właściwości danych wejściowych, opisujących kolekcja wejściowa i zmiennej powiązanie odpowiadający każdej danych wejściowych jest używana do reprezentowania każdy element dane wejściowe podczas przechodzenia kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7a076-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="7a076-133">Zmienna powiązania jest używany podczas odwoływania się do elementu wejściowego, na przykład w przypadku właściwości predykatu DbFilterExpression lub właściwości projekcji DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="7a076-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>  
  
 <span data-ttu-id="7a076-134">Gdy może agregowanie wyrażenie relacyjne większą liczbę węzłów w jednej instrukcji SQL SELECT, a obliczenia wyrażenia będącej częścią wyrażenie relacyjne (na przykład część właściwości projekcji DbProjectExpression) używa zmiennej powiązania nie być taka sama jak alias danych wejściowych, wiele powiązań wyrażenie musi być przekierowywane na jednym zakresie.</span><span class="sxs-lookup"><span data-stu-id="7a076-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="7a076-135">Ten problem jest nazywany, zmiana nazwy aliasu.</span><span class="sxs-lookup"><span data-stu-id="7a076-135">This problem is called alias renaming.</span></span>  
  
 <span data-ttu-id="7a076-136">Rozważmy przykład pierwszy w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="7a076-136">Consider the first example in this topic.</span></span> <span data-ttu-id="7a076-137">Jeśli podczas tłumaczenia prosty i tłumaczenia projekcji "a.x" (DbPropertyExpression (, x)), są prawidłowe do tłumaczenia go do `a.x` ponieważ mamy alias wejściowy jako "a" na zgodne powiązanie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7a076-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="7a076-138">Jednak podczas agregowania obu węzłów w jednej instrukcji SQL SELECT, potrzebne jest tłumaczenie tego samego DbPropertyExpression do `b.x`, jak dane wejściowe były używane z aliasem na "b".</span><span class="sxs-lookup"><span data-stu-id="7a076-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>  
  
## <a name="join-alias-flattening"></a><span data-ttu-id="7a076-139">Dołącz spłaszczanie aliasu</span><span class="sxs-lookup"><span data-stu-id="7a076-139">Join Alias Flattening</span></span>  
 <span data-ttu-id="7a076-140">W odróżnieniu od żadnych innych wyrażenie relacyjne w danych wyjściowych polecenia drzewa DbJoinExpression generuje typ wyniku, który wiersz składający się z dwóch kolumn, z których każdy odpowiada jednej z jej danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="7a076-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="7a076-141">DbPropertyExpresssion korzysta z wbudowanej dostępu do właściwości skalarnej pochodzące z sprzężenia, jest za pośrednictwem innego DbPropertyExpresssion.</span><span class="sxs-lookup"><span data-stu-id="7a076-141">When a DbPropertyExpresssion is built to access a scalar property originating from a join, it is over another DbPropertyExpresssion.</span></span>  
  
 <span data-ttu-id="7a076-142">Przykładami "a.b.y" w przykładzie 2 i "b.c.y" w przykładzie 3.</span><span class="sxs-lookup"><span data-stu-id="7a076-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="7a076-143">Jednak w odpowiedniej instrukcji SQL te są określane jako "b.y".</span><span class="sxs-lookup"><span data-stu-id="7a076-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="7a076-144">Aliasów ponowna nosi nazwę spłaszczanie alias sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="7a076-144">This re-aliasing is called join alias flattening.</span></span>  
  
## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="7a076-145">Nazwa kolumny i zakres Alias zmiana nazwy</span><span class="sxs-lookup"><span data-stu-id="7a076-145">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="7a076-146">Jeśli kwerendę SQL SELECT z sprzężenia ma zostać wykonane z projekcji, podczas wyliczania wszystkich uczestniczących kolumn danych wejściowych, kolizję nazw mogą wystąpić, jako więcej niż jedno wejście mogą mieć takiej samej nazwie kolumny.</span><span class="sxs-lookup"><span data-stu-id="7a076-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="7a076-147">Użyj innej nazwy dla kolumny, która umożliwi uniknięcie kolizji.</span><span class="sxs-lookup"><span data-stu-id="7a076-147">Use a different name for the column to avoid the collision.</span></span>  
  
 <span data-ttu-id="7a076-148">Ponadto podczas spłaszczania sprzężenia, tabele (ani podzapytań) może być kolizji aliasy, w którym przypadek te muszą zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="7a076-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>  
  
## <a name="avoid-select-"></a><span data-ttu-id="7a076-149">Unikaj SELECT \*</span><span class="sxs-lookup"><span data-stu-id="7a076-149">Avoid SELECT \*</span></span>  
 <span data-ttu-id="7a076-150">Nie używaj `SELECT *` można wybierać z tabel podstawowych.</span><span class="sxs-lookup"><span data-stu-id="7a076-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="7a076-151">W modelu magazynu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji może zawierać tylko podzestaw kolumn, które znajdują się w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7a076-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="7a076-152">W takim przypadku `SELECT *` może powodować niepoprawne wyniki.</span><span class="sxs-lookup"><span data-stu-id="7a076-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="7a076-153">Zamiast tego należy określić wszystkich uczestniczących kolumn za pomocą nazwy kolumn typu wyniku uczestniczących wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="7a076-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>  
  
## <a name="reuse-of-expressions"></a><span data-ttu-id="7a076-154">Ponowne użycie wyrażenia</span><span class="sxs-lookup"><span data-stu-id="7a076-154">Reuse of Expressions</span></span>  
 <span data-ttu-id="7a076-155">Wyrażenia może nastąpić w drzewie poleceń zapytania przekazany przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a076-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="7a076-156">Nie należy zakładać, każde wyrażenie jest wyświetlany w drzewie poleceń zapytania tylko raz.</span><span class="sxs-lookup"><span data-stu-id="7a076-156">Do not assume that each expression appears only once in the query command tree.</span></span>  
  
## <a name="mapping-primitive-types"></a><span data-ttu-id="7a076-157">Typy pierwotne mapowania</span><span class="sxs-lookup"><span data-stu-id="7a076-157">Mapping Primitive Types</span></span>  
 <span data-ttu-id="7a076-158">Podczas mapowania koncepcyjnej typów (EDM) do dostawcy typów tak, aby dopasować wszystkich możliwych wartości powinny mapy typowi najszerszych (Int32).</span><span class="sxs-lookup"><span data-stu-id="7a076-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="7a076-159">Ponadto uniknąć mapowania typów, których nie można używać w wielu operacjach, takich jak typy obiektów BLOB (na przykład `ntext` w programie SQL Server).</span><span class="sxs-lookup"><span data-stu-id="7a076-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a076-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a076-160">See Also</span></span>  
 [<span data-ttu-id="7a076-161">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="7a076-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
