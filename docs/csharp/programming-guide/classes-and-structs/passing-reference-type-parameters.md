---
title: "Przekazywanie parametrów typu odwołanie (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2cd862a9179e027ab82631631784203993d0465a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu odwołanie (Przewodnik programowania w języku C#)
Zmienna [zawierają odwołania do typu](../../../csharp/language-reference/keywords/reference-types.md) nie zawierają swoje dane bezpośrednio; zawiera odwołanie do danych. Jeśli przez wartość parametru typu odwołania, jest możliwość zmiany danych wskazywanego przez odwołanie, np. wartość elementu członkowskiego klasy. Jednak nie można zmienić wartości odwołania. oznacza to, że nie można użyć tego samego odwołania może przydzielić pamięci dla nowej klasy, a jego utrwalenia poza blokiem. Aby to zrobić, przekazać przy użyciu parametru [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out.md) — słowo kluczowe. Dla uproszczenia przedstawiono przykłady użycia `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Typy odwołań przekazywanie przez wartość  
 W poniższym przykładzie pokazano, przekazywanie parametrów typu odwołanie, `arr`, przez wartość do metody, `Change`. Ponieważ wartość parametru jest odwołanie do `arr`, można zmienić wartości elementów tablicy. Jednak próba ponownego przypisania parametrów do innej lokalizacji w pamięci tylko działa wewnątrz metody i nie dotyczy pierwotnej zmiennej `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 W powyższym przykładzie tablicy `arr`, który jest typem referencyjnym, jest przekazywany do metody bez `ref` parametru. W takim przypadku kopia odwołania, który wskazuje `arr`, jest przekazywany do metody. Dane wyjściowe wskazuje, że jest możliwe w dla metody zmienić zawartość elementu tablicy, w tym przypadku z `1` do `888`. Jednak alokowanie nowej części pamięci przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) operator wewnątrz `Change` metody sprawia, że zmienna `pArray` odwołania nowej tablicy. W związku z tym wszelkie zmiany, po którym nie wpłynie na tablicy oryginalnej `arr`, które jest tworzone wewnątrz `Main`. W rzeczywistości dwie tablice są tworzone w tym przykładzie jedną wewnątrz `Main` i wewnątrz jednej `Change` metody.  
  
## <a name="passing-reference-types-by-reference"></a>Typy odwołań przekazywanie przez odwołanie  
 Poniższy przykład jest taki sam jak poprzedni przykład, z wyjątkiem `ref` — słowo kluczowe zostanie dodany do nagłówka metody i wywołania. Wszelkie zmiany, które mają miejsce w metodzie wpływa na oryginalnej zmiennej w program wywołujący.  
  
 [!code-csharp[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Wszystkie zmiany, które odbywają się wewnątrz metody mają wpływ na oryginalnym tablicy w `Main`. W rzeczywistości tablicy oryginalnej alokowaniu przy użyciu `new` operatora. W związku z tym po wywołaniu `Change` metody odniesień do `arr` punktów do tablicy pięciu element, który jest tworzony w `Change` metody.  
  
## <a name="swapping-two-strings"></a>Trwa zamienianie dwa ciągi  
 Wymiana ciągów jest dobrym przykładem przekazywanie parametrów typu odwołanie poprzez odwołanie. W tym przykładzie dwa ciągi `str1` i `str2`, są inicjowane w `Main` i przekazywane do `SwapStrings` metody jako parametry zmodyfikowane przez `ref` — słowo kluczowe. Dwa ciągi są zamienione wewnątrz metody wewnątrz `Main` również.  
  
 [!code-csharp[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 W tym przykładzie parametry muszą być przekazywane przez odwołanie wpływa na zmienne program wywołujący. Jeśli usuniesz `ref` — słowo kluczowe z nagłówka metody i wywołania metody, żadne zmiany nie będą miały miejsce w program wywołujący.  
  
 Aby uzyskać więcej informacji na temat ciągów, zobacz [ciąg](../../../csharp/language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przekazywanie parametrów](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
 [REF](../../../csharp/language-reference/keywords/ref.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)
