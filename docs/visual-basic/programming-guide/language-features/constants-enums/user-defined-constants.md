---
title: Stałe zdefiniowane przez użytkownika (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: e519fcaf90c6f18e75d5c409cbe7067d5db36429
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975943"
---
# <a name="user-defined-constants-visual-basic"></a>Stałe zdefiniowane przez użytkownika (Visual Basic)
Stałe są znaczącą nazwę, która zajmuje miejsce liczbą lub ciągiem, który nie jest zmieniany. Stałe przechowywać wartości, które jak wskazuje nazwa, pozostają stałe w trakcie wykonywania aplikacji. Można użyć stałe, które są definiowane przez formanty lub składników, którymi pracujesz, lub możesz utworzyć swój własny. Stałe utworzone samodzielnie są określane jako *zdefiniowanych przez użytkownika*.  
  
 Deklarowanie stałej z `Const` instrukcję, używając te same wytyczne, jak w przypadku tworzenia nazwy zmiennej. Jeśli `Option Strict` jest `On`, należy jawnie deklarować typ stałej.  
  
## <a name="const-statement-usage"></a>Const — instrukcja użycia  
 A `Const` instrukcji może reprezentować matematyczne lub daty/godziny ilość:  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 On również zdefiniować `String` stałe:  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 Wyrażenie po prawej stronie znaku równości ( `=` ) jest często liczbą lub ciągiem literału, ale również może być wyrażeniem, które powoduje liczbą lub ciągiem (mimo że to wyrażenie nie może zawierać wywołania funkcji). Możesz nawet określić stałe pod względem wcześniej zdefiniowanego stałe:  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>Zakres stałe zdefiniowane przez użytkownika  
 A `Const` zakres instrukcji jest taka sama, jak Zmienna zadeklarowana w tej samej lokalizacji. Należy określić zakres, w dowolnym z następujących sposobów:  
  
-   Aby utworzyć stałą, że istnieje tylko w obrębie procedury, należy zadeklarować ją w ramach tej procedury.  
  
-   Aby utworzyć stałej dostępności, do wszystkich procedur w obrębie klasy, ale nie do kodu poza ten moduł, należy zadeklarować ją w sekcji deklaracji klasy.  
  
-   Aby utworzyć stałą, która jest dostępna, do wszystkich elementów członkowskich zestawu, ale nie do klientów poza zestawu, Zadeklaruj go przy użyciu `Friend` — słowo kluczowe w sekcji deklaracji klasy.  
  
-   Aby utworzyć stałą dostępne w całej aplikacji, Zadeklaruj go przy użyciu `Public` — słowo kluczowe w deklaracjach sekcji klasy.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie stałej](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Unikanie odwołań cyklicznych  
 Ponieważ stałe można zdefiniować pod względem inne stałe, jest możliwe utworzenie przypadkowo *cyklu*, lub odwołanie cykliczne, między co najmniej dwóch stałych. Cykl występuje, gdy masz co najmniej dwa publiczne stałe, z których każdy jest określana zgodnie z drugiej strony, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 W przypadku cyklu Visual Basic generuje błąd kompilatora.  
  
## <a name="see-also"></a>Zobacz także
- [Const, instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Stałe i wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Instrukcje: Deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
