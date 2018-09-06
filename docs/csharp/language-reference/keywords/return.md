---
title: Return — instrukcja (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 0d20da39d3f56220c4499f699e542bd24ded93ca
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742004"
---
# <a name="return-c-reference"></a>return (odwołanie w C#)

`return` Kończy wykonywanie metody, w którym występuje i zwraca kontrolę do metody wywołującej. Może również zwracać wartość opcjonalna. Jeśli metoda jest `void` typu `return` instrukcji, można pominąć.

 Jeśli znajduje się wewnątrz instrukcji return `try` bloku `finally` bloku, jeśli taki istnieje, zostanie wykonana zanim sterowanie powraca do wywoływania metody.

## <a name="example"></a>Przykład

 W poniższym przykładzie metoda `CalculateArea()` zwraca zmienna lokalna `area` jako [double](double.md) wartość.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [return, instrukcja](/cpp/cpp/return-statement-cpp)
- [Instrukcje skoku](jump-statements.md)
