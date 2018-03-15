---
title: "Przekazywanie tablic za pomocą ref i out (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f76f63aee0100c6af6bde73c8543b4e7136b1954
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>Przekazywanie tablic za pomocą ref i out (Przewodnik programowania w języku C#)
Takich jak wszystkie [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów `out` parametr typu tablicy musi być przypisany, zanim zostanie on użyty; oznacza to, musi być przypisany przez funkcję wywołującą. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Takich jak wszystkie [ref](../../../csharp/language-reference/keywords/ref.md) parametry, `ref` parametr typu tablicy musi być ostatecznie przypisany przez obiekt wywołujący. Dlatego też nie musi być zdecydowanie przypisywany przez obiekt wywoływany. A `ref` parametr typu tablicy mogą ulec zmianie w wyniku wywołania. Na przykład można przypisać tablicy [null](../../../csharp/language-reference/keywords/null.md) wartość lub mogą być inicjowane do innej tablicy. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 W poniższych dwóch przykładach pokazano różnicę między `out` i `ref` w przekazywanie tablic metod.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tablicy `theArray` jest zadeklarowana w wywołującego ( `Main` — metoda) i została zainicjowana w `FillArray` metody. Następnie elementy tablicy są zwracane do obiektu wywołującego i wyświetlane.  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tablicy `theArray` został zainicjowany w wywołującego ( `Main` — metoda) i przekazywane do `FillArray` metody przy użyciu `ref` parametru. Niektóre elementy tablicy są aktualizowane w `FillArray` metody. Następnie elementy tablicy są zwracane do obiektu wywołującego i wyświetlane.  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [out — modyfikator parametrów](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
