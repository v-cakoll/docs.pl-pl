---
title: Przekazywanie parametrów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: a1ccfff8081d101eee46360009653b0591dfb3ff
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404129"
---
# <a name="passing-parameters-c-programming-guide"></a>Przekazywanie parametrów (Przewodnik programowania w języku C#)
W języku C# argumenty można przekazać do parametrów, przez wartość lub przez odwołanie. Przekazywanie poprzez odwołanie włączenie funkcji elementów członkowskich, metody, właściwości, indeksatory, operatory i konstruktory, aby zmienić wartości parametrów i zmiana pozostają w środowiska wywołującego. Aby przekazać parametr według odwołania z zamiarem zmiany wartości, należy użyć `ref`, lub `out` — słowo kluczowe. Aby Przekaż przez odwołania z celem uniknięcia kopiowania, ale nie zostanie zmieniona wartość, należy użyć `in` modyfikator. Dla uproszczenia tylko `ref` — słowo kluczowe jest używana w przykładach w niniejszym temacie. Aby uzyskać więcej informacji na temat różnic między `in`, `ref`, i `out`, zobacz [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md), i [ Przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Poniższy przykład ilustruje różnicę między parametrami wartości i odwołań.  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Przekazywanie parametrów typu wartość](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
