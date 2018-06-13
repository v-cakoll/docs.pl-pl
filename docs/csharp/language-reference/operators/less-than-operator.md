---
title: '&lt; Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: eceb6214e4e625aa71e12788d5dd5e8324c75443
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270234"
---
# <a name="lt-operator-c-reference"></a>&lt; Operator (odwołanie w C#)
Wszystkie typy liczbowe oraz wyliczenie zdefiniować operator relacyjny "mniejsze niż" (`<`) zwracająca `true` Jeśli pierwszy argument operacji jest mniejsza od drugiej, `false` inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Typy definiowane przez użytkownika można przeciążać `<` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Jeśli `<` jest przeciążony [ > ](../../../csharp/language-reference/operators/greater-than-operator.md) również musi być przeciążony. Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
