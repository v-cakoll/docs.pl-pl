---
title: Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 3a78b97f2cac1f2c49be03bc351d9b6f4b6438e6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556629"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
Indeksatory są podobne właściwości. Z wyjątkiem różnic pokazano w poniższej tabeli wszystkich reguł, które są zdefiniowane dla metod dostępu do właściwości dotyczą metod dostępu indeksatora również.  
  
|Właściwość|Indeksator|  
|--------------|-------------|  
|Zezwala na metody wywołane, tak jakby były publiczne elementy członkowskie danych.|Umożliwia elementy kolekcji wewnętrznego obiektu można uzyskać dostęp przy użyciu tablicy notacji sam obiekt.|  
|Dostępna za pośrednictwem prostej nazwie.|Dostępna za pośrednictwem indeksu.|  
|Może być statyczna lub elementu członkowskiego wystąpienia.|Musi być składową wystąpienia.|  
|A [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu właściwości nie ma parametrów.|A `get` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora.|  
|A [ustaw](../../../csharp/language-reference/keywords/set.md) metody dostępu właściwości zawiera niejawny `value` parametru.|A `set` akcesor indeksator ma tę samą listę parametrów formalnych jako indeksatora, a także [wartość](../../../csharp/language-reference/keywords/value.md) parametru.|  
|Obsługuje skrócony składni [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Nie obsługuje skróconej składni.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
