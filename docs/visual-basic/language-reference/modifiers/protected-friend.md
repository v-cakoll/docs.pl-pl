---
title: Chroniony znajomy (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524777"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="188d2-102">Chroniony znajomy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="188d2-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="188d2-103">Kombinacja słowa kluczowego `Protected Friend` jest modyfikatorem dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="188d2-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="188d2-104">Przyznaje zarówno dostęp [znajomy](friend.md) i [chroniony](protected.md) dostęp do elementów zadeklarowanych, więc są one dostępne z dowolnego miejsca w tym samym zestawie, z własnej klasy i z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="188d2-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="188d2-105">Można określić `Protected Friend` tylko dla elementów członkowskich klasy; nie można zastosować `Protected Friend` do elementów członkowskich struktury, ponieważ struktury nie mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="188d2-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="188d2-106">W programie Visual Studio wybierz pozycję Pomoc F1 na `protected friend` zapewnia pomoc dla [ochrony](protected.md) lub [znajomych](friend.md).</span><span class="sxs-lookup"><span data-stu-id="188d2-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="188d2-107">IDE wybiera pojedynczy token w obszarze kursora zamiast słowa złożonego.</span><span class="sxs-lookup"><span data-stu-id="188d2-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="188d2-108">Przepisy</span><span class="sxs-lookup"><span data-stu-id="188d2-108">Rules</span></span>

<span data-ttu-id="188d2-109">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="188d2-109">**Declaration Context.**</span></span> <span data-ttu-id="188d2-110">@No__t_0 można używać tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="188d2-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="188d2-111">Oznacza to, że kontekst deklaracji dla elementu `Protected` musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="188d2-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="188d2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="188d2-112">See also</span></span>

- [<span data-ttu-id="188d2-113">Public</span><span class="sxs-lookup"><span data-stu-id="188d2-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="188d2-114">Protected</span><span class="sxs-lookup"><span data-stu-id="188d2-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="188d2-115">Friend</span><span class="sxs-lookup"><span data-stu-id="188d2-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="188d2-116">Private</span><span class="sxs-lookup"><span data-stu-id="188d2-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="188d2-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="188d2-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="188d2-118">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="188d2-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="188d2-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="188d2-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="188d2-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="188d2-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="188d2-121">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="188d2-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
