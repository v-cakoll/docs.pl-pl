---
title: throw — C# odwołania
ms.custom: seodec18
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f9729a3536a6611ed593f16ba3bc09e7af20a4c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238822"
---
# <a name="throw-c-reference"></a><span data-ttu-id="90bc8-102">throw (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="90bc8-102">throw (C# Reference)</span></span>

<span data-ttu-id="90bc8-103">Sygnalizuje zdarzenie wyjątku podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="90bc8-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90bc8-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90bc8-104">Remarks</span></span>

<span data-ttu-id="90bc8-105">Składnia `throw` jest:</span><span class="sxs-lookup"><span data-stu-id="90bc8-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```

<span data-ttu-id="90bc8-106">gdzie `e` jest wystąpieniem obiektu klasy pochodzącej od <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90bc8-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="90bc8-107">W poniższym przykładzie użyto `throw` instrukcję, aby zgłosić <xref:System.IndexOutOfRangeException> Jeśli argumentu przekazanego do metody o nazwie `GetNumber` nie odpowiada prawidłowy indeks tablicy wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="90bc8-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="90bc8-108">Następnie za pomocą obiektów wywołujących metodę `try-catch` lub `try-catch-finally` bloku, aby obsłużyć Wyrzucony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="90bc8-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="90bc8-109">Poniższy przykład obsługi wyjątku zgłoszonego przez `GetNumber` metody.</span><span class="sxs-lookup"><span data-stu-id="90bc8-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="90bc8-110">Ponownie zostanie zgłoszony wyjątek</span><span class="sxs-lookup"><span data-stu-id="90bc8-110">Re-throwing an exception</span></span>

<span data-ttu-id="90bc8-111">`throw` można również w `catch` bloku, aby można było ponownie zgłosić wyjątek obsłużony w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="90bc8-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="90bc8-112">W tym przypadku `throw` nie przyjmuje argumentu operacji wyjątku.</span><span class="sxs-lookup"><span data-stu-id="90bc8-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="90bc8-113">Może to być najbardziej przydatne, gdy metoda przekazuje argument z obiekt wywołujący do innej metody w bibliotece, a metoda biblioteki zgłasza wyjątek, który musi być przekazywane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="90bc8-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="90bc8-114">Na przykład, poniższy przykład generuje ponownie <xref:System.NullReferenceException> zgłaszany podczas próby pobrania pierwszego znaku ciągu niezainicjowany.</span><span class="sxs-lookup"><span data-stu-id="90bc8-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="90bc8-115">Można również użyć `throw e` składni `catch` bloku, aby utworzyć wystąpienie nowy wyjątek, który jest przekazywany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="90bc8-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="90bc8-116">W tym przypadku ślad stosu wyjątku, oryginalnym, który jest dostępny w <xref:System.Exception.StackTrace> właściwości nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="90bc8-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="90bc8-117">`throw` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="90bc8-117">The `throw` expression</span></span>

<span data-ttu-id="90bc8-118">Począwszy od C# 7.0, `throw` mogą być używane jako wyrażenie, a także instrukcję.</span><span class="sxs-lookup"><span data-stu-id="90bc8-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="90bc8-119">Dzięki temu zgłoszenie wyjątku w kontekstach, które były wcześniej obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="90bc8-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="90bc8-120">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="90bc8-120">These include:</span></span>

- <span data-ttu-id="90bc8-121">[operator warunkowy](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="90bc8-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="90bc8-122">W poniższym przykładzie użyto `throw` wyrażenie throw <xref:System.ArgumentException> Jeśli metoda jest przekazywana pustą tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="90bc8-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="90bc8-123">Przed C# 7.0, konieczne są wyświetlane w tę logikę `if` / `else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="90bc8-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="90bc8-124">[operator łączenia wartości null](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="90bc8-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="90bc8-125">W poniższym przykładzie `throw` wyrażenie jest używane z operatorem łączenia wartości null do zgłoszenia wyjątku, jeśli ciąg jest przypisany do `Name` właściwość `null`.</span><span class="sxs-lookup"><span data-stu-id="90bc8-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- <span data-ttu-id="90bc8-126">wyrażeniem [lambda](../../lambda-expressions.md) lub metody.</span><span class="sxs-lookup"><span data-stu-id="90bc8-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="90bc8-127">W poniższym przykładzie pokazano metodę wyrażeniem, które zgłasza <xref:System.InvalidCastException> ponieważ konwersja na <xref:System.DateTime> wartość nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="90bc8-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="90bc8-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="90bc8-128">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="90bc8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90bc8-129">See also</span></span>

- [<span data-ttu-id="90bc8-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="90bc8-130">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="90bc8-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="90bc8-131">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="90bc8-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="90bc8-132">try-catch</span></span>](try-catch.md)  
- [<span data-ttu-id="90bc8-133">Try, catch i throw instrukcji w języku C++</span><span class="sxs-lookup"><span data-stu-id="90bc8-133">The try, catch, and throw Statements in C++</span></span>](try-catch.md)  
- [<span data-ttu-id="90bc8-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="90bc8-134">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="90bc8-135">Instrukcje obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="90bc8-135">Exception Handling Statements</span></span>](exception-handling-statements.md)  
- [<span data-ttu-id="90bc8-136">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="90bc8-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)