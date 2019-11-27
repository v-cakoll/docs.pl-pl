---
title: 'Instrukcje: deklarowanie wyliczeń'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 042aea045313bcaf3832274acf1000f87a084b72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354044"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>Porady: deklarowanie wyliczeń (Visual Basic)
Wyliczenie można utworzyć za pomocą instrukcji `Enum` w sekcji deklaracji klasy lub modułu. Nie można zadeklarować wyliczenia w ramach metody. Aby określić odpowiedni poziom dostępu, użyj `Private`, `Protected`, `Friend`lub `Public`.  
  
 Typ `Enum` ma nazwę, typ podstawowy i zestaw pól, z których każdy reprezentuje stałą. Nazwa musi być prawidłowym kwalifikatorem Visual Basic platformy .NET. Typ podstawowy musi być jednym z typów całkowitych —`Byte`, `Short`, `Long` lub `Integer`. `Integer` jest wartością domyślną. Wyliczenia są zawsze silnie wpisane i nie mogą być zamienne z typami liczb całkowitych.  
  
 Wyliczenia nie mogą mieć wartości zmiennoprzecinkowych. Jeśli Wyliczenie ma przypisaną wartość zmiennoprzecinkową z `Option Strict On`, zostanie zwrócony błąd kompilatora. Jeśli `Option Strict` jest `Off`, wartość zostanie automatycznie przekonwertowana na typ `Enum`.  
  
 Aby uzyskać informacje o nazwach i sposobach używania instrukcji `Imports` w celu niepotrzebnej kwalifikacji nazw, zobacz [wyliczenia i kwalifikowanie nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### <a name="to-declare-an-enumeration"></a>Aby zadeklarować Wyliczenie  
  
1. Napisz deklarację zawierającą poziom dostępu do kodu, słowo kluczowe `Enum` i prawidłową nazwę, jak w poniższych przykładach, z których każdy deklaruje inny `Enum`.  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. Zdefiniuj stałe w wyliczeniu. Domyślnie pierwsza stała w wyliczeniu jest inicjowana do `0`, a kolejne stałe są inicjowane do wartości jednej z więcej niż poprzednia stała. Na przykład następujące Wyliczenie `Days`, zawiera stałą o nazwie `Sunday` z wartością `0`, stała o nazwie `Monday` z wartością `1`, stała o nazwie `Tuesday` z wartością `2`i tak dalej.  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. Można jawnie przypisać wartości do stałych w wyliczeniu przy użyciu instrukcji przypisania. Można przypisać dowolną liczbę całkowitą, łącznie z liczbami ujemnymi. Na przykład, możesz chcieć mieć stałe z wartościami mniejszymi od zera, aby reprezentować warunki błędu. W poniższym wyliczeniu, stała `Invalid` jest jawnie przypisana do `–1`wartości, a stała `Sunday` jest przypisana do `0`wartości. Ponieważ jest to pierwsza stała w wyliczeniu, `Saturday` jest również inicjowana do `0`wartości. Wartość `Monday` jest `1` (jedna większa niż wartość `Sunday`); wartość `Tuesday` jest `2`i tak dalej.  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>Aby zadeklarować Wyliczenie jako typ jawny  
  
- Określ typ wyliczenia przy użyciu klauzuli `As`, jak pokazano w poniższym przykładzie.  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Instrukcje: Iterowanie przez Wyliczenie w Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Kiedy stosować wyliczanie](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
