---
title: Struktura „<structurename>" musi zawierać co najmniej jedną zmienną elementu członkowskiego lub co najmniej jedną deklarację wystąpienia zdarzenia, która nie jest oznaczona „Custom"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 598aef3943a53ee6eb97064819c9128de1839f52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055111"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="46469-102">Struktura "\<structurename >" musi zawierać co najmniej jedną zmienną elementu członkowskiego wystąpienia lub co najmniej jedną deklarację wystąpienia zdarzenia nie jest oznaczona "Custom"</span><span class="sxs-lookup"><span data-stu-id="46469-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>
<span data-ttu-id="46469-103">Definicja struktury nie ma żadnych zmiennych nieudostępnionych lub nieudostępnionych, niestandardowych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="46469-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="46469-104">Co struktura musi być zmienną lub zdarzenie, które mają zastosowanie do każdego wystąpienia określonych (udostępniana), a nie do wszystkich wystąpień zbiorczo ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="46469-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="46469-105">Stałe nieudostępnionych, właściwości i procedury nie spełniają tego wymagania.</span><span class="sxs-lookup"><span data-stu-id="46469-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="46469-106">Ponadto w przypadku żadnych zmiennych nieudostępnionych i tylko jedno zdarzenie nieudostępnionych, to zdarzenie nie może być `Custom` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="46469-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="46469-107">**Identyfikator błędu:** BC30941</span><span class="sxs-lookup"><span data-stu-id="46469-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46469-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="46469-108">To correct this error</span></span>  
  
- <span data-ttu-id="46469-109">Zdefiniuj co najmniej jedną zmienną lub zdarzeń, który nie jest `Shared`.</span><span class="sxs-lookup"><span data-stu-id="46469-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="46469-110">Jeśli zdefiniujesz tylko jedno zdarzenie, musi ona standardowych, jak również nieudostępnionych.</span><span class="sxs-lookup"><span data-stu-id="46469-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46469-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46469-111">See also</span></span>

- [<span data-ttu-id="46469-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="46469-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="46469-113">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="46469-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="46469-114">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="46469-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
