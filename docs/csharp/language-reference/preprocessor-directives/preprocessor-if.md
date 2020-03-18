---
title: '#jeśli preprocesor dyrektywy - C# Reference'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899854"
---
# <a name="if-c-reference"></a><span data-ttu-id="cde78-102">#if (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="cde78-102">#if (C# reference)</span></span>

<span data-ttu-id="cde78-103">Gdy kompilator C# `#if` napotka dyrektywy, a następnie ostatecznie [#endif](preprocessor-endif.md) dyrektywy, kompiluje kod między dyrektywami tylko wtedy, gdy określony symbol jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="cde78-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="cde78-104">W przeciwieństwie do C i C++ nie można przypisać wartości liczbowej do symbolu.</span><span class="sxs-lookup"><span data-stu-id="cde78-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="cde78-105">Instrukcja `#if` w języku C# jest logiczna i sprawdza tylko, czy symbol został zdefiniowany, czy nie.</span><span class="sxs-lookup"><span data-stu-id="cde78-105">The `#if` statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="cde78-106">Przykład:</span><span class="sxs-lookup"><span data-stu-id="cde78-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="cde78-107">[==](../operators/equality-operators.md#equality-operator-) Operatory (równość) i [!=](../operators/equality-operators.md#inequality-operator-) (nierówności) można używać tylko `false`do testowania wartości `true` [bool](../builtin-types/bool.md) lub .</span><span class="sxs-lookup"><span data-stu-id="cde78-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for the [bool](../builtin-types/bool.md) values `true` or `false`.</span></span> <span data-ttu-id="cde78-108">`true`oznacza, że symbol jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="cde78-108">`true` means the symbol is defined.</span></span> <span data-ttu-id="cde78-109">Instrukcja `#if DEBUG` ma takie `#if (DEBUG == true)`samo znaczenie jak .</span><span class="sxs-lookup"><span data-stu-id="cde78-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="cde78-110">Możesz użyć [&&  (i)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;  (lub)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-)i [! (nie)](../operators/boolean-logical-operators.md#logical-negation-operator-) operatory, aby ocenić, czy zdefiniowano wiele symboli.</span><span class="sxs-lookup"><span data-stu-id="cde78-110">You can use the [&& (and)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124; (or)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), and [! (not)](../operators/boolean-logical-operators.md#logical-negation-operator-) operators to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="cde78-111">Można również grupować symbole i operatory z nawiasami.</span><span class="sxs-lookup"><span data-stu-id="cde78-111">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="cde78-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cde78-112">Remarks</span></span>

<span data-ttu-id="cde78-113">`#if`, wraz z [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)i [#undef](preprocessor-undef.md) dyrektywy, pozwala dołączyć lub wykluczyć kod na podstawie istnienia jednego lub więcej symboli.</span><span class="sxs-lookup"><span data-stu-id="cde78-113">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="cde78-114">Może to być przydatne podczas kompilowania kodu dla kompilacji debugowania lub podczas kompilowania dla określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cde78-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="cde78-115">Dyrektywa warunkowa `#if` rozpoczynająca się od dyrektywy `#endif` musi zostać wyraźnie zakończona dyrektywą.</span><span class="sxs-lookup"><span data-stu-id="cde78-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="cde78-116">`#define`umożliwia zdefiniowanie symbolu.</span><span class="sxs-lookup"><span data-stu-id="cde78-116">`#define` lets you define a symbol.</span></span> <span data-ttu-id="cde78-117">Następnie przy użyciu symbolu jako `#if` wyrażenie przekazane do dyrektywy, wyrażenie oblicza . `true`</span><span class="sxs-lookup"><span data-stu-id="cde78-117">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="cde78-118">Można również zdefiniować symbol z opcją [-define](../compiler-options/define-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="cde78-118">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="cde78-119">Można cofnąć definicję symbolu za pomocą [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="cde78-119">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="cde78-120">Symbol, który można `-define` zdefiniować `#define` z lub z nie powoduje konfliktu ze zmienną o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="cde78-120">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="cde78-121">Oznacza to, że nazwa zmiennej nie powinny być przekazywane do dyrektywy preprocesora, a symbol może być oceniane tylko przez dyrektywy preprocesora.</span><span class="sxs-lookup"><span data-stu-id="cde78-121">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="cde78-122">Zakres symbolu utworzonego `#define` za pomocą jest plik, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="cde78-122">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="cde78-123">System kompilacji jest również świadomy wstępnie zdefiniowanych symboli preprocesora reprezentujących różne struktury docelowe w [projektach](../../../standard/frameworks.md) w stylu SDK.</span><span class="sxs-lookup"><span data-stu-id="cde78-123">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md) in SDK-style projects.</span></span> <span data-ttu-id="cde78-124">Są one przydatne podczas tworzenia aplikacji, które mogą być przeznaczone dla więcej niż jednej implementacji lub wersji .NET.</span><span class="sxs-lookup"><span data-stu-id="cde78-124">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> <span data-ttu-id="cde78-125">W przypadku tradycyjnych projektów .NET Framework należy ręcznie skonfigurować symbole kompilacji warunkowej dla różnych struktur docelowych w programie Visual Studio za pośrednictwem stron właściwości projektu.</span><span class="sxs-lookup"><span data-stu-id="cde78-125">For traditional .NET Framework projects, you have to manually configure the conditional compilation symbols for the different target frameworks in Visual Studio via the project's properties pages.</span></span>

<span data-ttu-id="cde78-126">Inne wstępnie zdefiniowane symbole obejmują stałe DEBUG i TRACE.</span><span class="sxs-lookup"><span data-stu-id="cde78-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="cde78-127">Można zastąpić wartości ustawione dla projektu `#define`za pomocą .</span><span class="sxs-lookup"><span data-stu-id="cde78-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="cde78-128">Na przykład symbol DEBUG jest ustawiany automatycznie w zależności od właściwości konfiguracji kompilacji ("Debug" lub "Release").</span><span class="sxs-lookup"><span data-stu-id="cde78-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="cde78-129">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cde78-129">Examples</span></span>

<span data-ttu-id="cde78-130">W poniższym przykładzie pokazano, jak zdefiniować symbol MYTEST w pliku, a następnie przetestować wartości symboli MYTEST i DEBUG.</span><span class="sxs-lookup"><span data-stu-id="cde78-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="cde78-131">Dane wyjściowe w tym przykładzie zależy od tego, czy został utworzony projekt w trybie konfiguracji debugowania lub wydania.</span><span class="sxs-lookup"><span data-stu-id="cde78-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="cde78-132">W poniższym przykładzie pokazano, jak przetestować dla różnych platform docelowych, dzięki czemu można używać nowszych interfejsów API, jeśli to możliwe:</span><span class="sxs-lookup"><span data-stu-id="cde78-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cde78-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cde78-133">See also</span></span>

- [<span data-ttu-id="cde78-134">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="cde78-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cde78-135">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="cde78-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cde78-136">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="cde78-136">C# Preprocessor Directives</span></span>](index.md)
- [<span data-ttu-id="cde78-137">Instrukcje: Kompilowanie warunkowe ze śledzeniem i debugowaniem</span><span class="sxs-lookup"><span data-stu-id="cde78-137">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
