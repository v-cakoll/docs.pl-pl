---
title: Stałe zdefiniowane przez użytkownika
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 194a420b3749ca5c858a65c07b8c164287c1582a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354008"
---
# <a name="user-defined-constants-visual-basic"></a>Stałe zdefiniowane przez użytkownika (Visual Basic)
Stała jest zrozumiałą nazwą, która przyjmuje miejsce liczby lub ciągu, który nie jest zmieniany. Stałe wartości magazynu, których nazwa to oznacza, pozostają stałe przez cały czas wykonywania aplikacji. Możesz użyć stałych, które są zdefiniowane przez kontrolki lub składniki, z którymi pracujesz, lub możesz utworzyć własne. Utworzone przez Ciebie stałe są określane jako *zdefiniowane przez użytkownika*.  
  
 Można zadeklarować stałą za pomocą instrukcji `Const`, korzystając z tych samych wytycznych dotyczących tworzenia nazwy zmiennej. Jeśli `Option Strict` jest `On`, należy jawnie zadeklarować typ stałej.  
  
## <a name="const-statement-usage"></a>Użycie instrukcji const  
 Instrukcja `Const` może reprezentować liczbę matematyczną lub datę/godzinę:  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 Można również zdefiniować `String` stałych:  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 Wyrażenie po prawej stronie znaku równości (`=`) jest często ciągiem liczbowym lub literalnym, ale również może być wyrażeniem, które powoduje użycie liczby lub ciągu (chociaż wyrażenie nie może zawierać wywołań funkcji). Można nawet definiować stałe pod względem wcześniej zdefiniowanych stałych:  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>Zakres stałych zdefiniowanych przez użytkownika  
 Zakres instrukcji `Const` jest taki sam jak w przypadku zmiennej zadeklarowanej w tej samej lokalizacji. Można określić zakres w dowolny z następujących sposobów:  
  
- Aby utworzyć stałą, która istnieje tylko w ramach procedury, zadeklaruj ją w ramach tej procedury.  
  
- Aby utworzyć stałą dostępną dla wszystkich procedur w obrębie klasy, ale nie do żadnego kodu spoza tego modułu, zadeklaruj go w sekcji deklaracji klasy.  
  
- Aby utworzyć stałą dostępną dla wszystkich elementów członkowskich zestawu, ale nie do klientów zewnętrznych zestawu, zadeklaruj ją przy użyciu słowa kluczowego `Friend` w sekcji deklaracji klasy.  
  
- Aby utworzyć stałą dostępną w całej aplikacji, należy ją zadeklarować przy użyciu słowa kluczowego `Public` w sekcji deklaracji klasy.  
  
 Aby uzyskać więcej informacji, zobacz [How to: DECLARE A stała](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Unikanie odwołań cyklicznych  
 Ze względu na to, że stałe mogą być zdefiniowane w warunkach innych stałych, można przypadkowo utworzyć *cykl*lub odwołanie cykliczne między dwoma lub więcej stałych. Cykl występuje, gdy istnieją co najmniej dwie stałe publiczne, z których każdy jest zdefiniowany w warunkach innych, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 Jeśli wystąpi cykl, Visual Basic generuje błąd kompilatora.  
  
## <a name="see-also"></a>Zobacz także

- [Const, instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Stałe i wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Instrukcje: deklarowanie wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
