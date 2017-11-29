---
title: "&lt;Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76d53d4c943c886f6b8c8a68e2b8bb12bc9a9d6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a>&lt;Operator (odwołanie w C#)
Wszystkie typy liczbowe oraz wyliczenie zdefiniować operator relacyjny "mniejsze niż" (`<`) zwracająca `true` Jeśli pierwszy argument operacji jest mniejsza od drugiej, `false` inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Typy definiowane przez użytkownika można przeciążać `<` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Jeśli `<` jest przeciążony [ > ](../../../csharp/language-reference/operators/greater-than-operator.md) również musi być przeciążony. Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
