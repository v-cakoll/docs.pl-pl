---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350743"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="6d0df-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d0df-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="6d0df-103">Określa, że co najmniej jedna zadeklarowana zmienna składowej odnosi się do wystąpienia klasy, która może zgłaszać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6d0df-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d0df-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d0df-104">Remarks</span></span>

<span data-ttu-id="6d0df-105">Gdy zmienna jest definiowana przy użyciu `WithEvents`, można deklaratywnie określić, że metoda obsługuje zdarzenia zmiennej przy użyciu słowa kluczowego `Handles`.</span><span class="sxs-lookup"><span data-stu-id="6d0df-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="6d0df-106">`WithEvents` można używać tylko na poziomie klasy lub modułu.</span><span class="sxs-lookup"><span data-stu-id="6d0df-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="6d0df-107">Oznacza to, że kontekst deklaracji dla zmiennej `WithEvents` musi być klasą lub modułem i nie może być plikiem źródłowym, przestrzenią nazw, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="6d0df-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="6d0df-108">Nie można użyć `WithEvents` w składowej struktury.</span><span class="sxs-lookup"><span data-stu-id="6d0df-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="6d0df-109">Można zadeklarować tylko pojedyncze zmienne — nie tablice — z `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="6d0df-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="6d0df-110">Reguły</span><span class="sxs-lookup"><span data-stu-id="6d0df-110">Rules</span></span>

<span data-ttu-id="6d0df-111">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="6d0df-111">**Element Types.**</span></span> <span data-ttu-id="6d0df-112">Należy zadeklarować zmienne `WithEvents` jako zmienne obiektów, aby mogły akceptować wystąpienia klas.</span><span class="sxs-lookup"><span data-stu-id="6d0df-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="6d0df-113">Nie można jednak zadeklarować ich jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="6d0df-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="6d0df-114">Należy zadeklarować je jako konkretną klasę, która może zgłaszać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6d0df-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="6d0df-115">Modyfikator `WithEvents` może być używany w tym kontekście: [Dim — Instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="6d0df-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="6d0df-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d0df-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="6d0df-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d0df-117">See also</span></span>

- [<span data-ttu-id="6d0df-118">Realizuj</span><span class="sxs-lookup"><span data-stu-id="6d0df-118">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="6d0df-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6d0df-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="6d0df-120">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6d0df-120">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
