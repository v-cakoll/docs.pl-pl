---
title: "!= — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b69d0b12734e690f0ba0209ccbbc7627ff92fe8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>!= — Operator (odwołanie w C#)
Operator nierówności (`!=`) zwraca wartość false, jeśli swoich argumentów, są takie same, wartości true w przeciwnym razie wartość. Operatory nierówności są wstępnie zdefiniowane dla wszystkich typów, w tym ciągu lub obiektu. Typy definiowane przez użytkownika można przeciążać `!=` operatora.  
  
## <a name="remarks"></a>Uwagi  
 Dla wstępnie zdefiniowanych typów wartości, operator nierówności (`!=`) zwraca wartość true, jeśli wartości argumentów są różne, wartość false w przeciwnym razie wartość. Dla odwołania do typów innych niż `string`, `!=` zwraca wartość true, jeśli jego dwóch argumentów operacji odwołują się do różnych obiektów. Aby uzyskać `string` typu `!=` porównuje wartości ciągów.  
  
 Typy wartości zdefiniowane przez użytkownika można przeciążać `!=` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Dlatego można typy odwołań zdefiniowanych przez użytkownika, mimo że domyślnie `!=` zachowuje się jak opisano powyżej dla obu typów odniesienia wstępnie zdefiniowane i zdefiniowane przez użytkownika. Jeśli `!=` jest przeciążony [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) również musi być przeciążony. Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
