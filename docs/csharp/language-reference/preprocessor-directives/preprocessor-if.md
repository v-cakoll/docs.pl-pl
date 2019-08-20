---
title: '#Jeśli dyrektywa preprocesora — C# odwołanie'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d0297094fbb8098b706cb8c6338fa123afc0753b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605689"
---
# <a name="if-c-reference"></a><span data-ttu-id="82a0d-102">#if (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="82a0d-102">#if (C# Reference)</span></span>

<span data-ttu-id="82a0d-103">Gdy C# kompilator napotyka `#if` dyrektywę, a następnie [#endif](preprocessor-endif.md) dyrektywie, kompiluje kod między dyrektywami tylko wtedy, gdy określony symbol jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="82a0d-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="82a0d-104">W przeciwieństwie do C++języka C i nie można przypisać wartości liczbowej do symbolu.</span><span class="sxs-lookup"><span data-stu-id="82a0d-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="82a0d-105">Instrukcja #if w C# jest wartością logiczną i tylko testuje, czy symbol został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="82a0d-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="82a0d-106">Przykład:</span><span class="sxs-lookup"><span data-stu-id="82a0d-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="82a0d-107">[==](../operators/equality-operators.md#equality-operator-) Można użyć operatorów (równość) i [! =](../operators/equality-operators.md#inequality-operator-) (nierówność) tylko do testowania [wartości true](../keywords/true-literal.md) lub [false](../keywords/false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="82a0d-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for [true](../keywords/true-literal.md) or [false](../keywords/false-literal.md).</span></span> <span data-ttu-id="82a0d-108">Prawda oznacza, że symbol jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="82a0d-108">True means the symbol is defined.</span></span> <span data-ttu-id="82a0d-109">Instrukcja `#if DEBUG` ma takie samo znaczenie jak `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="82a0d-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="82a0d-110">Można użyć operatorów [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (i), [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (lub), i [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="82a0d-110">You can use the operators [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (and), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or), and [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span></span> <span data-ttu-id="82a0d-111">(nie), aby sprawdzić, czy zdefiniowano wiele symboli.</span><span class="sxs-lookup"><span data-stu-id="82a0d-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="82a0d-112">Można również grupować symbole i operatory za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="82a0d-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="82a0d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82a0d-113">Remarks</span></span>

<span data-ttu-id="82a0d-114">`#if`wraz z [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)i [#undef](preprocessor-undef.md) umożliwiają uwzględnienie lub wykluczenie kodu na podstawie istnienia jednego lub kilku symboli.</span><span class="sxs-lookup"><span data-stu-id="82a0d-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="82a0d-115">Może to być przydatne podczas kompilowania kodu dla kompilacji debugowania lub kompilowania dla określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="82a0d-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="82a0d-116">Dyrektywa warunkowa rozpoczynająca się `#if` od dyrektywy musi być jawnie zakończona `#endif` dyrektywą.</span><span class="sxs-lookup"><span data-stu-id="82a0d-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="82a0d-117">`#define`umożliwia zdefiniowanie symbolu.</span><span class="sxs-lookup"><span data-stu-id="82a0d-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="82a0d-118">Używając symbolu jako wyrażenia przesłanego do `#if` dyrektywy, wyrażenie daje w `true`wyniku.</span><span class="sxs-lookup"><span data-stu-id="82a0d-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="82a0d-119">Można również zdefiniować symbol z opcją [-define](../compiler-options/define-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="82a0d-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="82a0d-120">Aby anulować definicję symbolu, użyj dyrektywy [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="82a0d-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="82a0d-121">Symbol zdefiniowany za pomocą `-define` lub with `#define` nie powoduje konfliktu ze zmienną o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="82a0d-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="82a0d-122">Oznacza to, że nazwa zmiennej nie powinna być przenoszona do dyrektywy preprocesora, a symbol może być oceniany tylko przez dyrektywę preprocesora.</span><span class="sxs-lookup"><span data-stu-id="82a0d-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="82a0d-123">Zakres symbolu utworzonego za pomocą `#define` to plik, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="82a0d-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="82a0d-124">System kompilacji jest również świadomy wstępnie zdefiniowanych symboli preprocesora, które reprezentują różne [Platformy docelowe](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="82a0d-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="82a0d-125">Są one przydatne podczas tworzenia aplikacji, które mogą być ukierunkowane na więcej niż jedną implementację lub wersję platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="82a0d-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="82a0d-126">Inne wstępnie zdefiniowane symbole obejmują stałe debugowania i śledzenia.</span><span class="sxs-lookup"><span data-stu-id="82a0d-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="82a0d-127">Można zastąpić wartości ustawione dla projektu przy użyciu `#define`.</span><span class="sxs-lookup"><span data-stu-id="82a0d-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="82a0d-128">Symbol debugowania, na przykład, jest automatycznie ustawiany w zależności od właściwości konfiguracji kompilacji ("Debugowanie" lub "wersja").</span><span class="sxs-lookup"><span data-stu-id="82a0d-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="82a0d-129">Przykłady</span><span class="sxs-lookup"><span data-stu-id="82a0d-129">Examples</span></span>

<span data-ttu-id="82a0d-130">W poniższym przykładzie pokazano, jak zdefiniować symbol elementu WebTest dla pliku, a następnie przetestować wartości symboli TEST i DEBUG.</span><span class="sxs-lookup"><span data-stu-id="82a0d-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="82a0d-131">Dane wyjściowe tego przykładu zależą od tego, czy projekt został skompilowany w trybie konfiguracji debugowania czy wydania.</span><span class="sxs-lookup"><span data-stu-id="82a0d-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

```csharp
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

<span data-ttu-id="82a0d-132">Poniższy przykład pokazuje, jak przeprowadzić test dla różnych platform docelowych, aby można było używać nowszych interfejsów API, gdy jest to możliwe:</span><span class="sxs-lookup"><span data-stu-id="82a0d-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a><span data-ttu-id="82a0d-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82a0d-133">See also</span></span>

- [<span data-ttu-id="82a0d-134">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="82a0d-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="82a0d-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="82a0d-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="82a0d-136">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="82a0d-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="82a0d-137">Instrukcje: Kompiluj warunkowo z użyciem śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="82a0d-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
