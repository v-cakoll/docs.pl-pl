---
title: Przekazywanie parametrów typu odwołania — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: f4329c525995b8246427072d1f537d91d875ef95
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596262"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu odwołanie (Przewodnik programowania w języku C#)
Zmienna [typu referencyjnego](../../language-reference/keywords/reference-types.md) nie zawiera danych bezpośrednio; zawiera odwołanie do danych. W przypadku przekazania parametru typu odwołania przez wartość można zmienić dane należące do przywoływanego obiektu, takie jak wartość elementu członkowskiego klasy. Nie można jednak zmienić wartości samego odwołania; na przykład nie można użyć tego samego odwołania, aby przydzielić pamięć dla nowego obiektu i zachować go poza metodą. W tym celu Przekaż parametr za pomocą słowa kluczowego [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) . Dla uproszczenia w poniższych przykładach `ref`użyto.  
  
## <a name="passing-reference-types-by-value"></a>Przekazywanie typów odwołań przez wartość  
 Poniższy przykład demonstruje przekazywanie parametru typu odwołania, `arr`według wartości, do metody,. `Change` Ponieważ parametr jest odwołaniem do `arr`, można zmienić wartości elementów tablicy. Jednak próba ponownego przypisania parametru do innej lokalizacji w pamięci działa tylko wewnątrz metody i nie ma wpływu na oryginalną zmienną `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 W poprzednim przykładzie, tablica, `arr`, będąca typem referencyjnym, jest przenoszona do metody `ref` bez parametru. W takim przypadku kopia odwołania, która wskazuje na `arr`, jest przenoszona do metody. Dane wyjściowe pokazują, że można zmienić zawartość elementu tablicy, w tym przypadku z `1` do. `888` Jednak przydzielanie nowej części pamięci za pomocą operatora [New](../../language-reference/operators/new-operator.md) wewnątrz `Change` metody sprawia, że zmienna `pArray` odwołuje się do nowej tablicy. W ten sposób wszelkie zmiany po tym nie wpłyną na oryginalną tablicę `arr`, która jest tworzona wewnątrz. `Main` W rzeczywistości dwie tablice są tworzone w tym przykładzie, jeden wewnątrz `Main` i jeden `Change` wewnątrz metody.  
  
## <a name="passing-reference-types-by-reference"></a>Przekazywanie typów odwołań przez odwołanie  
 Poniższy przykład jest taki sam jak w poprzednim przykładzie, z tą różnicą `ref` , że słowo kluczowe jest dodawane do nagłówka i wywołania metody. Wszelkie zmiany, które mają miejsce w metodzie, wpływają na oryginalną zmienną w programie wywołującym.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Wszystkie zmiany, które miały miejsce wewnątrz metody, mają wpływ na oryginalną tablicę w `Main`. W rzeczywistości oryginalna tablica jest ponownie alokowana przy użyciu `new` operatora. W ten sposób po wywołaniu `Change` metody, każde odwołanie do `arr` punktu do tablicy pięciu elementów, `Change` która jest tworzona w metodzie.  
  
## <a name="swapping-two-strings"></a>Zamienianie dwóch ciągów  
 Zamienianie ciągów jest dobrym przykładem przekazywania parametrów typu odwołania przez odwołanie. W przykładzie dwa ciągi `str1` i `str2`, są inicjowane `SwapStrings` w `Main` i przechodzą `ref` do metody jako parametry zmodyfikowane przez słowo kluczowe. Dwa ciągi są wymieniane wewnątrz metody i również wewnątrz `Main` .  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 W tym przykładzie parametry muszą zostać przesłane przez odwołanie, aby wpływać na zmienne w programie wywołującym. Usunięcie `ref` słowa kluczowego z zarówno z nagłówka metody, jak i wywołania metody nie spowoduje zmiany w programie wywołującym.  
  
 Aby uzyskać więcej informacji na temat ciągów, zobacz [ciąg](../../language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Przekazywanie parametrów](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [in](../../language-reference/keywords/in-parameter-modifier.md)
- [out](../../language-reference/keywords/out.md)
- [Typy odwołań](../../language-reference/keywords/reference-types.md)
