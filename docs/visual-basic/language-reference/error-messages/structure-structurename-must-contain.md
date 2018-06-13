---
title: Struktura &#39; &lt;structurename&gt; &#39; musi zawierać co najmniej jedno wystąpienie zmiennej członkowskiej lub co najmniej jedno wystąpienie deklaracja zdarzenia nie jest oznaczony &#39;niestandardowe&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594503"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="6d687-102">Struktura &#39; &lt;structurename&gt; &#39; musi zawierać co najmniej jedno wystąpienie zmiennej członkowskiej lub co najmniej jedno wystąpienie deklaracja zdarzenia nie jest oznaczony &#39;niestandardowe&#39;</span><span class="sxs-lookup"><span data-stu-id="6d687-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="6d687-103">Definicji struktury nie zawiera żadnych zmiennych udostępniana lub udostępniana standardowych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6d687-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="6d687-104">Co struktura musi mieć zmiennej lub zdarzenie, które ma zastosowanie do każdego wystąpienia określonych (udostępniana), a nie do wszystkich wystąpień zbiorczo ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="6d687-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="6d687-105">Stałe udostępniana, właściwości i procedury nie spełniają to wymaganie.</span><span class="sxs-lookup"><span data-stu-id="6d687-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="6d687-106">Ponadto, jeśli istnieją żadnych udostępniana zmiennych i tylko jedno zdarzenie udostępniana, zdarzenie nie może być `Custom` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6d687-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="6d687-107">**Identyfikator błędu:** BC30941</span><span class="sxs-lookup"><span data-stu-id="6d687-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6d687-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6d687-108">To correct this error</span></span>  
  
-   <span data-ttu-id="6d687-109">Zdefiniuj co najmniej jedną zmienną lub zdarzenie, które nie jest `Shared`.</span><span class="sxs-lookup"><span data-stu-id="6d687-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="6d687-110">Po zdefiniowaniu tylko jedno zdarzenie musi być standardowych, jak również udostępniana.</span><span class="sxs-lookup"><span data-stu-id="6d687-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d687-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d687-111">See Also</span></span>  
 [<span data-ttu-id="6d687-112">Struktury</span><span class="sxs-lookup"><span data-stu-id="6d687-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6d687-113">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="6d687-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="6d687-114">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6d687-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
