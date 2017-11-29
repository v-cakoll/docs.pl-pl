---
title: "Porady: kontrolowanie dostępności zmiennej (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 004fb101661fadeaee084e1f9374ca8332ac7234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Porady: kontrolowanie dostępności zmiennej (Visual Basic)
Kontrolowanie dostępności zmiennej, określając jego *poziom dostępu*. Poziom dostępu określa, jaki kod ma uprawnienie do odczytu lub zapisu do zmiennej.  
  
-   *Zmienne Członkowskie* (zdefiniowane na poziomie modułu w i poza dowolnej procedury) domyślnie dostęp publiczny, co oznacza kodu, który można wyświetlić ich mogą uzyskiwać do nich dostęp. Można to zmienić, określając modyfikatora dostępu.  
  
-   *Zmienne lokalne* (zdefiniowany wewnątrz procedury) nominalnie mają dostęp publiczny, mimo że tylko kodu w ramach ich procedury mogą uzyskiwać do nich dostęp. Nie można zmienić poziom dostępu do zmiennej lokalnej, ale można zmienić poziom dostępu tej procedury, która go zawiera.  
  
 Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Prywatne i publiczne dostępu  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Aby zmienna dostępny tylko w obrębie swojego modułu, klasy lub struktury  
  
1.  Miejsce [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.  
  
2.  Obejmują [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe w `Dim` instrukcji.  
  
     Można odczytu lub zapisu do zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, ale nie z poza nią.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Aby udostępnić zmienną z kodu, który może go wyświetlać  
  
1.  Dla zmiennej członkowskiej, umieść `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.  
  
2.  Obejmują [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w `Dim` instrukcji.  
  
     Można odczytu lub zapisu do zmiennej kodu, który współdziała z tym zestawem.  
  
 —lub—  
  
1.  Do zmiennej lokalnej, umieść `Dim` instrukcji dla zmiennej wewnątrz procedury.  
  
2.  Nie dołączaj `Public` — słowo kluczowe w `Dim` instrukcji.  
  
     Można odczytu lub zapisu do zmiennej z dowolnego miejsca w ramach procedury, ale nie z poza nią.  
  
## <a name="protected-and-friend-access"></a>Protected Friend dostępu i  
 Można ograniczyć poziom dostępu do zmiennej do swojej klasy i wszystkie klasy pochodne, lub jego zestaw. Można również określić Unii tych ograniczeń, który zezwala na dostęp z kodu w dowolnej klasy pochodnej lub w innym miejscu, w tym samym zestawie. Określ ten Unii łącząc `Protected` i `Friend` słów kluczowych w tej samej deklaracji.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Aby zmienna dostępny tylko w obrębie swojej klasy i wszystkie klasy pochodne  
  
1.  Miejsce `Dim` instrukcji dla zmiennej wewnątrz klasy, ale poza dowolnej procedury.  
  
2.  Obejmują [chronione](../../../../visual-basic/language-reference/modifiers/protected.md) — słowo kluczowe w `Dim` instrukcji.  
  
     Można odczytu lub zapisu do zmiennej z dowolnego miejsca w klasie, a także z poziomu dowolnej klasy pochodnej, ale nie z poza dowolnej klasy w łańcuchu pochodnym.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Aby zmienna dostępny tylko w obrębie tego samego zestawu  
  
1.  Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.  
  
2.  Obejmują [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) — słowo kluczowe w `Dim` instrukcji.  
  
     Można odczytu lub zapisu do zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, a także z dowolnego kodu, w tym samym zestawie, ale nie z poza zestaw.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono deklaracje zmiennych o `Public`, `Protected`, `Friend`, `Protected Friend`, i `Private` poziomy dostępu. Należy pamiętać, że w przypadku `Dim` instrukcji określa poziom dostępu, nie musisz uwzględnić `Dim` — słowo kluczowe.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Bardziej restrykcyjne poziom dostępu do zmiennej z niego korzystać im mniejsza ryzyko, które złośliwy kod może wykonać niewłaściwy.  
  
## <a name="see-also"></a>Zobacz też  
 [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Dim — instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Publiczna](../../../../visual-basic/language-reference/modifiers/public.md)  
 [Chronione](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Prywatne](../../../../visual-basic/language-reference/modifiers/private.md)
