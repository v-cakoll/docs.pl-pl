---
title: '&#39;&lt;Element TypeName&gt; &#39; nie może dziedziczyć z &lt;typu&gt; &#39; &lt;basetypename&gt; &#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestawem'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 108025132bdd0fa86df5ed142aaa39c7b7e18062
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556486"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="65b45-102">&#39;&lt;Element TypeName&gt; &#39; nie może dziedziczyć z &lt;typu&gt; &#39; &lt;basetypename&gt; &#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestawem</span><span class="sxs-lookup"><span data-stu-id="65b45-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="65b45-103">Klasa lub interfejs dziedziczy z klasy bazowej lub interfejsu, lecz jest mniej restrykcyjny poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="65b45-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="65b45-104">Na przykład `Public` interfejs dziedziczy z `Friend` interfejsu, lub `Protected` klasa dziedziczy `Private` klasy.</span><span class="sxs-lookup"><span data-stu-id="65b45-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="65b45-105">Udostępnia to klasy bazowej lub interfejsu, aby uzyskać dostęp poza poziomem zamierzone.</span><span class="sxs-lookup"><span data-stu-id="65b45-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="65b45-106">**Identyfikator błędu:** BC30910</span><span class="sxs-lookup"><span data-stu-id="65b45-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65b45-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="65b45-107">To correct this error</span></span>  
  
-   <span data-ttu-id="65b45-108">Zmień poziom dostępu pochodne klasy lub interfejsu restrykcyjną co najmniej tak jak w przypadku klasy bazowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="65b45-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="65b45-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="65b45-109">-or-</span></span>  
  
-   <span data-ttu-id="65b45-110">Jeśli potrzebujesz mniej restrykcyjny poziom dostępu, Usuń `Inherits` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="65b45-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="65b45-111">Nie można dziedziczyć bardziej ograniczony klasy bazowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="65b45-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b45-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65b45-112">See also</span></span>
- [<span data-ttu-id="65b45-113">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="65b45-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="65b45-114">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="65b45-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="65b45-115">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="65b45-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="65b45-116">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65b45-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
