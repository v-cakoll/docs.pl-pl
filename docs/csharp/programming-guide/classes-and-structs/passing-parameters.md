---
title: Przekazywanie parametrów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: c8da86d2a8f5101acf5b9cc1bcc2f9ad50378fa4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969547"
---
# <a name="passing-parameters-c-programming-guide"></a>Przekazywanie parametrów (Przewodnik programowania w języku C#)
W języku C# argumenty można przekazać do parametrów, przez wartość lub przez odwołanie. Przekazywanie poprzez odwołanie włączenie funkcji elementów członkowskich, metody, właściwości, indeksatory, operatory i konstruktory, aby zmienić wartości parametrów i zmiana pozostają w środowiska wywołującego. Aby przekazać parametr według odwołania z zamiarem zmiany wartości, należy użyć `ref`, lub `out` — słowo kluczowe. Aby Przekaż przez odwołania z celem uniknięcia kopiowania, ale nie zostanie zmieniona wartość, należy użyć `in` modyfikator. Dla uproszczenia tylko `ref` — słowo kluczowe jest używana w przykładach w niniejszym temacie. Aby uzyskać więcej informacji na temat różnic między `in`, `ref`, i `out`, zobacz [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), i [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md).  
  
 Poniższy przykład ilustruje różnicę między parametrami wartości i odwołań.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Przekazywanie parametrów typu wartość](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [listy argumentów](~/_csharplang/spec/expressions.md#argument-lists) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
