---
title: Przekazywanie tablic jako argumentów — przewodnik programowania C#
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705694"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Przekazywanie tablic jako argumentów (Przewodnik programowania C#)

Tablice mogą być przekazywane jako argumenty do parametrów metody. Ponieważ tablice są typami odwołań, metoda może zmienić wartość elementów.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Przekazywanie tablic jednowymiarowych jako argumentów

Można przekazać inicjalizacją tablicę jednowymiarową do metody. Na przykład następująca instrukcja wysyła tablicę do metody drukowania.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Poniższy kod przedstawia częściową implementację metody drukowania.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Można zainicjować i przekazać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Przykład

W poniższym przykładzie tablica ciągów jest inicjowana i `DisplayArray` przekazywana jako argument do metody ciągów. Metoda wyświetla elementy tablicy. Następnie `ChangeArray` metoda odwraca elementy tablicy, a `ChangeArrayElements` następnie metoda modyfikuje pierwsze trzy elementy tablicy. Po każdej metody `DisplayArray` zwraca, metoda pokazuje, że przekazywanie tablicy przez wartość nie uniemożliwia zmiany elementów tablicy.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Przekazywanie tablic wielowymiarowych jako argumentów

Inicjalna tablica wielowymiarowa jest przekazana do metody w taki sam sposób, w jaki przekazujesię tablicę jednowymiarową.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Poniższy kod przedstawia częściową deklarację metody drukowania, która akceptuje tablicy dwuwymiarowej jako jego argument.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Można zainicjować i przekazać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Przykład

W poniższym przykładzie dwuwymiarowa tablica liczb całkowitych jest inicjowana i przekazywana `Print2DArray` do metody. Metoda wyświetla elementy tablicy.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Tablice](index.md)
- [Tablice jednowymiarowe](single-dimensional-arrays.md)
- [Tablice wielowymiarowe](multidimensional-arrays.md)
- [Tablice nieregularne](jagged-arrays.md)
