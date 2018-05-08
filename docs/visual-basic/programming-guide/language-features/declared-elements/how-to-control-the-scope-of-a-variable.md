---
title: 'Porady: kontrolowanie zakresu zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 6e8d1178398711226b88fee7e6defd5162b91fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Porady: kontrolowanie zakresu zmiennej (Visual Basic)
Zazwyczaj jest zmienną w *zakres*, czy widoczny dla odwołania w całym regionie ją zadeklarować. W niektórych przypadkach zmiennej w *poziom dostępu* mogą mieć wpływ na jego zakres.  
  
 Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Zakres na poziomie procedurę lub blok  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Aby wyświetlić tylko w bloku zmiennej  
  
-   Miejsce [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zmiennej między inicjowanie i kończenie instrukcji deklaracji tego bloku, na przykład między `For` i `Next` instrukcje `For` pętli.  
  
     Mogą odwoływać się do zmiennej tylko z wewnątrz bloku.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Aby wyświetlić tylko w obrębie procedury zmiennej  
  
-   Miejsce `Dim` instrukcji dla zmiennej wewnątrz procedury, ale poza bloku (takich jak `With`... `End With` bloku).  
  
     Mogą odwoływać się do zmiennej tylko z wewnątrz procedury, między innymi wewnątrz bloku zawarty w procedurze.  
  
## <a name="scope-at-module-or-namespace-level"></a>Zakres na poziomie Namespace lub modułu  
 Dla wygody pojedynczy termin *poziom modułu* dotyczą modułów, klasy i struktury. Poziom dostępu do zmiennej poziomu modułu określa jej zakres. Przestrzeń nazw, który zawiera modułu, klasy lub struktury wpływ również zakres.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Aby wyświetlić zmiennej w całym modułu, klasy lub struktury  
  
1.  Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.  
  
2.  Obejmują [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe w `Dim` instrukcji.  
  
3.  Można odwołać się do zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, ale nie z poza nią.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Aby zmienna widoczne w przestrzeni nazw  
  
1.  Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza dowolnej procedury.  
  
2.  Obejmują [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) lub [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w `Dim` instrukcji.  
  
3.  Mogą odwoływać się do zmiennej z dowolnego miejsca w przestrzeni nazw zawierającej modułu, klasy lub struktury.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie deklaruje zmienną na poziomie modułu i ogranicza ich widoczność jej do kodu w module.  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 W poprzednim przykładzie wszystkie procedury zdefiniowanego w module `demonstrateScope` mogą odwoływać się do `String` zmiennej `strMsg`. Gdy `usePrivateVariable` procedura jest wywoływana, wyświetla zawartość zmiennej ciągu `strMsg` w oknie dialogowym.  
  
 Z następującą modyfikacją jak w poprzednim przykładzie zmienna string `strMsg` mogą być przywoływane przez kod w dowolnym miejscu jego deklaracji przestrzeni nazw.  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Im bardziej doprecyzowane zakres zmiennej mniej możliwości, jakie masz przypadkowo odwołujące się do niego zamiast inna zmienna o takiej samej nazwie. Można również zminimalizować problemy odwołanie do dopasowania.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Im bardziej doprecyzowane zakresu zmiennej z niego korzystać im mniejsza ryzyko, które złośliwy kod może wykonać niewłaściwy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
