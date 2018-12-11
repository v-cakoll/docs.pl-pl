---
title: '&gt;&gt; Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: fc3d683f212c71620049ec6adee3d20bd5c1437c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239998"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; Operator (odwołanie w C#)
Operator przesunięcia w prawo (`>>`) przenosi pierwszy argument operacji w prawo o liczbę bitów określoną przez drugim argumentem operacji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli pierwszy argument jest [int](../../../csharp/language-reference/keywords/int.md) lub [uint](../../../csharp/language-reference/keywords/uint.md) (32-bitowy), licznik przesunięć oblicza mniej znaczące bity pięć, drugi operand (drugi operand & 0x1f).  
  
 Jeśli pierwszy argument jest [długie](../../../csharp/language-reference/keywords/long.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza mniej znaczące bity sześć, drugi operand (drugi operand & 0x3f).  
  
 Jeśli pierwszy argument jest [int](../../../csharp/language-reference/keywords/int.md) lub [długie](../../../csharp/language-reference/keywords/long.md), prawy shift jest arytmetycznego przesunięcia (wyższego rzędu pusty bity są ustawione na bit znaku). Jeśli pierwszy operand jest typu [uint](../../../csharp/language-reference/keywords/uint.md) lub [ulong](../../../csharp/language-reference/keywords/ulong.md), prawy shift to Przesunięcie logiczne (bity wyższego rzędu są wypełnione przez zera).  
  
 Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia `>>` operator; typ pierwszy operand musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być [int](../../../csharp/language-reference/keywords/int.md). Aby uzyskać więcej informacji, zobacz [operator](../../../csharp/language-reference/keywords/operator.md). Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
