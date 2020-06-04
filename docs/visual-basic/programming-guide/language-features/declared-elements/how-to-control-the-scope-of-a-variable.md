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
ms.openlocfilehash: 8b21f22edea84448e3f2969c3e4b07c08a17a338
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357351"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Porady: kontrolowanie zakresu zmiennej (Visual Basic)
Zwykle zmienna znajduje się w *zakresie*lub jest widoczna dla odwołania w całym regionie, w którym jest zadeklarowana. W niektórych przypadkach *poziom dostępu* zmiennej może mieć wpływ na jego zakres.  
  
 Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Zakres na poziomie bloku lub procedury  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Aby zmienna była widoczna tylko w bloku  
  
- Umieść [instrukcję Dim](../../../language-reference/statements/dim-statement.md) dla zmiennej między instrukcjami inicjującymi i kończącymi deklaracji tego bloku, na przykład między `For` instrukcjami i a `Next` `For` pętlą.  
  
     Można odwołać się do zmiennej tylko z poziomu bloku.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Aby zmienna była widoczna tylko w ramach procedury  
  
- Umieść `Dim` instrukcję dla zmiennej wewnątrz procedury, ale poza blokami (na przykład `With` blok... `End With` ).  
  
     Można odwołać się do zmiennej tylko z wewnątrz procedury, w tym w dowolnym bloku zawartym w procedurze.  
  
## <a name="scope-at-module-or-namespace-level"></a>Zakres na poziomie modułu lub przestrzeni nazw  
 Dla wygody poziom jednoterminowego *modułu* jest stosowany równomiernie dla modułów, klas i struktur. Poziom dostępu zmiennej poziomu modułu określa jej zakres. Przestrzeń nazw, która zawiera moduł, klasę lub strukturę, ma także wpływ na zakres.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Aby uczynić zmienną widoczną w całym module, klasie lub strukturze  
  
1. Umieść `Dim` instrukcję dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.  
  
2. Dołącz [prywatne](../../../language-reference/modifiers/private.md) słowo kluczowe do `Dim` instrukcji.  
  
3. Możesz odwołać się do zmiennej z dowolnego miejsca w module, klasie lub strukturze, ale nie spoza niej.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Aby uczynić zmienną widoczną w całym obszarze nazw  
  
1. Umieść `Dim` instrukcję dla zmiennej wewnątrz modułu, klasy lub struktury, ale poza jakąkolwiek procedurą.  
  
2. Dołącz słowo kluczowe [zaprzyjaźnione](../../../language-reference/modifiers/friend.md) lub [publiczne](../../../language-reference/modifiers/public.md) w `Dim` instrukcji.  
  
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
  
 W poprzednim przykładzie wszystkie procedury zdefiniowane w module `demonstrateScope` mogą odwoływać się do `String` zmiennej `strMsg` . Gdy `usePrivateVariable` procedura jest wywoływana, wyświetla zawartość zmiennej String `strMsg` w oknie dialogowym.  
  
 Przy następujących zmianach do powyższego przykładu zmienna String `strMsg` może być określana przez kod w dowolnym miejscu w przestrzeni nazw swojej deklaracji.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Im węższy zakres zmiennej, tym mniej możliwości odwołujące się do nich zamiast innej zmiennej o tej samej nazwie. Możesz również zminimalizować problemy pasujące do odwołania.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Im węższy zakres zmiennej, tym mniejsze prawdopodobieństwo, że złośliwy kod może być niewłaściwym użyciem.  
  
## <a name="see-also"></a>Zobacz też

- [Zakres w Visual Basic](scope.md)
- [Okres istnienia w Visual Basic](lifetime.md)
- [Poziomy dostępu w Visual Basic](access-levels.md)
- [Zmienne](../variables/index.md)
- [Deklaracja zmiennej](../variables/variable-declaration.md)
- [Dim, instrukcja](../../../language-reference/statements/dim-statement.md)
