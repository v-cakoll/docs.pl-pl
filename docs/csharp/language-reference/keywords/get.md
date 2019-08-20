---
title: get- C# Reference
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 783814a575e95fc9deb5c9cdef235a5636f5f529
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602146"
---
# <a name="get-c-reference"></a>get (odwołanie w C#)

Słowo kluczowe definiuje metodę dostępu we właściwości lub indeksatora, która zwraca wartość właściwości lub element indeksatora. `get` Aby uzyskać więcej informacji, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [zaimplementowane właściwości](../../programming-guide/classes-and-structs/auto-implemented-properties.md) i [indeksatory](../../programming-guide/indexers/index.md).  
  
W poniższym przykładzie zdefiniowano `get` `set` metodę dostępu a i dla właściwości o nazwie `Seconds`. Używa pola prywatnego o nazwie `_seconds` do wstecz wartości właściwości.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
`get` Często metoda dostępu składa się z pojedynczej instrukcji, która zwraca wartość, tak jak w poprzednim przykładzie. Począwszy od C# 7,0, można zaimplementować `get` metodę dostępu jako element członkowski w postaci wyrażenia. W poniższym przykładzie zaimplementowane są `get` `set` i Akcesory jako elementy członkowskie z wyrażeniami.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
W przypadku prostych przypadków, w których właściwości `get` i `set` metody dostępu nie wykonują żadnej innej operacji niż ustawienie lub pobranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi C# kompilatora w celu zaimplementowania. aœciwoœci. Poniższy przykład implementuje `Hours` jako właściwość, która jest implementowana. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Właściwości](../../programming-guide/classes-and-structs/properties.md)
