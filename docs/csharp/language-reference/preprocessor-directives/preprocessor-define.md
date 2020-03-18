---
title: '#define - Odwołanie do języka C#'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: c08d6f42c11184a4d14aa6712f9f0f8706a72cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173435"
---
# <a name="define-c-reference"></a><span data-ttu-id="12790-102">#define (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="12790-102">#define (C# Reference)</span></span>
<span data-ttu-id="12790-103">Symbol `#define` służy do definiowania symbolu.</span><span class="sxs-lookup"><span data-stu-id="12790-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="12790-104">Użycie symbolu jako wyrażenia przekazanego do [#if](./preprocessor-if.md) dyrektywy, wyrażenie `true`będzie oceniane , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="12790-104">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="12790-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12790-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12790-106">Dyrektywy `#define` nie można użyć do deklarowania stałych wartości, jak zwykle odbywa się w C i C++.</span><span class="sxs-lookup"><span data-stu-id="12790-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="12790-107">Stałe w języku C# są najlepiej zdefiniowane jako statyczne elementy członkowskie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="12790-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="12790-108">Jeśli masz kilka takich stałych, rozważ utworzenie oddzielnej klasy "Stałe", aby je przytrzymać.</span><span class="sxs-lookup"><span data-stu-id="12790-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="12790-109">Symbole mogą służyć do określania warunków kompilacji.</span><span class="sxs-lookup"><span data-stu-id="12790-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="12790-110">Możesz przetestować symbol z [#if](./preprocessor-if.md) lub [#elif](./preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="12790-110">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="12790-111">Można również użyć <xref:System.Diagnostics.ConditionalAttribute> do wykonania kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="12790-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="12790-112">Można zdefiniować symbol, ale nie można przypisać wartości do symbolu.</span><span class="sxs-lookup"><span data-stu-id="12790-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="12790-113">Dyrektywa `#define` musi pojawić się w pliku przed użyciem żadnych instrukcji, które nie są również dyrektywy preprocesora.</span><span class="sxs-lookup"><span data-stu-id="12790-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="12790-114">Można również zdefiniować symbol z opcją [-define](../compiler-options/define-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="12790-114">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="12790-115">Można cofnąć definicję symbolu za pomocą [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="12790-115">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="12790-116">Symbol, który można `-define` zdefiniować `#define` z lub z nie kolidów ze zmienną o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="12790-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="12790-117">Oznacza to, że nazwa zmiennej nie powinny być przekazywane do dyrektywy preprocesora i symbol może być oceniane tylko przez dyrektywy preprocesora.</span><span class="sxs-lookup"><span data-stu-id="12790-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="12790-118">Zakres symbolu, który został utworzony `#define` przy użyciu jest plik, w którym symbol został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="12790-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="12790-119">Jak pokazano w poniższym `#define` przykładzie, należy umieścić dyrektywy w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="12790-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="12790-120">Aby zapoznać się z przykładem jak cofnąć definicję symbolu, zobacz [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="12790-120">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12790-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12790-121">See also</span></span>

- [<span data-ttu-id="12790-122">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="12790-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="12790-123">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="12790-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="12790-124">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="12790-124">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="12790-125">const</span><span class="sxs-lookup"><span data-stu-id="12790-125">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="12790-126">Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="12790-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="12790-127">#undef</span><span class="sxs-lookup"><span data-stu-id="12790-127">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="12790-128">#if</span><span class="sxs-lookup"><span data-stu-id="12790-128">#if</span></span>](./preprocessor-if.md)
