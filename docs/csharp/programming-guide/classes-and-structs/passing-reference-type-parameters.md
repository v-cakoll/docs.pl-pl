---
title: Przekazywanie parametrów typu referencyjnego — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 6fa0e60fafabaa9fb04cdc5d5bf3f9e29490e84f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714719"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu odwołanie (Przewodnik programowania w języku C#)
Zmienna [typu odwołania](../../language-reference/keywords/reference-types.md) nie zawiera bezpośrednio swoich danych; zawiera odniesienie do swoich danych. Po przekazaniu parametru typu odwołania przez wartość, jest możliwe, aby zmienić dane należące do obiektu, do którego istnieje odwołanie, takich jak wartość elementu członkowskiego klasy. Nie można jednak zmienić wartości samego odwołania; na przykład nie można użyć tego samego odwołania do przydzielenia pamięci dla nowego obiektu i mieć go utrwalić poza metodą. Aby to zrobić, przekazać parametr przy użyciu [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) słowa kluczowego. Aby uzyskać prostotę, w `ref`poniższych przykładach użyć .  
  
## <a name="passing-reference-types-by-value"></a>Przekazywanie typów odwołań według wartości  
 W poniższym przykładzie przedstawiono przekazywanie parametru typu odwołania, `arr`według `Change`wartości, do metody. Ponieważ parametr jest odwołaniem do `arr`, możliwe jest zmiana wartości elementów tablicy. Jednak próba ponownego przypisania parametru do innej lokalizacji pamięci działa tylko wewnątrz metody `arr`i nie wpływa na oryginalną zmienną.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 W poprzednim przykładzie tablica `arr`, która jest typem odwołania, jest `ref` przekazywana do metody bez parametru. W takim przypadku kopia odniesienia, która wskazuje `arr`na , jest przekazywana do metody. Dane wyjściowe pokazują, że metoda może zmienić zawartość elementu tablicowego, w `1` `888`tym przypadku z na . Jednak przydzielanie nowej części pamięci przy użyciu [nowego](../../language-reference/operators/new-operator.md) `Change` operatora wewnątrz `pArray` metody sprawia, że zmienna odwołuje się do nowej tablicy. W związku z tym wszelkie zmiany po `arr`tym nie wpłynie `Main`na oryginalną tablicę, , który jest tworzony wewnątrz . W rzeczywistości dwie tablice są tworzone w `Main` tym przykładzie, `Change` jedna wewnątrz i jedna wewnątrz metody.  
  
## <a name="passing-reference-types-by-reference"></a>Przekazywanie typów odwołań przez odwołanie  
 Poniższy przykład jest taki sam jak w `ref` poprzednim przykładzie, z tą różnicą, że słowo kluczowe jest dodawane do nagłówka metody i wywołania. Wszelkie zmiany zachodzące w metodzie wpływają na oryginalną zmienną w programie wywołującym.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Wszystkie zmiany zachodzące wewnątrz metody wpływają na `Main`oryginalną tablicę w pliku . W rzeczywistości oryginalna tablica jest `new` ponownie przydzielana przy użyciu operatora. W związku z `Change` tym po `arr` wywołaniu metody, wszelkie odwołania do punktów `Change` do tablicy pięcioelementowej, która jest tworzona w metodzie.  
  
## <a name="swapping-two-strings"></a>Zamiana dwóch ciągów  
 Zamiana ciągów jest dobrym przykładem przekazywania parametrów typu odwołania przez odwołanie. W przykładzie dwa ciągi `str1` `str2`i , są `Main` inicjowane `SwapStrings` i przekazywane do metody `ref` jako parametry zmodyfikowane przez słowo kluczowe. Dwa ciągi są wymieniane wewnątrz metody `Main` i wewnątrz, jak również.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 W tym przykładzie parametry muszą być przekazywane przez odwołanie, aby wpłynąć na zmienne w programie wywołującym. Jeśli usuniesz `ref` słowo kluczowe zarówno z nagłówka metody, jak i wywołania metody, w programie wywołującym nie zostaną wprowadzone żadne zmiany.  
  
 Aby uzyskać więcej informacji na temat ciągów, zobacz [ciąg](../../language-reference/builtin-types/reference-types.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Przekazywanie parametrów](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [Cala](../../language-reference/keywords/in-parameter-modifier.md)
- [na zewnątrz](../../language-reference/keywords/out.md)
- [Typy odwołań](../../language-reference/keywords/reference-types.md)
