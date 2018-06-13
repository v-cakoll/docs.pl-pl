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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323108"
---
# <a name="passing-parameters-c-programming-guide"></a>Przekazywanie parametrów (Przewodnik programowania w języku C#)
W języku C# argumenty mogą być przekazywane do parametrów według wartości lub według odwołania. Przekazywanie poprzez odwołanie umożliwia członkom funkcji, metody, właściwości, indeksatorów, operatory, a konstruktorów może zmienić wartości parametrów, a zmiana pozostają w środowisku wywołującego. Aby przekazać parametr przez odwołanie z zamiarem zmiany wartości, należy użyć `ref`, lub `out` — słowo kluczowe. Aby przekazać przez odwołanie z zamiarem unikając kopiowania, ale nie zmienia się wartość, użyj `in` modyfikator. Dla uproszczenia tylko `ref` — słowo kluczowe jest używany w przykładach w niniejszym temacie. Aby uzyskać więcej informacji na temat różnic między `in`, `ref`, i `out`, zobacz [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md), i [ Przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Poniższy przykład przedstawia różnicę między odwołanie i wartości parametrów.  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Przekazywanie parametrów typu wartość](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
