---
title: "Funkcje anonimowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 888743bb1c49df123b57b4d09e0251dbe1e049d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="6cbf8-102">Funkcje anonimowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6cbf8-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="6cbf8-103">Funkcja anonimowa jest instrukcji "wbudowany" lub wyrażenie, które mogą służyć wszędzie tam, gdzie oczekiwany jest typ delegata.</span><span class="sxs-lookup"><span data-stu-id="6cbf8-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="6cbf8-104">Można go zainicjować delegata o nazwie lub przekaż go zamiast typu delegata o nazwie jako parametru metody.</span><span class="sxs-lookup"><span data-stu-id="6cbf8-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="6cbf8-105">Istnieją dwa rodzaje funkcje anonimowe, które są omawiane w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="6cbf8-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="6cbf8-106">[Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6cbf8-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="6cbf8-107">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="6cbf8-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="6cbf8-108">Wyrażenia lambda, może być powiązana do drzewa wyrażeń, a także do delegatów.</span><span class="sxs-lookup"><span data-stu-id="6cbf8-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="6cbf8-109">Rozwój delegatów w języku C#</span><span class="sxs-lookup"><span data-stu-id="6cbf8-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="6cbf8-110">W języku C# 1.0 utworzonego wystąpienia delegata przez jawne inicjowanie za pomocą metody, która została zdefiniowana w innym miejscu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6cbf8-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="6cbf8-111">C# 2.0 wprowadzono pojęcie usługi metod anonimowych jako sposób zapisu bloków instrukcji nienazwane wbudowanego wykonanych w wywołaniu obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="6cbf8-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="6cbf8-112">C# 3.0 wprowadzono wyrażenia lambda, które są podobne do metod anonimowych, ale bardziej obszerne i zwięzłe.</span><span class="sxs-lookup"><span data-stu-id="6cbf8-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="6cbf8-113">Te dwie funkcje są nazywane *funkcje anonimowe*.</span><span class="sxs-lookup"><span data-stu-id="6cbf8-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="6cbf8-114">Ogólnie rzecz biorąc, aplikacje których docelowe wersji 3.5 lub nowszej [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] powinien użycie wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="6cbf8-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="6cbf8-115">W poniższym przykładzie pokazano ewolucję utworzenia delegata z C# w wersji 1.0 C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="6cbf8-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6cbf8-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6cbf8-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6cbf8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cbf8-117">See Also</span></span>  
 [<span data-ttu-id="6cbf8-118">Instrukcje, wyrażenia i operatory</span><span class="sxs-lookup"><span data-stu-id="6cbf8-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [<span data-ttu-id="6cbf8-119">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="6cbf8-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="6cbf8-120">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="6cbf8-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="6cbf8-121">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6cbf8-121">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
