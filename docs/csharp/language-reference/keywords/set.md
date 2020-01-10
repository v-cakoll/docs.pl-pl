---
title: Ustaw słowo kluczowe C# -Reference
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 97b0dbf8716edc4cd465eb5ac693efa0ecaa498b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713082"
---
# <a name="set-c-reference"></a>set (odwołanie w C#)

Słowo kluczowe `set` definiuje metodę *dostępu* we właściwości lub indeksatora, która przypisuje wartość do właściwości lub elementu indeksatora. Aby uzyskać więcej informacji i przykładów, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [zaimplementowane właściwości](../../programming-guide/classes-and-structs/auto-implemented-properties.md), i [indeksatory](../../programming-guide/indexers/index.md).

W poniższym przykładzie zdefiniowano `get` i metodę dostępu `set` dla właściwości o nazwie `Seconds`. Używa prywatnego pola o nazwie `_seconds`, aby wrócić do wartości właściwości.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Często metoda dostępu `set` składa się z pojedynczej instrukcji, która przypisuje wartość, tak jak w poprzednim przykładzie. Począwszy od C# 7,0, można zaimplementować metodę dostępu `set` jako element członkowski będący w postaci wyrażeń. W poniższym przykładzie zaimplementowane są zarówno `get`, jak i metody dostępu `set` jako elementy członkowskie z wyrażeniami.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
W przypadku prostych przypadków, w których `get` `set` i metody dostępu do właściwości nie wykonują żadnej innej operacji niż ustawienie lub pobranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi C# kompilatora dla właściwości, które są implementowane. Poniższy przykład implementuje `Hours` jako właściwość, która jest implementowana. 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Właściwości](../../programming-guide/classes-and-structs/properties.md)
