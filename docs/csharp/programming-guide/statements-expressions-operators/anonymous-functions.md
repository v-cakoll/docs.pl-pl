---
title: Funkcje anonimowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 51a3c2e8399fdaae19ebe33f0d9ecc4bfd598799
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321850"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="45304-102">Funkcje anonimowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="45304-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="45304-103">Funkcja anonimowa jest instrukcji "wbudowany" lub wyrażenie, które mogą służyć wszędzie tam, gdzie oczekiwany jest typ delegata.</span><span class="sxs-lookup"><span data-stu-id="45304-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="45304-104">Można go zainicjować delegata o nazwie lub przekaż go zamiast typu delegata o nazwie jako parametru metody.</span><span class="sxs-lookup"><span data-stu-id="45304-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="45304-105">Istnieją dwa rodzaje funkcje anonimowe, które są omawiane w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="45304-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="45304-106">[Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="45304-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="45304-107">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="45304-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="45304-108">Wyrażenia lambda, może być powiązana do drzewa wyrażeń, a także do delegatów.</span><span class="sxs-lookup"><span data-stu-id="45304-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="45304-109">Rozwój delegatów w języku C#</span><span class="sxs-lookup"><span data-stu-id="45304-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="45304-110">W języku C# 1.0 utworzonego wystąpienia delegata przez jawne inicjowanie za pomocą metody, która została zdefiniowana w innym miejscu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="45304-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="45304-111">C# 2.0 wprowadzono pojęcie usługi metod anonimowych jako sposób zapisu bloków instrukcji nienazwane wbudowanego wykonanych w wywołaniu obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="45304-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="45304-112">C# 3.0 wprowadzono wyrażenia lambda, które są podobne do metod anonimowych, ale bardziej obszerne i zwięzłe.</span><span class="sxs-lookup"><span data-stu-id="45304-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="45304-113">Te dwie funkcje są nazywane *funkcje anonimowe*.</span><span class="sxs-lookup"><span data-stu-id="45304-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="45304-114">Ogólnie rzecz biorąc, aplikacje których docelowe wersji 3.5 lub nowszej [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] powinien użycie wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="45304-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="45304-115">W poniższym przykładzie pokazano ewolucję utworzenia delegata z C# w wersji 1.0 C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="45304-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="45304-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="45304-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45304-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45304-117">See Also</span></span>  
 [<span data-ttu-id="45304-118">Instrukcje, wyrażenia i operatory</span><span class="sxs-lookup"><span data-stu-id="45304-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [<span data-ttu-id="45304-119">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="45304-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="45304-120">Delegaci</span><span class="sxs-lookup"><span data-stu-id="45304-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="45304-121">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="45304-121">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
