---
title: Przekazywanie parametrów typu wartości — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: 13982254922d72337feeb502d2c84ebb42cf27bb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004559"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu wartość (Przewodnik programowania w języku C#)
Zmienna [typu wartości](../../language-reference/builtin-types/value-types.md) zawiera dane bezpośrednio w przeciwieństwie do zmiennej [typu odwołania](../../language-reference/keywords/reference-types.md) , która zawiera odwołanie do danych. Przekazanie zmiennej typu wartości do metody przez wartość oznacza przekazanie kopii zmiennej do metody. Wszelkie zmiany parametru, który ma miejsce wewnątrz metody, nie mają wpływu na oryginalne dane przechowywane w zmiennej argumentu. Jeśli metoda wywoływana ma zmienić wartość argumentu, należy przekazać ją przez odwołanie przy użyciu słowa kluczowego [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) . Możesz również użyć słowa kluczowego [in](../../language-reference/keywords/in-parameter-modifier.md) , aby przekazać parametr wartości przez odwołanie, aby uniknąć kopiowania, bez zagwarantowania, że wartość nie zostanie zmieniona. Dla uproszczenia w poniższych przykładach użyto `ref` .  
  
## <a name="passing-value-types-by-value"></a>Przekazywanie typów wartości według wartości  
 Poniższy przykład ilustruje przekazywanie parametrów typu wartości według wartości. Zmienna `n` jest przenoszona przez wartość do metody `SquareIt` . Wszelkie zmiany, które mają miejsce wewnątrz metody, nie mają wpływu na oryginalną wartość zmiennej.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Zmienna `n` jest typem wartości. Zawiera ona dane, wartość `5` . Gdy `SquareIt` jest wywoływana, zawartość `n` jest kopiowana do parametru `x` , który jest kwadratowy wewnątrz metody. W `Main` , jednak wartość `n` jest taka sama po wywołaniu `SquareIt` metody tak jak wcześniej. Zmiana, która ma miejsce wewnątrz metody, ma wpływ tylko na zmienną lokalną `x` .  
  
## <a name="passing-value-types-by-reference"></a>Przekazywanie typów wartości według odwołania  
 Poniższy przykład jest taki sam jak w poprzednim przykładzie, z tą różnicą, że argument jest przenoszona jako `ref` parametr. Wartość argumentu podstawowego, `n` , jest zmieniana `x` w przypadku zmiany w metodzie.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 W tym przykładzie nie jest to wartość `n` , która jest przenoszona, a odwołanie do `n` jest przesyłane. Parametr `x` nie jest liczbą całkowitą [int](../../language-reference/builtin-types/integral-numeric-types.md); jest to odwołanie do `int` , w tym przypadku odwołania do `n` . W związku z tym, gdy `x` jest kwadratem wewnątrz metody, to w rzeczywistości jest kwadratowa wartość `x` , do której odwołuje się, `n` .  
  
## <a name="swapping-value-types"></a>Zamienianie typów wartości  
 Typowym przykładem zmiany wartości argumentów jest metoda wymiany, w której przekazywane są dwie zmienne do metody, a metoda zamienia ich zawartość. Należy przekazać argumenty do metody zamiany przez odwołanie. W przeciwnym razie zastąpią lokalne kopie parametrów wewnątrz metody, a metoda wywołująca nie ma żadnych zmian. Poniższy przykład zamienia wartości całkowite.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 Po wywołaniu `SwapByRef` metody należy użyć `ref` słowa kluczowego w wywołaniu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Przekazywanie parametrów](./passing-parameters.md)
- [Przekazywanie parametrów typu odwołanie](./passing-reference-type-parameters.md)
