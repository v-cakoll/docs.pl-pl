---
title: Zdalne a lokalne wykonanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 02d0417bc05f8585dc469d365089c8123d395f64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164518"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="7346a-102">Zdalne a lokalne wykonanie</span><span class="sxs-lookup"><span data-stu-id="7346a-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="7346a-103">Możesz zdecydować się na wykonywanie zapytań albo zdalnie (oznacza to, że aparat bazy danych wykonuje zapytanie względem bazy danych) lub lokalnie ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje zapytanie względem lokalnej pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="7346a-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="7346a-104">Zdalne wykonywanie kodu</span><span class="sxs-lookup"><span data-stu-id="7346a-104">Remote Execution</span></span>  
 <span data-ttu-id="7346a-105">Należy wziąć pod uwagę następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="7346a-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="7346a-106">Jeśli baza danych zawiera tysiące wierszy zamówienia, czy chcesz pobrać je wszystkie do przetworzenia przechowywanego.</span><span class="sxs-lookup"><span data-stu-id="7346a-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="7346a-107">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> klasy implementuje <xref:System.Linq.IQueryable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7346a-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="7346a-108">To podejście zapewnia, że takich zapytań może być wykonywane zdalnie.</span><span class="sxs-lookup"><span data-stu-id="7346a-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="7346a-109">Przepływ dwie główne korzyści z tej techniki:</span><span class="sxs-lookup"><span data-stu-id="7346a-109">Two major benefits flow from this technique:</span></span>  
  
-   <span data-ttu-id="7346a-110">Zbędne dane nie są pobierane.</span><span class="sxs-lookup"><span data-stu-id="7346a-110">Unnecessary data is not retrieved.</span></span>  
  
-   <span data-ttu-id="7346a-111">Zapytania wykonywane przez aparat bazy danych jest często bardziej efektywne z powodu indeksy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7346a-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="7346a-112">lokalne wykonanie</span><span class="sxs-lookup"><span data-stu-id="7346a-112">Local Execution</span></span>  
 <span data-ttu-id="7346a-113">W innych sytuacjach możesz chcieć mieć kompletny zestaw powiązanych jednostek w lokalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7346a-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="7346a-114">W tym celu <xref:System.Data.Linq.EntitySet%601> zapewnia <xref:System.Data.Linq.EntitySet%601.Load%2A> metodę, aby jawnie załadować wszystkie elementy członkowskie <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="7346a-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="7346a-115">Jeśli <xref:System.Data.Linq.EntitySet%601> jest już załadowany, kolejne zapytania są wykonywane lokalnie.</span><span class="sxs-lookup"><span data-stu-id="7346a-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="7346a-116">Takie podejście pomaga na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="7346a-116">This approach helps in two ways:</span></span>  
  
-   <span data-ttu-id="7346a-117">Jeśli kompletny zestaw musi używać lokalnie lub wiele razy, możesz uniknąć zapytań zdalnych i skojarzone opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="7346a-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
-   <span data-ttu-id="7346a-118">Jednostki może być Zserializowany jako całą jednostkę.</span><span class="sxs-lookup"><span data-stu-id="7346a-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="7346a-119">Poniższy fragment kodu ilustruje sposób lokalnego wykonania można uzyskać:</span><span class="sxs-lookup"><span data-stu-id="7346a-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="7346a-120">Porównanie</span><span class="sxs-lookup"><span data-stu-id="7346a-120">Comparison</span></span>  
 <span data-ttu-id="7346a-121">Te dwie funkcje zapewniają kombinację opcji: zdalne wykonywanie kodu w dużych kolekcjach i lokalnych wykonań dla małych kolekcji lub w których wymagane jest pełną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="7346a-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="7346a-122">Implementowanie zdalne wykonywanie kodu za pomocą <xref:System.Linq.IQueryable>i lokalne miało zostać wykonane w pamięci <xref:System.Collections.Generic.IEnumerable%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7346a-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="7346a-123">Aby wymusić wykonanie lokalne (czyli <xref:System.Collections.Generic.IEnumerable%601>), zobacz [Konwertowanie typu do ogólnego interfejsu IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="7346a-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="7346a-124">Zapytania dotyczące nieuporządkowane zestawy</span><span class="sxs-lookup"><span data-stu-id="7346a-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="7346a-125">Należy pamiętać, istotną różnicą między kolekcji lokalnej, która implementuje <xref:System.Collections.Generic.List%601> i kolekcję, która umożliwia zdalne zapytania wykonywane względem *nieuporządkowane zestawy* relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7346a-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="7346a-126"><xref:System.Collections.Generic.List%601> metody, takich jak implementacje używające wartości indeksu wymagają semantyki listy, które zwykle nie można uzyskać za pośrednictwem zdalnego zapytanie względem zestawu nieuporządkowanego.</span><span class="sxs-lookup"><span data-stu-id="7346a-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="7346a-127">Z tego powodu takie metody niejawnie obciążenia <xref:System.Data.Linq.EntitySet%601> i umożliwia wykonywanie lokalne.</span><span class="sxs-lookup"><span data-stu-id="7346a-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7346a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7346a-128">See also</span></span>

- [<span data-ttu-id="7346a-129">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="7346a-129">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
