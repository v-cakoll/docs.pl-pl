---
title: "+ — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb0d66db2d777c046ccec69acc1f2069d21baf6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>+ — Operator (Visual Basic)
Dodaje dwie liczby i zwraca wartość dodatnią wyrażenia liczbowego. Można również do łączenia dwóch ciągów wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression1`|Wymagany. Dowolne wyrażenie numeryczny lub ciąg.|  
|`expression2`|Wymagany, chyba że `+` operator jest obliczenie wartości ujemnej. Dowolne wyrażenie numeryczny lub ciąg.|  
  
## <a name="result"></a>Wynik  
 Jeśli `expression1` i `expression2` są numeryczną, wynikiem jest ich arytmetyczne sum.  
  
 Jeśli `expression2` jest nieobecne, `+` operator jest *jednoargumentowy* operator tożsamości dla niezmienione wartości wyrażenia. W tym sensie, operacja składa się z zachowując znak `expression1`, więc wynik jest ujemny Jeśli `expression1` jest ujemna.  
  
 Jeśli `expression1` i `expression2` są oba ciągi wynik jest złączeniem ich wartości.  
  
 Jeśli `expression1` i `expression2` są mieszane typy akcji wykonywanej zależy od ich typów, ich zawartość i ustawienia [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md). Aby uzyskać więcej informacji zobacz tabelę w "Uwagi".  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe w tym typy bez znaku i liczb zmiennoprzecinkowych i `Decimal`, i `String`.  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc `+` przeprowadza dodanie arytmetyczne, gdy jest to możliwe, a następnie łączy tylko, gdy oba wyrażenia są ciągami.  
  
 Jeśli wyrażenie nie ani `Object`, Visual Basic wykonuje następujące akcje.  
  
|Typy danych wyrażeń|Akcja przez kompilator|  
|---|---|  
|Oba wyrażenia są numeryczne typy danych (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, lub `Double`)|Dodaj. Typ danych wyniku jest odpowiednie dla typów dane typu liczbowego `expression1` i `expression2`. Zobacz "Całkowitą arytmetycznego" tabele w [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba wyrażenia są typu`String`|Łączenie.|  
|Jedno wyrażenie to dane typu liczbowego, a drugi to ciąg|Jeśli `Option Strict` jest `On`, następnie wygenerowanie błędu kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertować `String` do `Double` i Dodaj.<br /><br /> Jeśli `String` nie można przekonwertować na `Double`, następnie throw <xref:System.InvalidCastException> wyjątku.|  
|Jedno wyrażenie to dane typu liczbowego, a drugi to [nic](../../../visual-basic/language-reference/nothing.md)|Dodawanie, z `Nothing` zwracającej wartość zero.|  
|Jedno wyrażenie jest ciągiem, a drugi to`Nothing`|ZŁĄCZ.teksty z `Nothing` ważnych jako "".|  
  
 Jeśli jest jedno wyrażenie `Object` wyrażenia języka Visual Basic wykonuje następujące akcje.  
  
|Typy danych wyrażeń|Akcja przez kompilator|  
|---|---|  
|`Object`wyrażenie zawiera wartość numeryczną, a drugi to dane typu liczbowego|Jeśli `Option Strict` jest `On`, następnie wygenerowanie błędu kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, następnie dodać.|  
|`Object`wyrażenie zawiera wartość liczbową i innych jest typu`String`|Jeśli `Option Strict` jest `On`, następnie wygenerowanie błędu kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertować `String` do `Double` i Dodaj.<br /><br /> Jeśli `String` nie można przekonwertować na `Double`, następnie throw <xref:System.InvalidCastException> wyjątku.|  
|`Object`wyrażenie zawiera ciąg, a drugi to dane typu liczbowego|Jeśli `Option Strict` jest `On`, następnie wygenerowanie błędu kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertować ciągu `Object` do `Double` i Dodaj.<br /><br /> Jeśli ciąg `Object` nie można przekonwertować na `Double`, następnie throw <xref:System.InvalidCastException> wyjątku.|  
|`Object`wyrażenie zawiera ciąg, a drugi to typu`String`|Jeśli `Option Strict` jest `On`, następnie wygenerowanie błędu kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertować `Object` do `String` i łączenia.|  
  
 Jeśli oba wyrażenia są `Object` wyrażenia, Visual Basic wykonuje następujące akcje (`Option Strict Off` tylko).  
  
|Typy danych wyrażeń|Akcja przez kompilator|  
|---|---|  
|Zarówno `Object` wyrażenia przechowywania wartości liczbowych|Dodaj.|  
|Zarówno `Object` wyrażenia są typu`String`|Łączenie.|  
|Jeden `Object` wyrażenie zawiera wartość liczbową i innych ma postać ciągu|Niejawnie przekonwertować ciągu `Object` do `Double` i Dodaj.<br /><br /> Jeśli ciąg `Object` nie można przekonwertować na wartość numeryczną, a następnie throw <xref:System.InvalidCastException> wyjątku.|  
  
 Jeśli dowolny `Object` wyrażenie daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md) lub <xref:System.DBNull>, `+` operator traktuje ją jako `String` o wartości "".  
  
> [!NOTE]
>  Jeśli używasz `+` operatora, może nie można ustalić, czy nastąpi dodanie lub ciąg łączenia. Użyj `&` operatora łączenia wyeliminować niejednoznaczności oraz zapewnienia automatycznie dokumentowane kodu.  
  
## <a name="overloading"></a>Przeciążenie  
 `+` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `+` operator dodawania numerów. Jeśli argumenty operacji są wartości liczbowe, Visual Basic oblicza wynik arytmetyczny. Wynik arytmetyczny reprezentuje sumę dwóch argumentów operacji.  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 Można również użyć `+` operatora łączenia ciągów. Jeśli argumenty operacji są oba parametry, Visual Basic łączy je. Wynik łączenia reprezentuje jeden ciąg składający się z zawartości dwóch argumentów operacji jeden po drugim.  
  
 Jeśli argumenty operacji są mieszane typy, wynik zależy od ustawienia [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md). Poniższy przykład przedstawia wynik po `Option Strict` jest `On`.  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 Poniższy przykład przedstawia wynik po `Option Strict` jest `Off`.  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 Aby usunąć niejednoznaczność, należy użyć `&` operator zamiast `+` dla łączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [& — Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
