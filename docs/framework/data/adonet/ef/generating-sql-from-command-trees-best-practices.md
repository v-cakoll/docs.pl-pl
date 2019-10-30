---
title: Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 869722b91550855a184a74e706271c3e2d417b84
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039995"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="6b7a4-102">Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="6b7a4-102">Generating SQL from Command Trees - Best Practices</span></span>

<span data-ttu-id="6b7a4-103">Drzewa poleceń zapytania danych wyjściowych ściśle modelują zapytania można wyrazić elementu w SQL.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="6b7a4-104">Jednak istnieją pewne typowe wyzwania dla autorów dostawcy podczas generowania kodu SQL z drzewa poleceń wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="6b7a4-105">W tym temacie omówiono te wyzwania.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-105">This topic discusses these challenges.</span></span> <span data-ttu-id="6b7a4-106">W następnym temacie Przykładowy dostawca pokazuje, jak rozwiązać te wyzwania.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-106">In the next topic, the sample provider shows how to address these challenges.</span></span>

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="6b7a4-107">Grupuj węzły DbExpression w instrukcji SELECT języka SQL</span><span class="sxs-lookup"><span data-stu-id="6b7a4-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>

<span data-ttu-id="6b7a4-108">Typowa instrukcja SQL ma zagnieżdżoną strukturę następującego kształtu:</span><span class="sxs-lookup"><span data-stu-id="6b7a4-108">A typical SQL statement has a nested structure of the following shape:</span></span>

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

<span data-ttu-id="6b7a4-109">Co najmniej jedna klauzula może być pusta.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="6b7a4-110">Zagnieżdżona instrukcja SELECT może wystąpić w dowolnym z wierszy.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-110">A nested SELECT statement could occur in any of the lines.</span></span>

<span data-ttu-id="6b7a4-111">Możliwe tłumaczenie drzewa poleceń zapytania do instrukcji SQL SELECT spowoduje utworzenie jednego podzapytania dla każdego operatora relacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="6b7a4-112">Jednak może to spowodować niepotrzebne zagnieżdżone podzapytania, które byłyby trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="6b7a4-113">W niektórych magazynach danych zapytanie może działać nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-113">On some data stores, the query may perform poorly.</span></span>

<span data-ttu-id="6b7a4-114">Rozważmy na przykład następujące drzewo poleceń zapytania</span><span class="sxs-lookup"><span data-stu-id="6b7a4-114">As an example, consider the following query command tree</span></span>

```csharp
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

<span data-ttu-id="6b7a4-115">Niewydajne tłumaczenie spowoduje wygenerowanie:</span><span class="sxs-lookup"><span data-stu-id="6b7a4-115">An inefficient translation would produce:</span></span>

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

<span data-ttu-id="6b7a4-116">Należy zauważyć, że każdy węzeł wyrażenia relacyjnego zostanie nowym instrukcją SELECT języka SQL.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>

<span data-ttu-id="6b7a4-117">W związku z tym ważne jest, aby w jednej instrukcji SQL SELECT agregować tyle węzłów wyrażenia, jak to możliwe, jednocześnie zachowując poprawność.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>

<span data-ttu-id="6b7a4-118">Wynikiem takiej agregacji dla przykładu przedstawionego powyżej byłoby:</span><span class="sxs-lookup"><span data-stu-id="6b7a4-118">The result of such aggregation for the example presented above would be:</span></span>

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="6b7a4-119">Spłaszczanie sprzężeń w instrukcji SELECT języka SQL</span><span class="sxs-lookup"><span data-stu-id="6b7a4-119">Flatten Joins in a SQL SELECT Statement</span></span>

<span data-ttu-id="6b7a4-120">Jednym z przypadków agregowania wielu węzłów w jednej instrukcji SQL SELECT jest agregowanie wielu wyrażeń sprzężenia do jednej instrukcji SELECT języka SQL.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="6b7a4-121">DbJoinExpression reprezentuje jedno sprzężenie między dwoma danymi wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="6b7a4-122">Jednakże w ramach jednej instrukcji SELECT języka SQL można określić więcej niż jedno sprzężenie.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="6b7a4-123">W takim przypadku sprzężenia są wykonywane w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-123">In that case the joins are performed in the order specified.</span></span>

<span data-ttu-id="6b7a4-124">Lewe sprzężenie z lewej strony (sprzężenia, które pojawiają się jako lewy element podrzędny innego sprzężenia), można łatwiej spłaszczyć do jednej instrukcji SELECT języka SQL.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="6b7a4-125">Rozważmy na przykład następujące drzewo poleceń zapytania:</span><span class="sxs-lookup"><span data-stu-id="6b7a4-125">For example, consider the following query command tree:</span></span>

```csharp
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

<span data-ttu-id="6b7a4-126">Można to prawidłowo przetłumaczyć na:</span><span class="sxs-lookup"><span data-stu-id="6b7a4-126">This can be correctly translated into:</span></span>

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

<span data-ttu-id="6b7a4-127">Nielewe sprzężenia kręgosłupa nie mogą być jednak w łatwy sposób spłaszczone i nie należy próbować ich spłaszczać.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="6b7a4-128">Na przykład sprzężenia w następującym drzewie poleceń zapytania:</span><span class="sxs-lookup"><span data-stu-id="6b7a4-128">For example, the joins in the following query command tree:</span></span>

```csharp
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

<span data-ttu-id="6b7a4-129">Zostałyby przetłumaczone na instrukcję SELECT języka SQL z podzapytaniem.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a><span data-ttu-id="6b7a4-130">Przekierowanie wejściowej aliasu</span><span class="sxs-lookup"><span data-stu-id="6b7a4-130">Input Alias Redirecting</span></span>

<span data-ttu-id="6b7a4-131">Aby wyjaśnić przekierowanie aliasów wejściowych, należy rozważyć strukturę wyrażeń relacyjnych, takich jak DbFilterExpression, DbProjectExpression, obiekt DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupAggregate, DbApplyExpression i DbSkipExpression.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>

<span data-ttu-id="6b7a4-132">Każdy z tych typów ma jedną lub więcej właściwości wejściowych, które opisują kolekcję wejściową, a zmienna powiązania odpowiadająca każdemu danemu wejściu jest używana do reprezentowania każdego elementu danych wejściowych podczas przechodzenia do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="6b7a4-133">Zmienna Binding jest używana podczas odwoływania się do elementu wejściowego, na przykład we właściwości predykatu DbFilterExpression lub właściwości projekcji DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>

<span data-ttu-id="6b7a4-134">Podczas agregowania bardziej relacyjnych węzłów wyrażeń do pojedynczej instrukcji SELECT języka SQL i oceniania wyrażenia, które jest częścią wyrażenia relacyjnego (na przykład część właściwości projekcji DbProjectExpression), zmienna powiązania, której używa może nie jest taki sam jak alias danych wejściowych, ponieważ wiele powiązań wyrażeń może być przekierowanych do jednego zakresu.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="6b7a4-135">Ten problem jest nazywany zmiana nazw aliasu.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-135">This problem is called alias renaming.</span></span>

<span data-ttu-id="6b7a4-136">Rozważmy pierwszy przykład w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-136">Consider the first example in this topic.</span></span> <span data-ttu-id="6b7a4-137">Jeśli wykonujesz translację algorytmie i przetłumaczmy projekcję a. x (DbPropertyExpression (a, x)), jest ona poprawna, aby przetłumaczyć ją na `a.x`, ponieważ jako "a" aliasuje dane wejściowe w celu dopasowania do zmiennej powiązania.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="6b7a4-138">Jednak podczas agregowania węzłów do pojedynczej instrukcji SELECT języka SQL należy przetłumaczyć te same DbPropertyExpression na `b.x`, ponieważ dane wejściowe mają alias "b".</span><span class="sxs-lookup"><span data-stu-id="6b7a4-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>

## <a name="join-alias-flattening"></a><span data-ttu-id="6b7a4-139">Przyłączanie spłaszczania aliasów</span><span class="sxs-lookup"><span data-stu-id="6b7a4-139">Join Alias Flattening</span></span>

<span data-ttu-id="6b7a4-140">W przeciwieństwie do dowolnego innego wyrażenia relacyjnego w drzewie poleceń wyjściowych, DbJoinExpression wyprowadza typ wyniku, który jest wiersz składający się z dwóch kolumn, z których każdy odpowiada jednemu z danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="6b7a4-141">Gdy DbPropertyExpression jest zbudowany w celu uzyskania dostępu do właściwości skalarnej pochodzącej z sprzężenia, znajduje się na innej DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-141">When a DbPropertyExpression is built to access a scalar property originating from a join, it is over another DbPropertyExpression.</span></span>

<span data-ttu-id="6b7a4-142">Przykłady obejmują "a. b. y" w przykładach 2 i "b. c. y" w przykładzie 3.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="6b7a4-143">Jednak w odpowiednich instrukcjach SQL są one określane jako "b. y".</span><span class="sxs-lookup"><span data-stu-id="6b7a4-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="6b7a4-144">Ta zmiana aliasu jest nazywana spłaszczaniem aliasu sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-144">This re-aliasing is called join alias flattening.</span></span>

## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="6b7a4-145">Zmiana nazwy kolumny i zakresu aliasu</span><span class="sxs-lookup"><span data-stu-id="6b7a4-145">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="6b7a4-146">Jeśli zapytanie SELECT SQL z funkcją Join musi zostać wykonane z projekcją, podczas wyliczania wszystkich uczestniczących kolumn w danych wejściowych może wystąpić kolizja nazw, ponieważ więcej niż jeden element wejściowy może mieć taką samą nazwę kolumny.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="6b7a4-147">Użyj innej nazwy dla kolumny, aby uniknąć kolizji.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-147">Use a different name for the column to avoid the collision.</span></span>

<span data-ttu-id="6b7a4-148">Ponadto podczas spłaszczania sprzężeń, uczestniczące tabele (lub podzapytania) mogą spowodować konflikt aliasów, w przypadku których należy zmienić nazwy.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>

## <a name="avoid-select-"></a><span data-ttu-id="6b7a4-149">Unikaj ZAZNACZania \*</span><span class="sxs-lookup"><span data-stu-id="6b7a4-149">Avoid SELECT \*</span></span>

<span data-ttu-id="6b7a4-150">Nie należy używać `SELECT *` do wybierania z tabel podstawowych.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="6b7a4-151">Model magazynu w aplikacji Entity Framework może zawierać tylko podzestaw kolumn znajdujących się w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-151">The storage model in an Entity Framework application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="6b7a4-152">W takim przypadku `SELECT *` może wygenerować niepoprawny wynik.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="6b7a4-153">Zamiast tego należy określić wszystkie kolumny uczestniczące przy użyciu nazw kolumn z typu wynik wyrażeń uczestniczących.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>

## <a name="reuse-of-expressions"></a><span data-ttu-id="6b7a4-154">Ponowne użycie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6b7a4-154">Reuse of Expressions</span></span>

<span data-ttu-id="6b7a4-155">Wyrażenia mogą być ponownie używane w drzewie poleceń zapytania przekazanym przez Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-155">Expressions may be reused in the query command tree passed by the Entity Framework.</span></span> <span data-ttu-id="6b7a4-156">Nie należy zakładać, że każde wyrażenie pojawia się tylko raz w drzewie poleceń zapytania.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-156">Do not assume that each expression appears only once in the query command tree.</span></span>

## <a name="mapping-primitive-types"></a><span data-ttu-id="6b7a4-157">Mapowanie typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="6b7a4-157">Mapping Primitive Types</span></span>

<span data-ttu-id="6b7a4-158">Podczas mapowania typów koncepcyjnych (EDM) na typy dostawców należy mapować do najszerszego typu (Int32), aby można było dopasować wszystkie możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="6b7a4-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="6b7a4-159">Należy również unikać mapowania do typów, które nie mogą być używane dla wielu operacji, takich jak typy obiektów BLOB (na przykład `ntext` w SQL Server).</span><span class="sxs-lookup"><span data-stu-id="6b7a4-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b7a4-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b7a4-160">See also</span></span>

- [<span data-ttu-id="6b7a4-161">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="6b7a4-161">SQL Generation</span></span>](sql-generation.md)
