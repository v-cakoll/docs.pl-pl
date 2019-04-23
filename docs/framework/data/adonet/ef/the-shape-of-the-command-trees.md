---
title: Kształt drzew poleceń
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 08a67c8d181188cbc14c6f60876a7e26cd6de25a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980086"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="7d10b-102">Kształt drzew poleceń</span><span class="sxs-lookup"><span data-stu-id="7d10b-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="7d10b-103">Moduł generowania SQL jest odpowiedzialny za wygenerowanie zapytania SQL określonych zaplecza opartego na wyrażenie kwerendy wejściowej danego polecenia drzewa.</span><span class="sxs-lookup"><span data-stu-id="7d10b-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="7d10b-104">W tej sekcji omówiono cech, właściwości i struktury drzew poleceń zapytania.</span><span class="sxs-lookup"><span data-stu-id="7d10b-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="7d10b-105">Omówienie drzew poleceń zapytania</span><span class="sxs-lookup"><span data-stu-id="7d10b-105">Query Command Trees Overview</span></span>

<span data-ttu-id="7d10b-106">Drzewo poleceń zapytania jest reprezentacja obiektu modelu zapytania.</span><span class="sxs-lookup"><span data-stu-id="7d10b-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="7d10b-107">Zapytanie drzew poleceń służą do dwóch celów:</span><span class="sxs-lookup"><span data-stu-id="7d10b-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="7d10b-108">Wyrażenia kwerendy wejściowej, który jest określony względem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d10b-108">To express an input query that is specified against the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>

- <span data-ttu-id="7d10b-109">Wyrażenia zapytań danych wyjściowych, znajduje się z dostawcą, który opisuje zapytanie do wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7d10b-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="7d10b-110">Wyślij zapytanie do polecenia drzewa obsługę semantyki bogatszy niż SQL:1999 kwerendy zgodne, w tym obsługę pracy z kolekcje zagnieżdżone oraz typ operacji, takich jak sprawdzanie, czy jednostka jest określonego typu lub filtrowanie na podstawie typu zestawów.</span><span class="sxs-lookup"><span data-stu-id="7d10b-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="7d10b-111">Właściwość DBQueryCommandTree.Query jest głównym drzewa wyrażeń, który opisuje logiki zapytania.</span><span class="sxs-lookup"><span data-stu-id="7d10b-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="7d10b-112">Właściwość DBQueryCommandTree.Parameters zawiera listę parametrów, które są używane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="7d10b-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="7d10b-113">Drzewo wyrażenia składa się z obiektów DbExpression.</span><span class="sxs-lookup"><span data-stu-id="7d10b-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="7d10b-114">Obiekt DbExpression reprezentuje niektórych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7d10b-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="7d10b-115">Kilka rodzajów wyrażenia są dostarczane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] do redagowania wyrażeń zapytania, łącznie ze stałymi, zmienne, funkcje, konstruktorów i standardowe operatory, takie jak filtrowanie i dołączania.</span><span class="sxs-lookup"><span data-stu-id="7d10b-115">Several kinds of expressions are provided by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="7d10b-116">Każdy obiekt DbExpression ma właściwość ResultType, który reprezentuje typ wynik tworzony przez to wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="7d10b-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="7d10b-117">Ten typ jest wyrażona jako właściwości TypeUsage.</span><span class="sxs-lookup"><span data-stu-id="7d10b-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="7d10b-118">Kształty drzewo poleceń kwerendy danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="7d10b-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="7d10b-119">Drzew poleceń kwerendy danych wyjściowych ściśle reprezentują kwerend relacyjnych (SQL) i spełnić znacznie bardziej rygorystyczne zasady niż te, które dotyczą drzew poleceń zapytania.</span><span class="sxs-lookup"><span data-stu-id="7d10b-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="7d10b-120">Zawierają one zazwyczaj konstrukcji, które łatwo są tłumaczone na SQL.</span><span class="sxs-lookup"><span data-stu-id="7d10b-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="7d10b-121">Drzew poleceń wejściowych są wyrażane względem modelu koncepcyjnego, która obsługuje właściwości nawigacji, skojarzenia między jednostkami i dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="7d10b-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="7d10b-122">Dane wyjściowe polecenia drzewa są wyrażane w modelu magazynu.</span><span class="sxs-lookup"><span data-stu-id="7d10b-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="7d10b-123">Wprowadź liczbę drzew poleceń umożliwiają projektu kolekcje zagnieżdżone, ale dane wyjściowe polecenia drzewa nie.</span><span class="sxs-lookup"><span data-stu-id="7d10b-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="7d10b-124">Drzew poleceń zapytania dane wyjściowe są tworzone za pomocą podzestawu dostępne obiekty DbExpression, a nawet niektóre wyrażenia, w tym podzbiór mają ograniczone użycie.</span><span class="sxs-lookup"><span data-stu-id="7d10b-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="7d10b-125">Typ operacji, takich jak sprawdzanie, czy podane wyrażenie jest określonego typu lub filtrowanie na podstawie typu, zestawy nie są obecne w danych wyjściowych drzew poleceń.</span><span class="sxs-lookup"><span data-stu-id="7d10b-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="7d10b-126">W danych wyjściowych polecenia drzewa tylko wyrażenia, które zwracają wartości logiczne są używane w przypadku projekcji i tylko w przypadku predykatów w wyrażeniach wymagające predykat filtru lub instrukcji case.</span><span class="sxs-lookup"><span data-stu-id="7d10b-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="7d10b-127">Główny drzew poleceń kwerendy danych wyjściowych jest obiektem DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="7d10b-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="7d10b-128">Typy wyrażenia nieobecne w drzew poleceń kwerendy danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="7d10b-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="7d10b-129">Następujące typy wyrażeń nie są prawidłowe w drzewie polecenia kwerendy danych wyjściowych i nie muszą być obsługiwane przez dostawców:</span><span class="sxs-lookup"><span data-stu-id="7d10b-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="7d10b-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-130">DbDerefExpression</span></span>

- <span data-ttu-id="7d10b-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="7d10b-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="7d10b-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-133">DbIsOfExpression</span></span>

- <span data-ttu-id="7d10b-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="7d10b-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-135">DbRefExpression</span></span>

- <span data-ttu-id="7d10b-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="7d10b-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="7d10b-138">Wyrażenie ograniczenia i uwagi</span><span class="sxs-lookup"><span data-stu-id="7d10b-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="7d10b-139">Wiele wyrażeń należy używać tylko w sposób ograniczony w drzew poleceń kwerendy danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="7d10b-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="7d10b-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-140">DbFunctionExpression</span></span>

<span data-ttu-id="7d10b-141">Można przekazać następujących funkcji:</span><span class="sxs-lookup"><span data-stu-id="7d10b-141">The following function types can be passed:</span></span>

- <span data-ttu-id="7d10b-142">Funkcje Canonical, które są rozpoznawane przez przestrzeń nazw Edm.</span><span class="sxs-lookup"><span data-stu-id="7d10b-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="7d10b-143">Funkcje wbudowane (Sklep), które są rozpoznawane przez BuiltInAttribute.</span><span class="sxs-lookup"><span data-stu-id="7d10b-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="7d10b-144">Funkcje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d10b-144">User-defined functions.</span></span>

<span data-ttu-id="7d10b-145">Funkcje Canonical (zobacz [funkcje Canonical](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Aby uzyskać więcej informacji) są określane jako część [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], oraz dostawcy powinni dostarczać implementacje dla funkcji kanonicznej na podstawie tych specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="7d10b-145">Canonical functions (see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) for more information) are specified as part of the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="7d10b-146">Funkcje Store są oparte na specyfikacji w odpowiedniej manifest dostawcy.</span><span class="sxs-lookup"><span data-stu-id="7d10b-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="7d10b-147">Funkcje zdefiniowane przez użytkownika są oparte na specyfikacjach SSDL.</span><span class="sxs-lookup"><span data-stu-id="7d10b-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="7d10b-148">Ponadto funkcje, w których atrybut NiladicFunction ma nie argumentów i powinien być tłumaczony bez nawiasów, na końcu.</span><span class="sxs-lookup"><span data-stu-id="7d10b-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="7d10b-149">Oznacza to,  *\<functionName >* zamiast  *\<functionName > ()*.</span><span class="sxs-lookup"><span data-stu-id="7d10b-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="7d10b-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="7d10b-151">Obiekt DbNewInstanceExpression mogą występować tylko w dwóch przypadkach:</span><span class="sxs-lookup"><span data-stu-id="7d10b-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="7d10b-152">Jako właściwość projekcji DbProjectExpression.</span><span class="sxs-lookup"><span data-stu-id="7d10b-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="7d10b-153">Gdy jest używana w związku z tym obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="7d10b-153">When used as such the following restrictions apply:</span></span>

  - <span data-ttu-id="7d10b-154">Typ wyniku musi być typu wiersza.</span><span class="sxs-lookup"><span data-stu-id="7d10b-154">The result type must be a row type.</span></span>

  - <span data-ttu-id="7d10b-155">Każdy z jej argumentów jest wyrażeniem, który produkuje wynik z parametrem typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="7d10b-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="7d10b-156">Zwykle każdy argument znajduje się wyrażenie skalarne, takie jak PropertyExpression nad DbVariableReferenceExpression, wywołania funkcji lub arytmetyczne obliczeń DbPropertyExpression DbVariableReferenceExpression lub wywołania funkcji .</span><span class="sxs-lookup"><span data-stu-id="7d10b-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="7d10b-157">Jednak wyrażenie reprezentujące podzapytania skalarnej może również wystąpić na liście argumentów obiekt DbNewInstanceExpression.</span><span class="sxs-lookup"><span data-stu-id="7d10b-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="7d10b-158">Wyrażenie, które reprezentuje skalarne podzapytania jest drzewo wyrażenia, reprezentujący podzapytania, która zwraca dokładnie jeden wiersz i jedną kolumnę typu prymitywnego za pomocą głównego obiektu DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="7d10b-159">Z typem zwracanym kolekcji w którym to przypadku definiuje nową kolekcję wyrażeń dostarczone jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="7d10b-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="7d10b-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="7d10b-161">DbVariableReferenceExpression musi być elementem podrzędnym węzła DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="7d10b-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="7d10b-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-162">DbGroupByExpression</span></span>

<span data-ttu-id="7d10b-163">Właściwość agregacje element dbgroupaggregate może zawierać tylko elementy typu DbFunctionAggregate.</span><span class="sxs-lookup"><span data-stu-id="7d10b-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="7d10b-164">Istnieją inne typy agregacji.</span><span class="sxs-lookup"><span data-stu-id="7d10b-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="7d10b-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-165">DbLimitExpression</span></span>

<span data-ttu-id="7d10b-166">Właściwość limitu tylko może być obiektem DbConstantExpression lub DbParameterReferenceExpression.</span><span class="sxs-lookup"><span data-stu-id="7d10b-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="7d10b-167">Również właściwość WithTies jest zawsze wartość false, począwszy od programu .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="7d10b-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="7d10b-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="7d10b-168">DbScanExpression</span></span>

<span data-ttu-id="7d10b-169">W przypadku użycia w danych wyjściowych drzew poleceń, DbScanExpression skutecznie reprezentuje skanowania za pośrednictwem tabeli, widoku lub zapytania magazynu, reprezentowane przez EntitySetBase::Target.</span><span class="sxs-lookup"><span data-stu-id="7d10b-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="7d10b-170">Jeśli właściwość metadanych "Definiowanie zapytania" element docelowy jest różna od null, reprezentuje zapytanie, tekst zapytania, dla której znajduje się w tej właściwości metadanych w dostawcy określonego języka (lub dialekt), jak to określono w definicji schematu magazynu.</span><span class="sxs-lookup"><span data-stu-id="7d10b-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="7d10b-171">W przeciwnym razie element docelowy reprezentuje tabelą ani widokiem.</span><span class="sxs-lookup"><span data-stu-id="7d10b-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="7d10b-172">Jej prefiks schematu jest albo we właściwości metadanych "Schema", jeśli nie ma wartość null, w przeciwnym razie jest nazwa kontenera jednostki.</span><span class="sxs-lookup"><span data-stu-id="7d10b-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="7d10b-173">Nazwa tabeli lub widoku jest albo właściwość metadanych "Table", o ile nie wartość null, w przeciwnym razie podstawowego zestawu właściwości Name obiektu jednostki.</span><span class="sxs-lookup"><span data-stu-id="7d10b-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="7d10b-174">Te właściwości pochodzą z definicji odpowiedniego obiektu EntitySet w pliku definicji schematu magazynu (SSDL).</span><span class="sxs-lookup"><span data-stu-id="7d10b-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="7d10b-175">Przy użyciu typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="7d10b-175">Using Primitive Types</span></span>

<span data-ttu-id="7d10b-176">Gdy typy pierwotne są wywoływane w danych wyjściowych drzew poleceń, zwykle występuje do nich w typach pierwotnych modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="7d10b-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="7d10b-177">Jednak niektóre wyrażenia dostawców na potrzeby odpowiedni typ pierwotny magazynu.</span><span class="sxs-lookup"><span data-stu-id="7d10b-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="7d10b-178">Takie wyrażenia przykładami DbCastExpression i prawdopodobnie DbNullExpression, jeśli dostawca musi można rzutować wartości null do odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="7d10b-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="7d10b-179">W takich przypadkach dostawców należy wykonać mapowanie na typ dostawcy, na podstawie typu pierwotnego typu i jego zestawów reguł.</span><span class="sxs-lookup"><span data-stu-id="7d10b-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d10b-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d10b-180">See also</span></span>

- [<span data-ttu-id="7d10b-181">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="7d10b-181">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
