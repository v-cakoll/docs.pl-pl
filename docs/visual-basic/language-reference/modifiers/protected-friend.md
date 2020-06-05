---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 202d4f4a3a05a64ab1d74621268f28f6b55e8952
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404839"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="f48c1-102">Chroniony znajomy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f48c1-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="f48c1-103">`Protected Friend`Kombinacja słowa kluczowego jest modyfikatorem dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="f48c1-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="f48c1-104">Przyznaje zarówno dostęp [znajomy](friend.md) i [chroniony](protected.md) dostęp do elementów zadeklarowanych, więc są one dostępne z dowolnego miejsca w tym samym zestawie, z własnej klasy i z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f48c1-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="f48c1-105">Można określić `Protected Friend` tylko dla elementów członkowskich klasy; nie można stosować `Protected Friend` do elementów członkowskich struktury, ponieważ struktury nie mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="f48c1-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="f48c1-106">W programie Visual Studio wybierz pozycję Pomoc F1, aby uzyskać pomoc dotyczącą `protected friend` [ochrony](protected.md) lub [znajomych](friend.md).</span><span class="sxs-lookup"><span data-stu-id="f48c1-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="f48c1-107">IDE wybiera pojedynczy token w obszarze kursora zamiast słowa złożonego.</span><span class="sxs-lookup"><span data-stu-id="f48c1-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="f48c1-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="f48c1-108">Rules</span></span>

<span data-ttu-id="f48c1-109">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="f48c1-109">**Declaration Context.**</span></span> <span data-ttu-id="f48c1-110">Można używać `Protected Friend` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="f48c1-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="f48c1-111">Oznacza to, że kontekst deklaracji dla `Protected` elementu musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, strukturą ani procedurą.</span><span class="sxs-lookup"><span data-stu-id="f48c1-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="f48c1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f48c1-112">See also</span></span>

- [<span data-ttu-id="f48c1-113">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="f48c1-113">Public</span></span>](public.md)
- [<span data-ttu-id="f48c1-114">Chronione</span><span class="sxs-lookup"><span data-stu-id="f48c1-114">Protected</span></span>](protected.md)
- [<span data-ttu-id="f48c1-115">Osoby</span><span class="sxs-lookup"><span data-stu-id="f48c1-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="f48c1-116">Użytek</span><span class="sxs-lookup"><span data-stu-id="f48c1-116">Private</span></span>](private.md)
- [<span data-ttu-id="f48c1-117">Prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="f48c1-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="f48c1-118">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f48c1-118">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="f48c1-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="f48c1-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="f48c1-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="f48c1-120">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f48c1-121">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="f48c1-121">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
