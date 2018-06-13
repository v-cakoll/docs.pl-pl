---
title: '&#39;&lt;membername&gt; &#39; nie może ujawnić typu &#39; &lt;typename&gt; &#39; poza projektem za pomocą &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 36add48ebee2d1804921eeeec0b59cdd4cbafecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588096"
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="8d08a-102">&#39;&lt;membername&gt; &#39; nie może ujawnić typu &#39; &lt;typename&gt; &#39; poza projektem za pomocą &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="8d08a-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="8d08a-103">Zmienna, parametr procedury lub funkcji, zwracany jest ujawniany poza jego kontenera, ale jest zadeklarowany jako typ, który nie może być wystawiona poza kontenera.</span><span class="sxs-lookup"><span data-stu-id="8d08a-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="8d08a-104">W poniższym kodzie szkielet pokazano sytuację, który generuje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="8d08a-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="8d08a-105">Typ, który jest zadeklarowana `Protected`, `Friend`, `Protected Friend`, lub `Private` ma mieć ograniczony dostęp poza kontekstem jego deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8d08a-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="8d08a-106">Używać go jako dane typu zmienną o mniej ograniczonym dostępie środki tego celu.</span><span class="sxs-lookup"><span data-stu-id="8d08a-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="8d08a-107">W poprzednim kodzie szkielet `exposedVar` jest `Public` i wystawi `privateClass` do kodu, który nie ma do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="8d08a-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="8d08a-108">**Identyfikator błędu:** BC30909</span><span class="sxs-lookup"><span data-stu-id="8d08a-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8d08a-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8d08a-109">To correct this error</span></span>  
  
-   <span data-ttu-id="8d08a-110">Zmień poziom dostępu do zmiennej, parametr procedury lub funkcji zwrócić się co najmniej stosować jak największe restrykcje poziom dostępu do jego typu danych.</span><span class="sxs-lookup"><span data-stu-id="8d08a-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d08a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d08a-111">See Also</span></span>  
 [<span data-ttu-id="8d08a-112">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d08a-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
