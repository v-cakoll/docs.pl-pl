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
ms.openlocfilehash: 14f3de39eb8d8e6820e2b40792a8e8e57217e410
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414379"
---
# <a name="user-defined-constants-visual-basic"></a>Stałe zdefiniowane przez użytkownika (Visual Basic)
Stała jest zrozumiałą nazwą, która przyjmuje miejsce liczby lub ciągu, który nie jest zmieniany. Stałe wartości magazynu, których nazwa to oznacza, pozostają stałe przez cały czas wykonywania aplikacji. Możesz użyć stałych, które są zdefiniowane przez kontrolki lub składniki, z którymi pracujesz, lub możesz utworzyć własne. Utworzone przez Ciebie stałe są określane jako *zdefiniowane przez użytkownika*.  
  
 Można zadeklarować stałą za pomocą `Const` instrukcji, korzystając z tych samych wytycznych, które należy wykonać w celu utworzenia nazwy zmiennej. Jeśli `Option Strict` jest `On` , należy jawnie zadeklarować typ stałej.  
  
## <a name="const-statement-usage"></a>Użycie instrukcji const  
 `Const`Instrukcja może reprezentować ilość matematyczną lub datę/godzinę:  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 Można także definiować `String` stałe:  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 Wyrażenie po prawej stronie znaku równości ( `=` ) jest często ciągiem liczbowym lub literalnym, ale również może być wyrażeniem, które powoduje użycie liczby lub ciągu (chociaż wyrażenie nie może zawierać wywołań funkcji). Można nawet definiować stałe pod względem wcześniej zdefiniowanych stałych:  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>Zakres stałych zdefiniowanych przez użytkownika  
 `Const`Zakres instrukcji jest taki sam jak w przypadku zmiennej zadeklarowanej w tej samej lokalizacji. Można określić zakres w dowolny z następujących sposobów:  
  
- Aby utworzyć stałą, która istnieje tylko w ramach procedury, zadeklaruj ją w ramach tej procedury.  
  
- Aby utworzyć stałą dostępną dla wszystkich procedur w obrębie klasy, ale nie do żadnego kodu spoza tego modułu, zadeklaruj go w sekcji deklaracji klasy.  
  
- Aby utworzyć stałą dostępną dla wszystkich elementów członkowskich zestawu, ale nie do klientów zewnętrznych zestawu, zadeklaruj ją przy użyciu `Friend` słowa kluczowego w sekcji deklaracji klasy.  
  
- Aby utworzyć stałą dostępną w całej aplikacji, należy ją zadeklarować przy użyciu `Public` słowa kluczowego w sekcji deklaracji klasy.  
  
 Aby uzyskać więcej informacji, zobacz [How to: DECLARE A stała](how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Unikanie odwołań cyklicznych  
 Ze względu na to, że stałe mogą być zdefiniowane w warunkach innych stałych, można przypadkowo utworzyć *cykl*lub odwołanie cykliczne między dwoma lub więcej stałych. Cykl występuje, gdy istnieją co najmniej dwie stałe publiczne, z których każdy jest zdefiniowany w warunkach innych, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 Jeśli wystąpi cykl, Visual Basic generuje błąd kompilatora.  
  
## <a name="see-also"></a>Zobacz też

- [Const, instrukcja](../../../language-reference/statements/const-statement.md)
- [Stała i typy literałów](constant-and-literal-data-types.md)
- [Stałe i wyliczenia](index.md)
- [Stałe i wyliczenia](../../../language-reference/constants-and-enumerations.md)
- [Enumerations — Przegląd](enumerations-overview.md)
- [Stałe — Przegląd](constants-overview.md)
- [Instrukcje: deklarowanie wyliczenia](how-to-declare-enumerations.md)
- [Wyliczenie i kwantyfikacja nazwy](enumerations-and-name-qualification.md)
- [Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)
