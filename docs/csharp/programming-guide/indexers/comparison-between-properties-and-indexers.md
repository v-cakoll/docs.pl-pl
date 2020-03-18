---
title: Porównanie właściwości i indeksatorów - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712133"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porównanie właściwości i indeksatorów (Przewodnik programowania w języku C#)
Indeksatory są jak właściwości. Z wyjątkiem różnic przedstawionych w poniższej tabeli, wszystkie reguły, które są zdefiniowane dla akcesorów właściwości stosuje się również do akcesorów indeksatorów.  
  
|Właściwość|Indeksator|  
|--------------|-------------|  
|Umożliwia wywoływanie metod tak, jakby były członkami danych publicznych.|Umożliwia dostęp do elementów wewnętrznej kolekcji obiektu przy użyciu notacji tablicowej na samym obiekcie.|  
|Dostęp za pomocą prostej nazwy.|Dostęp za pośrednictwem indeksu.|  
|Może być statyczny lub element członkowski wystąpienia.|Musi być członkiem wystąpienia.|  
|[A accessor](../../language-reference/keywords/get.md) właściwości nie ma parametrów.|Akcesor `get` indeksatora ma taką samą listę parametrów formalnych jak indeksator.|  
|[Set](../../language-reference/keywords/set.md) akcesor właściwości `value` zawiera parametr niejawny.|Akcesor `set` indeksatora ma taką samą listę parametrów formalnych jak indeksator, a także do parametru [value.](../../language-reference/keywords/value.md)|  
|Obsługuje skróconą składnię za pomocą [właściwości autoimplementowanych](../classes-and-structs/auto-implemented-properties.md).|Obsługuje wyrażenie zabudowane elementy członkowskie dla uzyskać tylko indeksatory.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Indexers](./index.md) (Indeksatory)
- [Właściwości](../classes-and-structs/properties.md)
