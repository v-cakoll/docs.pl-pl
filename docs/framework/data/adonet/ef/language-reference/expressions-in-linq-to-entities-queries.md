---
title: Wyrażenia w zapytaniach składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 0b77fc4c2a7c7df6efc9f4d8ce4001c39250ab94
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539900"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="5737f-102">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5737f-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="5737f-103">Wyrażenie jest fragment kodu, które może przyjąć jedną wartość, obiektu, metody lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5737f-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="5737f-104">Wyrażenia może zawierać wartości literału, wywołanie metody, operatora i argumentów lub prostą nazwą.</span><span class="sxs-lookup"><span data-stu-id="5737f-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="5737f-105">Proste nazwy mogą być nazwa zmiennej, składowej typu, parametru metody, przestrzeń nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="5737f-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="5737f-106">Wyrażenia można używać operatorów, które z kolei inne wyrażenia używane jako parametry lub metoda wywołuje metodę, której parametry są z kolei inne wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="5737f-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="5737f-107">W związku z tym w bardzo złożone wyrażenia może wynosić od prostego.</span><span class="sxs-lookup"><span data-stu-id="5737f-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="5737f-108">W zapytaniach składnika LINQ to Entities, wyrażeń może zawierać czymkolwiek dozwolonym przez typów w ramach <xref:System.Linq.Expressions> przestrzeń nazw, w tym wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="5737f-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="5737f-109">Wyrażenia, które może służyć w składniku LINQ do zapytań jednostki są podzbiorem wyrażeń, które mogą być używane do wykonywania zapytań [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5737f-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="5737f-110">Wyrażenia, które są dostępne w ramach zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są ograniczone do operacji obsługiwanych przez `ObjectQuery<T>` i źródle danych.</span><span class="sxs-lookup"><span data-stu-id="5737f-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="5737f-111">W poniższym przykładzie porównanie w `Where` klauzuli to wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="5737f-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  <span data-ttu-id="5737f-112">Tworzy określonego języka, takich jak C# `unchecked`, nie mają znaczenia w składniku LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="5737f-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5737f-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5737f-113">In This Section</span></span>  
 [<span data-ttu-id="5737f-114">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="5737f-114">Constant Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [<span data-ttu-id="5737f-115">Porównywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="5737f-115">Comparison Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [<span data-ttu-id="5737f-116">Porównania wartości Null</span><span class="sxs-lookup"><span data-stu-id="5737f-116">Null Comparisons</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [<span data-ttu-id="5737f-117">Wyrażenia inicjowania</span><span class="sxs-lookup"><span data-stu-id="5737f-117">Initialization Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [<span data-ttu-id="5737f-118">Relacje, właściwości nawigacji i kluczy obcych</span><span class="sxs-lookup"><span data-stu-id="5737f-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="5737f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5737f-119">See also</span></span>

- [<span data-ttu-id="5737f-120">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5737f-120">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
