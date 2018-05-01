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
Operator dekrementacji (`--`) zmeniejsza wartośc jego operandu o 1. Operator dekrementacji może występować przed lub po jego argumencie: `--variable` i `variable--`. Pierwszą formą jest dekrementacja prefiksowa. Wynikiem tej operacji jest wartość operandu po zmniejszeniu. Drugą formą jest dekrementacja postfiksowa. Wynikiem tej operacji jest wartość operandu przed jej zmniejszeniem.  
  
## <a name="remarks"></a>Uwagi  
 Typy numeryczne i wyliczenia mają wstępnie zdefiniowane operatory dekrementacji. W typach definiowanych przez użytkownika można przeciążać operator `--`. Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone. 
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
