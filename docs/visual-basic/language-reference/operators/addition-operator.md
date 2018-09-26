---
title: + — Operator (Visual Basic)
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
ms.openlocfilehash: 91806c204c313956b292eb9c9be078991f733b4e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231483"
---
# <a name="-operator-visual-basic"></a>+ — Operator (Visual Basic)
Dodaje dwie liczby i zwraca wartość dodatnią wyrażenia liczbowego. Można również do łączenia dwóch ciągów wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression1`|Wymagane. Dowolne wyrażenie, liczbą lub ciągiem.|  
|`expression2`|Wymagane, chyba że `+` operator obliczania wartości ujemnej. Dowolne wyrażenie, liczbą lub ciągiem.|  
  
## <a name="result"></a>Wynik  
 Jeśli `expression1` i `expression2` są liczbowe, wynik jest ich suma arytmetyczne.  
  
 Jeśli `expression2` jest nieobecne, `+` operator jest *jednoargumentowe* operator tożsamości dla niezmienione wartości wyrażenia. W tym sensie, operacja składa się z zachowaniem znak `expression1`, więc wynik jest ujemny Jeśli `expression1` jest ujemna.  
  
 Jeśli `expression1` i `expression2` są oba ciągi, wynik jest łączenie ich wartości.  
  
 Jeśli `expression1` i `expression2` są mieszane typy akcji wykonywanej zależy od ich typy, ich zawartość i ustawienia [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md). Aby uzyskać więcej informacji zobacz tabele w "Uwagi".  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`, i `String`.  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc `+` wykonuje arytmetyczne Dodawanie, gdy jest to możliwe, a następnie łączy tylko, gdy oba wyrażenia są ciągami.  
  
 Jeśli żadna wyrażenie jest `Object`, Visual Basic wykonuje następujące akcje.  
  
|Typy danych wyrażeń|Akcja przez kompilator|  
|---|---|  
|Oba wyrażenia są typy danych liczbowych (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, lub `Double`)|Dodaj. Typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`. Zobacz tabele "Integer arytmetyczny" w [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba wyrażenia są typu `String`|Łączenie.|  
|Jedno wyrażenie jest typu liczbowego, a drugi to ciąg|Jeśli `Option Strict` jest `On`, następnie generują błędy kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertować `String` do `Double` i Dodaj.<br /><br /> Jeśli `String` nie można przekonwertować na `Double`, następnie generują <xref:System.InvalidCastException> wyjątku.|  
|Jedno wyrażenie jest typu liczbowego, a drugi to [nic](../../../visual-basic/language-reference/nothing.md)|Dodawanie, za pomocą `Nothing` zwracająca wartość zero.|  
|Jedno wyrażenie jest ciągiem, a drugi to `Nothing`|ZŁĄCZ.teksty, za pomocą `Nothing` cenionym jako "".|  
  
 Jeśli jest jedno wyrażenie `Object` wyrażenie języka Visual Basic wykonuje następujące akcje.  
  
|Typy danych wyrażeń|Akcja przez kompilator|  
|---|---|  
|`Object` wyrażenie zawiera wartość liczbową, a drugi to dane typu liczbowego|Jeśli `Option Strict` jest `On`, następnie generują błędy kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, następnie dodać.|  
|`Object` wyrażenie zawiera wartość liczbową, a drugi to typu `String`|Jeśli `Option Strict` jest `On`, następnie generują błędy kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertować `String` do `Double` i Dodaj.<br /><br /> Jeśli `String` nie można przekonwertować na `Double`, następnie generują <xref:System.InvalidCastException> wyjątku.|  
|`Object` wyrażenie zawiera ciąg, a drugi to dane typu liczbowego|Jeśli `Option Strict` jest `On`, następnie generują błędy kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertować ciąg `Object` do `Double` i Dodaj.<br /><br /> Jeśli ciąg `Object` nie można przekonwertować na `Double`, następnie generują <xref:System.InvalidCastException> wyjątku.|  
|`Object` wyrażenie zawiera ciąg, a drugi to typu `String`|Jeśli `Option Strict` jest `On`, następnie generują błędy kompilatora.<br /><br /> Jeśli `Option Strict` jest `Off`, niejawnie przekonwertować `Object` do `String` i łączenia.|  
  
 Jeśli oba wyrażenia są `Object` wyrażenia języka Visual Basic wykonuje następujące akcje (`Option Strict Off` tylko).  
  
|Typy danych wyrażeń|Akcja przez kompilator|  
|---|---|  
|Zarówno `Object` wyrażeń przechowywać wartości liczbowe|Dodaj.|  
|Zarówno `Object` wyrażenia są typu `String`|Łączenie.|  
|Jeden `Object` wyrażenie zawiera wartość numeryczną i zawiera drugi ciąg|Niejawnie przekonwertować ciąg `Object` do `Double` i Dodaj.<br /><br /> Jeśli ciąg `Object` nie można przekonwertować na wartość liczbową, a następnie throw <xref:System.InvalidCastException> wyjątku.|  
  
 Jeśli `Object` wyrażenie daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md) lub <xref:System.DBNull>, `+` operator traktuje je jako `String` o wartości "".  
  
> [!NOTE]
>  Kiedy używasz `+` operatora, może nie można określić, czy dodanie lub ciąg łączenie wystąpi. Użyj `&` operatora łączenia, aby wyeliminować niejednoznaczności i zapewnienie automatycznie dokumentowane kodu.  
  
## <a name="overloading"></a>Przeciążenie  
 `+` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `+` operator dodawania numerów. Jeśli argumenty operacji są wartości liczbowe, Visual Basic oblicza wynik arytmetyczne. Wynik arytmetyczny reprezentuje sumę dwóch argumentów operacji.  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 Można również użyć `+` operatora łączenia ciągów. Jeśli argumenty operacji są oba ciągi, Visual Basic łączy je. Wynik łączenia reprezentuje pojedynczy ciąg składający się z zawartości dwóch argumentów operacji jeden po drugim.  
  
 Jeśli argumenty operacji są mieszane typy, wynik zależy od ustawienia [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md). Poniższy przykład ilustruje wynik po `Option Strict` jest `On`.  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 Poniższy przykład ilustruje wynik po `Option Strict` jest `Off`.  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 Aby usunąć niejednoznaczność, należy użyć `&` operator zamiast `+` dla łączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [&, operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
