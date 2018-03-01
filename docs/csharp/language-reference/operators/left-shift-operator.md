---
title: "&lt;&lt;Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 400dbc799c68bb9e1bc00695954115f2eb6af7c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;Operator (odwołanie w C#)
Operator przesunięcia w lewo (`<<`) zmiany jego pierwszym argumentem pozostawionego przez liczbę bitów określony przez jego drugi argument operacji. Typ drugiego argumentu operacji musi być [int](../../../csharp/language-reference/keywords/int.md) lub typu, który ma wstępnie zdefiniowanych niejawna konwersja liczbowa na `int`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli pierwszy argument operacji jest [int](../../../csharp/language-reference/keywords/int.md) lub [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitowy), licznik przesunięć oblicza znaczącymi bitami pięć bitów drugiego argumentu operacji. Licznik przesunięć rzeczywistego jest bitów 0 do 31.  
  
 Jeśli pierwszy argument operacji jest [długi](../../../csharp/language-reference/keywords/long.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza za pomocą liczby bitów sześciu znaczącymi bitami drugiego argumentu operacji. Licznik przesunięć rzeczywistego jest 0 – 63 bity.  
  
 Żadnych znaczących bitów, które są nie w zakresie typ pierwszego argumentu po zmiany zostaną odrzucone i bits pusty znaczącymi bitami są wypełnione zero. Operacje SHIFT nigdy nie powodują przepełnienia.  
  
 Typy definiowane przez użytkownika można przeciążać `<<` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)); typ pierwszego argumentu musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być `int`. Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a>Komentarze  
 Należy pamiętać, że `i<<1` i `i<<33` zapewniają takiego samego wyniku, ponieważ 1 i 33 ma tego samego pięć bitów znaczącymi bitami.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
