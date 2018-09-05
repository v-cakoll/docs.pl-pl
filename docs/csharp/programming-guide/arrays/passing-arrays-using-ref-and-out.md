---
title: Przekazywanie tablic za pomocą ref i out (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: 8da3bf9f8eede72a7bc3cf8380eab66ca2b56e86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526768"
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>Przekazywanie tablic za pomocą ref i out (Przewodnik programowania w języku C#)

Podobnie jak wszystkie [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów, `out` parametr typu tablicowego musi być przypisany, zanim zostaną one użyte; oznacza to, musi zostać przypisany przez obiekt wywoływany. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 Podobnie jak wszystkie [ref](../../../csharp/language-reference/keywords/ref.md) parametrów, `ref` parametr typu tablicowego musi zostać zdecydowanie przypisany przez obiekt wywołujący. Dlatego też nie musi być zdecydowanie przypisywany przez obiekt wywoływany. A `ref` parametr typu tablicowego może zostać zmieniony w wyniku wywołania. Na przykład tablicy może zostać przypisana [null](../../../csharp/language-reference/keywords/null.md) wartość albo może zostać zainicjowana do innej tablicy. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 Dwa poniższe przykłady pokazują różnicę między `out` i `ref` , gdy używane do przekazywania tablic do metod.  
  
## <a name="example"></a>Przykład

 W tym przykładzie tablica `theArray` jest zadeklarowany w obiekcie wywołującym ( `Main` metoda) i inicjowana w `FillArray` metody. Następnie elementy tablicy są zwracane do obiektu wywołującego i wyświetlane.  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]

## <a name="example"></a>Przykład

 W tym przykładzie tablica `theArray` jest inicjowany w obiekcie wywołującym ( `Main` metoda) i przekazywane do `FillArray` metody, używając `ref` parametru. Niektóre elementy tablicy są aktualizowane w `FillArray` metody. Następnie elementy tablicy są zwracane do obiektu wywołującego i wyświetlane.  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [ref](../../../csharp/language-reference/keywords/ref.md)  
- [out — modyfikator parametrów](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Tablice](../../../csharp/programming-guide/arrays/index.md)  
- [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
