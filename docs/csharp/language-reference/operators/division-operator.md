---
title: "/ — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>/ — Operator (odwołanie w C#)
Operator dzielenia (`/`) dzieli jego pierwszym argumentem przez jego drugi argument operacji. Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory dzielenia.  
  
## <a name="remarks"></a>Uwagi  
 Typy definiowane przez użytkownika można przeciążać `/` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Przeciążenie `/` operator niejawnie overloads [/ = — operator](division-assignment-operator.md).  
  
 Służy do dzielenia dwie liczb całkowitych, wynik jest zawsze liczbą całkowitą. Na przykład wynik 7 / 3 to 2. Aby określić w pozostałej części 7 / 3, użycie operator reszty ([%](../../../csharp/language-reference/operators/modulus-operator.md)). Aby uzyskać iloraz jako Liczba wymierna lub ułamek, nadaj dzielna lub dzielnik typu `float` lub typ `double`. Typ można przypisać niejawnie Jeśli express dzielna lub dzielnik jako wartości dziesiętnej poprzez umieszczenie cyfrę z prawej strony punktu dziesiętnego, jak przedstawiono na poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
