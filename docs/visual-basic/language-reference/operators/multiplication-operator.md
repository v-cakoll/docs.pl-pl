---
title: '* Operator'
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
ms.openlocfilehash: f1a7653fb3006ab3c9736ec168a8c5ea028f4763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409326"
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
 Wynikiem jest iloczyn `number1` i `number2` .  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal` .  
  
## <a name="remarks"></a>Uwagi  
 Typ danych wyniku zależy od typów operandów. W poniższej tabeli przedstawiono sposób określania typu danych wyniku.  
  
|Typy danych operandu|Typ danych wynikowych|  
|---|---|  
|Oba wyrażenia są typami danych całkowitych[(](../data-types/sbyte-data-type.md) [bajty, Byte](../data-types/byte-data-type.md), [krótkie](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger —](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULONG](../data-types/ulong-data-type.md))|Typ danych liczbowych odpowiedni dla typów danych `number1` i `number2` . Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](data-types-of-operator-results.md).|  
|Oba wyrażenia są [dziesiętne](../data-types/decimal-data-type.md)|`Decimal`|  
|Oba wyrażenia są [pojedynczymi](../data-types/single-data-type.md)|`Single`|  
|Oba wyrażenia są typu danych zmiennoprzecinkowych ( `Single` lub [Double](../data-types/double-data-type.md)), ale nie obu `Single` (Uwaga nie `Decimal` jest typem danych zmiennoprzecinkowych)|`Double`|  
  
 Jeśli wyrażenie zwróci wartość [Nothing](../nothing.md), jest traktowane jako zero.  
  
## <a name="overloading"></a>Przeciążenie  
 `*`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Ten przykład używa `*` operatora, aby pomnożyć dwie liczby. Wynikiem jest iloczyn dwóch operandów.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- [Operator * =](multiplication-assignment-operator.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
