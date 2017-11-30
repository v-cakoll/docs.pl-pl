---
title: "#<a name=\"if-c-reference\"></a>Jeśli (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a><span data-ttu-id="109f2-102">#if (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="109f2-102">#if (C# Reference)</span></span>
<span data-ttu-id="109f2-103">Gdy wystąpi kompilatora C# `#if` dyrektywy, a następnie po pewnym czasie przez [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) dyrektywy, go zostanie skompilowany kod między dyrektywami tylko wtedy, gdy zdefiniowano określony symbol.</span><span class="sxs-lookup"><span data-stu-id="109f2-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) directive, it will compile the code between the directives only if the specified symbol is defined.</span></span>  <span data-ttu-id="109f2-104">W przeciwieństwie do C i C++ nie można przypisać wartości numerycznej symbolu; wykonywanie instrukcji #if w języku C# jest wartość logiczna i tylko sprawdzenie, czy symbol został zdefiniowany lub nie.</span><span class="sxs-lookup"><span data-stu-id="109f2-104">Unlike C and C++, you cannot assign a numeric value to a symbol; the #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="109f2-105">Na przykład</span><span class="sxs-lookup"><span data-stu-id="109f2-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 <span data-ttu-id="109f2-106">Można używać operatorów [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) (równości) [! =](../../../csharp/language-reference/operators/not-equal-operator.md) (nierówność) tylko do testowania [true](../../../csharp/language-reference/keywords/true.md) lub [false](../../../csharp/language-reference/keywords/false.md) .</span><span class="sxs-lookup"><span data-stu-id="109f2-106">You can use the operators [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (equality), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inequality) only to test for [true](../../../csharp/language-reference/keywords/true.md) or [false](../../../csharp/language-reference/keywords/false.md) .</span></span> <span data-ttu-id="109f2-107">PRAWDA oznacza, że jest zdefiniowany symbol.</span><span class="sxs-lookup"><span data-stu-id="109f2-107">True means the symbol is defined.</span></span> <span data-ttu-id="109f2-108">Instrukcja `#if DEBUG` ma takie samo znaczenie jak `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="109f2-108">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="109f2-109">Można używać operatorów [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) (a), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (lub) i [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="109f2-109">You can use the operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (and), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or), and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="109f2-110">(nie) do oceny, czy zdefiniowano wiele symboli.</span><span class="sxs-lookup"><span data-stu-id="109f2-110">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="109f2-111">Można także grupować symbole i operatory w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="109f2-111">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="109f2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="109f2-112">Remarks</span></span>  
 <span data-ttu-id="109f2-113">`#if`, wraz z [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), i [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) dyrektywy, umożliwia Dołącz lub Wyklucz kodu opartego na istnienie jednego lub więcej symboli.</span><span class="sxs-lookup"><span data-stu-id="109f2-113">`#if`, along with the [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), and [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="109f2-114">Może to być przydatne podczas kompilowania kodu dla kompilacji debugowania lub w przypadku kompilowania kodu dla określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="109f2-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>  
  
 <span data-ttu-id="109f2-115">Warunkowe początku dyrektywy z `#if` dyrektywa musi być jawnie zakończona z `#endif` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="109f2-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>  
  
 <span data-ttu-id="109f2-116">`#define`pozwala zdefiniować symbol, taki sposób, że za pomocą symbolu jako wyrażenie przekazane do `#if` dyrektywy, wyrażenie, które będą oceniać do `true`.</span><span class="sxs-lookup"><span data-stu-id="109f2-116">`#define` lets you define a symbol, such that, by using the symbol as the expression passed to the `#if` directive, the expression will evaluate to `true`.</span></span>  
  
 <span data-ttu-id="109f2-117">Możesz również definiować symbol [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="109f2-117">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="109f2-118">Można nie zdefiniowany symbol [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="109f2-118">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="109f2-119">Symbol, który definiuje z `/define` lub `#define` nie powoduje konfliktu z zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="109f2-119">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="109f2-120">To, że nazwa zmiennej nie powinien zostać przekazany do dyrektywy preprocesora i symbol będzie możliwe tylko w dyrektywie preprocesora.</span><span class="sxs-lookup"><span data-stu-id="109f2-120">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="109f2-121">Zakres symbol utworzone za pomocą `#define` jest plikiem, w którym została zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="109f2-121">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="109f2-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="109f2-122">Example</span></span>  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
 <span data-ttu-id="109f2-123">**DEBUGOWANIE i test są zdefiniowane**</span><span class="sxs-lookup"><span data-stu-id="109f2-123">**DEBUG and MYTEST are defined**</span></span>  
## <a name="see-also"></a><span data-ttu-id="109f2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="109f2-124">See Also</span></span>  
 [<span data-ttu-id="109f2-125">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="109f2-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="109f2-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="109f2-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="109f2-127">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="109f2-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
