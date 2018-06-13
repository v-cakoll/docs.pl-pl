---
title: Operator == (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: f8356320817771cb559192c1ce720a80bf33bbf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273390"
---
# <a name="-operator-c-reference"></a>Operator == (odwołanie w C#)
Dla wstępnie zdefiniowanych typów wartości, operator równości (`==`) zwraca wartość true, jeśli wartości argumentów są takie same, `false` inaczej. Dla odwołania do typów innych niż [ciąg](../../../csharp/language-reference/keywords/string.md), `==` zwraca `true` Jeśli swoich argumentów, dwóch odwołują się do tego samego obiektu. Aby uzyskać `string` typu `==` porównuje wartości ciągów.  
  
## <a name="remarks"></a>Uwagi  
 Typy wartości zdefiniowane przez użytkownika można przeciążać `==` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Dlatego można typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `==` zachowuje się jak opisano powyżej dla obu typów odniesienia wstępnie zdefiniowane i zdefiniowane przez użytkownika. Jeśli `==` jest przeciążony [! =](../../../csharp/language-reference/operators/not-equal-operator.md) również musi być przeciążony. Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
