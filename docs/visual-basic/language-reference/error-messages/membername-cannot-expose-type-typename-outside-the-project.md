---
title: Element „<membername>” nie może ujawniać typu „<typename>” poza projektem za pomocą elementu <containertype> „<containertypename>”
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 16f579a05236ba8977a071cb08068be8e98799f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818348"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a>"\<membername >' nie może ujawnić typu"\<typename > "poza projektem za pomocą \<containertype >"\<containertypename > "
Zmiennej, parametr procedury lub funkcji, zwracany jest widoczna poza jej kontenerem, ale jest zadeklarowany jako typ, który nie muszą być widoczne na zewnątrz kontenera.  
  
 Poniższy kod szkielet przedstawia sytuację, która generuje ten błąd.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Typ, który jest zadeklarowany jako `Protected`, `Friend`, `Protected Friend`, lub `Private` ma ograniczony dostęp poza kontekstem jego deklaracji. On używany jako dane typu zmiennej mniej ograniczony dostęp będzie w tym celu pokonania. W poprzednim kodzie szkielet `exposedVar` jest `Public` i wystawi `privateClass` do kodu, które nie powinny mieć do niego dostęp.  
  
 **Identyfikator błędu:** BC30909  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień poziom dostępu do zmiennej, parametr procedury lub funkcji, zwróć się do co najmniej tak restrykcyjne uprawnienia na poziomie dostępu do jego typu danych.  
  
## <a name="see-also"></a>Zobacz także

- [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
