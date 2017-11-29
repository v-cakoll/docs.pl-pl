---
title: "Wyrażenia w składniku LINQ to Entities zapytań"
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
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4698921fbffa23f4a9fceadc84cfe24e19b2bdd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="89eca-102">Wyrażenia w składniku LINQ to Entities zapytań</span><span class="sxs-lookup"><span data-stu-id="89eca-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="89eca-103">Wyrażenie jest fragment kodu, które może przyjąć pojedynczą wartość, obiekt, metodę lub przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="89eca-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="89eca-104">Wyrażenia może zawierać wartość literału, wywołanie metody, operator i argumentów lub prostą nazwą.</span><span class="sxs-lookup"><span data-stu-id="89eca-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="89eca-105">Proste nazwy mogą być nazwę zmiennej, członka typu, parametru metody, przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="89eca-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="89eca-106">Wyrażenia można używać operatorów, które z kolei inne wyrażenia używane jako parametry lub wywołania metody, której parametry są z kolei inne wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="89eca-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="89eca-107">W związku z tym wyrażenia mogą należeć do zakresu od prostego do bardzo złożonych.</span><span class="sxs-lookup"><span data-stu-id="89eca-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="89eca-108">W [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, wyrażenia mogą zawierać dowolne elementy dozwolone przez typy w <xref:System.Linq.Expressions> przestrzeni nazw, w tym wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="89eca-108">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="89eca-109">Wyrażeń, które mogą być używane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania są podzbiorem wyrażeń, które mogą być używane w zapytaniu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89eca-109">The expressions that can be used in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="89eca-110">Wyrażeń, które są częścią zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są ograniczone do operacji obsługiwanych przez `ObjectQuery<T>` i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="89eca-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="89eca-111">W poniższym przykładzie porównania w `Where` klauzula jest wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="89eca-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="89eca-112">Tworzy określonego języka, takich jak C# `unchecked`, mają znaczenia w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89eca-112">Specific language constructs, such as C# `unchecked`, have no meaning in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89eca-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="89eca-113">In This Section</span></span>  
 [<span data-ttu-id="89eca-114">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="89eca-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="89eca-115">Porównywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="89eca-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="89eca-116">Porównania wartości null</span><span class="sxs-lookup"><span data-stu-id="89eca-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="89eca-117">Wyrażenia inicjowania</span><span class="sxs-lookup"><span data-stu-id="89eca-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="89eca-118">Właściwości nawigacji</span><span class="sxs-lookup"><span data-stu-id="89eca-118">Navigation Properties</span></span>](http://msdn.microsoft.com/en-us/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a><span data-ttu-id="89eca-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89eca-119">See Also</span></span>  
 [<span data-ttu-id="89eca-120">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="89eca-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
