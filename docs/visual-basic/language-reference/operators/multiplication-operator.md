---
title: '* — Operator (Visual Basic)'
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
ms.openlocfilehash: 09b95585325b05c0b7925c4c1c9e123f45791e10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936646"
---
# <a name="-operator-visual-basic"></a>* Operator (Visual Basic)
Mnoży dwie liczby.  
  
## <a name="syntax"></a>Składnia  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`number1`|Wymagana. Dowolne wyrażenie numeryczne.|  
|`number2`|Wymagana. Dowolne wyrażenie numeryczne.|  
  
## <a name="result"></a>Wynik  
 Wynik jest wynikiem `number1` i `number2`.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.  
  
## <a name="remarks"></a>Uwagi  
 Typ danych wynik zależy od typów argumentów. W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.  
  
|Argumentami o typach danych|Typ danych wyniku|  
|---|---|  
|Oba wyrażenia są integralnymi typami danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długie](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Typ danych numerycznych, odpowiednie dla typów danych `number1` i `number2`. Zobacz tabele "Integer arytmetyczny" w [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba wyrażenia są [dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Oba wyrażenia są [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Albo wyrażenie jest typu zmiennoprzecinkowego (`Single` lub [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale nie obu `Single` (Uwaga `Decimal` nie jest typu zmiennoprzecinkowego)|`Double`|  
  
 Jeśli wyrażenie ma [nic](../../../visual-basic/language-reference/nothing.md), jest ona traktowana jak zero.  
  
## <a name="overloading"></a>Przeciążenie  
 `*` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `*` operatora mnożenia dwóch liczb. Wynik jest iloczyn dwóch argumentów operacji.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [*=, operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
