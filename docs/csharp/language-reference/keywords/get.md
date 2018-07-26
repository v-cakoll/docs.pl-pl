---
title: get (odwołanie w C#)
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 671cadce0bd120ec0728562ec448b2ce6edf2dd7
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961355"
---
# <a name="get-c-reference"></a>get (odwołanie w C#)

`get` — Słowo kluczowe definiuje *akcesor* metoda we właściwości lub indeksatora, który zwraca wartość właściwości lub elementu indeksatora. Aby uzyskać więcej informacji, zobacz [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) i [indeksatory](../../../csharp/programming-guide/indexers/index.md).  
  
W poniższym przykładzie zdefiniowano zarówno `get` i `set` akcesora dla właściwości o nazwie `Seconds`. Używa prywatnego pola o nazwie `_seconds` kopii wartości właściwości.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Często `get` dostępu składa się z pojedynczej instrukcji, która nie zwraca wartości, tak jak w poprzednim przykładzie. Począwszy od języka C# 7.0, można zaimplementować `get` dostępu jako element członkowski wyrażeniem. Poniższy przykład implementuje interfejsy `get` i `set` dostępu jako elementy członkowskie z wyrażeniem.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Dla prostych sytuacjach, w których właściwość `get` i `set` Akcesory wykonać żadna inna operacja niż ustawienie lub odczytywania wartości pola prywatnego zapasowy, możesz korzystać z zalet Obsługa właściwości zaimplementowane automatycznie w kompilatorze języka C#. Poniższy przykład implementuje `Hours` jako automatycznie implementowanej właściwości. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md) [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
