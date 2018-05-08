---
title: '&amp; Operator (odwołanie w C#)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 59813b4bc5781776c9f9741c3e49e660c684bff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="amp-operator-c-reference"></a>&amp; Operator (odwołanie w C#)
`&` Operator może działać jako jednoargumentowy lub operator binarny.  
  
## <a name="remarks"></a>Uwagi  
 Jednoargumentowego `&` adres jej argument zwraca (wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu).  
  
 Binarny `&` operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`. Dla typu całkowitego typy & oblicza logiczne i bitowe dla argumentów. Dla `bool` operandy & oblicza logiczny i z argumentów; wynik jest `true` tylko wtedy, gdy są obie argumentów `true`.  
  
 Plik binarny `&` operator ocenia oba operatory niezależnie od pierwszego obiektu, w przeciwieństwie do wartości [operator warunkowy i](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`. Na przykład:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Typy definiowane przez użytkownika można przeciążać plik binarny `&` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu. Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
