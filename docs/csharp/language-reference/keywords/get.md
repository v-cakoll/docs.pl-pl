---
title: get - C# Odwołanie
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 61d8c02aaf13f43ff8ea17c1e868ea9fd52893c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173630"
---
# <a name="get-c-reference"></a>get (odwołanie w C#)

Słowo `get` kluczowe definiuje metodę *akcesora* we właściwości lub indeksatora, który zwraca wartość właściwości lub elementu indeksatora. Aby uzyskać więcej informacji, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [Właściwości autoimplementowane](../../programming-guide/classes-and-structs/auto-implemented-properties.md) i [indeksatory](../../programming-guide/indexers/index.md).  
  
W poniższym przykładzie `get` zdefiniowano zarówno a, jak `set` i akcesor dla właściwości o nazwie `Seconds`. Używa pola prywatnego `_seconds` o nazwie do tyłu wartości właściwości.  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Często `get` akcesor składa się z pojedynczej instrukcji, która zwraca wartość, jak to miało miejsce w poprzednim przykładzie. Począwszy od języka C# 7.0, można zaimplementować `get` akcesor jako element członkowski zabudowany wyrażeń. Poniższy przykład implementuje `get` zarówno `set` akcesor jako elementy członkowskie zabudowane wyrażeniem.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

W prostych przypadkach, w `get` których `set` właściwość i akcesory wykonać nie inną operację niż ustawienie lub pobieranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi kompilatora C# dla właściwości auto implementowane. Poniższy przykład implementuje `Hours` jako właściwości auto-implemented.
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Właściwości](../../programming-guide/classes-and-structs/properties.md)
