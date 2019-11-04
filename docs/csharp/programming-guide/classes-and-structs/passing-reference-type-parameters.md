---
title: Przekazywanie parametrów typu odwołania — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 6489d31ac1e466fdbf2b47ce1aae7e1139af0960
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419044"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu odwołanie (Przewodnik programowania w języku C#)
Zmienna [typu referencyjnego](../../language-reference/keywords/reference-types.md) nie zawiera danych bezpośrednio; zawiera odwołanie do danych. W przypadku przekazania parametru typu odwołania przez wartość można zmienić dane należące do przywoływanego obiektu, takie jak wartość elementu członkowskiego klasy. Nie można jednak zmienić wartości samego odwołania; na przykład nie można użyć tego samego odwołania, aby przydzielić pamięć dla nowego obiektu i zachować go poza metodą. W tym celu Przekaż parametr za pomocą słowa kluczowego [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) . Dla uproszczenia poniższe przykłady używają `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Przekazywanie typów odwołań przez wartość  
 Poniższy przykład demonstruje przekazywanie parametru typu odwołania, `arr`, według wartości, do metody `Change`. Ponieważ parametr jest odwołaniem do `arr`, istnieje możliwość zmiany wartości elementów tablicy. Jednak próba ponownego przypisania parametru do innej lokalizacji pamięci działa tylko wewnątrz metody i nie ma wpływu na oryginalną zmienną, `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 W poprzednim przykładzie tablica, `arr`, który jest typem referencyjnym, jest przenoszona do metody bez parametru `ref`. W takim przypadku kopia odwołania, która wskazuje na `arr`, jest przenoszona do metody. Dane wyjściowe pokazują, że można zmienić zawartość elementu tablicy, w tym przypadku z `1` `888`. Jednak przydzielanie nowej części pamięci za pomocą operatora [New](../../language-reference/operators/new-operator.md) wewnątrz metody `Change` powoduje, że zmienna `pArray` odwołanie do nowej tablicy. W tym przypadku wszelkie zmiany po tym nie wpłyną na oryginalną tablicę, `arr`, która jest tworzona w `Main`. W rzeczywistości dwie tablice są tworzone w tym przykładzie, jeden wewnątrz `Main` i jeden wewnątrz metody `Change`.  
  
## <a name="passing-reference-types-by-reference"></a>Przekazywanie typów odwołań przez odwołanie  
 Poniższy przykład jest taki sam jak w poprzednim przykładzie, z tą różnicą, że słowo kluczowe `ref` jest dodawane do nagłówka metody i wywołania. Wszelkie zmiany, które mają miejsce w metodzie, wpływają na oryginalną zmienną w programie wywołującym.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Wszystkie zmiany, które miały miejsce wewnątrz metody, mają wpływ na oryginalną tablicę w `Main`. W rzeczywistości oryginalna tablica jest ponownie alokowana przy użyciu operatora `new`. W takim przypadku po wywołaniu metody `Change` wszystkie odwołania do `arr` wskazują na tablicę zawierającą pięć elementów, która jest tworzona w `Change` metodzie.  
  
## <a name="swapping-two-strings"></a>Zamienianie dwóch ciągów  
 Zamienianie ciągów jest dobrym przykładem przekazywania parametrów typu odwołania przez odwołanie. W przykładzie dwa ciągi, `str1` i `str2`są inicjowane w `Main` i przesyłane do metody `SwapStrings` jako parametry zmodyfikowane przez słowo kluczowe `ref`. Dwa ciągi są wymieniane wewnątrz metody i wewnątrz `Main`.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 W tym przykładzie parametry muszą zostać przesłane przez odwołanie, aby wpływać na zmienne w programie wywołującym. Jeśli usuniesz słowo kluczowe `ref` zarówno z nagłówka metody, jak i wywołania metody, nie zostaną wprowadzone żadne zmiany w programie wywołującym.  
  
 Aby uzyskać więcej informacji na temat ciągów, zobacz [ciąg](../../language-reference/builtin-types/reference-types.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Przekazywanie parametrów](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [in](../../language-reference/keywords/in-parameter-modifier.md)
- [out](../../language-reference/keywords/out.md)
- [Typy odwołań](../../language-reference/keywords/reference-types.md)
