---
title: Struktura &#39; &lt;structurename&gt; &#39; musi zawierać co najmniej jedną zmienną elementu członkowskiego wystąpienia lub co najmniej jedną deklarację wystąpienia zdarzenia niezaznaczonych &#39;niestandardowe&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: d8c654c212a459d40c6cf20cd62c3e0fcda8511b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603784"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="a4ce8-102">Struktura &#39; &lt;structurename&gt; &#39; musi zawierać co najmniej jedną zmienną elementu członkowskiego wystąpienia lub co najmniej jedną deklarację wystąpienia zdarzenia niezaznaczonych &#39;niestandardowe&#39;</span><span class="sxs-lookup"><span data-stu-id="a4ce8-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="a4ce8-103">Definicja struktury nie ma żadnych zmiennych nieudostępnionych lub nieudostępnionych, niestandardowych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a4ce8-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="a4ce8-104">Co struktura musi być zmienną lub zdarzenie, które mają zastosowanie do każdego wystąpienia określonych (udostępniana), a nie do wszystkich wystąpień zbiorczo ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="a4ce8-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="a4ce8-105">Stałe nieudostępnionych, właściwości i procedury nie spełniają tego wymagania.</span><span class="sxs-lookup"><span data-stu-id="a4ce8-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="a4ce8-106">Ponadto w przypadku żadnych zmiennych nieudostępnionych i tylko jedno zdarzenie nieudostępnionych, to zdarzenie nie może być `Custom` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a4ce8-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="a4ce8-107">**Identyfikator błędu:** BC30941</span><span class="sxs-lookup"><span data-stu-id="a4ce8-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a4ce8-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a4ce8-108">To correct this error</span></span>  
  
-   <span data-ttu-id="a4ce8-109">Zdefiniuj co najmniej jedną zmienną lub zdarzeń, który nie jest `Shared`.</span><span class="sxs-lookup"><span data-stu-id="a4ce8-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="a4ce8-110">Jeśli zdefiniujesz tylko jedno zdarzenie, musi ona standardowych, jak również nieudostępnionych.</span><span class="sxs-lookup"><span data-stu-id="a4ce8-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ce8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4ce8-111">See also</span></span>
- [<span data-ttu-id="a4ce8-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="a4ce8-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a4ce8-113">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="a4ce8-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a4ce8-114">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a4ce8-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
