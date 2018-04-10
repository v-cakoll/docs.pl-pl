---
title: '#Zdefiniuj (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae72a1b6c19421c51348a0d93691ba3fe29a191c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-reference"></a><span data-ttu-id="08d87-102">#define (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="08d87-102">#define (C# Reference)</span></span>
<span data-ttu-id="08d87-103">Możesz użyć `#define` do definiowania symbolu.</span><span class="sxs-lookup"><span data-stu-id="08d87-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="08d87-104">Jeśli używasz symbol jako wyrażenie, które są przekazywane do [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy, wyrażenie, które będą oceniać do `true`, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="08d87-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="08d87-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08d87-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08d87-106">`#define` Dyrektywy nie można użyć do zadeklarowania stałe wartości, co jest zazwyczaj wykonywane w C i C++.</span><span class="sxs-lookup"><span data-stu-id="08d87-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="08d87-107">Stałe języka C# najlepiej są definiowane jako statyczne elementy członkowskie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="08d87-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="08d87-108">Jeśli masz kilka takich stałe, należy rozważyć utworzenie oddzielnych klasę "Stałe", aby je przechowywać.</span><span class="sxs-lookup"><span data-stu-id="08d87-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="08d87-109">Symbole może służyć do określenia warunków dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="08d87-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="08d87-110">Możesz przetestować dla symbolu przy użyciu jednej [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) lub [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="08d87-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="08d87-111">Można również użyć `conditional` atrybutu przeprowadzić kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="08d87-111">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="08d87-112">Można zdefiniować symbol, ale nie można przypisać wartości do symbolu.</span><span class="sxs-lookup"><span data-stu-id="08d87-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="08d87-113">`#define` Dyrektywa musi występować w pliku, aby korzystać z żadnych instrukcji, które nie są również dyrektywy preprocesora.</span><span class="sxs-lookup"><span data-stu-id="08d87-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="08d87-114">Możesz również definiować symbol [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="08d87-114">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="08d87-115">Można nie zdefiniowany symbol [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="08d87-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="08d87-116">Symbol, który definiuje z `/define` lub `#define` nie powoduje konfliktu z zmienna o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="08d87-116">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="08d87-117">To, że nazwa zmiennej nie powinien zostać przekazany do dyrektywy preprocesora i symbol będzie możliwe tylko w dyrektywie preprocesora.</span><span class="sxs-lookup"><span data-stu-id="08d87-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="08d87-118">Zakres symbol, który został utworzony przy użyciu `#define` jest plikiem, w którym symbol został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="08d87-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="08d87-119">Jak pokazano na poniższym przykładzie, możesz umieścić `#define` dyrektywy w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="08d87-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 <span data-ttu-id="08d87-120">Na przykład sposobu usuń symbol zobacz [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="08d87-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d87-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08d87-121">See Also</span></span>  
 [<span data-ttu-id="08d87-122">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="08d87-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="08d87-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="08d87-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="08d87-124">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="08d87-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="08d87-125">Const</span><span class="sxs-lookup"><span data-stu-id="08d87-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="08d87-126">Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="08d87-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [<span data-ttu-id="08d87-127">#undef</span><span class="sxs-lookup"><span data-stu-id="08d87-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [<span data-ttu-id="08d87-128">#if</span><span class="sxs-lookup"><span data-stu-id="08d87-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
