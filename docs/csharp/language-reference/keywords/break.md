---
title: BREAK — instrukcja (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 987ee1ca5601b3dd105412bf0fa18361c57a95fd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315241"
---
# <a name="break-c-reference"></a>break (odwołanie w C#)

`break` Instrukcji kończy najbliższej otaczającej pętli lub [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcji, w której znajduje się. Kontrola jest przekazywana do instrukcji następującej instrukcji zakończone, jeśli istnieje.

## <a name="example"></a>Przykład

W tym przykładzie instrukcji warunkowej zawiera licznika, który ma zostać liczba z zakresu od 1 do 100; jednak `break` instrukcji pętli kończy się po liczby 4.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Przykład

W tym przykładzie `break` używana jest instrukcja break poza wewnętrzny pętli zagnieżdżonych i zwrócić kontrolkę do zewnętrznego pętli.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono użycie `break` w [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcji.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Jeśli wprowadzono `4`, będą dane wyjściowe:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
[switch](../../../csharp/language-reference/keywords/switch.md)  
[Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)  
[Instrukcje iteracji](../../../csharp/language-reference/keywords/iteration-statements.md)
