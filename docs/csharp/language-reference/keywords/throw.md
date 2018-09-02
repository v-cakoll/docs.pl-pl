---
title: throw (odwołanie w C#)
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
ms.openlocfilehash: 831c4cce14e902697d84129e54cc54f07d26b9f3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417361"
---
# <a name="throw-c-reference"></a><span data-ttu-id="acdee-102">throw (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="acdee-102">throw (C# Reference)</span></span>
<span data-ttu-id="acdee-103">Sygnalizuje zdarzenie wyjątku podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="acdee-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acdee-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acdee-104">Remarks</span></span>

<span data-ttu-id="acdee-105">Składnia `throw` jest:</span><span class="sxs-lookup"><span data-stu-id="acdee-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="acdee-106">gdzie `e` jest wystąpieniem obiektu klasy pochodzącej od <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="acdee-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="acdee-107">W poniższym przykładzie użyto `throw` instrukcję, aby zgłosić <xref:System.IndexOutOfRangeException> Jeśli argumentu przekazanego do metody o nazwie `GetNumber` nie odpowiada prawidłowy indeks tablicy wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="acdee-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="acdee-108">Następnie za pomocą obiektów wywołujących metodę `try-catch` lub `try-catch-finally` bloku, aby obsłużyć Wyrzucony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="acdee-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="acdee-109">Poniższy przykład obsługi wyjątku zgłoszonego przez `GetNumber` metody.</span><span class="sxs-lookup"><span data-stu-id="acdee-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="acdee-110">Ponownie zostanie zgłoszony wyjątek</span><span class="sxs-lookup"><span data-stu-id="acdee-110">Re-throwing an exception</span></span>

<span data-ttu-id="acdee-111">`throw` można również w `catch` bloku, aby można było ponownie zgłosić wyjątek obsłużony w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="acdee-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="acdee-112">W tym przypadku `throw` nie przyjmuje argumentu operacji wyjątku.</span><span class="sxs-lookup"><span data-stu-id="acdee-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="acdee-113">Może to być najbardziej przydatne, gdy metoda przekazuje argument z obiekt wywołujący do innej metody w bibliotece, a metoda biblioteki zgłasza wyjątek, który musi być przekazywane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="acdee-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="acdee-114">Na przykład, poniższy przykład generuje ponownie <xref:System.NullReferenceException> zgłaszany podczas próby pobrania pierwszego znaku ciągu niezainicjowany.</span><span class="sxs-lookup"><span data-stu-id="acdee-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="acdee-115">Można również użyć `throw e` składni `catch` bloku, aby utworzyć wystąpienie nowy wyjątek, który jest przekazywany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="acdee-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="acdee-116">W tym przypadku ślad stosu wyjątku, oryginalnym, który jest dostępny w <xref:System.Exception.StackTrace> właściwości nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="acdee-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="acdee-117">`throw` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="acdee-117">The `throw` expression</span></span>

<span data-ttu-id="acdee-118">Począwszy od C# 7.0, `throw` mogą być używane jako wyrażenie, a także instrukcję.</span><span class="sxs-lookup"><span data-stu-id="acdee-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="acdee-119">Dzięki temu zgłoszenie wyjątku w kontekstach, które były wcześniej obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="acdee-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="acdee-120">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="acdee-120">These include:</span></span>

- <span data-ttu-id="acdee-121">[operator warunkowy](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="acdee-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="acdee-122">W poniższym przykładzie użyto `throw` wyrażenie throw <xref:System.ArgumentException> Jeśli metoda jest przekazywana pustą tablicę ciągów.</span><span class="sxs-lookup"><span data-stu-id="acdee-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="acdee-123">Przed C# 7.0, konieczne są wyświetlane w tę logikę `if` / `else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="acdee-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="acdee-124">[operator łączenia wartości null](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="acdee-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="acdee-125">W poniższym przykładzie `throw` wyrażenie jest używane z operatorem łączenia wartości null do zgłoszenia wyjątku, jeśli ciąg jest przypisany do `Name` właściwość `null`.</span><span class="sxs-lookup"><span data-stu-id="acdee-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- <span data-ttu-id="acdee-126">wyrażeniem [lambda](../../lambda-expressions.md) lub metody.</span><span class="sxs-lookup"><span data-stu-id="acdee-126">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="acdee-127">W poniższym przykładzie pokazano metodę wyrażeniem, które zgłasza <xref:System.InvalidCastException> ponieważ konwersja na <xref:System.DateTime> wartość nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="acdee-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="acdee-128">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="acdee-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="acdee-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="acdee-129">See Also</span></span>

- [<span data-ttu-id="acdee-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="acdee-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="acdee-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="acdee-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="acdee-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="acdee-132">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="acdee-133">Try, catch i throw instrukcji w języku C++</span><span class="sxs-lookup"><span data-stu-id="acdee-133">The try, catch, and throw Statements in C++</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="acdee-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="acdee-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="acdee-135">Instrukcje obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="acdee-135">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [<span data-ttu-id="acdee-136">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="acdee-136">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
