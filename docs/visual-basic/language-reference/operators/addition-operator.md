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
ms.openlocfilehash: 12c14b3be0562a31470ddbd2d5489ccdbdf3b62b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350291"
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
|`expression2`|Wymagany, chyba że operator `+` oblicza wartość ujemną. Dowolne wyrażenie liczbowe lub ciąg.|  
  
## <a name="result"></a>Wynik  
 Jeśli `expression1` i `expression2` są wartościami liczbowymi, wynik jest ich sumą arytmetyczną.  
  
 Jeśli `expression2` jest nieobecny, operator `+` jest operatorem tożsamości *jednoargumentowej* dla niezmienionej wartości wyrażenia. W tym sensie operacja składa się z zachowania znaku `expression1`, więc wynik jest ujemny, jeśli `expression1` jest ujemna.  
  
 Jeśli `expression1` i `expression2` są obydwoma ciągami, wynikiem jest łączenie ich wartości.  
  
 Jeśli `expression1` i `expression2` są typu mieszanego, podejmowana akcja zależy od ich typów, zawartości i ustawienia [Option Strict instrukcji](../../../visual-basic/language-reference/statements/option-strict-statement.md). Aby uzyskać więcej informacji, Zobacz tabele w "uwagi".  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`i `String`.  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, `+` wykonuje arytmetyczne Dodawanie, gdy jest to możliwe, i łączy się tylko wtedy, gdy oba wyrażenia są ciągami.  
  
 Jeśli żadne wyrażenie nie jest `Object`, Visual Basic wykonuje następujące czynności.  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|Oba wyrażenia są typami danych liczbowych (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`lub `Double`)|Dodana. Typ danych wyniku jest typem liczbowym odpowiednim dla typów danych `expression1` i `expression2`. Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba wyrażenia są typu `String`|Łączenie.|  
|Jedno wyrażenie jest typem danych liczbowych, a drugi jest ciągiem|Jeśli `Option Strict` jest `On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertuj `String` na `Double` i Dodaj.<br /><br /> Jeśli `String` nie można przekonwertować na `Double`, Zgłoś wyjątek <xref:System.InvalidCastException>.|  
|Jedno wyrażenie jest typu danych liczbowych, a drugi to [Nothing](../../../visual-basic/language-reference/nothing.md)|Dodaj, z `Nothing` wartością zero.|  
|Jedno wyrażenie jest ciągiem, a drugi jest `Nothing`|Połącz, z `Nothing` wartością "".|  
  
 Jeśli jedno wyrażenie jest wyrażeniem `Object`, Visual Basic wykonuje następujące czynności.  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|wyrażenie `Object` zawiera wartość liczbową, a drugi to typ danych liczbowych|Jeśli `Option Strict` jest `On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, Dodaj.|  
|wyrażenie `Object` zawiera wartość liczbową, a druga jest typu `String`|Jeśli `Option Strict` jest `On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertuj `String` na `Double` i Dodaj.<br /><br /> Jeśli `String` nie można przekonwertować na `Double`, Zgłoś wyjątek <xref:System.InvalidCastException>.|  
|wyrażenie `Object` zawiera ciąg, a drugi to typ danych liczbowych|Jeśli `Option Strict` jest `On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie Przekonwertuj ciąg `Object` na `Double` i Dodaj.<br /><br /> Jeśli ciąg `Object` nie może zostać skonwertowany na `Double`, Zgłoś wyjątek <xref:System.InvalidCastException>.|  
|wyrażenie `Object` zawiera ciąg, a drugi jest typu `String`|Jeśli `Option Strict` jest `On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertuj `Object` na `String` i Połącz.|  
  
 Jeśli oba wyrażenia są wyrażeniami `Object`, Visual Basic wykonuje następujące akcje (tylko`Option Strict Off`).  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|Oba wyrażenia `Object` przechowują wartości liczbowe|Dodana.|  
|Oba wyrażenia `Object` są typu `String`|Łączenie.|  
|Jedno wyrażenie `Object` zawiera wartość liczbową, a drugi zawiera ciąg|Niejawnie Przekonwertuj ciąg `Object` na `Double` i Dodaj.<br /><br /> Jeśli ciąg `Object` nie może zostać skonwertowany na wartość liczbową, Zgłoś wyjątek <xref:System.InvalidCastException>.|  
  
 Jeśli wyrażenie `Object` zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md) lub <xref:System.DBNull>, operator `+` traktuje go jako `String` z wartością "".  
  
> [!NOTE]
> Gdy używasz operatora `+`, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów. Użyj operatora `&`, aby nawiązać połączenie w celu wyeliminowania niejednoznaczności i zapewnienia kodu samoobsługowego.  
  
## <a name="overloading"></a>Przeciążenie  
 Operator `+` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `+`, aby dodać liczby. Jeśli operandy są liczbowe, Visual Basic oblicza wynik arytmetyczny. Wynik arytmetyczny reprezentuje sumę dwóch operandów.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Można również użyć operatora `+`, aby połączyć ciągi. Jeśli operandy są obu ciągów, Visual Basic je łączyć. Wynik łączenia reprezentuje pojedynczy ciąg składający się z zawartości dwóch operandów jeden po drugim.  
  
 Jeśli operandy są typu mieszanego, wynik zależy od ustawienia [Option Strict instrukcji](../../../visual-basic/language-reference/statements/option-strict-statement.md). Poniższy przykład ilustruje wynik, gdy `Option Strict` jest `On`.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Poniższy przykład ilustruje wynik, gdy `Option Strict` jest `Off`.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Aby wyeliminować niejednoznaczność, należy użyć operatora `&` zamiast `+` do łączenia.  
  
## <a name="see-also"></a>Zobacz także

- [&, operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
