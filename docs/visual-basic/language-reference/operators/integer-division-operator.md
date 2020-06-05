---
title: '\ — Operator'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 1f8095afc5f096928b946607adc715af49827022
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370885"
---
# <a name="-operator-visual-basic"></a>\ — Operator (Visual Basic)
Dzieli dwie liczby i zwraca wynik w postaci liczby całkowitej.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Części  
 `expression1`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
 `expression2`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="supported-types"></a>Obsługiwane typy  
 Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal` .  
  
## <a name="result"></a>Wynik  
 Wynikiem jest iloraz wartości całkowitej `expression1` podzieloną przez `expression2` , która odrzuca resztę i zachowuje tylko część całkowitą. Jest to tzw. *obcinanie*.  
  
 Typ danych wyniku jest typem liczbowym odpowiednim dla typów danych `expression1` i `expression2` . Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](data-types-of-operator-results.md).  
  
 [Operator/(Visual Basic)](floating-point-division-operator.md) zwraca pełny iloraz, który zachowuje resztę części ułamkowej.  
  
## <a name="remarks"></a>Uwagi  
 Przed przeprowadzeniem dzielenia, Visual Basic próbuje skonwertować dowolne wyrażenie liczbowe zmiennoprzecinkowe na `Long` . Jeśli `Option Strict` jest `On` , wystąpi błąd kompilatora. Jeśli `Option Strict` jest `Off` , <xref:System.OverflowException> jest to możliwe, jeśli wartość znajduje się poza zakresem [długiego typu danych](../data-types/long-data-type.md). Konwersja na `Long` jest również uwarunkowana *zaokrągleniem przez Bank*. Aby uzyskać więcej informacji, zobacz "części ułamkowe" w [funkcjach konwersji typów](../functions/type-conversion-functions.md).  
  
 Jeśli `expression1` lub `expression2` zwróci wartość [Nothing](../nothing.md), jest traktowany jako zero.  
  
## <a name="attempted-division-by-zero"></a>Próba dzielenia przez zero  
 Jeśli `expression2` wartość jest równa zero, `\` operator zgłasza <xref:System.DivideByZeroException> wyjątek. Dotyczy to wszystkich typów danych liczbowych argumentów operacji.  
  
> [!NOTE]
> `\`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `\` Aby wykonać dzielenie liczby całkowitej. Wynik jest liczbą całkowitą, która reprezentuje iloraz liczby całkowitej dwóch operandów, z odrzuconym resztą.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Wyrażenia w poprzednim przykładzie zwracają odpowiednio wartości 2, 3, 33 i-22.  
  
## <a name="see-also"></a>Zobacz też

- [\\= — Operator](integer-division-assignment-operator.md)
- [/— Operator (Visual Basic)](floating-point-division-operator.md)
- [Option Strict — Instrukcja](../statements/option-strict-statement.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
