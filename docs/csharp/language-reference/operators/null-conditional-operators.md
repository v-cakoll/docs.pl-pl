---
title: Operatory warunkowe null — C# odwołania
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 9cbf8a0f860f0bc0328cd98e558b20b5e8e1bf8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688881"
---
# <a name="-and--null-conditional-operators-c-reference"></a><span data-ttu-id="614e5-102">?.</span><span class="sxs-lookup"><span data-stu-id="614e5-102">?.</span></span> <span data-ttu-id="614e5-103">i? Operatory warunkowe null [] (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="614e5-103">and ?[] null-conditional operators (C# Reference)</span></span>

<span data-ttu-id="614e5-104">Testuje, czy wartość lewego argumentu operacji to „null”, zanim przeprowadzi operację dostępu do elementu (`?.`) lub indeksowania (`?[]`). Zwraca `null`, jeśli wartość lewego argumentu operacji to `null`.</span><span class="sxs-lookup"><span data-stu-id="614e5-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="614e5-105">Operatory te pomagają ograniczyć ilość kodu potrzebnego do sprawdzenia wystąpień wartości „null”, zwłaszcza w przypadku wchodzenia głębiej w struktury danych.</span><span class="sxs-lookup"><span data-stu-id="614e5-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

<span data-ttu-id="614e5-106">Operatory warunkowe `null` skracają łańcuch wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="614e5-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="614e5-107">Jeśli jedna operacja w łańcuchu operacji dostępu i indeks warunkowa składowa zwraca wartość null, nie będzie możliwy pozostałą część wykonania łańcucha.</span><span class="sxs-lookup"><span data-stu-id="614e5-107">If one operation in a chain of conditional member access and index operations returns null, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="614e5-108">W poniższym przykładzie `E` nie jest wykonywane, jeśli `A`, `B` lub `C` zwraca wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="614e5-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

<span data-ttu-id="614e5-109">Inne zastosowanie dostępu do elementu członkowskiego przy użyciu operatora warunkowego `null` polega na wywołaniu delegatów w sposób bezpieczny wątkowo i ze znacznie mniejszą ilością kodu.</span><span class="sxs-lookup"><span data-stu-id="614e5-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="614e5-110">Stary sposób wymaga kodu podobnego do poniższego:</span><span class="sxs-lookup"><span data-stu-id="614e5-110">The old way requires code like the following:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

<span data-ttu-id="614e5-111">Nowy sposób jest znacznie prostszy:</span><span class="sxs-lookup"><span data-stu-id="614e5-111">The new way is much simpler:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="614e5-112">Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby sprawdzić stan `PropertyChanged` tylko jeden raz, a następnie zapisuje wynik w zmiennej tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="614e5-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="614e5-113">Metodę `Invoke`trzeba wywołać jawnie, ponieważ nie istnieje składnia `PropertyChanged?(e)` do wywołania delegata przy użyciu operatora warunkowego „null”.</span><span class="sxs-lookup"><span data-stu-id="614e5-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>

## <a name="language-specifications"></a><span data-ttu-id="614e5-114">Specyfikacje języka</span><span class="sxs-lookup"><span data-stu-id="614e5-114">Language specifications</span></span>

<span data-ttu-id="614e5-115">Aby uzyskać więcej informacji, zobacz [operatorów warunkowych działających z wartością Null](~/_csharplang/spec/expressions.md#null-conditional-operator) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="614e5-115">For more information, see [Null-conditional operator](~/_csharplang/spec/expressions.md#null-conditional-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="614e5-116">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="614e5-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="614e5-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="614e5-117">See also</span></span>

- [<span data-ttu-id="614e5-118">?? (z operatorem łączenia wartości null)</span><span class="sxs-lookup"><span data-stu-id="614e5-118">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="614e5-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="614e5-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="614e5-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="614e5-120">C# Programming Guide</span></span>](../../programming-guide/index.md)