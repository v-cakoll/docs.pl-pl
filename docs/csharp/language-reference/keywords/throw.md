---
title: throw — C# odwołanie
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
ms.openlocfilehash: f274802c84ff8f3dd2588db8b83a0d0de36d2d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101773"
---
# <a name="throw-c-reference"></a><span data-ttu-id="0cbe0-102">throw (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0cbe0-102">throw (C# Reference)</span></span>

<span data-ttu-id="0cbe0-103">Sygnalizuje wystąpienie wyjątku podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cbe0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0cbe0-104">Remarks</span></span>

<span data-ttu-id="0cbe0-105">Składnia `throw` jest następująca:</span><span class="sxs-lookup"><span data-stu-id="0cbe0-105">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="0cbe0-106">gdzie `e` jest wystąpieniem klasy pochodzącej od <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0cbe0-107">Poniższy przykład używa instrukcji `throw`, aby zgłosić <xref:System.IndexOutOfRangeException>, jeśli argument przesłany do metody o nazwie `GetNumber` nie odpowiada prawidłowemu indeksowi tablicy wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="0cbe0-108">Metody wywołujące stosują następnie `try-catch` lub `try-catch-finally` bloku, aby obsłużyć zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="0cbe0-109">Poniższy przykład obsługuje wyjątek zgłoszony przez metodę `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="0cbe0-110">Ponowne zgłaszanie wyjątku</span><span class="sxs-lookup"><span data-stu-id="0cbe0-110">Re-throwing an exception</span></span>

<span data-ttu-id="0cbe0-111">`throw` można również użyć w bloku `catch`, aby ponownie zgłosić wyjątek obsłużony w bloku `catch`.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="0cbe0-112">W tym przypadku `throw` nie przyjmuje operandu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="0cbe0-113">Jest to najbardziej przydatne, gdy metoda przekazuje argument od wywołującego do innej metody biblioteki, a metoda Library zgłasza wyjątek, który musi zostać przekazana do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="0cbe0-114">Na przykład poniższy przykład ponownie generuje <xref:System.NullReferenceException>, który jest zgłaszany podczas próby pobrania pierwszego znaku niezainicjowanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="0cbe0-115">Możesz również użyć składni `throw e` w bloku `catch`, aby utworzyć wystąpienie nowego wyjątku przekazanego do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="0cbe0-116">W takim przypadku śledzenie stosu oryginalnego wyjątku, który jest dostępny we właściwości <xref:System.Exception.StackTrace>, nie jest zachowywane.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="0cbe0-117">Wyrażenie `throw`</span><span class="sxs-lookup"><span data-stu-id="0cbe0-117">The `throw` expression</span></span>

<span data-ttu-id="0cbe0-118">Począwszy od C# 7,0, `throw` może służyć jako wyrażenie, a także instrukcja.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="0cbe0-119">Pozwala to na wyrzucanie wyjątku w kontekstach, które były wcześniej nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="0cbe0-120">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="0cbe0-120">These include:</span></span>

- <span data-ttu-id="0cbe0-121">[operator warunkowy](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0cbe0-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="0cbe0-122">Poniższy przykład używa wyrażenia `throw`, aby zgłosić <xref:System.ArgumentException>, jeśli metoda jest przenoszona pustą tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="0cbe0-123">Przed C# 7,0, ta logika powinna być wyświetlana w instrukcji `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="0cbe0-124">[operator łączenia wartości null](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0cbe0-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="0cbe0-125">W poniższym przykładzie wyrażenie `throw` jest używane z operatorem łączenia wartości null, aby zgłosić wyjątek, jeśli ciąg przypisany do właściwości `Name` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="0cbe0-126">wyrażenie wyrażenia [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) lub metody.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="0cbe0-127">Poniższy przykład ilustruje metodę zanikającą z wyrażenia, która zgłasza <xref:System.InvalidCastException>, ponieważ konwersja do wartości <xref:System.DateTime> nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="0cbe0-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="0cbe0-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0cbe0-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0cbe0-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cbe0-129">See also</span></span>

- [<span data-ttu-id="0cbe0-130">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="0cbe0-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0cbe0-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0cbe0-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0cbe0-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="0cbe0-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="0cbe0-133">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0cbe0-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0cbe0-134">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="0cbe0-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
