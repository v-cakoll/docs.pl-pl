---
title: "&amp;Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eceee8e01ba46f65c6b182a40d14e62aaba5dd53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a>&amp;Operator (odwołanie w C#)
& — Operator może działać jako jednoargumentowy lub operator binarny.  
  
## <a name="remarks"></a>Uwagi  
 Operator & jednoargumentowy zwraca adres jej argument operacji (wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu).  
  
 Dane binarne & operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`. Dla typu całkowitego typy & oblicza logiczne i bitowe dla argumentów. Dla `bool` operandy & oblicza logiczny i z argumentów; wynik jest `true` tylko wtedy, gdy są obie argumentów `true`.  
  
 `&` Operator ocenia oba operatory niezależnie od pierwszego elementu wartości. Na przykład:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Typy definiowane przez użytkownika można przeciążać plik binarny `&` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu. Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
