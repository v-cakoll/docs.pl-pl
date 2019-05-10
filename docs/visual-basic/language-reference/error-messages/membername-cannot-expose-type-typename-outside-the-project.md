---
title: Element „<membername>” nie może ujawniać typu „<typename>” poza projektem za pomocą elementu <containertype> „<containertypename>”
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: cb5191442ed8d3ee47c5116b10740e277ffa5bac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661915"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="e0666-102">"\<membername >' nie może ujawnić typu"\<typename > "poza projektem za pomocą \<containertype >"\<containertypename > "</span><span class="sxs-lookup"><span data-stu-id="e0666-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="e0666-103">Zmiennej, parametr procedury lub funkcji, zwracany jest widoczna poza jej kontenerem, ale jest zadeklarowany jako typ, który nie muszą być widoczne na zewnątrz kontenera.</span><span class="sxs-lookup"><span data-stu-id="e0666-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="e0666-104">Poniższy kod szkielet przedstawia sytuację, która generuje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="e0666-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="e0666-105">Typ, który jest zadeklarowany jako `Protected`, `Friend`, `Protected Friend`, lub `Private` ma ograniczony dostęp poza kontekstem jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="e0666-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="e0666-106">On używany jako dane typu zmiennej mniej ograniczony dostęp będzie w tym celu pokonania.</span><span class="sxs-lookup"><span data-stu-id="e0666-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="e0666-107">W poprzednim kodzie szkielet `exposedVar` jest `Public` i wystawi `privateClass` do kodu, które nie powinny mieć do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="e0666-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="e0666-108">**Identyfikator błędu:** BC30909</span><span class="sxs-lookup"><span data-stu-id="e0666-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0666-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e0666-109">To correct this error</span></span>  
  
- <span data-ttu-id="e0666-110">Zmień poziom dostępu do zmiennej, parametr procedury lub funkcji, zwróć się do co najmniej tak restrykcyjne uprawnienia na poziomie dostępu do jego typu danych.</span><span class="sxs-lookup"><span data-stu-id="e0666-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0666-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0666-111">See also</span></span>

- [<span data-ttu-id="e0666-112">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e0666-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
