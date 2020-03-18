---
title: Przekazywanie parametrów typu wartości — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: 670af18d4b2b356aa33a0a03a29c05f5ba9bf78f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744495"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Przekazywanie parametrów typu wartość (Przewodnik programowania w języku C#)
Zmienna [typu wartości](../../language-reference/builtin-types/value-types.md) zawiera swoje dane bezpośrednio w przeciwieństwie do zmiennej [typu odwołania,](../../language-reference/keywords/reference-types.md) która zawiera odwołanie do jego danych. Przekazywanie zmiennej typu wartości do metody przez wartość oznacza przekazywanie kopii zmiennej do metody. Wszelkie zmiany parametru, które mają miejsce wewnątrz metody nie mają wpływu na oryginalne dane przechowywane w zmiennej argumentu. Jeśli chcesz, aby wywoływana metoda zmieniała wartość argumentu, należy przekazać ją przez odwołanie, używając [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) słowa kluczowego. Można również użyć słowa kluczowego [in,](../../language-reference/keywords/in-parameter-modifier.md) aby przekazać parametr wartości przez odwołanie, aby uniknąć kopii, gwarantując jednocześnie, że wartość nie zostanie zmieniona. Aby uzyskać prostotę, w `ref`poniższych przykładach użyć .  
  
## <a name="passing-value-types-by-value"></a>Przekazywanie typów wartości według wartości  
 W poniższym przykładzie przedstawiono przekazywanie parametrów typu wartości według wartości. Zmienna `n` jest przekazywana przez `SquareIt`wartość do metody . Wszelkie zmiany, które mają miejsce wewnątrz metody nie mają wpływu na oryginalną wartość zmiennej.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Zmienna `n` jest typem wartości. Zawiera swoje dane, `5`wartość . Gdy `SquareIt` jest wywoływana, zawartość `n` są kopiowane `x`do parametru , który jest do kwadratu wewnątrz metody. W `Main`, jednak wartość `n` jest taka sama `SquareIt` po wywołaniu metody, jak to było wcześniej. Zmiana, która ma miejsce wewnątrz metody wpływa `x`tylko na zmienną lokalną .  
  
## <a name="passing-value-types-by-reference"></a>Przekazywanie typów wartości przez odwołanie  
 Poniższy przykład jest taki sam jak w poprzednim przykładzie, `ref` z tą różnicą, że argument jest przekazywany jako parametr. Wartość argumentu źródłowego `n`, jest `x` zmieniana po zmianie w metodzie.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 W tym przykładzie nie jest `n` wartość, która jest przekazywana; przeciwnie, odniesienie `n` do jest przekazywana. Parametr `x` nie jest [int](../../language-reference/builtin-types/integral-numeric-types.md); jest to odniesienie `int`do , w tym `n`przypadku, odniesienia do . Dlatego, `x` gdy jest do kwadratu wewnątrz metody, `x` co faktycznie `n`jest do kwadratu jest to, co odnosi się do .  
  
## <a name="swapping-value-types"></a>Zamiana typów wartości  
 Typowym przykładem zmiany wartości argumentów jest metoda wymiany, w której przekazujesię dwie zmienne do metody, a metoda zamienia ich zawartość. Należy przekazać argumenty do metody wymiany przez odwołanie. W przeciwnym razie można zamienić lokalne kopie parametrów wewnątrz metody i nie nastąpi żadna zmiana w metodzie wywołującej. Poniższy przykład zamienia wartości całkowite.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 Podczas wywoływania `SwapByRef` metody należy `ref` użyć słowa kluczowego w wywołaniu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Przekazywanie parametrów](./passing-parameters.md)
- [Przekazywanie parametrów typu odwołanie](./passing-reference-type-parameters.md)
