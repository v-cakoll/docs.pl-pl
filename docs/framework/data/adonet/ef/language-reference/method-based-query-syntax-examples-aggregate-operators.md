---
title: "Przykłady składni zapytania oparte na metodzie: Operatory agregacji"
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
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e965720f7952715b7fec648c794dd8a0b8b9cd1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="e14ee-102">Przykłady składni zapytania oparte na metodzie: Operatory agregacji</span><span class="sxs-lookup"><span data-stu-id="e14ee-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="e14ee-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> metod do badania [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="e14ee-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="e14ee-104">Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e14ee-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e14ee-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="e14ee-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="e14ee-106">Średnia</span><span class="sxs-lookup"><span data-stu-id="e14ee-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="e14ee-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-107">Example</span></span>  
 <span data-ttu-id="e14ee-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średniej ceny listy produktów.</span><span class="sxs-lookup"><span data-stu-id="e14ee-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-109">Example</span></span>  
 <span data-ttu-id="e14ee-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia średniej ceny listy produktów każdy styl.</span><span class="sxs-lookup"><span data-stu-id="e14ee-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-111">Example</span></span>  
 <span data-ttu-id="e14ee-112">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metody do znalezienia Średnia łączna ukończenia.</span><span class="sxs-lookup"><span data-stu-id="e14ee-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-113">Example</span></span>  
 <span data-ttu-id="e14ee-114">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> nazwę metody można uzyskać Średnia łączna ukończenia każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="e14ee-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-115">Example</span></span>  
 <span data-ttu-id="e14ee-116">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Average%2A> metodę, aby uzyskać zamówień ze średnią całkowita ukończenia każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="e14ee-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="e14ee-117">Liczba</span><span class="sxs-lookup"><span data-stu-id="e14ee-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="e14ee-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-118">Example</span></span>  
 <span data-ttu-id="e14ee-119">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> metodę, aby zwracać liczbę produktów w tabeli produktu.</span><span class="sxs-lookup"><span data-stu-id="e14ee-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-120">Example</span></span>  
 <span data-ttu-id="e14ee-121">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> ma metodę, aby zwrócić listę skontaktuj się z identyfikatorów i ile porządkuje każdego.</span><span class="sxs-lookup"><span data-stu-id="e14ee-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-122">Example</span></span>  
 <span data-ttu-id="e14ee-123">W poniższym przykładzie grupy produktów przez kolor i używa <xref:System.Linq.Enumerable.Count%2A> metoda zwraca liczbę produktów w każdej grupie kolorów.</span><span class="sxs-lookup"><span data-stu-id="e14ee-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="e14ee-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="e14ee-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="e14ee-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-125">Example</span></span>  
 <span data-ttu-id="e14ee-126">Poniższy przykład pobiera liczbę kontaktów jako długich liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e14ee-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="e14ee-127">Maksymalna</span><span class="sxs-lookup"><span data-stu-id="e14ee-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="e14ee-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-128">Example</span></span>  
 <span data-ttu-id="e14ee-129">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metody, aby uzyskać największy termin całkowitej.</span><span class="sxs-lookup"><span data-stu-id="e14ee-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-130">Example</span></span>  
 <span data-ttu-id="e14ee-131">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać największy termin całkowitą dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="e14ee-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-132">Example</span></span>  
 <span data-ttu-id="e14ee-133">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> metodę, aby uzyskać zamówień z największych odpowiednim całkowita dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="e14ee-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="e14ee-134">Min</span><span class="sxs-lookup"><span data-stu-id="e14ee-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="e14ee-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-135">Example</span></span>  
 <span data-ttu-id="e14ee-136">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metody, aby uzyskać najmniejszą liczbę całkowitą ukończenia.</span><span class="sxs-lookup"><span data-stu-id="e14ee-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-137">Example</span></span>  
 <span data-ttu-id="e14ee-138">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby uzyskać najmniejszą termin całkowitą dla każdego skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="e14ee-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-139">Example</span></span>  
 <span data-ttu-id="e14ee-140">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Min%2A> metodę, aby pobrać zamówień z najmniejszą sumę do każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="e14ee-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="e14ee-141">Suma</span><span class="sxs-lookup"><span data-stu-id="e14ee-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="e14ee-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-142">Example</span></span>  
 <span data-ttu-id="e14ee-143">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby uzyskać sumę ilości kolejności w tabeli Szczegóły zamówienia sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="e14ee-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="e14ee-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="e14ee-144">Example</span></span>  
 <span data-ttu-id="e14ee-145">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Sum%2A> metodę, aby pobrać całkowitej ukończenia dla każdej skontaktuj się z identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="e14ee-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="e14ee-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e14ee-146">See Also</span></span>  
 [<span data-ttu-id="e14ee-147">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e14ee-147">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
