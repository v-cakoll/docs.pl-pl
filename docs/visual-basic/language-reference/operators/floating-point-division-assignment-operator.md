---
title: Operator /=
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 48ae78630aa66ad804d539f88524c456cf805889
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371248"
---
# <a name="-operator-visual-basic"></a>/= — Operator (Visual Basic)
Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik zmiennoprzecinkowy do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna zmienna lub właściwość numeryczna.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `/=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).  
  
 `/=`Operator najpierw dzieli wartość zmiennej lub właściwości (po lewej stronie operatora) na podstawie wartości wyrażenia (po prawej stronie operatora).... Następnie operator przypisuje wynik zmiennoprzecinkowy tej operacji do zmiennej lub właściwości.  
  
 Ta instrukcja przypisuje `Double` wartość do zmiennej lub właściwości po lewej stronie. Jeśli `Option Strict` jest `On` , `variableorproperty` musi być `Double` . Jeśli `Option Strict` jest `Off` , Visual Basic wykonuje niejawną konwersję i przypisuje wartość wyniki do `variableorproperty` , z możliwym błędem w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) oraz [ścisłe instrukcje Option](../statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Przeciążenie  
 [Operator/(Visual Basic)](floating-point-division-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie `/` operatora ma wpływ na zachowanie `/=` operatora. Jeśli kod korzysta z `/=` klasy lub struktury, która przeciążania `/` , należy poznać jej ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `/=` operatora do dzielenia jednej `Integer` zmiennej przez sekundę i przypisywania ilorazu do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz też

- [/— Operator (Visual Basic)](floating-point-division-operator.md)
- [\\= — Operator](integer-division-assignment-operator.md)
- [Operatory przypisania](assignment-operators.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
