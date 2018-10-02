---
title: params — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 089e31f3aad12c2303619e2a1998d0d6a5a0ad86
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028373"
---
# <a name="params-c-reference"></a>params (odwołanie w C#)

Za pomocą `params` — słowo kluczowe, można określić [parametru metody](method-parameters.md) która przyjmuje zmienną liczbę argumentów.

Możesz wysłać rozdzielana przecinkami lista argumentów o typie określonym w deklaracji parametrów lub tablice argumentów określonego typu. Możesz również wysłać bez argumentów. Jeśli wyślesz żadnych argumentów, długość `params` listy wynosi zero.

Żadne dodatkowe parametry są dozwolone po `params` — słowo kluczowe w deklaracji metody i tylko jeden `params` słowo kluczowe jest dozwolone w deklaracji metody.

Deklarowany typ `params` parametr musi być tablicy jednowymiarowej, co ilustruje poniższy przykład. W przeciwnym razie błąd kompilatora [CS0225](../../misc/cs0225.md) występuje.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano różne sposoby, w których argumenty mogą być wysyłane do `params` parametru.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Parametry metody](method-parameters.md)