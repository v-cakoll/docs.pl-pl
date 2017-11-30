---
title: "&#39; &lt;membername&gt;&#39; nie może ujawnić typu &#39;&lt; Właściwość TypeName&gt;&#39; poza projektem za pomocą &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords: BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd64c815286a5ffec111bcf1f68674a8e3558403
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a>&#39; &lt;membername&gt;&#39; nie może ujawnić typu &#39;&lt; Właściwość TypeName&gt;&#39; poza projektem za pomocą &lt;containertype&gt; &#39;&lt; containertypename&gt;&#39;
Zmienna, parametr procedury lub funkcji, zwracany jest ujawniany poza jego kontenera, ale jest zadeklarowany jako typ, który nie może być wystawiona poza kontenera.  
  
 W poniższym kodzie szkielet pokazano sytuację, który generuje ten błąd.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Typ, który jest zadeklarowana `Protected`, `Friend`, `Protected Friend`, lub `Private` ma mieć ograniczony dostęp poza kontekstem jego deklaracji. Używać go jako dane typu zmienną o mniej ograniczonym dostępie środki tego celu. W poprzednim kodzie szkielet `exposedVar` jest `Public` i wystawi `privateClass` do kodu, który nie ma do niego dostęp.  
  
 **Identyfikator błędu:** BC30909  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień poziom dostępu do zmiennej, parametr procedury lub funkcji zwrócić się co najmniej stosować jak największe restrykcje poziom dostępu do jego typu danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
