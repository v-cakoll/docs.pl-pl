---
title: 'Porady: kontrolowanie dostępności zmiennej (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 27ee5d3405ea24c0754cffa85e9b89b2ac561e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Porady: kontrolowanie dostępności zmiennej (Visual Basic)
Kontrolowanie dostępności zmiennej, określając jego *poziom dostępu*. Poziom dostępu określa, jaki kod ma uprawnienie do odczytu lub zapisu do zmiennej.  
  
-   *Zmienne Członkowskie* (zdefiniowane na poziomie modułu w i poza dowolnej procedury) domyślnie dostęp publiczny, co oznacza kodu, który można wyświetlić ich mogą uzyskiwać do nich dostęp. Można to zmienić, określając modyfikatora dostępu.  
  
-   *Zmienne lokalne* (zdefiniowany wewnątrz procedury) nominalnie mają dostęp publiczny, mimo że tylko kodu w ramach ich procedury mogą uzyskiwać do nich dostęp. Nie można zmienić poziom dostępu do zmiennej lokalnej, ale można zmienić poziom dostępu tej procedury, która go zawiera.  
  
 Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
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
 [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../../visual-basic/language-reference/modifiers/private.md)
