---
title: Kształt drzew poleceń
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: a3568f3deeaeeb31b69b41ac7c767001b792a8eb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248222"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="6f410-102">Kształt drzew poleceń</span><span class="sxs-lookup"><span data-stu-id="6f410-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="6f410-103">Moduł generowania kodu SQL jest odpowiedzialny za generowanie zapytania SQL specyficznego dla zaplecza na podstawie danego wyrażenia drzewa poleceń zapytania wejściowego.</span><span class="sxs-lookup"><span data-stu-id="6f410-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="6f410-104">W tej sekcji omówiono właściwości, właściwości i strukturę drzew poleceń zapytania.</span><span class="sxs-lookup"><span data-stu-id="6f410-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="6f410-105">Omówienie drzew poleceń zapytania</span><span class="sxs-lookup"><span data-stu-id="6f410-105">Query Command Trees Overview</span></span>

<span data-ttu-id="6f410-106">Drzewo poleceń zapytania jest reprezentacją modelu obiektu zapytania.</span><span class="sxs-lookup"><span data-stu-id="6f410-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="6f410-107">Drzewa poleceń zapytania mają dwa cele:</span><span class="sxs-lookup"><span data-stu-id="6f410-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="6f410-108">Aby wyrazić zapytanie wejściowe, które jest określone względem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f410-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>

- <span data-ttu-id="6f410-109">Aby wyrazić zapytanie wyjściowe dostarczone dla dostawcy i opisuje zapytanie dotyczące zaplecza.</span><span class="sxs-lookup"><span data-stu-id="6f410-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="6f410-110">Drzewa poleceń zapytania obsługują bogatszą semantykę niż zapytania zgodne z językiem SQL: 1999, w tym obsługę pracy z kolekcjami zagnieżdżonymi i operacjami typu, takich jak sprawdzanie, czy jednostka jest określonego typu, lub filtrowanie zestawów na podstawie typu.</span><span class="sxs-lookup"><span data-stu-id="6f410-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="6f410-111">Właściwość DBQueryCommandTree. Query jest korzeniem drzewa wyrażenia opisującym logikę zapytania.</span><span class="sxs-lookup"><span data-stu-id="6f410-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="6f410-112">Właściwość DBQueryCommandTree. Parameters zawiera listę parametrów, które są używane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="6f410-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="6f410-113">Drzewo wyrażenia składa się z obiektów DbExpression.</span><span class="sxs-lookup"><span data-stu-id="6f410-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="6f410-114">Obiekt DbExpression reprezentuje obliczanie.</span><span class="sxs-lookup"><span data-stu-id="6f410-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="6f410-115">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Do tworzenia wyrażeń zapytań są dostarczane różne rodzaje wyrażeń, w tym stałe, zmienne, funkcje, konstruktory i standardowe operatory relacyjne, takie jak Filter i Join.</span><span class="sxs-lookup"><span data-stu-id="6f410-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="6f410-116">Każdy obiekt DbExpression ma właściwość ResultType, która reprezentuje typ wyniku utworzonego przez to wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="6f410-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="6f410-117">Ten typ jest wyrażony jako TypeUsage.</span><span class="sxs-lookup"><span data-stu-id="6f410-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="6f410-118">Kształty drzewa poleceń zapytania wyjściowego</span><span class="sxs-lookup"><span data-stu-id="6f410-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="6f410-119">Drzewa poleceń kwerendy wyjściowej ściśle reprezentują zapytania relacyjne (SQL) i przestrzegają wielu surowszych reguł niż te, które są stosowane do drzew poleceń zapytania.</span><span class="sxs-lookup"><span data-stu-id="6f410-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="6f410-120">Zwykle zawierają konstrukcje, które można łatwo przetłumaczyć na SQL.</span><span class="sxs-lookup"><span data-stu-id="6f410-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="6f410-121">Drzewa poleceń wejściowych są wyrażane względem modelu koncepcyjnego, który obsługuje właściwości nawigacji, skojarzenia między jednostkami i dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="6f410-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="6f410-122">Drzewa poleceń wyjściowych są wyrażane względem modelu magazynu.</span><span class="sxs-lookup"><span data-stu-id="6f410-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="6f410-123">Drzewa poleceń wejściowych umożliwiają projektować kolekcje zagnieżdżone, ale nie są to drzewa poleceń wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6f410-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="6f410-124">Drzewa poleceń zapytania wyjściowego są kompilowane przy użyciu podzestawu dostępnych obiektów DbExpression, a nawet niektóre wyrażenia w tym podzbiorze mają ograniczone użycie.</span><span class="sxs-lookup"><span data-stu-id="6f410-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="6f410-125">Operacje typu, takie jak sprawdzanie, czy dane wyrażenie jest określonego typu lub zestawów filtrowania opartych na typie, nie są obecne w drzewach poleceń danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6f410-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="6f410-126">W drzewach poleceń wyjściowych tylko wyrażenia, które zwracają wartości logiczne, są używane dla projekcji i tylko dla predykatów w wyrażeniach wymagających predykatu, takiego jak filtr lub instrukcja Case.</span><span class="sxs-lookup"><span data-stu-id="6f410-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="6f410-127">Katalog główny drzew poleceń zapytania wyjściowego jest obiektem DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="6f410-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="6f410-128">Typy wyrażeń nieobecne w drzewach poleceń zapytania wyjściowego</span><span class="sxs-lookup"><span data-stu-id="6f410-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="6f410-129">Następujące typy wyrażeń nie są prawidłowe w drzewie poleceń zapytania wyjściowego i nie muszą być obsługiwane przez dostawców:</span><span class="sxs-lookup"><span data-stu-id="6f410-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="6f410-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-130">DbDerefExpression</span></span>

- <span data-ttu-id="6f410-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="6f410-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="6f410-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-133">DbIsOfExpression</span></span>

- <span data-ttu-id="6f410-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="6f410-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-135">DbRefExpression</span></span>

- <span data-ttu-id="6f410-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="6f410-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="6f410-138">Ograniczenia i uwagi dotyczące wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6f410-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="6f410-139">Wiele wyrażeń można używać tylko w ograniczony sposób w drzewach poleceń zapytania wyjściowego:</span><span class="sxs-lookup"><span data-stu-id="6f410-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="6f410-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-140">DbFunctionExpression</span></span>

<span data-ttu-id="6f410-141">Można przekazywać następujące typy funkcji:</span><span class="sxs-lookup"><span data-stu-id="6f410-141">The following function types can be passed:</span></span>

- <span data-ttu-id="6f410-142">Funkcje kanoniczne, które są rozpoznawane przez przestrzeń nazw modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="6f410-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="6f410-143">Wbudowane funkcje (Store), które są rozpoznawane przez wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="6f410-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="6f410-144">Funkcje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6f410-144">User-defined functions.</span></span>

<span data-ttu-id="6f410-145">Funkcje kanoniczne (zobacz [funkcje kanoniczne](./language-reference/canonical-functions.md) [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], aby uzyskać więcej informacji) są określone jako część, a dostawcy powinni dostarczać implementacje dla funkcji kanonicznych na podstawie tych specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="6f410-145">Canonical functions (see [Canonical Functions](./language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="6f410-146">Funkcje magazynu są oparte na specyfikacjach w odpowiednim manifeście dostawcy.</span><span class="sxs-lookup"><span data-stu-id="6f410-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="6f410-147">Funkcje zdefiniowane przez użytkownika są oparte na specyfikacjach w SSDL.</span><span class="sxs-lookup"><span data-stu-id="6f410-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="6f410-148">Ponadto funkcje mające atrybut NiladicFunction nie mają argumentów i powinny być tłumaczone bez nawiasów na końcu.</span><span class="sxs-lookup"><span data-stu-id="6f410-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="6f410-149">Oznacza to, że do  *\<funkcji FunctionName*  *\<> zamiast FunctionName > ()* .</span><span class="sxs-lookup"><span data-stu-id="6f410-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="6f410-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="6f410-151">Obiekt DbNewInstanceExpression może wystąpić tylko w następujących dwóch przypadkach:</span><span class="sxs-lookup"><span data-stu-id="6f410-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="6f410-152">Jako właściwość projekcji elementu DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="6f410-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="6f410-153">Gdy są stosowane następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="6f410-153">When used as such the following restrictions apply:</span></span>

  - <span data-ttu-id="6f410-154">Typ wyniku musi być typem wiersza.</span><span class="sxs-lookup"><span data-stu-id="6f410-154">The result type must be a row type.</span></span>

  - <span data-ttu-id="6f410-155">Każdy z argumentów jest wyrażeniem, które generuje wynik z typem pierwotnym.</span><span class="sxs-lookup"><span data-stu-id="6f410-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="6f410-156">Zazwyczaj każdy argument jest wyrażeniem skalarnym, takim jak PropertyExpression na DbVariableReferenceExpression, wywołanie funkcji lub obliczenia arytmetyczne DbPropertyExpression za pośrednictwem DbVariableReferenceExpression lub wywołania funkcji .</span><span class="sxs-lookup"><span data-stu-id="6f410-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="6f410-157">Jednak wyrażenie reprezentujące podzapytanie skalarne może również wystąpić na liście argumentów dla obiekt DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="6f410-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="6f410-158">Wyrażenie reprezentujące podzapytanie skalarne jest drzewem wyrażenia, które reprezentuje podzapytanie, które zwraca dokładnie jeden wiersz i jedną kolumnę typu pierwotnego z DbElementExpression obiektem głównym</span><span class="sxs-lookup"><span data-stu-id="6f410-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="6f410-159">Z typem zwracanym kolekcji, w tym przypadku definiuje nową kolekcję wyrażeń podanymi jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="6f410-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="6f410-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="6f410-161">DbVariableReferenceExpression musi być elementem podrzędnym węzła DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="6f410-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="6f410-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-162">DbGroupByExpression</span></span>

<span data-ttu-id="6f410-163">Właściwość Aggregates elementu DbGroupAggregate może zawierać tylko elementy typu DbFunctionAggregate.</span><span class="sxs-lookup"><span data-stu-id="6f410-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="6f410-164">Nie istnieją żadne inne typy agregacji.</span><span class="sxs-lookup"><span data-stu-id="6f410-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="6f410-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-165">DbLimitExpression</span></span>

<span data-ttu-id="6f410-166">Limitem właściwości może być tylko DbConstantExpression lub DbParameterReferenceExpression.</span><span class="sxs-lookup"><span data-stu-id="6f410-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="6f410-167">Właściwość WithTies ma zawsze wartość false w wersji 3,5 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f410-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="6f410-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="6f410-168">DbScanExpression</span></span>

<span data-ttu-id="6f410-169">W przypadku użycia w drzewach poleceń wyjściowych DbScanExpression skutecznie reprezentuje skanowanie w tabeli, widoku lub zapytaniu magazynu reprezentowane przez EntitySetBase:: Target.</span><span class="sxs-lookup"><span data-stu-id="6f410-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="6f410-170">Jeśli właściwość metadanych "definiujące zapytanie" obiektu docelowego ma wartość różną od null, oznacza to, że jest to zapytanie, którego tekst zapytania znajduje się w tej właściwości metadanych w określonym języku (lub dialektie) dostawcy, jak określono w definicji schematu magazynu.</span><span class="sxs-lookup"><span data-stu-id="6f410-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="6f410-171">W przeciwnym razie element docelowy reprezentuje tabelę lub widok.</span><span class="sxs-lookup"><span data-stu-id="6f410-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="6f410-172">Jego prefiks schematu znajduje się w właściwości metadanych "schemat", jeśli nie ma wartości null, w przeciwnym razie jest to nazwa kontenera jednostek.</span><span class="sxs-lookup"><span data-stu-id="6f410-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="6f410-173">Nazwa tabeli lub widoku to właściwość metadanych "Tabela", jeśli nie ma wartości null, w przeciwnym razie Właściwość Name bazy zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="6f410-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="6f410-174">Wszystkie te właściwości pochodzą z definicji odpowiedniego obiektu EntitySet w pliku definicji schematu magazynu (SSDL).</span><span class="sxs-lookup"><span data-stu-id="6f410-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="6f410-175">Używanie typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="6f410-175">Using Primitive Types</span></span>

<span data-ttu-id="6f410-176">Gdy istnieją odwołania do typów pierwotnych w drzewach poleceń wyjściowych, są one zwykle przywoływane w typach pierwotnych modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="6f410-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="6f410-177">Jednak w przypadku niektórych wyrażeń dostawcy potrzebują odpowiedniego typu pierwotnego magazynu.</span><span class="sxs-lookup"><span data-stu-id="6f410-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="6f410-178">Przykłady takich wyrażeń to DbCastExpression i DbNullExpression, jeśli dostawca musi rzutować wartość null na odpowiedni typ.</span><span class="sxs-lookup"><span data-stu-id="6f410-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="6f410-179">W takich przypadkach dostawcy powinni wykonać mapowanie do typu dostawcy na podstawie typu pierwotnego i jego aspektów.</span><span class="sxs-lookup"><span data-stu-id="6f410-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f410-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f410-180">See also</span></span>

- [<span data-ttu-id="6f410-181">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="6f410-181">SQL Generation</span></span>](sql-generation.md)
