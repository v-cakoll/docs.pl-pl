---
title: '#Jeśli dyrektywa preprocesora (odwołanie w C#)'
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: c54a1fe0dba5f6d57b03b2ffeb4f1737fadfe039
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000940"
---
# <a name="if-c-reference"></a><span data-ttu-id="86dd9-102">#if (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="86dd9-102">#if (C# Reference)</span></span>

<span data-ttu-id="86dd9-103">Gdy kompilator języka C# napotka `#if` dyrektywy, a następnie po pewnym czasie przez [#endif](preprocessor-endif.md) dyrektywy, kompiluje kod między dyrektyw tylko wtedy, gdy zdefiniowano określonego symbolu.</span><span class="sxs-lookup"><span data-stu-id="86dd9-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="86dd9-104">W przeciwieństwie do C i C++ nie można przypisać wartości numerycznej symbolu.</span><span class="sxs-lookup"><span data-stu-id="86dd9-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="86dd9-105">Instrukcji #if w języku C# jest wartością logiczną, a tylko sprawdzenie, czy symbol został zdefiniowany lub nie.</span><span class="sxs-lookup"><span data-stu-id="86dd9-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="86dd9-106">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="86dd9-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="86dd9-107">Można używać operatorów [ == ](../operators/equality-comparison-operator.md) (równości) i [! =](../operators/not-equal-operator.md) (nierówność) tylko do testowania [true](../keywords/true.md) lub [false](../keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="86dd9-107">You can use the operators [==](../operators/equality-comparison-operator.md) (equality) and [!=](../operators/not-equal-operator.md) (inequality) only to test for [true](../keywords/true.md) or [false](../keywords/false.md).</span></span> <span data-ttu-id="86dd9-108">PRAWDA oznacza, że symbol jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="86dd9-108">True means the symbol is defined.</span></span> <span data-ttu-id="86dd9-109">Wykonywanie instrukcji `#if DEBUG` ma takie samo znaczenie jak `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="86dd9-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="86dd9-110">Można używać operatorów [ && ](../operators/conditional-and-operator.md) (a) [ &#124; &#124; ](../operators/conditional-or-operator.md) (lub) i [!](../operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="86dd9-110">You can use the operators [&&](../operators/conditional-and-operator.md) (and), [&#124;&#124;](../operators/conditional-or-operator.md) (or), and [!](../operators/logical-negation-operator.md)</span></span> <span data-ttu-id="86dd9-111">(nie) do oceny, czy zostały zdefiniowane wiele symboli.</span><span class="sxs-lookup"><span data-stu-id="86dd9-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="86dd9-112">Można także grupować symboli i operatorów, za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="86dd9-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="86dd9-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86dd9-113">Remarks</span></span>

<span data-ttu-id="86dd9-114">`#if`, wraz z [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), i [#undef](preprocessor-undef.md) dyrektyw, umożliwia Dołącz lub Wyklucz kod oparty na istnienie jednego lub wielu symboli.</span><span class="sxs-lookup"><span data-stu-id="86dd9-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="86dd9-115">Może to być przydatne podczas kompilowania kodu do kompilacji debugowania lub podczas kompilowania dla konkretnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="86dd9-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="86dd9-116">Warunkowe dyrektywy zaczyna się od `#if` dyrektywy jawnie muszą być zakończone znakiem `#endif` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="86dd9-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="86dd9-117">`#define` pozwala zdefiniować symbol.</span><span class="sxs-lookup"><span data-stu-id="86dd9-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="86dd9-118">Za pomocą symbolu wyrażenia są przekazywane do `#if` dyrektywy, wyrażenie ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="86dd9-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="86dd9-119">Można również zdefiniować symbol za pomocą [— Zdefiniuj](../compiler-options/define-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="86dd9-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="86dd9-120">Aby anulować definicję symbolu, użyj dyrektywy [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="86dd9-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="86dd9-121">Symbol, który zdefiniujesz z `-define` lub `#define` nie koliduje ze zmienną o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="86dd9-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="86dd9-122">Oznacza to, że nazwa zmiennej nie powinna być przekazywana do dyrektywy preprocesora i symbol może być oceniany tylko przez dyrektywy preprocesora.</span><span class="sxs-lookup"><span data-stu-id="86dd9-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="86dd9-123">Zakres symbolu utworzonych za pomocą `#define` jest plikiem, w którym został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="86dd9-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="86dd9-124">System kompilacji jest również pamiętać o wstępnie zdefiniowanych symboli preprocesora reprezentująca różne [ustalać platformy docelowe](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="86dd9-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="86dd9-125">Są one przydatne podczas tworzenia aplikacji przeznaczonych więcej niż jednej implementacji .NET lub wersji.</span><span class="sxs-lookup"><span data-stu-id="86dd9-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="86dd9-126">Inne wstępnie zdefiniowane symbole obejmują stałe debugowania i śledzenia.</span><span class="sxs-lookup"><span data-stu-id="86dd9-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="86dd9-127">Można zastąpić wartości ustawione dla projektu za pomocą `#define`.</span><span class="sxs-lookup"><span data-stu-id="86dd9-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="86dd9-128">Symbol debugowania, na przykład, jest automatycznie ustawiana w zależności od właściwości konfiguracji kompilacji (w trybie "Debug" lub "Release").</span><span class="sxs-lookup"><span data-stu-id="86dd9-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="86dd9-129">Przykłady</span><span class="sxs-lookup"><span data-stu-id="86dd9-129">Examples</span></span>

<span data-ttu-id="86dd9-130">Poniższy przykład pokazuje jak zdefiniować symbol test dla pliku, a następnie przetestować wartości symboli test i debugowania.</span><span class="sxs-lookup"><span data-stu-id="86dd9-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="86dd9-131">Dane wyjściowe w tym przykładzie zależy od tego, czy projekt jest oparty na tryb konfiguracji Debug i Release.</span><span class="sxs-lookup"><span data-stu-id="86dd9-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

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

<span data-ttu-id="86dd9-132">Poniższy przykład pokazuje, jak przetestować dla platform docelowych innej, aby można było używać nowszych interfejsów API, jeśli jest to możliwe:</span><span class="sxs-lookup"><span data-stu-id="86dd9-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="86dd9-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86dd9-133">See also</span></span>

- [<span data-ttu-id="86dd9-134">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="86dd9-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="86dd9-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86dd9-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="86dd9-136">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="86dd9-136">C# Preprocessor Directives</span></span>](index.md)  
- <span data-ttu-id="86dd9-137">[Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span><span class="sxs-lookup"><span data-stu-id="86dd9-137">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span></span>
