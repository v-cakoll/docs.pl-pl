---
title: Operator -- (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 615b100447233856ab3740d075d69e3ae19285fd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45588088"
---
# <a name="---operator-c-reference"></a>Operator -- (odwołanie w C#)
Operator dekrementacji (`--`) zmniejsza wartość jego argumentu operacji o 1. Operator dekrementacji może występować przed argumentem operacji lub po nim: `--variable` i `variable--`. Pierwszą formą jest dekrementacja prefiksowa. Wynikiem tej operacji jest wartość argumentu operacji po zmniejszeniu. Drugą formą jest dekrementacja odwrotna.  Wynikiem tej operacji jest wartość argumentu przed zmniejszeniem.  
  
## <a name="remarks"></a>Uwagi  
 Typy numeryczne i wyliczenia mają wstępnie zdefiniowane operatory dekrementacji.  
  
 W typach definiowanych przez użytkownika można przeciążać operator `--` (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
