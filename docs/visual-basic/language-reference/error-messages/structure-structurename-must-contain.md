---
title: Struktura „<structurename>" musi zawierać co najmniej jedną zmienną elementu członkowskiego lub co najmniej jedną deklarację wystąpienia zdarzenia, która nie jest oznaczona „Custom"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 7b5bda7b1a2ae37eb509c736deae1652dc5e6ab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374021"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="0b60e-102">Struktura „\<structurename>" musi zawierać co najmniej jedną zmienną elementu członkowskiego lub co najmniej jedną deklarację wystąpienia zdarzenia, która nie jest oznaczona „Custom"</span><span class="sxs-lookup"><span data-stu-id="0b60e-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>
<span data-ttu-id="0b60e-103">Definicja struktury nie zawiera żadnych zmiennych nieudostępnionych lub nieudostępnianych zdarzeń nieniestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0b60e-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="0b60e-104">Każda struktura musi mieć zmienną lub zdarzenie, które stosuje się do każdego określonego wystąpienia (nieudostępnione) zamiast do wszystkich wystąpień zbiorczo ([współużytkowane](../modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="0b60e-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="0b60e-105">Nieudostępnione stałe, właściwości i procedury nie spełniają tego wymagania.</span><span class="sxs-lookup"><span data-stu-id="0b60e-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="0b60e-106">Ponadto, jeśli nie istnieją zmienne nieudostępnione i tylko jedno nieudostępnione zdarzenie, to zdarzenie nie może być `Custom` zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="0b60e-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="0b60e-107">**Identyfikator błędu:** BC30941</span><span class="sxs-lookup"><span data-stu-id="0b60e-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0b60e-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0b60e-108">To correct this error</span></span>  
  
- <span data-ttu-id="0b60e-109">Zdefiniuj co najmniej jedną zmienną lub zdarzenie, które nie jest `Shared` .</span><span class="sxs-lookup"><span data-stu-id="0b60e-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="0b60e-110">Jeśli zdefiniujesz tylko jedno zdarzenie, musi ono być nieniestandardowe i nieudostępnione.</span><span class="sxs-lookup"><span data-stu-id="0b60e-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b60e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b60e-111">See also</span></span>

- [<span data-ttu-id="0b60e-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="0b60e-112">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0b60e-113">Instrukcje: Deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="0b60e-113">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="0b60e-114">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="0b60e-114">Structure Statement</span></span>](../statements/structure-statement.md)
