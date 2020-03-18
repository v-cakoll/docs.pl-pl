---
title: instrukcja continue - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713660"
---
# <a name="continue-c-reference"></a>continue (odwołanie w C#)

Instrukcja `continue` przechodzi kontrolę do następnej iteracji otaczającego [podczas](./while.md), [zrobić](./do.md), [dla](./for.md), lub [foreach](./foreach-in.md) instrukcji, w którym się pojawia.

## <a name="example"></a>Przykład

W tym przykładzie licznik jest inicjowany do zliczania od 1 do 10. Za pomocą `continue` instrukcji w połączeniu z `(i < 9)` `continue` wyrażeniem , `for` instrukcje między i na końcu treści są pomijane.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [break, instrukcja](/cpp/cpp/break-statement-cpp)
