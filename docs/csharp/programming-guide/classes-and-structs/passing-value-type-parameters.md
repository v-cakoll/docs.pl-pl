---
title: Przekazywanie parametrów typu wartości - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: 0c9d8c33715b4baf11bfac05cd4881d1475f8844
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57847001"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu wartość (Przewodnik programowania w języku C#)
A [typ wartości](../../../csharp/language-reference/keywords/value-types.md) zmienna zawiera swoje dane bezpośrednio w przeciwieństwie do [Typ referencyjny](../../../csharp/language-reference/keywords/reference-types.md) zmienną, która zawiera odwołanie do jego danych. Przekazywanie zmiennej typu wartości do metody poprzez wartość oznacza, że przekazywanie kopię zmiennej do metody. Wszelkie zmiany do parametru, które odbywają się wewnątrz metody mają nie będzie miała wpływu na oryginalne dane przechowywane w zmiennej argumentu. Jeśli ma metodę o nazwie, aby zmienić wartość argumentu, należy przekazać jej przez odwołanie, za pomocą [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) — słowo kluczowe. Można także użyć [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) — słowo kluczowe do przekazywania parametru wartości przez odwołanie, aby uniknąć kopii przy jednoczesnym zagwarantowaniu, że wartości nie zostaną zmienione. Dla uproszczenia w poniższych przykładach używane `ref`.  
  
## <a name="passing-value-types-by-value"></a>Przekazywanie typów wartości przez wartość  
 Poniższy przykład demonstruje typ wartości przekazywanie parametrów wg wartości. Zmienna `n` jest przekazywany przez wartość do metody `SquareIt`. Wszelkie zmiany, które odbywają się wewnątrz metody mają nie będzie stosowana w oryginalnej wartości zmiennej.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Zmienna `n` jest typem wartości. Zawiera on własnych danych, a wartość `5`. Gdy `SquareIt` zostanie wywołana, zawartość `n` są kopiowane do parametru `x`, który jest kwadrat wewnątrz metody. W `Main`, ale wartość `n` jest taka sama po wywołaniu `SquareIt` metody był wcześniej. Zmiany, które odbywa się wewnątrz metody ma wpływ tylko na zmiennej lokalnej `x`.  
  
## <a name="passing-value-types-by-reference"></a>Przekazywanie typów wartości przez odwołanie  
 Poniższy przykład jest taki sam, jak w poprzednim przykładzie, z tą różnicą, że argument jest przekazywany jako `ref` parametru. Wartość argumentu bazowego, `n`, to zmienić, gdy `x` zostanie zmieniony w metodzie.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 W tym przykładzie nie jest wartością `n` przekazana; zamiast odwołania do `n` jest przekazywany. Parametr `x` nie [int](../../../csharp/language-reference/keywords/int.md); jest odwołaniem do `int`, w tym przypadku odwołania do `n`. W związku z tym, kiedy `x` jest kwadrat wewnątrz metody, co faktycznie jest kwadrat to `x` odwołuje się do, `n`.  
  
## <a name="swapping-value-types"></a>Trwa zamienianie typów wartości  
 Typowym przykładem, zmieniając wartości argumentów jest metodą wymiany, gdzie możesz przekazać do metody dwie zmienne, a metoda zamienia ich zawartość. Należy przekazać argumenty do metody wymiany przez odwołanie. W przeciwnym razie wymiany lokalne kopie parametry wewnątrz metody, a nie zmienią się w przypadku wywołania metody. Poniższy przykład zamienia wartości całkowitych.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 Gdy wywołujesz `SwapByRef` metody, użyj `ref` — słowo kluczowe w wywołaniu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Przekazywanie parametrów](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
- [Przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
