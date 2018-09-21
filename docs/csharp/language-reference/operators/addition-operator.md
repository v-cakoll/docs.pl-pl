---
title: + Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: b49694bc8937c58bd295f0f8e57c378802d0dfb9
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46470788"
---
# <a name="-operator-c-reference"></a>+ — Operator (odwołanie w C#)
`+` Operator może działać jako jednoargumentowy lub binarny.  
  
## <a name="remarks"></a>Uwagi  
 Jednoargumentowy `+` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych. Wynik jednoargumentowy `+` operacja na typ liczbowy jest po prostu wartość operandu.  
  
 Binarny `+` operatory są wstępnie zdefiniowane dla typów liczbowych i. Dla liczbowych typów i oblicza sumę dwóch argumentów operacji. Kiedy jeden lub obydwa operandy są typu ciąg i łączy ciągów reprezentujących argumenty operacji.  
  
 Typy delegatów udostępniają dane binarne `+` operatora, który wykonuje łączenie delegatów.  
  
 Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia jednoargumentowe `+` binarnej i `+` operatorów. Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone. Aby uzyskać więcej informacji, zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
- [Operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)
