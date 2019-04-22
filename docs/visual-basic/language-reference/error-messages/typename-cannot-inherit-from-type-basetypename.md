---
title: Element „<typename>” nie może dziedziczyć po elemencie <type> „<basetypename>", ponieważ rozszerza dostęp podstawowego elementu <type> poza zestawem
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838953"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="4ba7d-102">"\<typename >' nie może dziedziczyć z \<typu >"\<basetypename > ", ponieważ rozszerza on dostęp podstawowego \<typ > spoza zestawu</span><span class="sxs-lookup"><span data-stu-id="4ba7d-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>
<span data-ttu-id="4ba7d-103">Klasa lub interfejs dziedziczy z klasy bazowej lub interfejsu, lecz jest mniej restrykcyjny poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="4ba7d-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="4ba7d-104">Na przykład `Public` interfejs dziedziczy z `Friend` interfejsu, lub `Protected` klasa dziedziczy `Private` klasy.</span><span class="sxs-lookup"><span data-stu-id="4ba7d-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="4ba7d-105">Udostępnia to klasy bazowej lub interfejsu, aby uzyskać dostęp poza poziomem zamierzone.</span><span class="sxs-lookup"><span data-stu-id="4ba7d-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="4ba7d-106">**Identyfikator błędu:** BC30910</span><span class="sxs-lookup"><span data-stu-id="4ba7d-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ba7d-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4ba7d-107">To correct this error</span></span>  
  
-   <span data-ttu-id="4ba7d-108">Zmień poziom dostępu pochodne klasy lub interfejsu restrykcyjną co najmniej tak jak w przypadku klasy bazowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4ba7d-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="4ba7d-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="4ba7d-109">-or-</span></span>  
  
-   <span data-ttu-id="4ba7d-110">Jeśli potrzebujesz mniej restrykcyjny poziom dostępu, Usuń `Inherits` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4ba7d-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="4ba7d-111">Nie można dziedziczyć bardziej ograniczony klasy bazowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4ba7d-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba7d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ba7d-112">See also</span></span>

- [<span data-ttu-id="4ba7d-113">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4ba7d-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="4ba7d-114">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="4ba7d-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="4ba7d-115">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4ba7d-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="4ba7d-116">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ba7d-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
