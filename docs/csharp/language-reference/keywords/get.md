---
title: get- C# Reference
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: d6c0452a7890a6ade480054115c1383199a3f91c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713493"
---
# <a name="get-c-reference"></a>get (odwołanie w C#)

Słowo kluczowe `get` definiuje metodę *dostępu* do właściwości lub indeksatora, który zwraca wartość właściwości lub element indeksatora. Aby uzyskać więcej informacji, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [zaimplementowane właściwości](../../programming-guide/classes-and-structs/auto-implemented-properties.md) i [indeksatory](../../programming-guide/indexers/index.md).  
  
W poniższym przykładzie zdefiniowano `get` i metodę dostępu `set` dla właściwości o nazwie `Seconds`. Używa prywatnego pola o nazwie `_seconds`, aby wrócić do wartości właściwości.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Często metoda dostępu `get` składa się z pojedynczej instrukcji, która zwraca wartość, tak jak w poprzednim przykładzie. Począwszy od C# 7,0, można zaimplementować metodę dostępu `get` jako element członkowski będący w postaci wyrażeń. W poniższym przykładzie wdrożono zarówno `get`, jak i metodę dostępu `set` jako elementy członkowskie z wyrażeniami.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
W przypadku prostych przypadków, w których `get` `set` i metody dostępu do właściwości nie wykonują żadnej innej operacji niż ustawienie lub pobranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi C# kompilatora dla właściwości, które są implementowane. Poniższy przykład implementuje `Hours` jako właściwość, która jest implementowana. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Właściwości](../../programming-guide/classes-and-structs/properties.md)
