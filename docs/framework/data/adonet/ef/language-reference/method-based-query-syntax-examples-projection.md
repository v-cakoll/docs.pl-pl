---
title: 'Przykłady składni zapytania oparte na metodzie: Rzut'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 287be3648fa6c21df836fc09d197e1a23e83eec8
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827061"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="92831-102">Przykłady składni zapytania oparte na metodzie: Rzut</span><span class="sxs-lookup"><span data-stu-id="92831-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="92831-103">Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.Select%2A> i <xref:System.Linq.Enumerable.SelectMany%2A> metod do wykonywania zapytań [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) za pomocą składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="92831-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="92831-104">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="92831-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="92831-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="92831-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="92831-106">Wybierz</span><span class="sxs-lookup"><span data-stu-id="92831-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="92831-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="92831-107">Example</span></span>  
 <span data-ttu-id="92831-108">W poniższym przykładzie użyto <xref:System.Linq.Queryable.Select%2A> metody do projektu `Product.Name` i `Product.ProductID` właściwości sekwencję typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="92831-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="92831-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="92831-109">Example</span></span>  
 <span data-ttu-id="92831-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> metody w celu zwrócenia sekwencji tylko nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="92831-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="92831-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="92831-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="92831-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="92831-112">Example</span></span>  
 <span data-ttu-id="92831-113">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.SelectMany%2A> metodę, aby wybrać wszystkie zamówienia gdzie `TotalDue` jest mniejsza niż 500,00.</span><span class="sxs-lookup"><span data-stu-id="92831-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="92831-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="92831-114">Example</span></span>  
 <span data-ttu-id="92831-115">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.SelectMany%2A> metodę, aby wybrać wszystkie zamówienia, w którym kolejność została wprowadzona w 1 października 2002 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="92831-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="92831-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92831-116">See also</span></span>
- [<span data-ttu-id="92831-117">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="92831-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
