---
title: 'Porady: deklarowanie wyliczeń (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: e2dbdbbf6bf7fe3e4b71cbe7edc7a19b18f96ef2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Porady: deklarowanie wyliczeń (Visual Basic)
Utwórz wyliczenie z `Enum` instrukcji w sekcji deklaracji klasy lub modułu. Nie można zadeklarować wyliczenia w metodzie. Aby określić odpowiedni poziom dostępu, użyj `Private`, `Protected`, `Friend`, lub `Public`.  
  
 `Enum` Typu ma nazwę, typ podstawowy oraz zestawu pól, każda reprezentujący stałą. Nazwa musi być prawidłową kwalifikatora Visual Basic .NET. Typ podstawowy musi być jednego z typów całkowitych —`Byte`, `Short`, `Long` lub `Integer`. `Integer` jest ustawieniem domyślnym. Wyliczenia są zawsze silnie typizowane i nie są wymienne z typów liczb całkowitych.  
  
 Wyliczenia nie może mieć wartości zmiennoprzecinkowych. Wyliczenie przypisane wartość zmiennoprzecinkową o `Option Strict On`, wyniki błąd kompilatora. Jeśli `Option Strict` jest `Off`, wartość jest automatycznie konwertowany do `Enum` typu.  
  
 Dla informacji o nazwach i sposobu użycia `Imports` oświadczenie kwantyfikacja nazwy niepotrzebne, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Aby zadeklarować wyliczenie  
  
1.  Zapis deklaracji, która zawiera poziom dostępu kodu, `Enum` — słowo kluczowe i prawidłową nazwę, na przykład, z których każdy deklaruje inną `Enum`.  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  Definiowanie stałych w wyliczeniu. Domyślnie pierwszy stała w wyliczeniu jest ustawiana na `0`, i kolejne stałe są inicjowane na wartość jednego więcej niż poprzedniego stała. Na przykład następujące wyliczenie `Days`, zawiera stałą o nazwie `Sunday` z wartością `0`, stałą o nazwie `Monday` z wartością `1`, stałą o nazwie `Tuesday` z wartością `2`i tak dalej.  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  Można jawnie przypisać wartości stałe w wyliczeniu za pomocą instrukcji przypisania. Można przypisać dowolną liczbą całkowitą, łącznie z liczbami ujemnymi. Na przykład może być stałe o wartości mniejszej niż zero, aby reprezentować warunki błędów. W poniższych wyliczenia, stała `Invalid` jest jawnie przypisanej wartości `–1`i stałą `Sunday` jest przypisywana wartość `0`. Ponieważ jest pierwszym stała w wyliczeniu, `Saturday` również jest ustawiana na wartość `0`. Wartość `Monday` jest `1` (jeden większa niż wartość `Sunday`); wartość `Tuesday` jest `2`i tak dalej.  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Aby zadeklarować wyliczenie jako typu jawnego  
  
-   Określ typ wyliczenia za pomocą `As` klauzuli, jak pokazano w poniższym przykładzie.  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Porady: iterowanie za pomocą wyliczania w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
