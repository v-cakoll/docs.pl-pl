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
Operatory binarne `^` są wstępnie zdefiniowane dla typów całkowitych i `bool`. W przypadku typów całkowitych `^` oblicza bitową alternatywę rozłączną dla operandu. Dla operacji na zmiennych typu `bool` `^` oblicza alternatywę rozłączną dla jej argumentów. Wynik jest `true` tylko wtedy, gdy dokładnie jeden z argumentów to `true`.  
  
## <a name="remarks"></a>Uwagi  
 Typy definiowane przez użytkownika mogą przeciążać operator `^` — (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Operacje na typach całkowitych zazwyczaj są dozwolone na wyliczeniach.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 Obliczenie `0xf8 ^ 0x3f` w poprzednim przykładzie powoduje wykonanie bitowej operacji wyłącznej OR na następnych dwóch wartościach binarnych, które odpowiadają wartościom szesnastkowym F8 i 3F:  
  
 `1111 1000`  
  
 `0011 1111`  
  
 Wynik alternatywy rozłącznej to `1100 0111`, czyli C7 w formacie szesnastkowym.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
