---
title: instrukcja return - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713134"
---
# <a name="return-c-reference"></a>return (odwołanie w C#)

Instrukcja `return` kończy wykonywanie metody, w którym pojawia się i zwraca kontrolę do metody wywołującej. Można również zwrócić wartość opcjonalną. Jeśli metoda jest `void` typem, instrukcja `return` może zostać pominięta.

 Jeśli return instrukcji znajduje `try` się `finally` wewnątrz bloku, blok, jeśli istnieje, zostaną wykonane przed kontroli zwraca do metody wywołującej.

## <a name="example"></a>Przykład

 W poniższym przykładzie `CalculateArea()` metoda zwraca `area` zmienną `double` lokalną jako wartość.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [return, instrukcja](/cpp/cpp/return-statement-cpp)
