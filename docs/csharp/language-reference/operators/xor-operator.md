---
title: ^ — Operator (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4ccd32ea8abd8ca3252380083eafecad2b572ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
