---
title: '* — Operator (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 450d728e44ef5639d75369e05b47cb3009b4d769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
|`number1`|Wymagany. Dowolne wyrażenie liczbowe.|  
|`number2`|Wymagany. Dowolne wyrażenie liczbowe.|  
  
## <a name="result"></a>Wynik  
 Wynik jest iloczyn `number1` i `number2`.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe w tym typy bez znaku i liczb zmiennoprzecinkowych i `Decimal`.  
  
## <a name="remarks"></a>Uwagi  
 Typ danych w wyniku zależy od typów argumenty operacji. W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.  
  
|Argument operacji typy danych|Typ danych wyników|  
|---|---|  
|Oba wyrażenia są typy całkowite danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długi](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Dane typu liczbowego odpowiednie dla typów danych `number1` i `number2`. Zobacz "Całkowitą arytmetycznego" tabele w [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba wyrażenia są [dziesiętną](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Oba wyrażenia są [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Jedno z wyrażeń ma typ danych liczb zmiennoprzecinkowych (`Single` lub [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale nie oba `Single` (Uwaga `Decimal` nie jest typem danych zmiennoprzecinkowych)|`Double`|  
  
 Jeśli wyrażenie ma [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.  
  
## <a name="overloading"></a>Przeciążenie  
 `*` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `*` operatora, aby pomnożyć dwóch liczb. Wynik jest iloczyn dwóch argumentów operacji.  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [* = — Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
