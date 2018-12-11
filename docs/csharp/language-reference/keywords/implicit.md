---
title: niejawne - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: ee40db31aeb39a37c6ab15b26b48f1f7d02d6780
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240583"
---
# <a name="implicit-c-reference"></a>implicit (odwołanie w C#)

`implicit` Słowo kluczowe jest używane do deklarowania niejawnego typu zdefiniowanego przez użytkownika operatora konwersji. Umożliwia włączanie niejawnych konwersji między typem zdefiniowanym przez użytkownika i innego typu, jeśli konwersja daje gwarancję spowodować utratę danych.

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

Dzięki wyeliminowaniu zbędnych rzutowania, niejawne konwersje można zwiększyć czytelność kodu źródłowego. Jednak ponieważ niejawne konwersje nie wymagają programistom jawnie rzutowane z jednego typu na drugi, należy uważać, aby uniknąć nieoczekiwanych wyników. Ogólnie rzecz biorąc operatory niejawnej konwersji powinno nigdy nie zgłaszają wyjątków i nigdy nie utracą informacje, aby używane bezpiecznie bez świadomości programisty. Jeśli operator konwersji nie spełniają te kryteria, powinien być oznaczony `explicit`. Aby uzyskać więcej informacji, zobacz [Używanie operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [explicit](explicit.md)  
- [Operator (odwołanie w C#)](operator.md)  
- [Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
