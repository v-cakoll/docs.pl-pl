---
title: 'Porady: deklarowanie struktury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: c3090b5b8e53e5a5a990ae11c91464797bde9803
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582306"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Porady: deklarowanie struktury (Visual Basic)
Należy rozpocząć deklarację struktury za pomocą [instrukcji Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)i zakończyć ją za pomocą instrukcji `End Structure`. Między tymi dwiema instrukcjami należy zadeklarować co najmniej jeden *element*. Elementy mogą być dowolnego typu danych, ale co najmniej jeden musi być zmienną nieudostępnioną lub niestandardowym zdarzeniem.  
  
 Nie można zainicjować któregokolwiek z elementów struktury w deklaracji struktury. Podczas deklarowania zmiennej jako typu struktury, należy przypisać wartości do elementów, uzyskując dostęp do nich za pomocą zmiennej.  
  
 Aby zapoznać się z omówieniem różnic między strukturami i klasami, zobacz [struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 W celach demonstracyjnych Rozważmy sytuację, w której chcesz śledzić nazwisko pracownika, numer telefonu i wynagrodzenie. Struktura pozwala wykonać tę czynność w jednej zmiennej.  
  
### <a name="to-declare-a-structure"></a>Aby zadeklarować strukturę  
  
1. Utwórz instrukcje początkowe i końcowe dla struktury.  
  
     Możesz określić poziom dostępu struktury za pomocą [publicznego](../../../../visual-basic/language-reference/modifiers/public.md), [chronionego](../../../../visual-basic/language-reference/modifiers/protected.md), [przyjaznego](../../../../visual-basic/language-reference/modifiers/friend.md)lub [prywatnego](../../../../visual-basic/language-reference/modifiers/private.md) słowa kluczowego lub można zezwolić na `Public`.  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Dodaj elementy do treści struktury.  
  
     Struktura musi mieć co najmniej jeden element. Należy zadeklarować każdy element i określić dla niego poziom dostępu. Jeśli używasz [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) bez żadnych słów kluczowych, dostępność jest domyślnie `Public`.  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     Pole `salary` w poprzednim przykładzie jest `Private`, co oznacza, że jest niedostępne poza strukturą, nawet z klasy zawierającej. Jednakże procedura `giveRaise` jest `Public`, dlatego można ją wywołać spoza struktury. Podobnie można wywołać zdarzenie `salaryReviewTime` spoza struktury.  
  
     Oprócz zmiennych, procedur `Sub` i zdarzeń, można także definiować stałe, procedury `Function` i właściwości w strukturze. Można wyznaczyć najwyżej jedną właściwość jako *Właściwość domyślną*, pod warunkiem, że przyjmuje co najmniej jeden argument. Można obsłużyć zdarzenie z użyciem procedury `Sub` [udostępnionej](../../../../visual-basic/language-reference/modifiers/shared.md) . Aby uzyskać więcej informacji, zobacz [jak: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Zmienne struktur](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [User-Defined, typ danych](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
