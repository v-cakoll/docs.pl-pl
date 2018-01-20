---
title: "Przykłady składni wyrażeń zapytania: Operatory agregacji"
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
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 76af42681767b17fd69fac5bfd924e02b0f6b9b0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="51fdb-102">Przykłady składni wyrażeń zapytania: Operatory agregacji</span><span class="sxs-lookup"><span data-stu-id="51fdb-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="51fdb-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> metod do badania [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="51fdb-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="51fdb-104">Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="51fdb-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="51fdb-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="51fdb-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="51fdb-106">Średnia</span><span class="sxs-lookup"><span data-stu-id="51fdb-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="51fdb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-107">Example</span></span>  
 <span data-ttu-id="51fdb-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średniej ceny listy produktów każdy styl.</span><span class="sxs-lookup"><span data-stu-id="51fdb-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="51fdb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-109">Example</span></span>  
 <span data-ttu-id="51fdb-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> uzyskanie Średnia łączna powodu dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="51fdb-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="51fdb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-111">Example</span></span>  
 <span data-ttu-id="51fdb-112">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> można uzyskać zamówień ze średnią całkowita ukończenia każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="51fdb-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="51fdb-113">Liczba</span><span class="sxs-lookup"><span data-stu-id="51fdb-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="51fdb-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-114">Example</span></span>  
 <span data-ttu-id="51fdb-115">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> aby zwrócić listę skontaktuj się z identyfikatorów i ile porządkuje każdy ma.</span><span class="sxs-lookup"><span data-stu-id="51fdb-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="51fdb-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-116">Example</span></span>  
 <span data-ttu-id="51fdb-117">W poniższym przykładzie grupy produktów przez kolor i używa <xref:System.Linq.Enumerable.Count%2A> do zwrócenia liczba produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="51fdb-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="51fdb-118">Maksymalna</span><span class="sxs-lookup"><span data-stu-id="51fdb-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="51fdb-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-119">Example</span></span>  
 <span data-ttu-id="51fdb-120">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać największy termin całkowitą dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="51fdb-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="51fdb-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-121">Example</span></span>  
 <span data-ttu-id="51fdb-122">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać zamówień z największych odpowiednim całkowita dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="51fdb-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="51fdb-123">Min</span><span class="sxs-lookup"><span data-stu-id="51fdb-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="51fdb-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-124">Example</span></span>  
 <span data-ttu-id="51fdb-125">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać najmniejszą termin całkowitą dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="51fdb-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="51fdb-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-126">Example</span></span>  
 <span data-ttu-id="51fdb-127">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby pobrać zamówień z najmniejszą sumę do każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="51fdb-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="51fdb-128">Suma</span><span class="sxs-lookup"><span data-stu-id="51fdb-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="51fdb-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="51fdb-129">Example</span></span>  
 <span data-ttu-id="51fdb-130">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby pobrać całkowitej ukończenia dla każdej skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="51fdb-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="51fdb-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51fdb-131">See Also</span></span>  
 [<span data-ttu-id="51fdb-132">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="51fdb-132">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
