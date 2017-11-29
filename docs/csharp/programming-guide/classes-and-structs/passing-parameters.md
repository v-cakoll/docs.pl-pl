---
title: "Przekazywanie parametrów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9e0e06d67f9da39c6b55f91e35d4a75b43353f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="passing-parameters-c-programming-guide"></a>Przekazywanie parametrów (Przewodnik programowania w języku C#)
W języku C# argumenty mogą być przekazywane do parametrów według wartości lub według odwołania. Przekazywanie poprzez odwołanie umożliwia członkom funkcji, metody, właściwości, indeksatorów, operatory, a konstruktorów może zmienić wartości parametrów, a zmiana pozostają w środowisku wywołującego. Aby przekazać parametr przez odwołanie, użyj `ref` lub `out` — słowo kluczowe. Dla uproszczenia tylko `ref` — słowo kluczowe jest używany w przykładach w niniejszym temacie. Aby uzyskać więcej informacji na temat różnic między `ref` i `out`, zobacz [ref](../../../csharp/language-reference/keywords/ref.md), [limit](../../../csharp/language-reference/keywords/out.md), i [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
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
