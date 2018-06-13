---
title: Przekazywanie parametrów typu wartość (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: b64968a89f010f3f904d3a281d346d2ddf999e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317027"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu wartość (Przewodnik programowania w języku C#)
A [typ wartości](../../../csharp/language-reference/keywords/value-types.md) zmienna zawiera dane bezpośrednio w przeciwieństwie do [Typ referencyjny](../../../csharp/language-reference/keywords/reference-types.md) zmiennej, która zawiera odwołanie do danych. Przekazywanie zmiennej typu wartość do metody przez wartość oznacza, że przekazywanie kopię zmienną do metody. Wszelkie zmiany do parametru, które odbywają się wewnątrz metody ma nie będzie miała wpływu na oryginalne dane przechowywane w zmiennej argumentu. Jeśli chcesz wywołaną metodę, aby zmienić wartości parametru, trzeba przekazać go przez odwołanie, za pomocą [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) — słowo kluczowe. Można także użyć [w](../../../csharp/language-reference/keywords/out-parameter-modifier.md) — słowo kluczowe do przekazania parametrów wartość przez odwołanie, aby uniknąć kopii przy jednoczesnym zagwarantowaniu, że wartość nie zostanie zmieniona. Dla uproszczenia przedstawiono przykłady użycia `ref`.  
  
## <a name="passing-value-types-by-value"></a>Przekazywanie typów wartości przez wartość  
 W poniższym przykładzie pokazano typ wartości przekazywanie parametrów przez wartość. Zmienna `n` jest przekazywany przez wartość do metody `SquareIt`. Wszelkie zmiany, które odbywają się wewnątrz metody ma nie wpływa na oryginalnej wartości zmiennej.  
  
 [!code-csharp[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 Zmienna `n` jest typem wartości. Zawiera dane, wartość `5`. Gdy `SquareIt` zostanie wywołany, zawartość `n` są kopiowane do parametru `x`, który jest kwadrat wewnątrz metody. W `Main`, jednak wartość `n` jest taka sama po wywołaniu `SquareIt` metody, w jakiej została przed. Zmiany, która ma miejsce wewnątrz metody ma wpływ tylko na zmiennej lokalnej `x`.  
  
## <a name="passing-value-types-by-reference"></a>Przekazywanie typów wartości przez odwołanie  
 Poniższy przykład jest taki sam jak poprzedni przykład, z wyjątkiem tego, że argument jest przekazywany jako `ref` parametru. Wartość argumentu podstawowej, `n`, zostanie zmieniona, gdy `x` zostanie zmieniona w metodzie.  
  
 [!code-csharp[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 W tym przykładzie nie jest wartością `n` przekazanego; zamiast odwołania do `n` została przekazana. Parametr `x` nie jest [int](../../../csharp/language-reference/keywords/int.md); jest odwołanie do `int`, w tym przypadku odwołanie do `n`. W związku z tym, kiedy `x` jest kwadrat wewnątrz metody, co faktycznie jest kwadrat jest co `x` odwołuje się do, `n`.  
  
## <a name="swapping-value-types"></a>Trwa zamienianie typy wartości  
 Typowym przykładem zmiany wartości argumentów to metoda wymiany, gdzie przekazać dwie zmienne do metody, a metoda zamienia ich zawartość. Należy podać argumenty metody wymiany przez odwołanie. W przeciwnym razie wymiany lokalne kopie parametry wewnątrz metody i nie zmieniono występuje w przypadku wywołania metody. Poniższy przykład zamienia wartości będące liczbami całkowitymi.  
  
 [!code-csharp[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 Podczas wywoływania `SwapByRef` metody, użyj `ref` — słowo kluczowe w wywołaniu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przekazywanie parametrów](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
