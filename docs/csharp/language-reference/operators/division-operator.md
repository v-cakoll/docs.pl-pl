---
title: / — Operator (odwołanie w C#)
ms.date: 04/04/2018
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
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b17d122e3e3f75012e084903b6f8975fb53d46c
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a>/ — Operator (odwołanie w C#)
Operator dzielenia (`/`) dzieli jego pierwszym argumentem przez jego drugi argument operacji. Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory dzielenia.
  
## <a name="remarks"></a>Uwagi  
 Typy definiowane przez użytkownika można przeciążać `/` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Przeciążenie `/` operator niejawnie overloads [/ = — operator](division-assignment-operator.md).  
  
 Służy do dzielenia dwie liczb całkowitych, wynik jest zawsze liczbą całkowitą. Na przykład wynik 7 / 3 to 2. Pozwala to nie należy mylić z dzielenia floored jako `/` operator Zaokrągla wartość w kierunku zera: -7 / 3 -2.  
  
 Aby uzyskać iloraz jako Liczba wymierna, użyj `float`, `double`, lub `decimal` typów. Istnieje wiele sposobów, aby dokonać konwersji między [wbudowane typy liczbowe](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
 Aby określić pozostałą, użyj [operator reszty](../../../csharp/language-reference/operators/remainder-operator.md) `%`.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
