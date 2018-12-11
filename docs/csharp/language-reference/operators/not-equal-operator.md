---
title: '! = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 15f1b5930117e608644a58343fb855562f36b21c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237821"
---
# <a name="-operator-c-reference"></a>!= — Operator (odwołanie w C#)
Operator nierówności (`!=`) zwraca wartość false, jeśli jego operandy są takie same wartości true w przeciwnym razie. Operatory nierówności są wstępnie zdefiniowane dla wszystkich typów, w tym ciągi i obiekty. Typy definiowane przez użytkownika mogą przeciążać operator `!=`.  
  
## <a name="remarks"></a>Uwagi  
 Dla wstępnie zdefiniowanych typów wartości, operator nierówności (`!=`) zwraca wartość true, jeśli wartości argumentów są różne, wartość false w przeciwnym razie. Dla odwołania do typów innych niż `string`, `!=` zwraca wartość true, jeśli jego dwa operandy odnoszą się do różnych obiektów. Aby uzyskać `string` typu `!=` porównuje wartości ciągów.  
  
 Typy wartości zdefiniowanej przez użytkownika może doprowadzić do przeciążenia `!=` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Ty też typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `!=` zachowuje się jak opisano powyżej dla obu typów referencyjnych wstępnie zdefiniowanych i zdefiniowanych przez użytkownika. Jeśli `!=` jest przeciążona, [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) musi również być przeciążony. Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
