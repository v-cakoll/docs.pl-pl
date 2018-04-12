---
title: Operator -- (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4eb68143103d44defeac7191e7c4ce7d1ee90e9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="---operator-c-reference"></a>Operator -- (odwołanie w C#)
Operator dekrementacji (`--`) zmniejsza jej argument operacji o 1. Operator dekrementacji może występować przed lub po jej argument: `--variable` i `variable--`. Pierwszy formularz jest operacją dekrementacja prefiks. Wynikiem operacji jest wartość operandu "po" została zmniejszona. Drugi formularz jest operacją dekrementacja przyrostek. Wynik operacji jest wartość operandu "przed" została zmniejszona.  
  
## <a name="remarks"></a>Uwagi  
 Typy numeryczne i wyliczenia mają wstępnie zdefiniowane dekrementacji.  
  
 Typy definiowane przez użytkownika można przeciążać `--` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
