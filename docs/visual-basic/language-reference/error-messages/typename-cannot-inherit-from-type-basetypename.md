---
title: '&#39;&lt;Właściwość TypeName&gt; &#39; nie może dziedziczyć po &lt;typu&gt; &#39; &lt;basetypename&gt; &#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestaw'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="1717b-102">&#39;&lt;Właściwość TypeName&gt; &#39; nie może dziedziczyć po &lt;typu&gt; &#39; &lt;basetypename&gt; &#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestaw</span><span class="sxs-lookup"><span data-stu-id="1717b-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="1717b-103">Klasy lub interfejsu dziedziczy z klasy podstawowej lub interfejsu, ale ma mniej restrykcyjną poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="1717b-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="1717b-104">Na przykład `Public` dziedziczy interfejs `Friend` interfejsu, lub `Protected` klasa dziedziczy `Private` klasy.</span><span class="sxs-lookup"><span data-stu-id="1717b-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="1717b-105">Udostępnia to klasy podstawowej lub interfejsu dostępu poza poziomem przeznaczone do.</span><span class="sxs-lookup"><span data-stu-id="1717b-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="1717b-106">**Identyfikator błędu:** BC30910</span><span class="sxs-lookup"><span data-stu-id="1717b-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1717b-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1717b-107">To correct this error</span></span>  
  
-   <span data-ttu-id="1717b-108">Zmień poziom dostępu do klasy pochodnej lub interfejsu się co najmniej stosować jak największe restrykcje klasy podstawowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1717b-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="1717b-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="1717b-109">-or-</span></span>  
  
-   <span data-ttu-id="1717b-110">Jeśli potrzebujesz poziom dostępu mniej restrykcyjny, Usuń `Inherits` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1717b-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="1717b-111">Nie można dziedziczyć bardziej ograniczony w klasie podstawowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1717b-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1717b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1717b-112">See Also</span></span>  
 [<span data-ttu-id="1717b-113">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1717b-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="1717b-114">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1717b-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="1717b-115">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1717b-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="1717b-116">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1717b-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
