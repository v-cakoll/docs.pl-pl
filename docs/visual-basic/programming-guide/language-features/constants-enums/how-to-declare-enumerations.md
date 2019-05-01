---
title: 'Instrukcje: Deklarowanie wyliczeń (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: f168d6d9cd6970353e75fa35a7e52cc7156fda72
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907650"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Instrukcje: Deklarowanie wyliczeń (Visual Basic)
Utwórz wyliczenie z `Enum` instrukcji w sekcji deklaracji klasy lub modułu. Nie można zadeklarować wyliczenie wewnątrz metody. Aby określić odpowiedni poziom dostępu, użyj `Private`, `Protected`, `Friend`, lub `Public`.  
  
 `Enum` Typ ma nazwę, typ podstawowy i zestaw pól, każdy reprezentuje stałą. Nazwa musi być prawidłową kwalifikator Visual Basic .NET. Typ podstawowy musi mieć jedną z typami całkowitymi —`Byte`, `Short`, `Long` lub `Integer`. `Integer` jest ustawieniem domyślnym. Wyliczenia są zawsze jednoznacznie określone i nie są wymienne z typów liczb całkowitych.  
  
 Wyliczenia nie może mieć różne wartości zmiennoprzecinkowe. Jeśli wyliczenie nie zostanie przypisana wartość zmiennoprzecinkowa o `Option Strict On`, powoduje błąd kompilatora. Jeśli `Option Strict` jest `Off`, wartość jest automatycznie konwertowany do `Enum` typu.  
  
 Dla informacji o nazwach i sposobu użycia `Imports` oświadczenie kwantyfikacja nazwy zbędne, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Aby zadeklarować wyliczenie  
  
1. Zapis deklarację, że obejmuje poziom dostępu do kodu, `Enum` — słowo kluczowe i prawidłową nazwą, tak jak w poniższych przykładach, z których każdy deklaruje inną `Enum`.  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Definiowanie stałych w wyliczeniu. Domyślnie pierwszej stałej wyliczenia jest inicjowany do `0`, i kolejne stałe są inicjowane na wartość jeden więcej niż poprzedniego — stała. Na przykład, poniższy wyliczenie `Days`, zawiera stałą o nazwie `Sunday` wartością `0`, stałą o nazwie `Monday` wartością `1`, stałą o nazwie `Tuesday` z wartością `2`i tak dalej.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Można jawnie przypisać wartości do stałe, wyliczenia, korzystając z instrukcji przypisania. Możesz przypisać dowolnej wartości liczby całkowitej, łącznie z liczbami ujemnymi. Na przykład może być stałe przy użyciu wartości mniejsze od zera do reprezentowania warunków błędów. W poniższym wyliczenia, stała `Invalid` jawnie jest przypisywana wartość `–1`i stałą `Sunday` jest przypisywana wartość `0`. Ponieważ jest on pierwszy stała wyliczenia `Saturday` również jest ustawiana na wartość `0`. Wartość `Monday` jest `1` (jeden więcej niż wartość `Sunday`); wartość `Tuesday` jest `2`i tak dalej.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Aby zadeklarować wyliczenie jako jawnego typu  
  
- Określ typ wyliczenia przy użyciu `As` klauzuli, jak pokazano w poniższym przykładzie.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
