---
title: '!= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e974ffb1b25944e24fca23864dc7e932ec1876d5
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537504"
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
