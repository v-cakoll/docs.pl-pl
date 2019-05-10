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
ms.openlocfilehash: 77228def3a6426b6e0383d657c2eaeac37e5e273
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600135"
---
# <a name="passing-parameters-c-programming-guide"></a>Przekazywanie parametrów (Przewodnik programowania w języku C#)
W języku C# argumenty można przekazać do parametrów, przez wartość lub przez odwołanie. Przekazywanie poprzez odwołanie włączenie funkcji elementów członkowskich, metody, właściwości, indeksatory, operatory i konstruktory, aby zmienić wartości parametrów i zmiana pozostają w środowiska wywołującego. Aby przekazać parametr według odwołania z zamiarem zmiany wartości, należy użyć `ref`, lub `out` — słowo kluczowe. Aby Przekaż przez odwołania z celem uniknięcia kopiowania, ale nie zostanie zmieniona wartość, należy użyć `in` modyfikator. Dla uproszczenia tylko `ref` — słowo kluczowe jest używana w przykładach w niniejszym temacie. Aby uzyskać więcej informacji na temat różnic między `in`, `ref`, i `out`, zobacz [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), i [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md).  
  
 Poniższy przykład ilustruje różnicę między parametrami wartości i odwołań.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Więcej informacji znajduje się w następujących tematach:  
  
- [Przekazywanie parametrów typu wartość](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
- [Przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [listy argumentów](~/_csharplang/spec/expressions.md#argument-lists) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
