---
title: Chronione Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 331c63dc290d4096e8158f265ee869b47743a273
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151778"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="47351-102">Chronione Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47351-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="47351-103">`Protected Friend` Kombinacja słów kluczowych jest modyfikator dostępu składowej.</span><span class="sxs-lookup"><span data-stu-id="47351-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="47351-104">Wiąże się zarówno [Friend](friend.md) dostępu i [chronione](protected.md) dostęp do elementów zadeklarowanych, dzięki czemu są one dostępne z dowolnego miejsca na tym samym zestawie, z własnych klas i klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="47351-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="47351-105">Można określić `Protected Friend` tylko na składowych klas; nie można zastosować `Protected Friend` do elementów członkowskich struktury ponieważ struktury nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="47351-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="47351-106">W programie Visual Studio, wybierając opcję pomocy F1 na `protected friend` zapewnia pomoc dla dowolnego [chronione](protected.md) lub [friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="47351-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="47351-107">Środowisko IDE wybiera jednego tokenu pod kursorem, a nie jako wyraz złożony.</span><span class="sxs-lookup"><span data-stu-id="47351-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="47351-108">reguły</span><span class="sxs-lookup"><span data-stu-id="47351-108">Rules</span></span>

- <span data-ttu-id="47351-109">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="47351-109">**Declaration Context.**</span></span> <span data-ttu-id="47351-110">Możesz użyć `Protected Friend` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="47351-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="47351-111">Oznacza to, że kontekst deklaracji `Protected` element musi być klasą i nie może być plik źródłowy, przestrzeń nazw, interfejsu, moduł, struktura lub procedury.</span><span class="sxs-lookup"><span data-stu-id="47351-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 

## <a name="see-also"></a><span data-ttu-id="47351-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47351-112">See also</span></span>

- [<span data-ttu-id="47351-113">Public</span><span class="sxs-lookup"><span data-stu-id="47351-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="47351-114">Protected</span><span class="sxs-lookup"><span data-stu-id="47351-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="47351-115">Friend</span><span class="sxs-lookup"><span data-stu-id="47351-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="47351-116">Private</span><span class="sxs-lookup"><span data-stu-id="47351-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="47351-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="47351-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="47351-118">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47351-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="47351-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="47351-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="47351-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="47351-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="47351-121">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="47351-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
