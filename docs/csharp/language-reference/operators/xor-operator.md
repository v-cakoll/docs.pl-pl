---
title: ^ — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>^ — Operator (odwołanie w C#)
Binarny `^` operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`. W przypadku typów całkowitych `^` oblicza bitowej OR wyłączne argumentów. Dla `bool` argumentów operacji, `^` oblicza logicznej wyłącznie — lub z argumentów; wynik jest `true` tylko wtedy, gdy jest dokładnie jeden z argumentów `true`.  
  
## <a name="remarks"></a>Uwagi  
 Typy definiowane przez użytkownika można przeciążać `^` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 Do obliczenia `0xf8 ^ 0x3f` w poprzednim przykładzie wykonuje bitowej OR wyłączne następujących dwóch wartości binarnych, które odpowiadają wartości szesnastkowe F8 i 3F:  
  
 `1111 1000`  
  
 `0011 1111`  
  
 Wynik OR wyłączne jest `1100 0111`, która jest w formacie szesnastkowym C7.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
