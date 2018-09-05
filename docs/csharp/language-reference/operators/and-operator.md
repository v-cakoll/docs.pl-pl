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
ms.openlocfilehash: b257c7d41618464e26ab3b54bcfb1f1e2c2e420e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510981"
---
# <a name="amp-operator-c-reference"></a>&amp; Operator (odwołanie w C#)
`&` Operator może działać jako jednoargumentowy lub binarny.  
  
## <a name="remarks"></a>Uwagi  
 Jednoargumentowy `&` operator zwraca adres jego operandu (wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu).  
  
 Operatory binarne `&` są wstępnie zdefiniowane dla typów całkowitych i `bool`. Dla całkowite typy i oblicza logiczne bitowe AND swoich argumentów. Dla `bool` operandy & oblicza logicznym i jego operandu; oznacza to wynik jest `true` tylko wtedy, gdy oba jego operandy są `true`.  
  
 Plik binarny `&` operator ocenia oba operandy niezależnie od tego, pierwszy z nich wartości, w przeciwieństwie do [operatora warunkowego i](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`. Na przykład:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia pliku binarnego `&` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone. Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
