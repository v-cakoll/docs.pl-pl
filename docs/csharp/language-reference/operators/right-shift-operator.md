---
title: '&gt;&gt;Operator (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7c2eddf06d7b8417c9fcb0fed395b2bf51e07144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;Operator (odwołanie w C#)
Operator przesunięcia w prawo (`>>`) przesuwa jego pierwszy argument operacji po prawej przez liczbę bitów określony przez jego drugi argument operacji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli pierwszy argument operacji jest [int](../../../csharp/language-reference/keywords/int.md) lub [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitowy), licznik przesunięć oblicza znaczącymi bitami pięć bitów drugi argument operacji (drugi operand & 0x1f).  
  
 Jeśli pierwszy argument operacji jest [długi](../../../csharp/language-reference/keywords/long.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza za pomocą liczby bitów sześciu znaczącymi bitami drugi operand (drugi operand & 0x3f).  
  
 Jeśli pierwszy argument operacji jest [int](../../../csharp/language-reference/keywords/int.md) lub [długi](../../../csharp/language-reference/keywords/long.md), prawy klawisz shift jest arytmetyczne przesunięcie (pusta bardziej znaczących bitów ustawiono bitu znaku). Jeśli pierwszy argument operacji jest typu [uint](../../../csharp/language-reference/keywords/uint.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md), prawy klawisz shift jest Przesunięcie logiczne (bardziej znaczących bitów są wypełnione zero).  
  
 Typy definiowane przez użytkownika można przeciążać `>>` operator; typ pierwszego argumentu musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być [int](../../../csharp/language-reference/keywords/int.md). Aby uzyskać więcej informacji, zobacz [operator](../../../csharp/language-reference/keywords/operator.md). Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
