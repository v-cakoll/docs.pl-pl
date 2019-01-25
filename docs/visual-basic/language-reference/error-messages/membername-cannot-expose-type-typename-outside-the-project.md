---
title: '&#39;&lt;membername&gt; &#39; nie może ujawnić typu &#39; &lt;typename&gt; &#39; poza projektem za pomocą &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 39d316aca5ec306de4b1e43e2eb2d1495f5525d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672347"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="96123-102">&#39;&lt;membername&gt; &#39; nie może ujawnić typu &#39; &lt;typename&gt; &#39; poza projektem za pomocą &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="96123-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="96123-103">Zmiennej, parametr procedury lub funkcji, zwracany jest widoczna poza jej kontenerem, ale jest zadeklarowany jako typ, który nie muszą być widoczne na zewnątrz kontenera.</span><span class="sxs-lookup"><span data-stu-id="96123-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="96123-104">Poniższy kod szkielet przedstawia sytuację, która generuje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="96123-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="96123-105">Typ, który jest zadeklarowany jako `Protected`, `Friend`, `Protected Friend`, lub `Private` ma ograniczony dostęp poza kontekstem jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="96123-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="96123-106">On używany jako dane typu zmiennej mniej ograniczony dostęp będzie w tym celu pokonania.</span><span class="sxs-lookup"><span data-stu-id="96123-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="96123-107">W poprzednim kodzie szkielet `exposedVar` jest `Public` i wystawi `privateClass` do kodu, które nie powinny mieć do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="96123-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="96123-108">**Identyfikator błędu:** BC30909</span><span class="sxs-lookup"><span data-stu-id="96123-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="96123-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="96123-109">To correct this error</span></span>  
  
-   <span data-ttu-id="96123-110">Zmień poziom dostępu do zmiennej, parametr procedury lub funkcji, zwróć się do co najmniej tak restrykcyjne uprawnienia na poziomie dostępu do jego typu danych.</span><span class="sxs-lookup"><span data-stu-id="96123-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96123-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96123-111">See also</span></span>
- [<span data-ttu-id="96123-112">Poziomy dostępu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96123-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
