---
title: Wyrażenia w składniku LINQ do zapytań jednostki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: dccf3ab1a619222cdf2db54673718eb103aee2fb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422272"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="3bd6e-102">Wyrażenia w składniku LINQ do zapytań jednostki</span><span class="sxs-lookup"><span data-stu-id="3bd6e-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="3bd6e-103">Wyrażenie jest fragment kodu, które może przyjąć jedną wartość, obiektu, metody lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3bd6e-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="3bd6e-104">Wyrażenia może zawierać wartości literału, wywołanie metody, operatora i argumentów lub prostą nazwą.</span><span class="sxs-lookup"><span data-stu-id="3bd6e-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="3bd6e-105">Proste nazwy mogą być nazwa zmiennej, składowej typu, parametru metody, przestrzeń nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="3bd6e-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="3bd6e-106">Wyrażenia można używać operatorów, które z kolei inne wyrażenia używane jako parametry lub metoda wywołuje metodę, której parametry są z kolei inne wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="3bd6e-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="3bd6e-107">W związku z tym w bardzo złożone wyrażenia może wynosić od prostego.</span><span class="sxs-lookup"><span data-stu-id="3bd6e-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="3bd6e-108">W [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, wyrażenia mogą zawierać czymkolwiek dozwolonym przez typów w ramach <xref:System.Linq.Expressions> przestrzeń nazw, w tym wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="3bd6e-108">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="3bd6e-109">Wyrażenia, które mogą być używane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania są podzbiorem wyrażeń, które mogą być używane do wykonywania zapytań [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3bd6e-109">The expressions that can be used in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="3bd6e-110">Wyrażenia, które są dostępne w ramach zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są ograniczone do operacji obsługiwanych przez `ObjectQuery<T>` i źródle danych.</span><span class="sxs-lookup"><span data-stu-id="3bd6e-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="3bd6e-111">W poniższym przykładzie porównanie w `Where` klauzuli to wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="3bd6e-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="3bd6e-112">Tworzy określonego języka, takiego jak C# `unchecked`, nie mają znaczenia [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3bd6e-112">Specific language constructs, such as C# `unchecked`, have no meaning in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3bd6e-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3bd6e-113">In This Section</span></span>  
 [<span data-ttu-id="3bd6e-114">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="3bd6e-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="3bd6e-115">Porównywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3bd6e-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="3bd6e-116">Porównania wartości Null</span><span class="sxs-lookup"><span data-stu-id="3bd6e-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="3bd6e-117">Wyrażenia inicjowania</span><span class="sxs-lookup"><span data-stu-id="3bd6e-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="3bd6e-118">Właściwości nawigacji</span><span class="sxs-lookup"><span data-stu-id="3bd6e-118">Navigation Properties</span></span>](https://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a><span data-ttu-id="3bd6e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bd6e-119">See Also</span></span>  
 [<span data-ttu-id="3bd6e-120">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3bd6e-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
