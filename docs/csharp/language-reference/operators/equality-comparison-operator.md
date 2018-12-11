---
title: == Operator — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: c6f93be4d422fe42787e36f5b86e2cccbfc645b7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239017"
---
# <a name="-operator-c-reference"></a>Operator == (odwołanie w C#)
Dla wstępnie zdefiniowanych typów wartości, operatora równości (`==`) zwraca wartość true, jeśli wartości argumentów są takie same `false` inaczej. Dla odwołania do typów innych niż [ciąg](../../../csharp/language-reference/keywords/string.md), `==` zwraca `true` Jeśli dwóch argumentów operacji odnoszą się do tego samego obiektu. Aby uzyskać `string` typu `==` porównuje wartości ciągów.  
  
## <a name="remarks"></a>Uwagi  
 Typy wartości zdefiniowanej przez użytkownika może doprowadzić do przeciążenia `==` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Ty też typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `==` zachowuje się jak opisano powyżej dla obu typów referencyjnych wstępnie zdefiniowanych i zdefiniowanych przez użytkownika. Jeśli `==` jest przeciążona, [! =](../../../csharp/language-reference/operators/not-equal-operator.md) musi również być przeciążony. Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
