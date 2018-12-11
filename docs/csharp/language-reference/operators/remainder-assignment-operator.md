---
title: '% = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: d0732f9578b64c894ecc1d3bb15cee11a8d5b6a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245564"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9f873-102">Operator %= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9f873-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="9f873-103">Operator przypisania reszty.</span><span class="sxs-lookup"><span data-stu-id="9f873-103">The remainder assignment operator.</span></span>

<span data-ttu-id="9f873-104">Usługi za pomocą wyrażenia `%=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="9f873-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="9f873-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="9f873-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="9f873-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="9f873-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="9f873-107">[Operator reszty](remainder-operator.md) `%` oblicza pozostałą po dzielenia swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="9f873-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="9f873-108">Jest ona obsługiwana przez wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="9f873-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="9f873-109">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator reszty](remainder-operator.md) `%`, operator przypisania reszty `%=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="9f873-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="9f873-110">W poniższym przykładzie pokazano użycie `%=` operator:</span><span class="sxs-lookup"><span data-stu-id="9f873-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="9f873-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f873-111">See also</span></span>

- [<span data-ttu-id="9f873-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9f873-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9f873-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9f873-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9f873-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="9f873-114">C# Operators</span></span>](index.md)
