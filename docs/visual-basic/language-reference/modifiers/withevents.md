---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 48261e27de302c1809c9725e6e2fc0705a803930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386779"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="856e9-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="856e9-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="856e9-103">Określa, że co najmniej jedna zadeklarowana zmienna składowej odnosi się do wystąpienia klasy, która może zgłaszać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="856e9-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="856e9-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="856e9-104">Remarks</span></span>

<span data-ttu-id="856e9-105">Gdy zmienna jest zdefiniowana przy użyciu `WithEvents` , można deklaratywnie określić, że metoda obsługuje zdarzenia zmiennej przy użyciu `Handles` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="856e9-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="856e9-106">Można używać `WithEvents` tylko na poziomie klasy lub modułu.</span><span class="sxs-lookup"><span data-stu-id="856e9-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="856e9-107">Oznacza to, że kontekst deklaracji dla `WithEvents` zmiennej musi być klasą lub modułem i nie może być plikiem źródłowym, przestrzenią nazw, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="856e9-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="856e9-108">Nie można użyć `WithEvents` w składowej struktury.</span><span class="sxs-lookup"><span data-stu-id="856e9-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="856e9-109">Można zadeklarować tylko pojedyncze zmienne — nie tablice — za pomocą `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="856e9-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="856e9-110">Reguły</span><span class="sxs-lookup"><span data-stu-id="856e9-110">Rules</span></span>

<span data-ttu-id="856e9-111">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="856e9-111">**Element Types.**</span></span> <span data-ttu-id="856e9-112">Należy zadeklarować `WithEvents` zmienne jako zmienne obiektów, aby mogły akceptować wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="856e9-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="856e9-113">Nie można jednak zadeklarować ich jako `Object` .</span><span class="sxs-lookup"><span data-stu-id="856e9-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="856e9-114">Należy zadeklarować je jako konkretną klasę, która może zgłaszać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="856e9-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="856e9-115">`WithEvents`Modyfikator może być używany w tym kontekście: [Dim — Instrukcja](../statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="856e9-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="856e9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="856e9-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="856e9-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="856e9-117">See also</span></span>

- [<span data-ttu-id="856e9-118">Handles</span><span class="sxs-lookup"><span data-stu-id="856e9-118">Handles</span></span>](../statements/handles-clause.md)
- [<span data-ttu-id="856e9-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="856e9-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="856e9-120">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="856e9-120">Events</span></span>](../../programming-guide/language-features/events/index.md)
