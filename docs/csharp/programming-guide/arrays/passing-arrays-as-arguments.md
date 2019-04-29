---
title: Przekazywanie tablic jako argumentów - C# Programming Guide
ms.custom: seodec18
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 1538988c1145a19055074b440f04cbaac4ef7aa7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651990"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Przekazywanie tablic jako argumenty (C# Programming Guide)

Tablice mogą być przekazywane jako argumenty do parametrów metody. Ponieważ tablice są typami odwołań, metody można zmienić wartości elementów.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Tablice jednowymiarowe przekazywanie jako argumentów

Można przekazać zainicjowanej tablicy jednowymiarowej, do metody. Na przykład następująca instrukcja wysyła tablicę do drukowania metody.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Poniższy kod przedstawia częściową implementację metody drukowania.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Możesz zainicjować i przekazywać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Przykład

W poniższym przykładzie tablica ciągów zostanie zainicjowana i przekazywany jako argument do `DisplayArray` metody dla ciągów. Metoda Wyświetla elementy tablicy. Następnie `ChangeArray` metoda odwraca elementów tablicy, a następnie `ChangeArrayElements` metoda modyfikuje pierwsze trzy elementy tablicy. Po powrocie każdą metodę, `DisplayArray` metoda ma pokazać, że przekazywanie tablicę według wartości nie uniemożliwiają zmiany do elementów tablicy.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Przekazywanie tablic wielowymiarowych jako argumentów

Zainicjowanej tablicy wielowymiarowej są przekazywane do metody w taki sam sposób, jak przekazać tablicę jednowymiarową.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Poniższy kod przedstawia częściowa deklaracja metody drukowania, która akceptuje dwuwymiarową tablicę jako argumentem.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Możesz zainicjować i przekazywać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Przykład

W poniższym przykładzie zostanie zainicjowana i przekazywane do tablicę dwuwymiarową liczb całkowitych `Print2DArray` metody. Metoda Wyświetla elementy tablicy.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](index.md)
- [Tablice jednowymiarowe](single-dimensional-arrays.md)
- [Tablice wielowymiarowe](multidimensional-arrays.md)
- [Tablice nieregularne](jagged-arrays.md)
