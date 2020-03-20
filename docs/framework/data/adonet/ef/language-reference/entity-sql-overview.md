---
title: Przegląd języka Entity SQL
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 880b81f2b6d4c4b893d28c919490f88dfb2a42e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150379"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="d67ba-102">Przegląd języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d67ba-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d67ba-103">jest językiem sql-like, który umożliwia wykonywanie zapytań o modele koncepcyjne w ramach encji.</span><span class="sxs-lookup"><span data-stu-id="d67ba-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="d67ba-104">Modele koncepcyjne reprezentują dane jako jednostki i relacje i [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia wykonywanie zapytań o te jednostki i relacje w formacie znanym osobom, które korzystały z języka SQL.</span><span class="sxs-lookup"><span data-stu-id="d67ba-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="d67ba-105">Entity Framework współpracuje z dostawcami danych [!INCLUDE[esql](../../../../../../includes/esql-md.md)] specyficznych dla magazynu, aby przetłumaczyć ogólne na zapytania specyficzne dla magazynu.</span><span class="sxs-lookup"><span data-stu-id="d67ba-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="d67ba-106">Dostawca EntityClient dostarcza sposób wykonania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] polecenia względem modelu jednostki i zwraca bogate typy danych, w tym wyniki skalarne, zestawy wyników i wykresy obiektów.</span><span class="sxs-lookup"><span data-stu-id="d67ba-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="d67ba-107">Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiektów można określić nazwę procedury składowanej lub [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tekst kwerendy, przypisując ciąg zapytania do jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d67ba-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d67ba-108">Ujawnia <xref:System.Data.EntityClient.EntityDataReader> wyniki wykonywania <xref:System.Data.EntityClient.EntityCommand> przeciwko EDM.</span><span class="sxs-lookup"><span data-stu-id="d67ba-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="d67ba-109">Aby wykonać polecenie, <xref:System.Data.EntityClient.EntityDataReader>które <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>zwraca polecenie , call .</span><span class="sxs-lookup"><span data-stu-id="d67ba-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="d67ba-110">Oprócz dostawcy EntityClient entity Framework umożliwia wykonywanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytań względem modelu koncepcyjnego i zwracanie danych jako silnie typizowane obiekty CLR, które są wystąpieniami typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="d67ba-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="d67ba-111">Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d67ba-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="d67ba-112">Ta sekcja zawiera informacje [!INCLUDE[esql](../../../../../../includes/esql-md.md)]koncepcyjne na temat .</span><span class="sxs-lookup"><span data-stu-id="d67ba-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d67ba-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d67ba-113">In This Section</span></span>  
 [<span data-ttu-id="d67ba-114">Czym język Entity SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d67ba-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="d67ba-115">Szybkie odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d67ba-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="d67ba-116">System typów</span><span class="sxs-lookup"><span data-stu-id="d67ba-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-117">Definicje typu</span><span class="sxs-lookup"><span data-stu-id="d67ba-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-118">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="d67ba-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-119">Buforowanie planu zapytania</span><span class="sxs-lookup"><span data-stu-id="d67ba-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="d67ba-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-121">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="d67ba-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-122">Parametry</span><span class="sxs-lookup"><span data-stu-id="d67ba-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-123">Zmienne</span><span class="sxs-lookup"><span data-stu-id="d67ba-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-124">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="d67ba-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-125">Literały</span><span class="sxs-lookup"><span data-stu-id="d67ba-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-126">Literały null i wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="d67ba-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-127">Wejściowy zestaw znaków</span><span class="sxs-lookup"><span data-stu-id="d67ba-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-128">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="d67ba-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-129">Funkcje</span><span class="sxs-lookup"><span data-stu-id="d67ba-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-130">Kolejność wykonywania działań</span><span class="sxs-lookup"><span data-stu-id="d67ba-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-131">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="d67ba-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-132">Semantyka porównania</span><span class="sxs-lookup"><span data-stu-id="d67ba-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="d67ba-133">Tworzenie zagnieżdżonych zapytań w języku Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d67ba-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="d67ba-134">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="d67ba-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="d67ba-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d67ba-135">See also</span></span>

- [<span data-ttu-id="d67ba-136">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="d67ba-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="d67ba-137">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="d67ba-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="d67ba-138">Specyfikacje CSDL, SSDL i MSL</span><span class="sxs-lookup"><span data-stu-id="d67ba-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
