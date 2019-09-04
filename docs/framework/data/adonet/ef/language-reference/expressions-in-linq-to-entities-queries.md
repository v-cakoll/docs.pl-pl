---
title: Wyrażenia w zapytaniach składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250970"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="80ce8-102">Wyrażenia w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="80ce8-102">Expressions in LINQ to Entities Queries</span></span>
<span data-ttu-id="80ce8-103">Wyrażenie to fragment kodu, który może zostać oceniony jako pojedyncza wartość, obiekt, metoda lub przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="80ce8-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="80ce8-104">Wyrażenia mogą zawierać wartość literału, wywołanie metody, operator i jego operandy albo prostą nazwę.</span><span class="sxs-lookup"><span data-stu-id="80ce8-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="80ce8-105">Proste nazwy mogą być nazwą zmiennej, składową, parametrem metody, przestrzenią nazw lub typem.</span><span class="sxs-lookup"><span data-stu-id="80ce8-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="80ce8-106">Wyrażenia mogą używać operatorów, które z kolei używają innych wyrażeń jako parametrów lub wywołania metody, których parametry są z kolei inne wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="80ce8-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="80ce8-107">W związku z tym wyrażenia mogą być różne od prostych do bardzo złożonych.</span><span class="sxs-lookup"><span data-stu-id="80ce8-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="80ce8-108">W zapytaniach LINQ to Entities wyrażenia mogą zawierać dowolne elementy dozwolone przez typy w <xref:System.Linq.Expressions> przestrzeni nazw, w tym wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="80ce8-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="80ce8-109">Wyrażenia, które mogą być używane w zapytaniach LINQ to Entities są nadzbiorem wyrażeń, których można użyć do wykonywania [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]zapytań względem.</span><span class="sxs-lookup"><span data-stu-id="80ce8-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="80ce8-110">Wyrażenia, które są częścią zapytań, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są ograniczone do operacji obsługiwanych przez `ObjectQuery<T>` i bazowe źródło danych.</span><span class="sxs-lookup"><span data-stu-id="80ce8-110">Expressions that are part of queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="80ce8-111">W poniższym przykładzie porównanie w `Where` klauzuli jest wyrażeniem:</span><span class="sxs-lookup"><span data-stu-id="80ce8-111">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="80ce8-112">Określone konstrukcje języka, takie jak C# `unchecked`, nie mają znaczenia w LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="80ce8-112">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80ce8-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="80ce8-113">In This Section</span></span>  
 [<span data-ttu-id="80ce8-114">Wyrażenia stałe</span><span class="sxs-lookup"><span data-stu-id="80ce8-114">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="80ce8-115">Porównywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="80ce8-115">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="80ce8-116">Porównania wartości Null</span><span class="sxs-lookup"><span data-stu-id="80ce8-116">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="80ce8-117">Wyrażenia inicjowania</span><span class="sxs-lookup"><span data-stu-id="80ce8-117">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="80ce8-118">Relacje, właściwości nawigacji i klucze obce</span><span class="sxs-lookup"><span data-stu-id="80ce8-118">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="80ce8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80ce8-119">See also</span></span>

- [<span data-ttu-id="80ce8-120">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="80ce8-120">ADO.NET Entity Framework</span></span>](../index.md)
