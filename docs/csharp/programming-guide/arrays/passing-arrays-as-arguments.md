---
title: Przekazywanie tablic jako argumentów — C# Przewodnik programowania
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705694"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Przekazywanie tablic jako argumentów (C# Przewodnik programowania)

Tablice mogą być przekazane jako argumenty do parametrów metody. Ponieważ tablice są typami odwołań, Metoda może zmienić wartość elementów.

## <a name="passing-single-dimensional-arrays-as-arguments"></a>Przekazywanie tablic jednowymiarowych jako argumentów

Można przekazać zainicjowaną tablicę jednowymiarową do metody. Na przykład poniższa instrukcja wysyła tablicę do metody Print.

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

Poniższy kod przedstawia częściową implementację metody Print.

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

Można zainicjować i przekazać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie.

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a>Przykład

W poniższym przykładzie tablica ciągów jest inicjowana i przenoszona jako argument do metody `DisplayArray` dla ciągów. Metoda wyświetla elementy tablicy. Następnie Metoda `ChangeArray` odwraca elementy tablicy, a następnie Metoda `ChangeArrayElements` modyfikuje pierwsze trzy elementy tablicy. Po powrocie każdej metody Metoda `DisplayArray` pokazuje, że przekazywanie tablicy przez wartość nie zapobiega zmianom elementów tablicy.

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a>Przekazywanie tablic wielowymiarowych jako argumentów

Można przekazać zainicjowaną tablicę wielowymiarową do metody w taki sam sposób, w jaki przeszedł tablicę jednowymiarową.

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

Poniższy kod przedstawia częściową deklarację metody Print, która akceptuje tablicę dwuwymiarową jako argument.

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

Można zainicjować i przekazać nową tablicę w jednym kroku, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a>Przykład

W poniższym przykładzie jest inicjowana Dwuwymiarowa tablica liczb całkowitych, która jest przenoszona do metody `Print2DArray`. Metoda wyświetla elementy tablicy.

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](index.md)
- [Tablice jednowymiarowe](single-dimensional-arrays.md)
- [Tablice wielowymiarowe](multidimensional-arrays.md)
- [Tablice nieregularne](jagged-arrays.md)
