---
title: '#Zdefiniuj - C# odwołania'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 7be2a2d00e96b4b734e1a68f6dc63180bcbe5e82
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244976"
---
# <a name="define-c-reference"></a><span data-ttu-id="ddd36-102">#define (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ddd36-102">#define (C# Reference)</span></span>
<span data-ttu-id="ddd36-103">Dyrektywa `#define` umożliwia zdefiniowanie symbolu.</span><span class="sxs-lookup"><span data-stu-id="ddd36-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="ddd36-104">Jeżeli używasz symbolu jako wyrażenia, które jest przekazywane do dyrektywy [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), wyrażenie zostanie oszacowane jako `true`, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ddd36-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="ddd36-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddd36-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddd36-106">Dyrektywy `#define` nie można użyć do deklarowania wartości stałych, co jest zazwyczaj wykonywane w językach C i C++.</span><span class="sxs-lookup"><span data-stu-id="ddd36-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="ddd36-107">Stałe języka C# najlepiej definiować jako statyczne elementy członkowskie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ddd36-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="ddd36-108">Jeśli masz kilka takich stałych, rozważ utworzenie oddzielnej klasy, aby je przechowywać.</span><span class="sxs-lookup"><span data-stu-id="ddd36-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="ddd36-109">Symbole mogą służyć do określenia warunków dla kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ddd36-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="ddd36-110">Można przetestować symbol przy użyciu dyrektywy [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) lub [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="ddd36-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="ddd36-111">Można również użyć <xref:System.Diagnostics.ConditionalAttribute> Aby przeprowadzić warunkową kompilację.</span><span class="sxs-lookup"><span data-stu-id="ddd36-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="ddd36-112">Symbol można zdefiniować, ale nie można do niego przypisać wartości.</span><span class="sxs-lookup"><span data-stu-id="ddd36-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="ddd36-113">Dyrektywa `#define` musi występować w pliku, zanim będzie można wykonać instrukcje, które nie są również dyrektywami preprocesora.</span><span class="sxs-lookup"><span data-stu-id="ddd36-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="ddd36-114">Można również zdefiniować symbol za pomocą [— Zdefiniuj](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ddd36-114">You can also define a symbol with the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="ddd36-115">Aby anulować definicję symbolu, użyj dyrektywy [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="ddd36-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="ddd36-116">Symbol zdefiniowany z użyciem opcji `-define` lub `#define` nie powoduje konfliktu ze zmienną o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ddd36-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="ddd36-117">Oznacza to, że nazwa zmiennej nie powinna być przekazywana do dyrektywy preprocesora i symbol będzie można oszacować tylko przy użyciu tej dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="ddd36-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="ddd36-118">Zakresem symbolu utworzonego przy użyciu dyrektywy `#define` jest plik, w którym został zdefiniowany symbol.</span><span class="sxs-lookup"><span data-stu-id="ddd36-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="ddd36-119">Jak pokazano na poniższym przykładzie, musisz umieścić dyrektywy `#define` w górnej części pliku. </span><span class="sxs-lookup"><span data-stu-id="ddd36-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="ddd36-120">Aby zapoznać się z przykładem anulowania definicji symbolu, zobacz [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="ddd36-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd36-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddd36-121">See Also</span></span>

- [<span data-ttu-id="ddd36-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ddd36-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ddd36-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ddd36-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ddd36-124">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="ddd36-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="ddd36-125">const</span><span class="sxs-lookup"><span data-stu-id="ddd36-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
- [<span data-ttu-id="ddd36-126">Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="ddd36-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
- [<span data-ttu-id="ddd36-127">#undef</span><span class="sxs-lookup"><span data-stu-id="ddd36-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
- [<span data-ttu-id="ddd36-128">#if</span><span class="sxs-lookup"><span data-stu-id="ddd36-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
