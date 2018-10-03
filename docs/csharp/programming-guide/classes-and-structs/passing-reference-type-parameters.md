---
title: Przekazywanie parametrów typu odwołanie (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: d577754e8cb686c40172abd6c0bbd00bc481f737
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027182"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu odwołanie (Przewodnik programowania w języku C#)
Zmienna [odwołania do typu](../../../csharp/language-reference/keywords/reference-types.md) nie zawierają swoje dane bezpośrednio; zawiera on odwołanie do swoich danych. Należy podać parametr typu odwołania przez wartość, jest możliwość zmiany danych należących do przywoływanego obiektu, na przykład wartość składowej klasy. Jednak nie możesz zmienić wartości odwołania. na przykład nie można użyć tego samego odwołania można przydzielić pamięci dla nowej klasy i jego utrwalenia poza metodą. Aby to zrobić, należy przekazać przy użyciu parametru [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) — słowo kluczowe. Dla uproszczenia w poniższych przykładach używane `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Przekazywanie typów referencyjnych przez wartość  
 W poniższym przykładzie pokazano przekazywanie parametrów typu odwołanie `arr`, przez wartość do metody, `Change`. Ponieważ parametr jest odwołaniem do `arr`, można zmienić wartości elementów tablicy. Jednak próba ponownego przypisania parametru do innej lokalizacji w pamięci tylko działa wewnątrz metody i nie ma wpływu na oryginalny zmiennej `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 W poprzednim przykładzie, tablica, `arr`, który jest typem odwołania, jest przekazywany do metody bez `ref` parametru. W takim przypadku kopia odwołania, który wskazuje `arr`, jest przekazywany do metody. Dane wyjściowe pokazują, że jest możliwe dla metody zmienić zawartość elementu tablicy, w tym przypadku z `1` do `888`. Jednak alokowanie nowej części pamięci za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operator wewnątrz `Change` metody sprawia, że zmienna `pArray` odwoływać się do nowej tablicy. W efekcie wszelkie zmiany od, nie wpływa na tablicy oryginalnej `arr`, który jest tworzony w `Main`. W rzeczywistości dwie tablice są tworzone w tym przykładzie jeden wewnątrz `Main` i znajdującą się wewnątrz jednego `Change` metody.  
  
## <a name="passing-reference-types-by-reference"></a>Przekazywanie typów referencyjnych przez odwołanie  
 Poniższy przykład jest taki sam, jak w poprzednim przykładzie, chyba że `ref` — słowo kluczowe jest dodawany do nagłówka metody i wywołania. Wszelkie zmiany, które odbywają się w metodzie wpływają na oryginalny zmiennej w program wywołujący.  
  
 [!code-csharp[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Wszystkie zmiany, które odbywają się wewnątrz metody wpływają na oryginalny tablicy `Main`. W rzeczywistości, oryginalnym tablicy są ponownie przydzielane przy użyciu `new` operatora. W związku z tym, po wywołaniu `Change` metody wszelkie odwołanie do `arr` wskazuje na 5 elementowej tablicy, w którym utworzono `Change` metody.  
  
## <a name="swapping-two-strings"></a>Trwa zamienianie dwa ciągi  
 Trwa zamienianie ciągów jest dobrym przykładem przekazywanie parametrów typu odwołanie przez odwołanie. W tym przykładzie dwa ciągi `str1` i `str2`, są inicjowane w `Main` i przekazywane do `SwapStrings` metodę jako parametry zmodyfikowane przez `ref` — słowo kluczowe. Dwa ciągi są zamienione wewnątrz metody i znajdującą się wewnątrz `Main` także.  
  
 [!code-csharp[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 W tym przykładzie parametry muszą być przekazywane przez odwołanie, wpływ na zmienne w program wywołujący. Jeśli usuniesz `ref` — słowo kluczowe z nagłówka metody i wywołania metody, żadne zmiany nie będą miały miejsce w program wywołujący.  
  
 Aby uzyskać więcej informacji na temat ciągów, zobacz [ciąg](../../../csharp/language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Przekazywanie parametrów](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
- [ref](../../../csharp/language-reference/keywords/ref.md)  
- [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
- [out](../../../csharp/language-reference/keywords/out.md)  
- [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)
