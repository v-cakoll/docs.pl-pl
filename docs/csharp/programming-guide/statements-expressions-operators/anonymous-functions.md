---
title: Funkcje anonimowe - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 05098d1f26526c60656cca2255a2f93922c025da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613730"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="af3c1-102">Funkcje anonimowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="af3c1-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="af3c1-103">Funkcja anonimowa jest "inline" instrukcję lub wyrażenie, który może służyć wszędzie tam, gdzie oczekiwany jest typ delegatu.</span><span class="sxs-lookup"><span data-stu-id="af3c1-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="af3c1-104">Służy on do zainicjowania delegat nazwany lub przekazać je zamiast typu delegat nazwany, jako parametr metody.</span><span class="sxs-lookup"><span data-stu-id="af3c1-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="af3c1-105">Istnieją dwa rodzaje funkcje anonimowe, które są omawiane w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="af3c1-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="af3c1-106">[Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="af3c1-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="af3c1-107">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="af3c1-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="af3c1-108">Wyrażenia lambda może być powiązana, drzew wyrażeń, a także delegatów.</span><span class="sxs-lookup"><span data-stu-id="af3c1-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="af3c1-109">Rozwój delegatów w języku C#</span><span class="sxs-lookup"><span data-stu-id="af3c1-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="af3c1-110">W języku C# w wersji 1.0 utworzono wystąpienie delegata przez jawne inicjowanie przy użyciu metody, która została zdefiniowana w innym miejscu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="af3c1-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="af3c1-111">C# w wersji 2.0 wprowadzono koncepcję metod anonimowych, jako sposób pisania bloków instrukcji nienazwane wbudowanych, które mogą być wykonywane w wywołaniu delegata.</span><span class="sxs-lookup"><span data-stu-id="af3c1-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="af3c1-112">C# 3.0 wprowadzono wyrażenia lambda, które są podobne do metod anonimowych, ale bardziej ekspresyjnego i zwięzłe.</span><span class="sxs-lookup"><span data-stu-id="af3c1-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="af3c1-113">Te dwie funkcje są określane zbiorczo jako *funkcjami anonimowymi*.</span><span class="sxs-lookup"><span data-stu-id="af3c1-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="af3c1-114">Ogólnie rzecz biorąc, aplikacje przeznaczone na platformę w wersji 3.5 lub nowszy z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] należy używać wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="af3c1-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="af3c1-115">W poniższym przykładzie pokazano ewolucji tworzenia delegata z C# w wersji 1.0 do języka C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="af3c1-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="af3c1-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="af3c1-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af3c1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af3c1-117">See also</span></span>

- [<span data-ttu-id="af3c1-118">Instrukcje, wyrażenia i operatory</span><span class="sxs-lookup"><span data-stu-id="af3c1-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [<span data-ttu-id="af3c1-119">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="af3c1-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="af3c1-120">Delegaty</span><span class="sxs-lookup"><span data-stu-id="af3c1-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="af3c1-121">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="af3c1-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
