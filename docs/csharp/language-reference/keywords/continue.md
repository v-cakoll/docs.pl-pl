---
title: Continue — instrukcja (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 37315caf14ba829dfc91da065bc49982f21b947f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408234"
---
# <a name="continue-c-reference"></a>continue (odwołanie w C#)

`continue` Instrukcji przekazuje kontrolę do kolejnej iteracji otaczającej [podczas](../../../csharp/language-reference/keywords/while.md), [czy](../../../csharp/language-reference/keywords/do.md), [dla](../../../csharp/language-reference/keywords/for.md), lub [foreach](../../../csharp/language-reference/keywords/foreach-in.md) oświadczenie, w której występuje.

## <a name="example"></a>Przykład

W tym przykładzie licznik jest ustawiana na liczba z zakresu od 1 do 10. Za pomocą `continue` instrukcji w połączeniu z wyrażeniem `(i < 9)`, instrukcji między `continue` wraz z upływem `for` są pomijane ciała.

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [break, instrukcja](/cpp/cpp/break-statement-cpp)  
- [Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)