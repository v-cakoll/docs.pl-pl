---
title: 'Przykłady składni zapytania oparte na metodzie: projekcji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: b938e32ae0e10498203e141c34d35a18a3515257
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="ea0c6-102">Przykłady składni zapytania oparte na metodzie: projekcji</span><span class="sxs-lookup"><span data-stu-id="ea0c6-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="ea0c6-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Select%2A> i <xref:System.Linq.Enumerable.SelectMany%2A> zapytania methodsto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="ea0c6-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methodsto query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="ea0c6-104">Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ea0c6-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ea0c6-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="ea0c6-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="ea0c6-106">Wybierz</span><span class="sxs-lookup"><span data-stu-id="ea0c6-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="ea0c6-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea0c6-107">Example</span></span>  
 <span data-ttu-id="ea0c6-108">W poniższym przykładzie użyto <xref:System.Linq.Queryable.Select%2A> metody do projektu `Product.Name` i `Product.ProductID` właściwości do sekwencji typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="ea0c6-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="ea0c6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea0c6-109">Example</span></span>  
 <span data-ttu-id="ea0c6-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> metodę, aby zwrócić sekwencję tylko nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="ea0c6-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="ea0c6-111">Operacja SelectMany</span><span class="sxs-lookup"><span data-stu-id="ea0c6-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="ea0c6-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea0c6-112">Example</span></span>  
 <span data-ttu-id="ea0c6-113">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.SelectMany%2A> metody, aby wybrać wszystkie porządkuje where `TotalDue` jest mniejsza niż 500,00.</span><span class="sxs-lookup"><span data-stu-id="ea0c6-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="ea0c6-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea0c6-114">Example</span></span>  
 <span data-ttu-id="ea0c6-115">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.SelectMany%2A> metody, aby wybrać wszystkie zlecenia, których kolejność została wprowadzona w 1 października 2002 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="ea0c6-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ea0c6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea0c6-116">See Also</span></span>  
 [<span data-ttu-id="ea0c6-117">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ea0c6-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
