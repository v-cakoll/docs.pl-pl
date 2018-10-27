---
title: Operator %= (odwołanie w C#)
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: ab3a6a8d5cbfeb4d527ca1f9c233ddfaba3d35ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188719"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="120b8-102">Operator %= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="120b8-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="120b8-103">Operator przypisania reszty.</span><span class="sxs-lookup"><span data-stu-id="120b8-103">The remainder assignment operator.</span></span>

<span data-ttu-id="120b8-104">Usługi za pomocą wyrażenia `%=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="120b8-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="120b8-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="120b8-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="120b8-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="120b8-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="120b8-107">[Operator reszty](remainder-operator.md) `%` oblicza pozostałą po dzielenia swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="120b8-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="120b8-108">Jest ona obsługiwana przez wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="120b8-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="120b8-109">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator reszty](remainder-operator.md) `%`, operator przypisania reszty `%=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="120b8-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="120b8-110">W poniższym przykładzie pokazano użycie `%=` operator:</span><span class="sxs-lookup"><span data-stu-id="120b8-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="120b8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="120b8-111">See also</span></span>

- [<span data-ttu-id="120b8-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="120b8-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="120b8-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="120b8-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="120b8-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="120b8-114">C# Operators</span></span>](index.md)
