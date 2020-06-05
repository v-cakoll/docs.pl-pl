---
title: + Operator
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 6ae3feae6ecb63b82426f2aa69359625bbffcec8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372119"
---
# <a name="-operator-visual-basic"></a>+ — Operator (Visual Basic)
Dodaje dwie liczby lub zwraca wartość dodatnią wyrażenia liczbowego. Można również użyć do łączenia dwóch wyrażeń ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```vb
expression1 + expression2
```
  
lub

```vb  
+expression1  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression1`|Wymagany. Dowolne wyrażenie liczbowe lub ciąg.|  
|`expression2`|Wymagane, chyba że `+` operator oblicza wartość ujemną. Dowolne wyrażenie liczbowe lub ciąg.|  
  
## <a name="result"></a>Wynik  
 Jeśli `expression1` i `expression2` są wartościami liczbowymi, wynik jest ich sumą arytmetyczną.  
  
 Jeśli `expression2` jest nieobecny, `+` operator jest *jednoargumentowym* operatorem tożsamości dla niezmienionej wartości wyrażenia. W tym sensie operacja składa się z zachowania znaku `expression1` , dlatego wynik jest ujemny, jeśli `expression1` jest ujemny.  
  
 Jeśli `expression1` i `expression2` są oba ciągi, wynikiem jest łączenie ich wartości.  
  
 Jeśli `expression1` i `expression2` są typu mieszanego, podejmowana akcja zależy od ich typów, zawartości i ustawienia [Option Strict instrukcji](../statements/option-strict-statement.md). Aby uzyskać więcej informacji, Zobacz tabele w "uwagi".  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal` , i `String` .  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, program `+` wykonuje operacje arytmetyczne, jeśli jest to możliwe, i łączy się tylko wtedy, gdy oba wyrażenia są ciągami.  
  
 Jeśli żadne wyrażenie nie jest `Object` , Visual Basic wykonuje następujące akcje.  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|Oba wyrażenia są typami danych liczbowych (,,,,,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` , lub `Double` )|Dodawanie. Typ danych wyniku jest typem liczbowym odpowiednim dla typów danych `expression1` i `expression2` . Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](data-types-of-operator-results.md).|  
|Oba wyrażenia są typu`String`|Łączenie.|  
|Jedno wyrażenie jest typem danych liczbowych, a drugi jest ciągiem|Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off` , następnie niejawnie przekonwertuj wartość `String` na `Double` i Dodaj.<br /><br /> Jeśli `String` nie można przekonwertować na `Double` , a następnie zgłosić <xref:System.InvalidCastException> wyjątek.|  
|Jedno wyrażenie jest typu danych liczbowych, a drugi to [Nothing](../nothing.md)|Dodaj, przy `Nothing` wartości równej zero.|  
|Jedno wyrażenie jest ciągiem, a drugi to`Nothing`|Połącz, używając `Nothing` wartości "".|  
  
 Jeśli jedno wyrażenie jest `Object` wyrażeniem, Visual Basic wykonuje następujące akcje.  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|`Object`wyrażenie zawiera wartość liczbową, a druga jest typem danych liczbowych|Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off` , a następnie Dodaj.|  
|`Object`wyrażenie zawiera wartość liczbową, a druga jest typu`String`|Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off` , następnie niejawnie przekonwertuj wartość `String` na `Double` i Dodaj.<br /><br /> Jeśli `String` nie można przekonwertować na `Double` , a następnie zgłosić <xref:System.InvalidCastException> wyjątek.|  
|`Object`wyrażenie zawiera ciąg, a drugi to typ danych liczbowych|Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` tak `Off` , następnie niejawnie Przekonwertuj ciąg `Object` na `Double` i Dodaj.<br /><br /> Jeśli `Object` nie można przekonwertować ciągu na `Double` , a następnie zgłosić <xref:System.InvalidCastException> wyjątek.|  
|`Object`wyrażenie zawiera ciąg, a drugi jest typu`String`|Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off` , a następnie niejawnie Przekształć `Object` do `String` i Połącz.|  
  
 Jeśli oba wyrażenia są `Object` wyrażeniami, Visual Basic wykonuje następujące akcje ( `Option Strict Off` tylko).  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|Oba `Object` wyrażenia przechowują wartości liczbowe|Dodawanie.|  
|Oba `Object` wyrażenia są typu`String`|Łączenie.|  
|Jedno `Object` wyrażenie zawiera wartość liczbową, a druga przechowuje ciąg|Niejawnie Przekonwertuj ciąg `Object` na `Double` i Dodaj.<br /><br /> Jeśli `Object` nie można przekonwertować ciągu na wartość liczbową, zgłoś <xref:System.InvalidCastException> wyjątek.|  
  
 Jeśli dowolne `Object` wyrażenie zwróci wartość [Nothing](../nothing.md) lub <xref:System.DBNull> , `+` operator traktuje go jako element `String` o wartości "".  
  
> [!NOTE]
> Gdy używasz `+` operatora, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów. Użyj `&` operatora do łączenia, aby wyeliminować niejednoznaczność i zapewnić kod służący do samodokumentowania.  
  
## <a name="overloading"></a>Przeciążenie  
 `+`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `+` Aby dodać liczby. Jeśli operandy są liczbowe, Visual Basic oblicza wynik arytmetyczny. Wynik arytmetyczny reprezentuje sumę dwóch operandów.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Można również użyć operatora, `+` Aby połączyć ciągi. Jeśli operandy są obu ciągów, Visual Basic je łączyć. Wynik łączenia reprezentuje pojedynczy ciąg składający się z zawartości dwóch operandów jeden po drugim.  
  
 Jeśli operandy są typu mieszanego, wynik zależy od ustawienia [Option Strict instrukcji](../statements/option-strict-statement.md). Poniższy przykład ilustruje wynik `Option Strict` `On` .  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Poniższy przykład ilustruje wynik `Option Strict` `Off` .  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Aby wyeliminować niejednoznaczności, należy użyć `&` operatora zamiast `+` łączenia.  
  
## <a name="see-also"></a>Zobacz też

- [Operator&](concatenation-operator.md)
- [Concatenation — Operatory](concatenation-operators.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory arytmetyczne w Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict — Instrukcja](../statements/option-strict-statement.md)
