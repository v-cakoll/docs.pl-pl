---
title: ++ — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: a52f614ce1bbfb8e9d9be686b277c1e69f6f9d35
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47202254"
---
# <a name="-operator-c-reference"></a>++ — Operator (odwołanie w C#)
Operator inkrementacji (`++`) zwiększa wartość argumentu operacji o 1. Operator inkrementacji może występować przed argumentem operacji lub po nim: `++variable` i `variable++`.  
  
## <a name="remarks"></a>Uwagi  
 Pierwsza forma to inkrementacja prefiksowa. Wynikiem tej operacji jest wartość argumentu po zwiększeniu.  
  
 Druga forma to inkrementacja odwrotna. Wynikiem tej operacji jest wartość argumentu przed zwiększeniem.  
  
 Typy numeryczne i wyliczenia mają wstępnie zdefiniowane operatory inkrementacji. W typach definiowanych przez użytkownika można przeciążać operator `++`. Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
