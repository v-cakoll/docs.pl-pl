---
title: "Przykłady składni zapytania oparte na metodzie: konwersja"
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
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8c61d84d4ef03f7c62cc055ec125514df6fe9d53
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="e744f-102">Przykłady składni zapytania oparte na metodzie: konwersja</span><span class="sxs-lookup"><span data-stu-id="e744f-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="e744f-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> i <xref:System.Linq.Enumerable.ToList%2A> metod do badania [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="e744f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="e744f-104">Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e744f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e744f-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="e744f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="e744f-106">toArray</span><span class="sxs-lookup"><span data-stu-id="e744f-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="e744f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e744f-107">Example</span></span>  
 <span data-ttu-id="e744f-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.ToArray%2A> metodę, aby natychmiast ocenić sekwencji do tablicy.</span><span class="sxs-lookup"><span data-stu-id="e744f-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="e744f-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="e744f-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="e744f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e744f-110">Example</span></span>  
 <span data-ttu-id="e744f-111">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.ToDictionary%2A> metodę, aby natychmiast ocenę sekwencji i powiązane wyrażenia klucza do słownika.</span><span class="sxs-lookup"><span data-stu-id="e744f-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="e744f-112">tolist —</span><span class="sxs-lookup"><span data-stu-id="e744f-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="e744f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="e744f-113">Example</span></span>  
 <span data-ttu-id="e744f-114">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.ToList%2A> metodę, aby natychmiast ocenić sekwencji do <xref:System.Collections.Generic.List%601>, gdzie `T` jest typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="e744f-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="e744f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e744f-115">See Also</span></span>  
 [<span data-ttu-id="e744f-116">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e744f-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
