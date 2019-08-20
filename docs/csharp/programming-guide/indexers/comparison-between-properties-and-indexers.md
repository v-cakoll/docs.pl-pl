---
title: Porównanie właściwości i indeksatorów — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 4a14c2bf80ff203c5db7fc7663afeb816dc4a2c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589468"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
Indeksatory są podobne do właściwości. Z wyjątkiem różnic przedstawionych w poniższej tabeli, wszystkie reguły, które są zdefiniowane dla metod dostępu do właściwości stosuje się również do metod dostępu indeksatora.  
  
|Właściwość|Indeksatora|  
|--------------|-------------|  
|Umożliwia wywoływanie metod w taki sposób, jakby były publicznymi elementami członkowskimi danych.|Zezwala na dostęp do elementów w wewnętrznej kolekcji obiektów przy użyciu notacji tablicy dla samego obiektu.|  
|Dostępne za pomocą prostej nazwy.|Dostępne za za poorednictwem indeksu.|  
|Może być elementem członkowskim typu static lub instance.|Musi być elementem członkowskim wystąpienia.|  
|Metoda dostępu [Get](../../language-reference/keywords/get.md) właściwości nie ma parametrów.|`get` Metoda dostępu indeksatora ma taką samą formalną listę parametrów jak indeksator.|  
|Metoda dostępu [Set](../../language-reference/keywords/set.md) właściwości zawiera parametr niejawny `value` .|Metoda dostępu indeksatora ma taką samą formalną listę parametrów jak indeksator, a także parametr [Value.](../../language-reference/keywords/value.md) `set`|  
|Obsługuje skróconą składnię [](../classes-and-structs/auto-implemented-properties.md)z zaimplementowanymi właściwościami.|Obsługuje składowe wyrażeń składowanych tylko dla indeksatorów tylko do pobrania.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Indeksatory](./index.md)
- [Właściwości](../classes-and-structs/properties.md)
