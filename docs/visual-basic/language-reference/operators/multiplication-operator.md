---
title: '* Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: b5b601c7604cb7ce1afaebc98b2157634a77fda4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701091"
---
# <a name="-operator-visual-basic"></a>* Operator (Visual Basic)
Mnoży dwie liczby.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`number1`|Wymagany. Dowolne wyrażenie liczbowe.|  
|`number2`|Wymagany. Dowolne wyrażenie liczbowe.|  
  
## <a name="result"></a>Wynik  
 Wynikiem jest iloczyn `number1` i `number2`.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`.  
  
## <a name="remarks"></a>Uwagi  
 Typ danych wyniku zależy od typów operandów. W poniższej tabeli przedstawiono sposób określania typu danych wyniku.  
  
|Typy danych operandu|Typ danych wynikowych|  
|---|---|  
|Oba wyrażenia są typami danych całkowitych[(](../../../visual-basic/language-reference/data-types/sbyte-data-type.md) [bajty, Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótkie](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULONG](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Typ danych liczbowych odpowiedni dla typów danych `number1` i `number2`. Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba wyrażenia są [dziesiętne](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Oba wyrażenia są [pojedynczymi](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Oba wyrażenia są typu danych zmiennoprzecinkowych (`Single` lub [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale nie obu `Single` (Uwaga `Decimal` nie jest typem danych zmiennoprzecinkowych)|`Double`|  
  
 Jeśli wyrażenie zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), jest traktowane jako zero.  
  
## <a name="overloading"></a>Przeciążenie  
 Operator `*` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa operatora `*`, aby pomnożyć dwie liczby. Wynikiem jest iloczyn dwóch operandów.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [*=, operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
