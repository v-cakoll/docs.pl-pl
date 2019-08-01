---
title: Porównanie właściwości i indeksatorów — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 31e6b4b10a6ffec031a2e41a2bd16c843f802fb7
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671678"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
Indeksatory są podobne do właściwości. Z wyjątkiem różnic przedstawionych w poniższej tabeli, wszystkie reguły, które są zdefiniowane dla metod dostępu do właściwości stosuje się również do metod dostępu indeksatora.  
  
|Właściwość|Indeksatora|  
|--------------|-------------|  
|Umożliwia wywoływanie metod w taki sposób, jakby były publicznymi elementami członkowskimi danych.|Zezwala na dostęp do elementów w wewnętrznej kolekcji obiektów przy użyciu notacji tablicy dla samego obiektu.|  
|Dostępne za pomocą prostej nazwy.|Dostępne za za poorednictwem indeksu.|  
|Może być elementem członkowskim typu static lub instance.|Musi być elementem członkowskim wystąpienia.|  
|Metoda dostępu [Get](../../../csharp/language-reference/keywords/get.md) właściwości nie ma parametrów.|`get` Metoda dostępu indeksatora ma taką samą formalną listę parametrów jak indeksator.|  
|Metoda dostępu [Set](../../../csharp/language-reference/keywords/set.md) właściwości zawiera parametr niejawny `value` .|Metoda dostępu indeksatora ma taką samą formalną listę parametrów jak indeksator, a także parametr [Value.](../../../csharp/language-reference/keywords/value.md) `set`|  
|Obsługuje skróconą składnię z [zaimplementowanymi właściwościami](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Obsługuje składowe wyrażeń składowanych tylko dla indeksatorów tylko do pobrania.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
