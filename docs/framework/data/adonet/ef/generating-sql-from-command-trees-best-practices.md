---
title: Generowanie kodu SQL na podstawie drzew poleceń — najlepsze rozwiązania
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 476a2b9d6d3a8efb6094afce0143abed765bdb48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659098"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="0d1a0-102">Generowanie kodu SQL na podstawie drzew poleceń — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="0d1a0-102">Generating SQL from Command Trees - Best Practices</span></span>
<span data-ttu-id="0d1a0-103">Drzew poleceń kwerendy danych wyjściowych dokładnie modelowały zapytania można wyrazić w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="0d1a0-104">Istnieją pewne typowe wyzwania dla dostawcy modułów zapisujących podczas generowania SQL z poziomu drzewa poleceń w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="0d1a0-105">W tym temacie omówiono te wyzwania.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-105">This topic discusses these challenges.</span></span> <span data-ttu-id="0d1a0-106">W następnym temacie dostawcy przykładowych pokazano, jak te wyzwania.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-106">In the next topic, the sample provider shows how to address these challenges.</span></span>  
  
## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="0d1a0-107">Grupowanie węzłów DbExpression w instrukcji SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="0d1a0-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="0d1a0-108">Typowe instrukcji SQL ma zagnieżdżonej struktury kształtu następujące:</span><span class="sxs-lookup"><span data-stu-id="0d1a0-108">A typical SQL statement has a nested structure of the following shape:</span></span>  
  
```  
SELECT …  
FROM …  
WHERE …  
GROUP BY …  
ORDER BY …  
```  
  
 <span data-ttu-id="0d1a0-109">Jeden lub więcej klauzul, może być pusta.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="0d1a0-110">Użycie zagnieżdżonej instrukcji SELECT może wystąpić w dowolnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-110">A nested SELECT statement could occur in any of the lines.</span></span>  
  
 <span data-ttu-id="0d1a0-111">Możliwe tłumaczenie zapytania drzewa poleceń na instrukcję SQL SELECT dałby w efekcie podzapytania jeden dla każdego operator relacyjny.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="0d1a0-112">Jednakże, co może spowodować niepotrzebne zagnieżdżonych podzapytań, które byłyby trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="0d1a0-113">Na niektóre magazyny danych zapytanie może działać nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-113">On some data stores, the query may perform poorly.</span></span>  
  
 <span data-ttu-id="0d1a0-114">Na przykład należy wziąć pod uwagę następujące drzewo poleceń zapytania</span><span class="sxs-lookup"><span data-stu-id="0d1a0-114">As an example, consider the following query command tree</span></span>  
  
```  
Project (  
a.x,  
   a = Filter(  
      b.y = 5,   
      b = Scan("TableA")  
   )  
)  
```  
  
 <span data-ttu-id="0d1a0-115">Tłumaczenie nieefektywne dałby w efekcie:</span><span class="sxs-lookup"><span data-stu-id="0d1a0-115">An inefficient translation would produce:</span></span>  
  
```  
SELECT a.x  
FROM (   SELECT *  
         FROM TableA as b  
         WHERE b.y = 5) as a  
```  
  
 <span data-ttu-id="0d1a0-116">Należy pamiętać, że każdy węzeł wyrażenie relacyjne staje się nowych instrukcji SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>  
  
 <span data-ttu-id="0d1a0-117">W związku z tym należy zagregować dowolną liczbę węzłów wyrażenia jak to możliwe w pojedynczej instrukcji SQL SELECT przy jednoczesnym zachowaniu poprawności.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>  
  
 <span data-ttu-id="0d1a0-118">Będzie wynik takiego agregacji, na przykład przedstawiony powyżej:</span><span class="sxs-lookup"><span data-stu-id="0d1a0-118">The result of such aggregation for the example presented above would be:</span></span>  
  
```  
SELECT b.x   
FROM TableA as b  
WHERE b.y = 5  
```  
  
## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="0d1a0-119">Spłaszczanie sprzężenia w instrukcji SQL SELECT</span><span class="sxs-lookup"><span data-stu-id="0d1a0-119">Flatten Joins in a SQL SELECT Statement</span></span>  
 <span data-ttu-id="0d1a0-120">Jeden przypadek agregowanie wielu węzłów w pojedynczej instrukcji SQL SELECT jest agregowanie wielu wyrażeniach sprzężenia w pojedynczej instrukcji SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="0d1a0-121">DbJoinExpression reprezentuje pojedynczy łączenia dwóch wartościach wejściowych.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="0d1a0-122">Jednak w ramach pojedynczej instrukcji SQL SELECT, można określić więcej niż jedno połączenie.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="0d1a0-123">W takim przypadku sprzężeń są wykonywane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-123">In that case the joins are performed in the order specified.</span></span>  
  
 <span data-ttu-id="0d1a0-124">Pozostanie grzbietu sprzężeń, (sprzężenia, które są wyświetlane jako element podrzędny lewego sprzężenia innego) może być łatwiej jako spłaszczone do pojedynczą instrukcję SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="0d1a0-125">Na przykład należy wziąć pod uwagę następujące drzewo poleceń kwerendy:</span><span class="sxs-lookup"><span data-stu-id="0d1a0-125">For example, consider the following query command tree:</span></span>  
  
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
  
 <span data-ttu-id="0d1a0-126">Może zostać poprawnie przetłumaczony na:</span><span class="sxs-lookup"><span data-stu-id="0d1a0-126">This can be correctly translated into:</span></span>  
  
```  
SELECT *  
FROM TableA as b  
LEFT OUTER JOIN TableB as c ON b.y = c.x  
INNER JOIN TableC as d ON b.y = d.z  
```  
  
 <span data-ttu-id="0d1a0-127">Jednak sprzężeń grzbietu — po lewej stronie nie można łatwo spłaszczone i nie należy próbować spłaszczanie ich.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="0d1a0-128">Na przykład sprzężeń w następującym zapytaniu polecenie drzewa:</span><span class="sxs-lookup"><span data-stu-id="0d1a0-128">For example, the joins in the following query command tree:</span></span>  
  
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
  
 <span data-ttu-id="0d1a0-129">Może zostać przetłumaczone na instrukcję SQL SELECT podzapytaniu.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>  
  
```  
SELECT *  
FROM TableA as a  
INNER JOIN (SELECT *   
   FROM TableB as c   
   LEFT OUTER JOIN TableC as d  
   ON c.y = d.x) as b  
ON b.y = d.z  
```  
  
## <a name="input-alias-redirecting"></a><span data-ttu-id="0d1a0-130">Wprowadź Alias przekierowania folderu</span><span class="sxs-lookup"><span data-stu-id="0d1a0-130">Input Alias Redirecting</span></span>  
 <span data-ttu-id="0d1a0-131">Aby wyjaśnić, przekierowywanie alias danych wejściowych, należy wziąć pod uwagę Struktura wyrażeń relacyjnych, takich jak DbFilterExpression DbProjectExpression, obiekt DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, metody DbApplyExpression, i DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>  
  
 <span data-ttu-id="0d1a0-132">Każdy z tych typów ma jedną lub więcej właściwości danych wejściowych, które opisują kolekcję danych wejściowych, a zmienna powiązania odpowiadający każdej danych wejściowych jest używana do reprezentowania każdy element te dane wejściowe podczas przechodzenia kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="0d1a0-133">Zmienna powiązania jest używana przy odwoływaniu się do elementu danych wejściowych, na przykład w predykacie własności DbFilterExpression lub właściwości projekcji DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>  
  
 <span data-ttu-id="0d1a0-134">Podczas agregowania więcej węzłów wyrażenie relacyjne w pojedynczej instrukcji SQL SELECT i ocenianie wyrażenia, który jest częścią wyrażenie relacyjne (na przykład część właściwości projekcji DbProjectExpression) Zmienna powiązania, która używa może nie być taka sama jak alias danych wejściowych, jak wiele powiązań wyrażenie musi zostać przekierowany do jednego zakresu.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="0d1a0-135">Ten problem jest wywoływana, zmiana nazwy aliasu.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-135">This problem is called alias renaming.</span></span>  
  
 <span data-ttu-id="0d1a0-136">Należy wziąć pod uwagę pierwszego przykładu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-136">Consider the first example in this topic.</span></span> <span data-ttu-id="0d1a0-137">Jeśli podczas tłumaczenia naiwni i tłumaczenie projekcji "a.x" (DbPropertyExpression (, x)), jest poprawna do tłumaczenia go do `a.x` dysponujemy alias danych wejściowych jako "a", aby dopasować zmienna powiązania.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="0d1a0-138">Jednak podczas agregowania obu węzłów w pojedynczej instrukcji SQL SELECT, potrzebne jest tłumaczenie tych samych DbPropertyExpression do `b.x`, jak dane wejściowe były aliasem znakiem "b".</span><span class="sxs-lookup"><span data-stu-id="0d1a0-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>  
  
## <a name="join-alias-flattening"></a><span data-ttu-id="0d1a0-139">Dołącz do spłaszczanie aliasu</span><span class="sxs-lookup"><span data-stu-id="0d1a0-139">Join Alias Flattening</span></span>  
 <span data-ttu-id="0d1a0-140">W odróżnieniu od wszelkich innych wyrażenie relacyjne w danych wyjściowych polecenia drzewa DbJoinExpression danych wyjściowych typu wyniku, który jest wiersz składający się z dwóch kolumn, z których każdy odpowiada jednej z danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="0d1a0-141">DbPropertyExpresssion został opracowany pod kątem dostępu do właściwości skalarne pochodzące z sprzężenia, jest za pośrednictwem innego DbPropertyExpresssion.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-141">When a DbPropertyExpresssion is built to access a scalar property originating from a join, it is over another DbPropertyExpresssion.</span></span>  
  
 <span data-ttu-id="0d1a0-142">Przykłady obejmują "a.b.y" w przykładzie 2 i "b.c.y" w przykładzie 3.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="0d1a0-143">Jednak w odpowiedniej instrukcji SQL są one określane jako "b.y".</span><span class="sxs-lookup"><span data-stu-id="0d1a0-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="0d1a0-144">Aliasów re nosi nazwę spłaszczanie alias sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-144">This re-aliasing is called join alias flattening.</span></span>  
  
## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="0d1a0-145">Nazwa kolumny i zakresu, Alias zmiana nazwy</span><span class="sxs-lookup"><span data-stu-id="0d1a0-145">Column Name and Extent Alias Renaming</span></span>  
 <span data-ttu-id="0d1a0-146">Jeśli kwerendę SQL SELECT z sprzężenia ma zostać wykonane z projekcją, podczas wyliczania wszystkich kolumn uczestniczących w programie z wprowadzonymi danymi, może wystąpić kolizja nazwy, jako więcej niż jeden zestaw danych wejściowych może mieć taką samą nazwę kolumny.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="0d1a0-147">Użyj innej nazwy dla kolumny, aby uniknąć kolizji.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-147">Use a different name for the column to avoid the collision.</span></span>  
  
 <span data-ttu-id="0d1a0-148">Ponadto podczas spłaszczanie sprzężeń, tabele (ani podzapytań) może być kolizji aliasy, w którym zamierzone, Zapisz te potrzeby można zmienić jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>  
  
## <a name="avoid-select-"></a><span data-ttu-id="0d1a0-149">Należy unikać SELECT \*</span><span class="sxs-lookup"><span data-stu-id="0d1a0-149">Avoid SELECT \*</span></span>  
 <span data-ttu-id="0d1a0-150">Nie używaj `SELECT *` dokonania wyboru z tabel podstawowych.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="0d1a0-151">Model magazynu w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplikacji mogą zawierać tylko podzbiór kolumn, które znajdują się w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="0d1a0-152">W tym przypadku `SELECT *` może wygenerować niepoprawny wynik.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="0d1a0-153">Zamiast tego należy określić wszystkich kolumn uczestniczących w programie przy użyciu nazwy kolumn z typu wyniku wyrażenia uczestniczących w programie.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>  
  
## <a name="reuse-of-expressions"></a><span data-ttu-id="0d1a0-154">Ponowne użycie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="0d1a0-154">Reuse of Expressions</span></span>  
 <span data-ttu-id="0d1a0-155">Wyrażenia może zostać ponownie użyte w drzewo poleceń zapytania, które są przekazywane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d1a0-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0d1a0-156">Nie należy zakładać, każde wyrażenie jest wyświetlany w drzewie polecenia kwerendy tylko raz.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-156">Do not assume that each expression appears only once in the query command tree.</span></span>  
  
## <a name="mapping-primitive-types"></a><span data-ttu-id="0d1a0-157">Mapowanie typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="0d1a0-157">Mapping Primitive Types</span></span>  
 <span data-ttu-id="0d1a0-158">Podczas mapowania koncepcyjny typów (EDM struktury) do dostawcy typów, powinny być mapowane do najszerszego typu (Int32) tak, aby dopasować wszystkich możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="0d1a0-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="0d1a0-159">Ponadto należy unikać mapowanie dla typów, których nie można używać w wielu operacjach, takich jak typy obiektów BLOB (na przykład `ntext` w programie SQL Server).</span><span class="sxs-lookup"><span data-stu-id="0d1a0-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d1a0-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d1a0-160">See also</span></span>
- [<span data-ttu-id="0d1a0-161">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="0d1a0-161">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
