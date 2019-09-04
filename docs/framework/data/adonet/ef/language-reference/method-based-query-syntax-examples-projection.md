---
title: 'Przykłady składni zapytania oparte na metodzie: Rzut'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 231fe6072d9a9a561aa91d3cb52fa6963f2d72dd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250065"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="bc39c-102">Przykłady składni zapytania oparte na metodzie: Rzut</span><span class="sxs-lookup"><span data-stu-id="bc39c-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="bc39c-103">W przykładach w tym temacie pokazano, <xref:System.Linq.Enumerable.Select%2A> jak za pomocą metod i <xref:System.Linq.Enumerable.SelectMany%2A> zbadać [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni zapytania opartego na metodzie.</span><span class="sxs-lookup"><span data-stu-id="bc39c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="bc39c-104">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bc39c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="bc39c-105">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="bc39c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="bc39c-106">Wybierz</span><span class="sxs-lookup"><span data-stu-id="bc39c-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="bc39c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc39c-107">Example</span></span>  
 <span data-ttu-id="bc39c-108">W poniższym przykładzie zastosowano <xref:System.Linq.Queryable.Select%2A> metodę w celu `Product.Name` zaprojektowania właściwości i `Product.ProductID` w sekwencji typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="bc39c-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="bc39c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc39c-109">Example</span></span>  
 <span data-ttu-id="bc39c-110">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Select%2A> metodę, aby zwrócić sekwencję tylko nazw produktów.</span><span class="sxs-lookup"><span data-stu-id="bc39c-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="bc39c-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="bc39c-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="bc39c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc39c-112">Example</span></span>  
 <span data-ttu-id="bc39c-113">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.SelectMany%2A> metodę, aby wybrać wszystkie zamówienia `TotalDue` , których wartość jest mniejsza niż 500,00.</span><span class="sxs-lookup"><span data-stu-id="bc39c-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="bc39c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc39c-114">Example</span></span>  
 <span data-ttu-id="bc39c-115">W poniższym przykładzie użyto metody <xref:System.Linq.Enumerable.SelectMany%2A> , aby wybrać wszystkie zamówienia, w których zamówienie zostało wykonane w dniu 1 października 2002 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="bc39c-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="bc39c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc39c-116">See also</span></span>

- [<span data-ttu-id="bc39c-117">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="bc39c-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
