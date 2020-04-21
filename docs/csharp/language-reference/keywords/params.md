---
title: params — słowo kluczowe dla tablic parametrów — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738842"
---
# <a name="params-c-reference"></a>params (odwołanie w C#)

Za pomocą `params` słowa kluczowego można określić [parametr metody,](method-parameters.md) który przyjmuje zmienną liczbę argumentów. Typ parametru musi być tablicą jednowymiarową.

Żadne dodatkowe parametry są `params` dozwolone po słowie kluczowym `params` w deklaracji metody i tylko jedno słowo kluczowe jest dozwolone w deklaracji metody.

Jeśli zadeklarowany typ `params` parametru nie jest tablicą jednowymiarową, występuje błąd kompilatora [CS0225.](../../misc/cs0225.md)

Po wywołaniu metody `params` z parametrem można przekazać:

- Oddzielona przecinkami lista argumentów typu elementów tablicy.
- Tablica argumentów określonego typu.
- Brak argumentów. Jeśli nie wyślesz żadnych argumentów, długość `params` listy wynosi zero.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono różne sposoby, w jaki argumenty mogą być wysyłane do parametru. `params`

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [Parametry metody](method-parameters.md)
