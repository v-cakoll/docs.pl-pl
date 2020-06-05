---
title: 'Instrukcje: Deklarowanie struktury'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a6b70d0973e92db90e35e61b7fed2279c5b0bac3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393977"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Porady: deklarowanie struktury (Visual Basic)
Należy rozpocząć deklarację struktury za pomocą [instrukcji Structure](../../../language-reference/statements/structure-statement.md)i zakończyć ją za pomocą `End Structure` instrukcji. Między tymi dwiema instrukcjami należy zadeklarować co najmniej jeden *element*. Elementy mogą być dowolnego typu danych, ale co najmniej jeden musi być zmienną nieudostępnioną lub niestandardowym zdarzeniem.  
  
 Nie można zainicjować któregokolwiek z elementów struktury w deklaracji struktury. Podczas deklarowania zmiennej jako typu struktury, należy przypisać wartości do elementów, uzyskując dostęp do nich za pomocą zmiennej.  
  
 Aby zapoznać się z omówieniem różnic między strukturami i klasami, zobacz [struktury i klasy](structures-and-classes.md).  
  
 W celach demonstracyjnych Rozważmy sytuację, w której chcesz śledzić nazwisko pracownika, numer telefonu i wynagrodzenie. Struktura pozwala wykonać tę czynność w jednej zmiennej.  
  
### <a name="to-declare-a-structure"></a>Aby zadeklarować strukturę  
  
1. Utwórz instrukcje początkowe i końcowe dla struktury.  
  
     Możesz określić poziom dostępu struktury za pomocą [publicznego](../../../language-reference/modifiers/public.md), [chronionego](../../../language-reference/modifiers/protected.md), [przyjaznego](../../../language-reference/modifiers/friend.md)lub [prywatnego](../../../language-reference/modifiers/private.md) słowa kluczowego lub można zezwolić na ustawienie domyślne `Public` .  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Dodaj elementy do treści struktury.  
  
     Struktura musi mieć co najmniej jeden element. Należy zadeklarować każdy element i określić dla niego poziom dostępu. Jeśli używasz [instrukcji Dim](../../../language-reference/statements/dim-statement.md) bez żadnych słów kluczowych, dostępność domyślna to `Public` .  
  
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
  
     `salary`Pole w powyższym przykładzie jest `Private` , co oznacza, że jest niedostępne poza strukturą, nawet z klasy zawierającej. Jednak `giveRaise` procedura jest `Public` , dlatego można ją wywołać spoza struktury. Analogicznie, można zgłosić `salaryReviewTime` zdarzenie spoza struktury.  
  
     Oprócz zmiennych, `Sub` procedur i zdarzeń można także definiować stałe, `Function` procedury i właściwości w strukturze. Można wyznaczyć najwyżej jedną właściwość jako *Właściwość domyślną*, pod warunkiem, że przyjmuje co najmniej jeden argument. Można obsłużyć zdarzenie z [wspólną](../../../language-reference/modifiers/shared.md) `Sub` procedurą. Aby uzyskać więcej informacji, zobacz [jak: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](index.md)
- [Typy danych podstawowych](elementary-data-types.md)
- [Złożone typy danych](composite-data-types.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Struktury](structures.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Zmienne struktur](structure-variables.md)
- [Struktury oraz inne elementy programowania](structures-and-other-programming-elements.md)
- [Struktury i klasy](structures-and-classes.md)
- [User-Defined Data Type](../../../language-reference/data-types/user-defined-data-type.md)
