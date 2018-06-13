---
title: Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: a8b347be33ea6acbdf8a78a7af45fd3d0c27f8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330375"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
Indeksatory są podobne do właściwości. Z wyjątkiem różnice przedstawiono w poniższej tabeli wszystkie reguły, które są zdefiniowane dla metod dostępu do właściwości dotyczą akcesorów indeksatora również.  
  
|Właściwość|indeksator|  
|--------------|-------------|  
|Umożliwia metody do wywołania, tak jakby były publiczne elementy członkowskie danych.|Umożliwia elementy kolekcji wewnętrznego obiektu można uzyskać dostęp przy użyciu tablicy notacji sam obiekt.|  
|Dostępne za pośrednictwem prostą nazwą.|Dostępne za pośrednictwem indeksu.|  
|Może być statycznymi lub elementu członkowskiego wystąpienia.|Musi być członkiem wystąpienia.|  
|A [uzyskać](../../../csharp/language-reference/keywords/get.md) akcesor właściwości nie ma parametrów.|A `get` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora.|  
|A [ustawić](../../../csharp/language-reference/keywords/set.md) akcesor właściwości zawiera niejawne `value` parametru.|A `set` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora, a także aby [wartość](../../../csharp/language-reference/keywords/value.md) parametru.|  
|Obsługuje skrócony składni [Auto-Implemented właściwości](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Nie obsługuje skróconą składni.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
