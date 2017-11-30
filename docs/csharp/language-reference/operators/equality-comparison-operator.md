---
title: "Operator == (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
