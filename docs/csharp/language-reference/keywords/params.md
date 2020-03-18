---
title: słowo kluczowe params - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: f462ccc2421fef3ea111d263ec035a701cf04775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173552"
---
# <a name="params-c-reference"></a>params (odwołanie w C#)

Za pomocą `params` słowa kluczowego, można określić [parametr metody,](method-parameters.md) który przyjmuje zmienną liczbę argumentów.

Można wysłać oddzieloną przecinkami listę argumentów typu określonego w deklaracji parametrów lub tablicę argumentów określonego typu. Można również wysyłać żadnych argumentów. Jeśli nie wyślesz żadnych `params` argumentów, długość listy wynosi zero.

Żadne dodatkowe parametry nie są `params` dozwolone po słowa kluczowego `params` w deklaracji metody i tylko jedno słowo kluczowe jest dozwolone w deklaracji metody.

Zadeklarowany typ `params` parametru musi być tablicą jednowymiarową, jak pokazano w poniższym przykładzie. W przeciwnym razie wystąpi błąd kompilatora [CS0225.](../../misc/cs0225.md)

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono różne sposoby, w `params` których argumenty mogą być wysyłane do parametru.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Parametry metody](method-parameters.md)
