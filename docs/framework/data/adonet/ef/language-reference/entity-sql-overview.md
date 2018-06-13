---
title: Omówienie SQL jednostki
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e7cadbd357ab96d67c6d1f1e49ba0d8b3883bf3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760742"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="5b70f-102">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="5b70f-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5b70f-103"> jest języka przypominającego SQL umożliwia zapytania modeli koncepcyjnych w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b70f-103"> is a SQL-like language that enables you to query conceptual models in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="5b70f-104">Modele koncepcyjne zawierają dane jako jednostki i relacje, i [!INCLUDE[esql](../../../../../../includes/esql-md.md)] umożliwia kwerendy te jednostki i relacje w formacie, który jest znana do tych, którzy użyli SQL.</span><span class="sxs-lookup"><span data-stu-id="5b70f-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
  
 <span data-ttu-id="5b70f-105">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Współpracuje z dostawców magazynu danych do tłumaczenia ogólnego [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do specyficznych dla magazynu zapytań.</span><span class="sxs-lookup"><span data-stu-id="5b70f-105">The [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="5b70f-106">Dostawca EntityClient udostępnia sposób wykonywania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] polecenia w odniesieniu do modelu jednostki i zwracanych zaawansowanych typów danych w tym skalarne wyników, zestawów wyników i wykresów obiektów.</span><span class="sxs-lookup"><span data-stu-id="5b70f-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="5b70f-107">Podczas konstruowania <xref:System.Data.EntityClient.EntityCommand> obiekty, można określić nazwę procedury składowanej lub tekst zapytania, przypisując [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ciągu do zapytania jego <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b70f-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5b70f-108"><xref:System.Data.EntityClient.EntityDataReader> Przedstawia wyniki wykonania <xref:System.Data.EntityClient.EntityCommand> przed EDM.</span><span class="sxs-lookup"><span data-stu-id="5b70f-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="5b70f-109">Do wykonania polecenia, która zwraca <xref:System.Data.EntityClient.EntityDataReader>, wywołaj <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b70f-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="5b70f-110">Oprócz dostawcy EntityClient [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] pozwala na użycie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wykonywanie zapytań względem modelu koncepcyjnego i zwraca dane jako silnie typizowanych obiektów CLR, które wystąpień typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="5b70f-110">In addition to the EntityClient provider, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="5b70f-111">Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="5b70f-111">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="5b70f-112">Ta sekcja zawiera informacje o pojęciach dotyczących [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b70f-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b70f-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5b70f-113">In This Section</span></span>  
 [<span data-ttu-id="5b70f-114">Jak jednostka SQL różni się od języka Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5b70f-114">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="5b70f-115">Szybkie odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b70f-115">Entity SQL Quick Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="5b70f-116">System typów</span><span class="sxs-lookup"><span data-stu-id="5b70f-116">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-117">Definicje typu</span><span class="sxs-lookup"><span data-stu-id="5b70f-117">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-118">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="5b70f-118">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-119">Buforowanie planu zapytania</span><span class="sxs-lookup"><span data-stu-id="5b70f-119">Query Plan Caching</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="5b70f-120">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-121">Identyfikatory</span><span class="sxs-lookup"><span data-stu-id="5b70f-121">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-122">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b70f-122">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-123">Zmienne</span><span class="sxs-lookup"><span data-stu-id="5b70f-123">Variables</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-124">Nieobsługiwane wyrażenia</span><span class="sxs-lookup"><span data-stu-id="5b70f-124">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-125">Literały</span><span class="sxs-lookup"><span data-stu-id="5b70f-125">Literals</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-126">Literały null i wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="5b70f-126">Null Literals and Type Inference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-127">Wejściowy zestaw znaków</span><span class="sxs-lookup"><span data-stu-id="5b70f-127">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-128">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="5b70f-128">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-129">Funkcje</span><span class="sxs-lookup"><span data-stu-id="5b70f-129">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-130">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="5b70f-130">Operator Precedence</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-131">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="5b70f-131">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-132">Semantyka porównania</span><span class="sxs-lookup"><span data-stu-id="5b70f-132">Comparison Semantics</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="5b70f-133">Tworzenie zagnieżdżonych zapytań jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b70f-133">Composing Nested Entity SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="5b70f-134">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="5b70f-134">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b70f-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b70f-135">See Also</span></span>  
 [<span data-ttu-id="5b70f-136">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b70f-136">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="5b70f-137">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="5b70f-137">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [<span data-ttu-id="5b70f-138">Specyfikacje CSDL, SSDL i MSL</span><span class="sxs-lookup"><span data-stu-id="5b70f-138">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
