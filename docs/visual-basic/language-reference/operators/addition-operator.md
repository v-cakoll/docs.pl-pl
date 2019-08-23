---
title: + Operator (Visual Basic)
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
ms.openlocfilehash: ab18a7137a31ed8e616f465e7d617305c96d7b10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943026"
---
# <a name="-operator-visual-basic"></a>+ — Operator (Visual Basic)
Dodaje dwie liczby lub zwraca wartość dodatnią wyrażenia liczbowego. Można również użyć do łączenia dwóch wyrażeń ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression1`|Wymagana. Dowolne wyrażenie liczbowe lub ciąg.|  
|`expression2`|Wymagane, `+` chyba że operator oblicza wartość ujemną. Dowolne wyrażenie liczbowe lub ciąg.|  
  
## <a name="result"></a>Wynik  
 Jeśli `expression1` i`expression2` są wartościami liczbowymi, wynik jest ich sumą arytmetyczną.  
  
 Jeśli `expression2` jest nieobecny `+` , operator jest jednoargumentowym operatorem tożsamości dla niezmienionej wartości wyrażenia. W tym sensie operacja składa się z zachowania znaku `expression1`, dlatego wynik jest ujemny, jeśli `expression1` jest ujemny.  
  
 Jeśli `expression1` i`expression2` są oba ciągi, wynikiem jest łączenie ich wartości.  
  
 Jeśli `expression1` i`expression2` są typu mieszanego, podejmowana akcja zależy od ich typów, zawartości i ustawienia [Option Strict instrukcji](../../../visual-basic/language-reference/statements/option-strict-statement.md). Aby uzyskać więcej informacji, Zobacz tabele w "uwagi".  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`, i `String`.  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc `+` , program wykonuje operacje arytmetyczne, jeśli jest to możliwe, i łączy się tylko wtedy, gdy oba wyrażenia są ciągami.  
  
 Jeśli żadne wyrażenie nie jest `Object`, Visual Basic wykonuje następujące akcje.  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|Oba wyrażenia są typami danych liczbowych`SByte`( `Byte`, `Short` `UShort` `Integer` `ULong`, ,,`Decimal`,, ,`Single`,,, lub`Double`) `Long` `UInteger`|Dodana. Typ danych wyniku jest typem liczbowym odpowiednim dla typów `expression1` danych i. `expression2` Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba wyrażenia są typu`String`|Łączenie.|  
|Jedno wyrażenie jest typem danych liczbowych, a drugi jest ciągiem|Jeśli `Option Strict` jest`On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` `String` `Double` jest `Off`, następnie niejawnie przekonwertuj wartość na i Dodaj.<br /><br /> Jeśli nie można przekonwertować na `Double`, a następnie zgłosić <xref:System.InvalidCastException> wyjątek. `String`|  
|Jedno wyrażenie jest typu danych liczbowych, a drugi to [Nothing](../../../visual-basic/language-reference/nothing.md)|Dodaj, przy `Nothing` wartości równej zero.|  
|Jedno wyrażenie jest ciągiem, a drugi to`Nothing`|Połącz, używając `Nothing` wartości "".|  
  
 Jeśli jedno wyrażenie jest `Object` wyrażeniem, Visual Basic wykonuje następujące akcje.  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|`Object`wyrażenie zawiera wartość liczbową, a druga jest typem danych liczbowych|Jeśli `Option Strict` jest`On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` jest`Off`, a następnie Dodaj.|  
|`Object`wyrażenie zawiera wartość liczbową, a druga jest typu`String`|Jeśli `Option Strict` jest`On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` `String` `Double` jest `Off`, następnie niejawnie przekonwertuj wartość na i Dodaj.<br /><br /> Jeśli nie można przekonwertować na `Double`, a następnie zgłosić <xref:System.InvalidCastException> wyjątek. `String`|  
|`Object`wyrażenie zawiera ciąg, a drugi to typ danych liczbowych|Jeśli `Option Strict` jest`On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` `Object` `Double` tak `Off`, następnie niejawnie Przekonwertuj ciąg na i Dodaj.<br /><br /> Jeśli nie można `Object` przekonwertować ciągu na `Double`, a następnie zgłosić <xref:System.InvalidCastException> wyjątek.|  
|`Object`wyrażenie zawiera ciąg, a drugi jest typu`String`|Jeśli `Option Strict` jest`On`, wygeneruj błąd kompilatora.<br /><br /> Jeśli `Option Strict` `Object` `String` jest `Off`, a następnie niejawnie Przekształć do i Połącz.|  
  
 Jeśli oba wyrażenia są `Object` wyrażeniami, Visual Basic wykonuje następujące akcje (`Option Strict Off` tylko).  
  
|Typy danych wyrażeń|Akcja według kompilatora|  
|---|---|  
|Oba `Object` wyrażenia przechowują wartości liczbowe|Dodana.|  
|Oba `Object` wyrażenia są typu`String`|Łączenie.|  
|Jedno `Object` wyrażenie zawiera wartość liczbową, a druga przechowuje ciąg|Niejawnie przekonwertuj `Object` ciąg `Double` na i Dodaj.<br /><br /> Jeśli nie można `Object` przekonwertować ciągu na wartość liczbową, <xref:System.InvalidCastException> Zgłoś wyjątek.|  
  
 Jeśli dowolne `Object` wyrażenie zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md) <xref:System.DBNull>lub, `+` operator traktuje go jako element `String` o wartości "".  
  
> [!NOTE]
> Gdy używasz `+` operatora, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów. `&` Użyj operatora do łączenia, aby wyeliminować niejednoznaczność i zapewnić kod służący do samodokumentowania.  
  
## <a name="overloading"></a>Przeciążenie  
 Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `+` Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `+` aby dodać liczby. Jeśli operandy są liczbowe, Visual Basic oblicza wynik arytmetyczny. Wynik arytmetyczny reprezentuje sumę dwóch operandów.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Można również użyć operatora, `+` aby połączyć ciągi. Jeśli operandy są obu ciągów, Visual Basic je łączyć. Wynik łączenia reprezentuje pojedynczy ciąg składający się z zawartości dwóch operandów jeden po drugim.  
  
 Jeśli operandy są typu mieszanego, wynik zależy od ustawienia [Option Strict instrukcji](../../../visual-basic/language-reference/statements/option-strict-statement.md). Poniższy przykład ilustruje wynik `Option Strict`. `On`  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Poniższy przykład ilustruje wynik `Option Strict`. `Off`  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Aby wyeliminować niejednoznaczności, należy użyć `&` operatora `+` zamiast łączenia.  
  
## <a name="see-also"></a>Zobacz także

- [&, operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
