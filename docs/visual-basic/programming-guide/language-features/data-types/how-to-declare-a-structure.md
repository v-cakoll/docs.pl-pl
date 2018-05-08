---
title: 'Porady: deklarowanie struktury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 6128addd60609bfc88a1409648fb320bc7089974
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Porady: deklarowanie struktury (Visual Basic)
Rozpocznij deklaracji struktury z [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md), i zakończyć je z `End` `Structure` instrukcji. Między te dwie instrukcje muszą deklarować co najmniej jeden *elementu*. Elementy mogą być dowolnego typu danych, ale co najmniej jeden musi być udostępniana zmiennej lub zdarzeń udostępniana, standardowych.  
  
 Nie można zainicjować elementy struktury w deklaracji struktury. Podczas zadeklarować zmiennej typu struktury, można przypisać wartości do elementów, uzyskując dostęp do nich za pośrednictwem zmiennej.  
  
 Omówienie różnice między struktury i klasy, zobacz [struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Dla celów demonstracyjnych Rozważmy sytuację, w miejscu do śledzenia nazwa, numer wewnętrzny i wynagrodzenie pracownika. Struktura umożliwia to zrobić w pojedynczej zmiennej.  
  
### <a name="to-declare-a-structure"></a>Deklarowanie struktury  
  
1.  Utwórz początkowy i końcowy instrukcje dla struktury.  
  
     Możesz określić poziom dostępu, używając struktury [publicznego](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe lub możesz pozwolić, aby go Domyślnie `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  Dodawanie elementów do treści struktury.  
  
     Struktura musi mieć co najmniej jeden element. Należy zadeklarować wszystkie elementy i określ poziom dostępu. Jeśli używasz [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) bez żadnych słów kluczowych, domyślnie dostępność `Public`.  
  
    ```  
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
  
     `salary` Pole w poprzednim przykładzie jest `Private`, co oznacza, że jest niedostępny poza struktury, nawet z zawierające klasy. Jednak `giveRaise` procedura jest `Public`, dlatego może być wywołana z poza struktury. Podobnie można zwiększyć `salaryReviewTime` zdarzenia z poza struktury.  
  
     Oprócz zmiennych `Sub` procedur i zdarzeń, stałe, można również zdefiniować `Function` procedury i właściwości w strukturze. Można określić co najwyżej jedną właściwość jako *domyślna właściwość*, o ile potrzebny co najmniej jednego argumentu. Można obsługiwać zdarzenia z [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedury. Aby uzyskać więcej informacji, zobacz [porady: deklarowanie i wywoływanie właściwości domyślne w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Zmienne struktur](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [Struktury oraz inne elementy programowania](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [User-Defined, typ danych](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
