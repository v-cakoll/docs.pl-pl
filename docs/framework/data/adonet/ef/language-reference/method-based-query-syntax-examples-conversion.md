---
title: 'Przykłady składni zapytania oparte na metodzie: Konwersja'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: a78588cb4bd09f8a8a8ce8ed4a60dd45fce1d386
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397480"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="3070e-102">Przykłady składni zapytania oparte na metodzie: Konwersja</span><span class="sxs-lookup"><span data-stu-id="3070e-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="3070e-103">W przykładach w <xref:System.Linq.Enumerable.ToArray%2A>tym temacie pokazano, jak użyć metod, <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToDictionary%2A> i zbadać [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) przy użyciu składni zapytania opartego na metodzie.</span><span class="sxs-lookup"><span data-stu-id="3070e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="3070e-104">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3070e-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3070e-105">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="3070e-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="3070e-106">ToArray —</span><span class="sxs-lookup"><span data-stu-id="3070e-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="3070e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3070e-107">Example</span></span>  
 <span data-ttu-id="3070e-108">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.ToArray%2A> metodę, aby natychmiast oszacować sekwencję do tablicy.</span><span class="sxs-lookup"><span data-stu-id="3070e-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="3070e-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="3070e-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="3070e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="3070e-110">Example</span></span>  
 <span data-ttu-id="3070e-111">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.ToDictionary%2A> metodę, aby natychmiast oszacować sekwencję i wyrażenie powiązanego klucza do słownika.</span><span class="sxs-lookup"><span data-stu-id="3070e-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="3070e-112">ToList —</span><span class="sxs-lookup"><span data-stu-id="3070e-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="3070e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3070e-113">Example</span></span>  
 <span data-ttu-id="3070e-114">Poniższy przykład używa <xref:System.Linq.Enumerable.ToList%2A> metody do natychmiastowego oszacowania sekwencji <xref:System.Collections.Generic.List%601>do, gdzie `T` jest typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="3070e-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="3070e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3070e-115">See also</span></span>

- [<span data-ttu-id="3070e-116">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="3070e-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
