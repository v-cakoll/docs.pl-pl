---
title: Wyniki zapytania
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
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d2e8dc70007a0f3a411c4c8e48015f98c23da573
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="query-results"></a><span data-ttu-id="002ce-102">Wyniki zapytania</span><span class="sxs-lookup"><span data-stu-id="002ce-102">Query Results</span></span>
<span data-ttu-id="002ce-103">Po [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania jest konwertować na drzewa polecenia i wykonywane, wyniki zapytania są zazwyczaj zwracane jako jedną z następujących:</span><span class="sxs-lookup"><span data-stu-id="002ce-103">After a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is converted to command trees and executed, the query results are usually returned as one of the following:</span></span>  
  
-   <span data-ttu-id="002ce-104">Kolekcja zero lub więcej obiektów typów jednostek lub dla projekcji typu złożonego w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="002ce-104">A collection of zero or more typed entity objects or a projection of complex types in the conceptual model.</span></span>  
  
-   <span data-ttu-id="002ce-105">Typy CLR obsługiwane przez modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="002ce-105">CLR types supported by the conceptual model.</span></span>  
  
-   <span data-ttu-id="002ce-106">Kolekcje wbudowane.</span><span class="sxs-lookup"><span data-stu-id="002ce-106">Inline collections.</span></span>  
  
-   <span data-ttu-id="002ce-107">Typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="002ce-107">Anonymous types.</span></span>  
  
 <span data-ttu-id="002ce-108">Zapytanie zostało wykonane w źródle danych, wyniki są zmaterializowany na typy CLR i zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="002ce-108">When the query has executed against the data source, the results are materialized into CLR types and returned to the client.</span></span> <span data-ttu-id="002ce-109">Wszystkie materialization obiektu jest wykonywane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="002ce-109">All object materialization is performed by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="002ce-110">Błędów spowodowanych brakiem do mapowania między [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] i spowoduje, że wyjątki, aby zostać wygenerowany podczas materialization obiektu CLR.</span><span class="sxs-lookup"><span data-stu-id="002ce-110">Any errors that result from an inability to map between the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] and the CLR will cause exceptions to be thrown during object materialization.</span></span>  
  
 <span data-ttu-id="002ce-111">Jeśli wykonanie kwerendy zwraca typów pierwotnych modelu koncepcyjnego, wyniki składają się z typów CLR, które są autonomiczne i jest odłączony od [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="002ce-111">If the query execution returns primitive conceptual model types, the results consist of CLR types that are stand-alone and disconnected from the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="002ce-112">Jednak jeśli zapytanie zwraca kolekcję obiektów typów jednostek, reprezentowany przez <xref:System.Data.Objects.ObjectQuery%601>, te typy są śledzone przez obiekt kontekstu.</span><span class="sxs-lookup"><span data-stu-id="002ce-112">However, if the query returns a collection of typed entity objects, represented by <xref:System.Data.Objects.ObjectQuery%601>, those types are tracked by the object context.</span></span> <span data-ttu-id="002ce-113">Wszystkie zachowanie obiektu (na przykład kolekcje podrzędne i nadrzędne, śledzenia zmian polimorfizm i tak dalej) zostały zdefiniowane w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="002ce-113">All object behavior (such as child/parent collections, change tracking, polymorphism, and so on) are as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="002ce-114">Te funkcje mogą być używane w jego pojemność, zgodnie z definicją w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="002ce-114">This functionality can be used in its capacity, as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="002ce-115">Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="002ce-115">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="002ce-116">Typy struktur zwracane z zapytań (np. typy anonimowe i typy złożone dopuszczające wartości zerowe) mogą być `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="002ce-116">Struct types returned from queries (such as anonymous types and nullable complex types) can be of `null` value.</span></span> <span data-ttu-id="002ce-117"><xref:System.Data.Objects.DataClasses.EntityCollection%601> Właściwości zwróconą jednostkę również mogą być `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="002ce-117">An <xref:System.Data.Objects.DataClasses.EntityCollection%601> property of a returned entity can also be of `null` value.</span></span> <span data-ttu-id="002ce-118">Może to wynikać z projekcji właściwości kolekcji jednostki, która jest `null` wartość, na przykład wywołanie <xref:System.Linq.Queryable.FirstOrDefault%2A> na <xref:System.Data.Objects.ObjectQuery%601> który nie ma żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="002ce-118">This can result from projecting the collection property of an entity that is of `null` value, such as calling <xref:System.Linq.Queryable.FirstOrDefault%2A> on an <xref:System.Data.Objects.ObjectQuery%601> that has no elements.</span></span>  
  
 <span data-ttu-id="002ce-119">W niektórych sytuacjach zapytania mogą być wyświetlane do generowania zmaterializowanym wyniku podczas jej wykonywania, ale będzie można wykonać zapytania na serwerze i nigdy nie będzie można było zmaterializować obiekt jednostki w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="002ce-119">In certain situations, a query might appear to generate a materialized result during its execution, but the query will be executed on the server and the entity object will never be materialized in the CLR.</span></span> <span data-ttu-id="002ce-120">Może to powodować problemy, jeśli są zależnie od efektami ubocznymi materialization obiektu.</span><span class="sxs-lookup"><span data-stu-id="002ce-120">This can cause problems if you are depending on side effects of object materialization.</span></span>  
  
 <span data-ttu-id="002ce-121">Poniższy przykład zawiera klasy niestandardowej `MyContact`, z `LastName` właściwości.</span><span class="sxs-lookup"><span data-stu-id="002ce-121">The following example contains a custom class, `MyContact`, with a `LastName` property.</span></span> <span data-ttu-id="002ce-122">Gdy `LastName` właściwość jest ustawiona, `count` zmiennej jest zwiększany.</span><span class="sxs-lookup"><span data-stu-id="002ce-122">When the `LastName` property is set, a `count` variable is incremented.</span></span> <span data-ttu-id="002ce-123">Jeśli można wykonywać następujące dwa zapytania, pierwsza kwerenda powoduje zwiększenie `count` podczas, gdy nie będzie drugiego zapytania.</span><span class="sxs-lookup"><span data-stu-id="002ce-123">If you execute the two following queries, the first query will increment `count` while the second query will not.</span></span> <span data-ttu-id="002ce-124">Wynika to z faktu w drugiej kwerendy `LastName` właściwości jest zaprojektowana z wyników i `MyContact` klasa jest tworzona nigdy, ponieważ nie jest wymagane do wykonania zapytania w magazynie.</span><span class="sxs-lookup"><span data-stu-id="002ce-124">This is because in the second query the `LastName` property is projected from the results and the `MyContact` class is never created, because it is not required to execute the query on the store.</span></span>  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
