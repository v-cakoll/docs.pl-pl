---
title: 'Instrukcje: Deklarowanie struktury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: cee2768d0e7475d2df123491e2b506bf5c08785f
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066119"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Instrukcje: Deklarowanie struktury (Visual Basic)
Rozpocznij deklaracji struktury z [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md), i kończy z `End Structure` instrukcji. Między te dwie instrukcje należy zadeklarować co najmniej jeden *elementu*. Elementy mogą być dowolnego typu danych, ale co najmniej jedna musi być zmienną nieudostępnionych lub nieudostępnionych, niestandardowych zdarzeń.  
  
 Nie można zainicjować elementy struktury w deklaracji struktury. Kiedy Deklarujesz zmienną typu struktury, należy przypisać wartości do elementów, uzyskując dostęp do nich za pośrednictwem zmiennej.  
  
 Omówienie różnic między strukturami i klasami, zobacz [struktury i klasy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Dla celów demonstracyjnych Rozważmy sytuację, w miejscu do śledzenia nazwa, numer wewnętrzny i wynagrodzenia pracownika. Struktura umożliwia to zrobić w pojedynczej zmiennej.  
  
### <a name="to-declare-a-structure"></a>Aby zadeklarować strukturę  
  
1.  Utwórz początkowy i końcowy instrukcji w strukturze.  
  
     Można określić poziom dostępu przy użyciu struktury [publicznych](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), lub [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe lub można pozwolić, aby go Domyślnie `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  Dodawanie elementów do treści struktury.  
  
     Struktura musi mieć co najmniej jeden element. Musisz zadeklarować każdego elementu i określić poziom dostępu dla niego. Jeśli używasz [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) bez żadnych słów kluczowych, domyślnie dostępność `Public`.  
  
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
  
     `salary` Pole w powyższym przykładzie jest `Private`, co oznacza, że jest niedostępny poza struktury, nawet z zawierający klasy. Jednak `giveRaise` procedura jest `Public`, dzięki czemu mogą być wywoływane z poza struktury. Podobnie, można podnieść `salaryReviewTime` zdarzenie z poza struktury.  
  
     Oprócz zmiennych `Sub` procedur i zdarzeń, można również zdefiniować stałych, `Function` procedur i właściwości w strukturze. Możesz wyznaczyć co najwyżej jedną właściwość jako *właściwość domyślna*, o ile trwa co najmniej jednego argumentu. Można obsługiwać zdarzenia z [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedury. Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
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
