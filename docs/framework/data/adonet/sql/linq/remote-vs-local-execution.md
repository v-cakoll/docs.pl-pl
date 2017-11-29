---
title: Zdalne vs. Wykonanie lokalne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b04ba6dde572aa0a8edddc8a2a30a8e11a3e79c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="db79d-102">Zdalne vs. Wykonanie lokalne</span><span class="sxs-lookup"><span data-stu-id="db79d-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="db79d-103">Można wykonać zapytania albo zdalnie (to znaczy aparatu bazy danych wykonuje zapytanie w bazie danych) lub lokalnie ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje zapytanie lokalnej pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="db79d-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="db79d-104">Zdalne wykonywanie kodu</span><span class="sxs-lookup"><span data-stu-id="db79d-104">Remote Execution</span></span>  
 <span data-ttu-id="db79d-105">Należy wziąć pod uwagę następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="db79d-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="db79d-106">Jeśli Twoja baza danych zawiera tysiące wierszy zleceń, czy chcesz pobrać je wszystkie do przetwarzania małych podzbioru.</span><span class="sxs-lookup"><span data-stu-id="db79d-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="db79d-107">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> klasa implementuje <xref:System.Linq.IQueryable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db79d-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="db79d-108">Takie podejście upewnia się, czy takie zapytania mogą być wykonywane zdalnie.</span><span class="sxs-lookup"><span data-stu-id="db79d-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="db79d-109">Dwie główne korzyści przepływać z tej techniki:</span><span class="sxs-lookup"><span data-stu-id="db79d-109">Two major benefits flow from this technique:</span></span>  
  
-   <span data-ttu-id="db79d-110">Zbędne dane nie została pobrana.</span><span class="sxs-lookup"><span data-stu-id="db79d-110">Unnecessary data is not retrieved.</span></span>  
  
-   <span data-ttu-id="db79d-111">Zapytanie wykonywane przez aparat bazy danych jest często bardziej wydajne, ponieważ indeksy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="db79d-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="db79d-112">Wykonanie lokalne</span><span class="sxs-lookup"><span data-stu-id="db79d-112">Local Execution</span></span>  
 <span data-ttu-id="db79d-113">W innych sytuacjach możesz chcieć ma kompletnego zestawu powiązanych jednostek w lokalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="db79d-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="db79d-114">W tym celu <xref:System.Data.Linq.EntitySet%601> zapewnia <xref:System.Data.Linq.EntitySet%601.Load%2A> metodę, aby wszystkie elementy członkowskie w sposób jawny załadować <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="db79d-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="db79d-115">Jeśli <xref:System.Data.Linq.EntitySet%601> jest już załadowany, kolejne zapytania są wykonywane lokalnie.</span><span class="sxs-lookup"><span data-stu-id="db79d-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="db79d-116">Takie podejście pozwala na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="db79d-116">This approach helps in two ways:</span></span>  
  
-   <span data-ttu-id="db79d-117">Jeśli pełny zestaw musi być używane lokalnie lub wiele razy, można uniknąć zapytań zdalnych i skojarzone opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="db79d-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
-   <span data-ttu-id="db79d-118">Może być Zserializowany obiekt jako całą jednostkę.</span><span class="sxs-lookup"><span data-stu-id="db79d-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="db79d-119">Poniższy fragment kodu przedstawia sposób lokalne wykonanie można uzyskać:</span><span class="sxs-lookup"><span data-stu-id="db79d-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="db79d-120">Porównanie</span><span class="sxs-lookup"><span data-stu-id="db79d-120">Comparison</span></span>  
 <span data-ttu-id="db79d-121">Te dwie funkcje Podaj kombinację opcji zaawansowanych: zdalne wykonywanie kodu w dużych kolekcjach i wykonanie lokalne dla małych kolekcji lub gdy potrzebne jest pełną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="db79d-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="db79d-122">Wdrożenie zdalne wykonywanie kodu za pomocą <xref:System.Linq.IQueryable>oraz lokalnego miało zostać wykonane w pamięci <xref:System.Collections.Generic.IEnumerable%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="db79d-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="db79d-123">Aby wymusić wykonanie lokalne (to znaczy <xref:System.Collections.Generic.IEnumerable%601>), zobacz [przekonwertować typem rodzajowym interfejsem IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="db79d-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="db79d-124">Zapytania względem nieuporządkowaną zestawów</span><span class="sxs-lookup"><span data-stu-id="db79d-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="db79d-125">Należy zwrócić uwagę istotną różnicą między kolekcji lokalnej, która implementuje <xref:System.Collections.Generic.List%601> i kolekcja, która zapewnia zdalnego zapytania wykonywane *nieuporządkowane zestawy* relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="db79d-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="db79d-126"><xref:System.Collections.Generic.List%601>metody takich jak implementacje używające wartości indeksu wymagają semantyki listy, które zwykle nie można uzyskać za pośrednictwem zdalnego zapytanie nieuporządkowaną zestawu.</span><span class="sxs-lookup"><span data-stu-id="db79d-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="db79d-127">Z tego powodu niejawnie obciążenia tych metod <xref:System.Data.Linq.EntitySet%601> umożliwia wykonanie lokalne.</span><span class="sxs-lookup"><span data-stu-id="db79d-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db79d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db79d-128">See Also</span></span>  
 [<span data-ttu-id="db79d-129">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="db79d-129">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
