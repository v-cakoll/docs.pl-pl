---
title: Return — instrukcja C# -Reference
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713134"
---
# <a name="return-c-reference"></a>return (odwołanie w C#)

Instrukcja `return` przerywa wykonywanie metody, w której występuje i zwraca kontrolę do metody wywołującej. Może również zwrócić wartość opcjonalną. Jeśli metoda jest typu `void`, instrukcja `return` może zostać pominięta.

 Jeśli instrukcja return znajduje się wewnątrz bloku `try`, blok `finally`, jeśli taki istnieje, zostanie wykonany przed powracaniem kontroli do metody wywołującej.

## <a name="example"></a>Przykład

 W poniższym przykładzie metoda `CalculateArea()` zwraca zmienną lokalną `area` jako wartość `double`.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [return, instrukcja](/cpp/cpp/return-statement-cpp)
