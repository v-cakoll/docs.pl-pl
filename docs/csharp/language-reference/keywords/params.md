---
title: params — słowo C# kluczowe-Reference
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 90d224080f607cbac96514aaf5ac6d67affef9e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713238"
---
# <a name="params-c-reference"></a>params (odwołanie w C#)

Za pomocą słowa kluczowego `params` można określić [parametr metody](method-parameters.md) , który przyjmuje zmienną liczbę argumentów.

Można wysłać rozdzieloną przecinkami listę argumentów typu określonego w deklaracji parametru lub tablicy argumentów określonego typu. Nie można również wysyłać żadnych argumentów. Jeśli nie wyślesz żadnych argumentów, długość listy `params` wynosi zero.

Żadne dodatkowe parametry nie są dozwolone po słowie kluczowym `params` w deklaracji metody, a w deklaracji metody dozwolony jest tylko jeden `params` słowo kluczowe.

Zadeklarowany typ parametru `params` musi być tablicą jednowymiarową, jak pokazano w poniższym przykładzie. W przeciwnym razie wystąpi błąd kompilatora [CS0225](../../misc/cs0225.md) .

## <a name="example"></a>Przykład

Poniższy przykład ilustruje różne sposoby, w których argumenty mogą być wysyłane do parametru `params`.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Parametry metody](method-parameters.md)
