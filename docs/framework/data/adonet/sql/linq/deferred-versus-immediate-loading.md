---
title: "Odroczone i ładowania bezpośredniego"
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
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 992d9a018f81bbd3f0c9204168f513024769e079
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deferred-versus-immediate-loading"></a><span data-ttu-id="edb98-102">Odroczone i ładowania bezpośredniego</span><span class="sxs-lookup"><span data-stu-id="edb98-102">Deferred versus Immediate Loading</span></span>
<span data-ttu-id="edb98-103">Określona w zapytaniu dla obiekt faktycznie pobrać tylko żądanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="edb98-103">When you query for an object, you actually retrieve only the object you requested.</span></span> <span data-ttu-id="edb98-104">*Powiązane* obiekty nie są automatycznie dołączone w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="edb98-104">The *related* objects are not automatically fetched at the same time.</span></span> <span data-ttu-id="edb98-105">(Aby uzyskać więcej informacji, zobacz [zapytań w relacji](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Nie widać fakt, że powiązane obiekty nie są już załadowana, ponieważ próba dostępu do nich tworzy żądanie, które pobierają je.</span><span class="sxs-lookup"><span data-stu-id="edb98-105">(For more information, see [Querying Across Relationships](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) You cannot see the fact that the related objects are not already loaded, because an attempt to access them produces a request that retrieves them.</span></span>  
  
 <span data-ttu-id="edb98-106">Na przykład można wyszukać określonego zestawu zamówienia, a następnie sporadycznie Wyślij powiadomienie e-mail klientom określonego.</span><span class="sxs-lookup"><span data-stu-id="edb98-106">For example, you might want to query for a particular set of orders and then only occasionally send an e-mail notification to particular customers.</span></span> <span data-ttu-id="edb98-107">Nie zawsze konieczne będzie początkowo pobrać wszystkich danych klientów z każdej kolejności.</span><span class="sxs-lookup"><span data-stu-id="edb98-107">You would not necessarily need initially to retrieve all customer data with every order.</span></span> <span data-ttu-id="edb98-108">Ładowanie odłożone umożliwia odroczenie pobierania dodatkowe informacje do momentu bezwzględnie konieczne.</span><span class="sxs-lookup"><span data-stu-id="edb98-108">You can use deferred loading to defer retrieval of extra information until you absolutely have to.</span></span> <span data-ttu-id="edb98-109">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="edb98-109">Consider the following example:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 <span data-ttu-id="edb98-110">Wartość true, może być również odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="edb98-110">The opposite might also be true.</span></span> <span data-ttu-id="edb98-111">Może być aplikacji, aby wyświetlić klienta i kolejność danych w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="edb98-111">You might have an application that has to view customer and order data at the same time.</span></span> <span data-ttu-id="edb98-112">Wiadomo, że należy oba zestawy danych.</span><span class="sxs-lookup"><span data-stu-id="edb98-112">You know you need both sets of data.</span></span> <span data-ttu-id="edb98-113">Wiadomo, że aplikacja wymaga informacji o zamówieniu dla każdego klienta, jak uzyskać wyniki.</span><span class="sxs-lookup"><span data-stu-id="edb98-113">You know your application needs order information for each customer as soon as you get the results.</span></span> <span data-ttu-id="edb98-114">Czy chcesz przesłać poszczególnych zapytania dotyczące zamówienia dla każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="edb98-114">You would not want to submit individual queries for orders for every customer.</span></span> <span data-ttu-id="edb98-115">Co naprawdę jest pobrać dane zlecenia wraz z klientów.</span><span class="sxs-lookup"><span data-stu-id="edb98-115">What you really want is to retrieve the order data together with the customers.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 <span data-ttu-id="edb98-116">Można również dołączyć klienci i zamówienia w zapytaniu tworzące iloczyn wektorowy i pobierania względną bitów danych jako jeden rzut duże.</span><span class="sxs-lookup"><span data-stu-id="edb98-116">You can also join customers and orders in a query by forming the cross-product and retrieving all the relative bits of data as one large projection.</span></span> <span data-ttu-id="edb98-117">Jednak te wyniki nie są jednostek.</span><span class="sxs-lookup"><span data-stu-id="edb98-117">But these results are not entities.</span></span> <span data-ttu-id="edb98-118">(Aby uzyskać więcej informacji, zobacz [LINQ w modelu obiektu SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span><span class="sxs-lookup"><span data-stu-id="edb98-118">(For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span></span> <span data-ttu-id="edb98-119">Jednostki są obiektów, które mają tożsamości i że można modyfikować, te wyniki byłoby projekcje, które nie mogą być zmienione i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="edb98-119">Entities are objects that have identity and that you can modify, whereas these results would be projections that cannot be changed and persisted.</span></span> <span data-ttu-id="edb98-120">Nawet gorsza można będzie można pobieranie wiele zbędnych danych zgodnie z każdego klienta powtarza się dla każdej kolejności w danych wyjściowych spłaszczoną sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="edb98-120">Even worse, you would be retrieving lots of redundant data as each customer repeats for each order in the flattened join output.</span></span>  
  
 <span data-ttu-id="edb98-121">Co naprawdę potrzebne jest sposobem pobrania zestawu powiązanych obiektów w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="edb98-121">What you really need is a way to retrieve a set of related objects at the same time.</span></span> <span data-ttu-id="edb98-122">Zestaw jest nakreślono części wykres, dzięki czemu można będzie nigdy nie być pobierania większa lub mniejsza niż niezbędne do zamierzonego użycia.</span><span class="sxs-lookup"><span data-stu-id="edb98-122">The set is a delineated section of a graph so that you would never be retrieving more or less than was necessary for your intended use.</span></span> <span data-ttu-id="edb98-123">W tym celu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia <xref:System.Data.Linq.DataLoadOptions> do ładowania bezpośredniego regionu modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="edb98-123">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides <xref:System.Data.Linq.DataLoadOptions> for immediate loading of a region of your object model.</span></span> <span data-ttu-id="edb98-124">Metody obejmują:</span><span class="sxs-lookup"><span data-stu-id="edb98-124">Methods include:</span></span>  
  
-   <span data-ttu-id="edb98-125"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Metody, aby natychmiast załadować dane powiązane z głównym celem.</span><span class="sxs-lookup"><span data-stu-id="edb98-125">The  <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method, to immediately load data related to the main target.</span></span>  
  
-   <span data-ttu-id="edb98-126"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Sposób pobrane dla określonego relacji obiekty filtru.</span><span class="sxs-lookup"><span data-stu-id="edb98-126">The <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method, to filter objects retrieved for a particular relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb98-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edb98-127">See Also</span></span>  
 [<span data-ttu-id="edb98-128">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="edb98-128">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
