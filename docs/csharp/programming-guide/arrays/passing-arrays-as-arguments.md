---
title: Przekazywanie tablic jako argumenty (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: d863cdc33a8a1a844aabbea9ba5876614e6e8dba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Przekazywanie tablic jako argumenty (Przewodnik programowania w języku C#)
Tablice mogą być przekazywane jako argumenty do parametrów metody. Ponieważ tablice typów referencyjnych, metoda można zmienić wartości elementów.  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>Tablice jednowymiarowe przekazywanie jako argumentów  
 Zainicjowanej tablicy jednowymiarowej można przekazać do metody. Na przykład następująca instrukcja wysyła tablicy do metody drukowania.  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 Poniższy kod przedstawia częściowa implementacja metody drukowania.  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 Możesz zainicjować i przekazać nowej tablicy w jednym kroku, jak to pokazano w poniższym przykładzie.  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie zostanie zainicjowana i przekazany jako argument tablicy ciągów `PrintArray` metody dla ciągów. Metoda Wyświetla elementy tablicy. Następnie metody `ChangeArray` i `ChangeArrayElement` są nazywane wykazać, że wysyłania przez wartość argumentu tablicy nie uniemożliwia zmiany do elementów tablicy.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>Przekazywanie jako argumentów tablice wielowymiarowe  
 Zainicjowanej tablicy wielowymiarowej są przekazywane do metody w taki sam sposób, który jest przekazywany jest tablicą jednowymiarową.  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 Poniższy kod przedstawia częściowa deklaracja metody wydruku, która akceptuje jest tablicą dwuwymiarową jako jej argument.  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 Możesz zainicjować i przekazać nowej tablicy w jednym kroku, jak to pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie jest tablicą dwuwymiarową liczb całkowitych zostanie zainicjowana i przekazane do `Print2DArray` metody. Metoda Wyświetla elementy tablicy.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
