---
title: Funkcje anonimowe C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: cfb0190ee263e65e8130a8925f76357a382eafa3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712003"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="2a1b9-102">Funkcje anonimoweC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="2a1b9-102">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="2a1b9-103">Funkcja anonimowa jest instrukcją "inline" lub wyrażeniem, które może być używane wszędzie tam, gdzie oczekiwany jest typ delegata.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="2a1b9-104">Można go użyć do zainicjowania nazwanego delegata lub przekazać go zamiast nazwanego typu delegata jako parametru metody.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="2a1b9-105">Możesz użyć [wyrażenia lambda](lambda-expressions.md) lub [metody anonimowej](../../language-reference/operators/delegate-operator.md) , aby utworzyć funkcję anonimową.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-105">You can use a [lambda expression](lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="2a1b9-106">Zalecamy używanie wyrażeń lambda, ponieważ zapewniają one bardziej zwięzły i jednoznaczny sposób pisania kodu śródwierszowego.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-106">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="2a1b9-107">W przeciwieństwie do metod anonimowych niektóre typy wyrażeń lambda można przekonwertować na typy drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-107">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="2a1b9-108">Ewolucja delegatów w języku C\#</span><span class="sxs-lookup"><span data-stu-id="2a1b9-108">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="2a1b9-109">W C# 1,0, utworzono wystąpienie delegata, jawnie inicjując go za pomocą metody, która została zdefiniowana w innym miejscu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-109">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="2a1b9-110">C#2,0 wprowadza koncepcję metod anonimowych jako sposób pisania nienazwanych bloków instrukcji wbudowanych, które mogą być wykonywane w wywołaniu delegata.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-110">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="2a1b9-111">C#3,0 wprowadzono wyrażenia lambda, które są podobne w koncepcji metod anonimowych, ale bardziej wyraźne i zwięzłe.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-111">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="2a1b9-112">Te dwie funkcje są określane zbiorczo jako *funkcje anonimowe*.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-112">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="2a1b9-113">Ogólnie rzecz biorąc, aplikacje docelowe w wersji 3,5 i nowszej .NET Framework powinny używać wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="2a1b9-113">In general, applications that target version 3.5 and later of the .NET Framework should use lambda expressions.</span></span>  
  
 <span data-ttu-id="2a1b9-114">Poniższy przykład ilustruje ewolucję tworzenia delegatów z C# 1,0 do C# 3,0:</span><span class="sxs-lookup"><span data-stu-id="2a1b9-114">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2a1b9-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2a1b9-115">C# language specification</span></span>

<span data-ttu-id="2a1b9-116">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2a1b9-116">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2a1b9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a1b9-117">See also</span></span>

- [<span data-ttu-id="2a1b9-118">Instrukcje, wyrażenia i operatory</span><span class="sxs-lookup"><span data-stu-id="2a1b9-118">Statements, Expressions, and Operators</span></span>](./index.md)
- [<span data-ttu-id="2a1b9-119">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="2a1b9-119">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="2a1b9-120">Delegaci</span><span class="sxs-lookup"><span data-stu-id="2a1b9-120">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="2a1b9-121">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="2a1b9-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
