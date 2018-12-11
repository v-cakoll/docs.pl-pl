---
title: / — Operator - C# odwołania
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: c77d9264baac05f2212db37fe50490516359e96e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242324"
---
# <a name="-operator-c-reference"></a>/ — Operator (odwołanie w C#)
Operator dzielenia (`/`) dzieli pierwszy argument operacji za drugim argumentem. Wszystkie typy liczbowe zostały wstępnie zdefiniowane operatory dzielenia.
  
## <a name="remarks"></a>Uwagi  
 W typach definiowanych przez użytkownika można przeciążać operator `/` (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Przeciążenia `/` niejawnie przeciążenia [/ = — operator](division-assignment-operator.md).  
  
 Dzielenia dwóch liczb całkowitych, wynik jest zawsze liczbą całkowitą. Na przykład wynikiem 7 / 3 to 2. Nie należy mylić z dzielenia floored jako `/` operator Zaokrągla wartość w kierunku zera: -7 / 3 -2.  
  
 Aby uzyskać iloraz jako Liczba wymierna, użyj `float`, `double`, lub `decimal` typów. Istnieje wiele sposobów, aby wykonać konwersję między [wbudowane typy liczbowe](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
 Aby sprawdzić resztę, użyj [operator reszty](../../../csharp/language-reference/operators/remainder-operator.md) `%`.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
