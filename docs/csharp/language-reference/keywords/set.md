---
title: Ustaw słowo kluczowe — odwołanie w C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: cdd84c824cc4dc93f4433f07e9978d22cba3f245
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795069"
---
# <a name="set-c-reference"></a>set (odwołanie w C#)

`set` Słowo kluczowe definiuje metodę *dostępu* we właściwości lub indeksatora, która przypisuje wartość do właściwości lub elementu indeksatora. Aby uzyskać więcej informacji i przykładów, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [zaimplementowane właściwości](../../programming-guide/classes-and-structs/auto-implemented-properties.md), i [indeksatory](../../programming-guide/indexers/index.md).

W poniższym przykładzie zdefiniowano `get` `set` metodę dostępu a i dla właściwości o nazwie `Seconds`. Używa pola prywatnego o nazwie `_seconds` do wstecz wartości właściwości.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Często `set` metoda dostępu składa się z pojedynczej instrukcji, która przypisuje wartość, tak jak w poprzednim przykładzie. Począwszy od języka C# 7,0, można zaimplementować `set` metodę dostępu jako element członkowski będący w postaci wyrażeń. W poniższym przykładzie zaimplementowane są `get` i metody `set` dostępu jako elementy członkowskie, które są członkami wyrażeń.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
W przypadku prostych przypadków, w których właściwości `get` i `set` metody dostępu nie wykonują innej operacji niż ustawienie lub pobranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi kompilatora języka C# dla właściwości, które są implementowane. Poniższy przykład implementuje `Hours` jako właściwość, która jest implementowana.

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Właściwości](../../programming-guide/classes-and-structs/properties.md)
