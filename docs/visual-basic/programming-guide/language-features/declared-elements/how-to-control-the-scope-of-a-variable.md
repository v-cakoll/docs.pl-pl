---
title: 'Porady: kontrolowanie zakresu zmiennej'
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
ms.openlocfilehash: 0ee6ce183310aa836ecdbbc0bc819e0e83d1872d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345376"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Porady: kontrolowanie zakresu zmiennej (Visual Basic)
Zwykle zmienna znajduje się w *zakresie*lub jest widoczna dla odwołania w całym regionie, w którym jest zadeklarowana. W niektórych przypadkach *poziom dostępu* zmiennej może mieć wpływ na jego zakres.  
  
 Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Zakres na poziomie bloku lub procedury  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Aby zmienna była widoczna tylko w bloku  
  
- Umieść [instrukcję Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) dla zmiennej między instrukcjami inicjującymi i kończącymi deklaracji tego bloku, na przykład między instrukcjami `For` i `Next` pętli `For`.  
  
     Można odwołać się do zmiennej tylko z poziomu bloku.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Aby zmienna była widoczna tylko w ramach procedury  
  
- Umieść instrukcję `Dim` dla zmiennej wewnątrz procedury, ale poza blokami (takimi jak `With`...`End With` bloku).  
  
     Można odwołać się do zmiennej tylko z wewnątrz procedury, w tym w dowolnym bloku zawartym w procedurze.  
  
## <a name="scope-at-module-or-namespace-level"></a>Zakres na poziomie modułu lub przestrzeni nazw  
 Dla wygody poziom jednoterminowego *modułu* jest stosowany równomiernie dla modułów, klas i struktur. Poziom dostępu zmiennej poziomu modułu określa jej zakres. Przestrzeń nazw, która zawiera moduł, klasę lub strukturę, ma także wpływ na zakres.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Aby uczynić zmienną widoczną w całym module, klasie lub strukturze  
  
1. Umieść instrukcję `Dim` dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.  
  
2. Dołącz [prywatne](../../../../visual-basic/language-reference/modifiers/private.md) słowo kluczowe do instrukcji `Dim`.  
  
3. Możesz odwołać się do zmiennej z dowolnego miejsca w module, klasie lub strukturze, ale nie spoza niej.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Aby uczynić zmienną widoczną w całym obszarze nazw  
  
1. Umieść instrukcję `Dim` dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.  
  
2. Dołącz słowo kluczowe [zaprzyjaźnione](../../../../visual-basic/language-reference/modifiers/friend.md) lub [publiczne](../../../../visual-basic/language-reference/modifiers/public.md) w instrukcji `Dim`.  
  
3. Możesz odwołać się do zmiennej z dowolnego miejsca w przestrzeni nazw zawierającej moduł, klasę lub strukturę.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje zmienną na poziomie modułu i ogranicza jej widoczność do kodu w module.  
  
```vb  
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
  
 W poprzednim przykładzie wszystkie procedury zdefiniowane w module `demonstrateScope` mogą odwoływać się do zmiennej `String` `strMsg`. Po wywołaniu procedury `usePrivateVariable` zostanie wyświetlona zawartość zmiennej ciągu `strMsg` w oknie dialogowym.  
  
 Przy następujących zmianach do poprzedniego przykładu zmienna ciągu `strMsg` może być określana przez kod w dowolnym miejscu w przestrzeni nazw swojej deklaracji.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Im węższy zakres zmiennej, tym mniej możliwości odwołujące się do nich zamiast innej zmiennej o tej samej nazwie. Możesz również zminimalizować problemy pasujące do odwołania.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Im węższy zakres zmiennej, tym mniejsze prawdopodobieństwo, że złośliwy kod może być niewłaściwym użyciem.  
  
## <a name="see-also"></a>Zobacz także

- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)
