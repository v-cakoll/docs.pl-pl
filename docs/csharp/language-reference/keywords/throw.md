---
title: throw - Odwołanie do języka C#
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 04d3138e3390627355b4b2d4e25c6b00248cec1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399337"
---
# <a name="throw-c-reference"></a><span data-ttu-id="f07bc-102">throw (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f07bc-102">throw (C# Reference)</span></span>

<span data-ttu-id="f07bc-103">Sygnalizuje wystąpienie wyjątku podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="f07bc-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f07bc-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f07bc-104">Remarks</span></span>

<span data-ttu-id="f07bc-105">Składnia `throw` jest:</span><span class="sxs-lookup"><span data-stu-id="f07bc-105">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="f07bc-106">gdzie `e` jest wystąpienieklasy pochodzącej <xref:System.Exception?displayProperty=nameWithType>z .</span><span class="sxs-lookup"><span data-stu-id="f07bc-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f07bc-107">W poniższym `throw` przykładzie użyto <xref:System.IndexOutOfRangeException> instrukcji do wyrzucania, jeśli argument przekazany do metody o nazwie `GetNumber` nie odpowiada prawidłowy indeks tablicy wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="f07bc-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="f07bc-108">Wywoływanie metody następnie `try-catch` `try-catch-finally` użyć lub bloku do obsługi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f07bc-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="f07bc-109">Poniższy przykład obsługuje wyjątek zgłoszony `GetNumber` przez metodę.</span><span class="sxs-lookup"><span data-stu-id="f07bc-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="f07bc-110">Ponowne zgłaszanie wyjątku</span><span class="sxs-lookup"><span data-stu-id="f07bc-110">Re-throwing an exception</span></span>

<span data-ttu-id="f07bc-111">`throw`może być również `catch` używany w bloku, aby ponownie `catch` zgłosić wyjątek obsługiwany w bloku.</span><span class="sxs-lookup"><span data-stu-id="f07bc-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="f07bc-112">W tym `throw` przypadku nie ma argumentu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f07bc-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="f07bc-113">Jest to najbardziej przydatne, gdy metoda przekazuje argument z obiektu wywołującego do innej metody biblioteki, a metoda biblioteki zgłasza wyjątek, który musi zostać przekazany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f07bc-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="f07bc-114">Na przykład w poniższym przykładzie <xref:System.NullReferenceException> ponownie zgłasza, który jest generowany podczas próby pobrania pierwszego znaku niezainicjowanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="f07bc-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="f07bc-115">Można również użyć `throw e` składni `catch` w bloku, aby utworzyć wystąpienie nowego wyjątku, który można przekazać do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f07bc-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="f07bc-116">W takim przypadku ślad stosu oryginalnego wyjątku, który jest dostępny z <xref:System.Exception.StackTrace> właściwości, nie jest zachowywany.</span><span class="sxs-lookup"><span data-stu-id="f07bc-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="f07bc-117">Wyrażenie `throw`</span><span class="sxs-lookup"><span data-stu-id="f07bc-117">The `throw` expression</span></span>

<span data-ttu-id="f07bc-118">Począwszy od języka C# 7.0, `throw` może służyć jako wyrażenie, a także instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f07bc-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="f07bc-119">Dzięki temu wyjątek wyjątek w kontekstach, które wcześniej nie były obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f07bc-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="f07bc-120">Należą do nich:</span><span class="sxs-lookup"><span data-stu-id="f07bc-120">These include:</span></span>

- <span data-ttu-id="f07bc-121">[operatora warunkowego](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f07bc-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="f07bc-122">W poniższym `throw` przykładzie użyto <xref:System.ArgumentException> wyrażenia do wyrzucania, jeśli metoda jest przekazywana tablicy pustyciąg.</span><span class="sxs-lookup"><span data-stu-id="f07bc-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="f07bc-123">Przed C# 7.0, ta logika `if` / `else` musi pojawić się w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f07bc-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="f07bc-124">[operatora zerowego łączenia](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f07bc-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="f07bc-125">W poniższym `throw` przykładzie wyrażenie jest używane z operatorem łączenia wartości null, aby zgłosić wyjątek, jeśli ciąg przypisany do `Name` właściwości jest `null`.</span><span class="sxs-lookup"><span data-stu-id="f07bc-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="f07bc-126">[lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) lub metoda osażeniu.</span><span class="sxs-lookup"><span data-stu-id="f07bc-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="f07bc-127">W poniższym przykładzie przedstawiono metodę zabudowaną <xref:System.InvalidCastException> wyrażeniem, która <xref:System.DateTime> zgłasza, ponieważ konwersja na wartość nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="f07bc-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="f07bc-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f07bc-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f07bc-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f07bc-129">See also</span></span>

- [<span data-ttu-id="f07bc-130">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="f07bc-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f07bc-131">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="f07bc-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f07bc-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="f07bc-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="f07bc-133">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f07bc-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f07bc-134">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="f07bc-134">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
