---
title: "Przykłady składni zapytania oparte na metodzie: partycjonowanie"
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
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f4db203ece2431bd19cc05879dc7d3db88159dec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="1b618-102">Przykłady składni zapytania oparte na metodzie: partycjonowanie</span><span class="sxs-lookup"><span data-stu-id="1b618-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="1b618-103">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Skip%2A>, i <xref:System.Linq.Enumerable.Take%2A> metod do badania [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="1b618-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="1b618-104">Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1b618-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1b618-105">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1b618-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="1b618-106">Skip</span><span class="sxs-lookup"><span data-stu-id="1b618-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="1b618-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b618-107">Example</span></span>  
 <span data-ttu-id="1b618-108">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Skip%2A> metodę, aby pobrać wszystkie, ale pierwsze pięć kontaktów, skontaktuj się z tabeli.</span><span class="sxs-lookup"><span data-stu-id="1b618-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="1b618-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b618-109">Example</span></span>  
 <span data-ttu-id="1b618-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Skip%2A> metodę, aby pobrać wszystkie, ale najpierw dwa adresy w Seattle.</span><span class="sxs-lookup"><span data-stu-id="1b618-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="1b618-111">Take</span><span class="sxs-lookup"><span data-stu-id="1b618-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="1b618-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b618-112">Example</span></span>  
 <span data-ttu-id="1b618-113">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Take%2A> metodę, aby pobrać tylko pierwsze pięć kontakty z tabeli Kontakt.</span><span class="sxs-lookup"><span data-stu-id="1b618-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="1b618-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b618-114">Example</span></span>  
 <span data-ttu-id="1b618-115">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Take%2A> metody można uzyskać od pierwszych trzech adresów w Seattle.</span><span class="sxs-lookup"><span data-stu-id="1b618-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="1b618-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b618-116">See Also</span></span>  
 [<span data-ttu-id="1b618-117">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1b618-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
