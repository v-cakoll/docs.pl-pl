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
ms.openlocfilehash: d4a269c07e0d6dc2ac6a6a101f200653c6ea7a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267410"
---
# <a name="-operator-c-reference"></a>+ — Operator (odwołanie w C#)
`+` Operator może działać jako jednoargumentowy lub operator binarny.  
  
## <a name="remarks"></a>Uwagi  
 Jednoargumentowy `+` operatory są wstępnie zdefiniowane dla wszystkich typów numerycznych. Wynik jednoargumentowy `+` operacji na typ liczbowy jest tylko wartość argumentu operacji.  
  
 Binarny `+` operatory są wstępnie zdefiniowane dla typu liczbowego i ciąg. Dla numeryczne typy + oblicza sumę dwóch argumentów. Jeśli jeden lub obydwa argumenty operacji są typu ciąg + łączy reprezentacji ciągu argumenty operacji.  
  
 Typy delegatów również udostępniać dane binarne `+` operatora, który wykonuje łączenia obiektu delegowanego.  
  
 Typy definiowane przez użytkownika można przeciążać jednoargumentowego `+` i binarne `+` operatorów. Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu. Aby uzyskać więcej informacji, zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
 [Operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)
