---
title: 'Instrukcje: Kontrolowanie zakresu zmiennej (Visual Basic)'
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
ms.openlocfilehash: ef7957a991718112fe01c4fa3a85f29b9226abd3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818726"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Instrukcje: Kontrolowanie zakresu zmiennej (Visual Basic)
Zazwyczaj jest zmienną *zakres*, lub widoczny dla odwołania w całym regionie, w którym trzeba je zadeklarować. W niektórych przypadkach zmienna firmy *poziom dostępu* mogą mieć wpływ na jego zakres.  
  
 Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Zakresu na poziomie bloku lub procedury  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Aby uwidocznić zmienną tylko w obrębie bloku  
  
-   Miejsce [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) zmiennej między inicjowanie i kończenie instrukcje deklaracji tego bloku, na przykład między `For` i `Next` instrukcje `For` pętli.  
  
     Można odwołać się do zmiennej tylko z w obrębie bloku.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Aby uwidocznić zmienną tylko w obrębie procedury  
  
-   Miejsce `Dim` instrukcji dla zmiennej wewnątrz procedury, ale poza bloku (takie jak `With`... `End With` bloku).  
  
     Można odwołać się do zmiennej tylko z w ramach procedury, między innymi wewnątrz bloku znajdujących się w procedurze.  
  
## <a name="scope-at-module-or-namespace-level"></a>Zakresu na poziomie Namespace lub modułu  
 Dla wygody pojedynczego terminu *poziom modułu* stosuje się jednakowo do modułów, klas i struktur. Poziom dostępu zmiennej poziomu modułu określa jego zakres. Przestrzeń nazw zawierająca modułu, klasy lub struktury również wpływ na zakres.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Aby uwidocznić zmienną w całym modułu, klasy lub struktury  
  
1.  Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza programem dowolnej procedury.  
  
2.  Obejmują [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe w `Dim` instrukcji.  
  
3.  Można odwołać się do zmiennej z dowolnego miejsca w ramach modułu, klasy lub struktury, ale nie z poza nim.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Aby uwidocznić zmienną w całej przestrzeni nazw  
  
1.  Miejsce `Dim` instrukcji dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza programem dowolnej procedury.  
  
2.  Obejmują [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) lub [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w `Dim` instrukcji.  
  
3.  Można odwołać się do zmiennej z dowolnego miejsca w przestrzeni nazw, zawierające modułu, klasy lub struktury.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje zmienną na poziomie modułu i ogranicza jego widoczność dla kodu w module.  
  
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
  
 W poprzednim przykładzie, wszystkie procedury zdefiniowanego w module `demonstrateScope` mogą odwoływać się do `String` zmiennej `strMsg`. Gdy `usePrivateVariable` procedura jest wywoływana, wyświetla się zawartość zmiennej ciągu `strMsg` w oknie dialogowym.  
  
 Z następującą modyfikacją do poprzedniego przykładu, zmiennej ciągu `strMsg` mogą być przywoływane przez kod w dowolnym miejscu w przestrzeni nazw w jego deklaracji.  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Im bardziej doprecyzowane zakres zmiennej, mniej możliwości, jakie masz przypadkowo odwołując się do niego zamiast inną zmienną o takiej samej nazwie. Można także zminimalizować problemy, odwołanie do dopasowania.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Im bardziej doprecyzowane zakres zmiennej z niego korzystać mniejszy szanse, że złośliwy kod może być niepoprawne.  
  
## <a name="see-also"></a>Zobacz także

- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
