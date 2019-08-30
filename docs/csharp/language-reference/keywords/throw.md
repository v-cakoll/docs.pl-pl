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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a9a235da06427e12bb5866a48f76f9c5896a572
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168747"
---
# <a name="throw-c-reference"></a><span data-ttu-id="b15df-102">throw (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b15df-102">throw (C# Reference)</span></span>

<span data-ttu-id="b15df-103">Sygnalizuje wystąpienie wyjątku podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="b15df-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b15df-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b15df-104">Remarks</span></span>

<span data-ttu-id="b15df-105">Składnia `throw` :</span><span class="sxs-lookup"><span data-stu-id="b15df-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```

<span data-ttu-id="b15df-106">gdzie `e` to wystąpienie klasy <xref:System.Exception?displayProperty=nameWithType>pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b15df-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b15df-107">Poniższy przykład używa instrukcji, `throw` aby <xref:System.IndexOutOfRangeException> zgłosić, czy argument przesłany do metody o nazwie `GetNumber` nie odpowiada prawidłowemu indeksowi tablicy wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="b15df-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="b15df-108">Metody wywołujące używają `try-catch` następnie bloku lub `try-catch-finally` do obsługi zgłoszonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b15df-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="b15df-109">Poniższy przykład obsługuje wyjątek zgłoszony przez `GetNumber` metodę.</span><span class="sxs-lookup"><span data-stu-id="b15df-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="b15df-110">Ponowne zgłaszanie wyjątku</span><span class="sxs-lookup"><span data-stu-id="b15df-110">Re-throwing an exception</span></span>

<span data-ttu-id="b15df-111">`throw`można go również użyć w `catch` bloku, aby ponownie zgłosić wyjątek obsłużony `catch` w bloku.</span><span class="sxs-lookup"><span data-stu-id="b15df-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="b15df-112">W tym przypadku `throw` nie przyjmuje operandu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b15df-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="b15df-113">Jest to najbardziej przydatne, gdy metoda przekazuje argument od wywołującego do innej metody biblioteki, a metoda Library zgłasza wyjątek, który musi zostać przekazana do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b15df-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="b15df-114">Na przykład poniższy przykład generuje ponownie zdarzenie <xref:System.NullReferenceException> , które jest zgłaszane podczas próby pobrania pierwszego znaku niezainicjowanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="b15df-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="b15df-115">Możesz również użyć `throw e` składni `catch` w bloku, aby utworzyć wystąpienie nowego wyjątku przekazywanego do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b15df-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="b15df-116">W takim przypadku śledzenie stosu oryginalnego wyjątku, który jest dostępny we <xref:System.Exception.StackTrace> właściwości, nie jest zachowywane.</span><span class="sxs-lookup"><span data-stu-id="b15df-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="b15df-117">`throw` Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="b15df-117">The `throw` expression</span></span>

<span data-ttu-id="b15df-118">Począwszy od C# 7,0, `throw` można użyć jako wyrażenia, a także instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b15df-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="b15df-119">Pozwala to na wyrzucanie wyjątku w kontekstach, które były wcześniej nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b15df-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="b15df-120">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="b15df-120">These include:</span></span>

- <span data-ttu-id="b15df-121">[operator warunkowy](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b15df-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="b15df-122">Poniższy przykład używa `throw` wyrażenia, aby <xref:System.ArgumentException> zgłosić, czy metoda jest przenoszona pustą tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="b15df-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="b15df-123">Przed C# 7,0, ta logika musi pojawić się w `if` / `else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b15df-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="b15df-124">[operator łączenia wartości null](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b15df-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="b15df-125">W poniższym przykładzie `throw` wyrażenie jest używane z operatorem łączenia wartości null, aby zgłosić wyjątek, jeśli ciąg przypisany `Name` do właściwości jest `null`.</span><span class="sxs-lookup"><span data-stu-id="b15df-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- <span data-ttu-id="b15df-126">wyrażenie wyrażenia [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) lub metody.</span><span class="sxs-lookup"><span data-stu-id="b15df-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="b15df-127">Poniższy przykład ilustruje metodę zanikającą z wyrażenia, która zgłasza <xref:System.InvalidCastException> , ponieważ konwersja <xref:System.DateTime> do wartości nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="b15df-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="b15df-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b15df-128">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b15df-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b15df-129">See also</span></span>

- [<span data-ttu-id="b15df-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b15df-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b15df-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b15df-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b15df-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="b15df-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="b15df-133">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="b15df-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b15df-134">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="b15df-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
