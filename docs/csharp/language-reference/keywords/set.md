---
title: set — słowo kluczowe — odwołanie do języka C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 0b293709abe64a0a82d8575f6793a07ca6c9533b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173500"
---
# <a name="set-c-reference"></a>set (odwołanie w C#)

Słowo `set` kluczowe definiuje metodę *akcesora* we właściwości lub indeksatora, który przypisuje wartość do właściwości lub elementu indeksatora. Aby uzyskać więcej informacji i przykładów, zobacz [Właściwości](../../programming-guide/classes-and-structs/properties.md), [Właściwości autoimplementowane](../../programming-guide/classes-and-structs/auto-implemented-properties.md)i [Indeksatory](../../programming-guide/indexers/index.md).

W poniższym przykładzie `get` zdefiniowano zarówno a, jak `set` i akcesor dla właściwości o nazwie `Seconds`. Używa pola prywatnego `_seconds` o nazwie do tyłu wartości właściwości.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Często `set` akcesor składa się z pojedynczej instrukcji, która przypisuje wartość, jak to miało miejsce w poprzednim przykładzie. Począwszy od języka C# 7.0, można zaimplementować `set` akcesor jako element członkowski zabudowany wyrażeń. Poniższy przykład implementuje `get` zarówno `set` akcesorów jako elementy członkowskie zabudowane wyrażeniem.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
W prostych przypadkach, w `get` których `set` właściwość i akcesory wykonać nie inną operację niż ustawienie lub pobieranie wartości w prywatnym polu zapasowym, można skorzystać z obsługi kompilatora C# dla właściwości auto implementowane. Poniższy przykład implementuje `Hours` jako właściwości auto-implemented.

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Właściwości](../../programming-guide/classes-and-structs/properties.md)
