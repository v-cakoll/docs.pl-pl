---
title: Operator %= (odwołanie w C#)
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738291"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="fc750-102">Operator %= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fc750-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="fc750-103">Operator przypisania reszty.</span><span class="sxs-lookup"><span data-stu-id="fc750-103">The remainder assignment operator.</span></span>

<span data-ttu-id="fc750-104">Usługi za pomocą wyrażenia `%=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="fc750-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="fc750-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="fc750-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="fc750-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="fc750-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="fc750-107">[Operator reszty](remainder-operator.md) `%` jest obsługiwany przez wszystkie typy liczbowe i oblicza pozostałą po dzielenia swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="fc750-107">The [remainder operator](remainder-operator.md) `%` is supported by all numeric types and computes the remainder after division of its operands.</span></span>

<span data-ttu-id="fc750-108">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator reszty](remainder-operator.md) `%`, operator przypisania reszty `%=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="fc750-108">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="fc750-109">W poniższym przykładzie pokazano użycie `%=` operator:</span><span class="sxs-lookup"><span data-stu-id="fc750-109">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="fc750-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc750-110">See also</span></span>

- [<span data-ttu-id="fc750-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fc750-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc750-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fc750-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc750-113">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="fc750-113">C# Operators</span></span>](index.md)
