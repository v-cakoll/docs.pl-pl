---
title: Zdalne a lokalne wykonanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: a21d5bbffdb1a78d3062929a1ca384a750af59a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781156"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="41ec4-102">Zdalne a lokalne wykonanie</span><span class="sxs-lookup"><span data-stu-id="41ec4-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="41ec4-103">Możesz zdecydować się na zdalne wykonywanie zapytań (to oznacza, że aparat bazy danych wykonuje zapytanie względem bazy danych) lub lokalnie ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje zapytanie względem lokalnej pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="41ec4-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="41ec4-104">Zdalne wykonywanie kodu</span><span class="sxs-lookup"><span data-stu-id="41ec4-104">Remote Execution</span></span>  
 <span data-ttu-id="41ec4-105">Rozważ następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="41ec4-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="41ec4-106">Jeśli baza danych ma tysiące rzędów zamówień, nie chcesz pobierać ich wszystkich, aby przetwarzać mały podzestaw.</span><span class="sxs-lookup"><span data-stu-id="41ec4-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="41ec4-107">W programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Klasaimplementuje<xref:System.Linq.IQueryable>interfejs. <xref:System.Data.Linq.EntitySet%601></span><span class="sxs-lookup"><span data-stu-id="41ec4-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="41ec4-108">Takie podejście gwarantuje, że takie zapytania można wykonać zdalnie.</span><span class="sxs-lookup"><span data-stu-id="41ec4-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="41ec4-109">Przepływ dwóch głównych korzyści z tej techniki:</span><span class="sxs-lookup"><span data-stu-id="41ec4-109">Two major benefits flow from this technique:</span></span>  
  
- <span data-ttu-id="41ec4-110">Nie pobrano zbędnych danych.</span><span class="sxs-lookup"><span data-stu-id="41ec4-110">Unnecessary data is not retrieved.</span></span>  
  
- <span data-ttu-id="41ec4-111">Zapytanie wykonywane przez aparat bazy danych jest często wydajniejsze ze względu na indeksy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="41ec4-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="41ec4-112">lokalne wykonanie</span><span class="sxs-lookup"><span data-stu-id="41ec4-112">Local Execution</span></span>  
 <span data-ttu-id="41ec4-113">W innych sytuacjach może być konieczne posiadanie kompletnego zestawu powiązanych jednostek w lokalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="41ec4-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="41ec4-114">W tym celu <xref:System.Data.Linq.EntitySet%601> zapewnia metodę, <xref:System.Data.Linq.EntitySet%601.Load%2A> aby jawnie załadować <xref:System.Data.Linq.EntitySet%601>wszystkie elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="41ec4-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="41ec4-115"><xref:System.Data.Linq.EntitySet%601> Jeśli jest już załadowany, kolejne zapytania są wykonywane lokalnie.</span><span class="sxs-lookup"><span data-stu-id="41ec4-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="41ec4-116">To podejście jest pomocne na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="41ec4-116">This approach helps in two ways:</span></span>  
  
- <span data-ttu-id="41ec4-117">Jeśli kompletny zestaw musi być używany lokalnie lub wiele razy, można uniknąć zdalnych zapytań i skojarzonych opóźnień.</span><span class="sxs-lookup"><span data-stu-id="41ec4-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
- <span data-ttu-id="41ec4-118">Jednostkę można serializować jako kompletną jednostkę.</span><span class="sxs-lookup"><span data-stu-id="41ec4-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="41ec4-119">Poniższy fragment kodu ilustruje sposób uzyskania lokalnego wykonania:</span><span class="sxs-lookup"><span data-stu-id="41ec4-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="41ec4-120">Porównanie</span><span class="sxs-lookup"><span data-stu-id="41ec4-120">Comparison</span></span>  
 <span data-ttu-id="41ec4-121">Te dwie możliwości oferują zaawansowaną kombinację opcji: zdalne wykonywanie dużych kolekcji i wykonywanie lokalne dla małych kolekcji lub, gdzie jest wymagana kompletna kolekcja.</span><span class="sxs-lookup"><span data-stu-id="41ec4-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="41ec4-122">Implementowanie zdalnego wykonywania przez <xref:System.Linq.IQueryable>program i wykonywanie lokalne w odniesieniu do <xref:System.Collections.Generic.IEnumerable%601> kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="41ec4-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="41ec4-123">Aby wymusić wykonanie lokalne (czyli <xref:System.Collections.Generic.IEnumerable%601>), zobacz [konwertowanie typu na rodzajowy interfejs IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="41ec4-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="41ec4-124">Zapytania dotyczące nieuporządkowanych zestawów</span><span class="sxs-lookup"><span data-stu-id="41ec4-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="41ec4-125">Należy zwrócić uwagę na istotną różnicę między lokalną kolekcją, która implementuje <xref:System.Collections.Generic.List%601> i kolekcję, która zapewnia zapytania zdalne wykonywane w odniesieniu do *nieuporządkowanych zestawów* w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="41ec4-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="41ec4-126"><xref:System.Collections.Generic.List%601>metody, takie jak te, które używają wartości indeksu, wymagają semantyki list, która zazwyczaj nie można uzyskać za pomocą zapytania zdalnego dla nieuporządkowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="41ec4-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="41ec4-127">Z tego powodu takie metody niejawnie ładują <xref:System.Data.Linq.EntitySet%601> , aby umożliwić wykonanie lokalne.</span><span class="sxs-lookup"><span data-stu-id="41ec4-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ec4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41ec4-128">See also</span></span>

- [<span data-ttu-id="41ec4-129">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="41ec4-129">Query Concepts</span></span>](query-concepts.md)
