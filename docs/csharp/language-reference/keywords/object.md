---
title: obiekt - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 99ce5300d06c500d2e45897a6bd57153dc40d34e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633388"
---
# <a name="object-c-reference"></a>object (odwołanie w C#)

`object` Typu jest aliasem dla <xref:System.Object> na platformie .NET. W systemie zunifikowany typ w języku C#, wszystkie typy, wstępnie zdefiniowanych i zdefiniowanych przez użytkownika typy odwołań i typy wartości dziedziczyć bezpośrednio lub pośrednio <xref:System.Object>. Można przypisać wartości dowolnego typu do zmiennych typu `object`. Kiedy zmienną typu wartości jest konwertowany na obiekt, jest określany jako *opakowany*. Zmienną obiektu typu jest konwertowany na typ wartości, jest określane jako *rozpakowany*. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](../../../csharp/programming-guide/types/boxing-and-unboxing.md).

## <a name="example"></a>Przykład

Następujące przykładowe pokazuje, jak zmienne typu `object` może akceptować wartości dowolnego typu danych i w jaki sposób zmienne typu `object` można użyć metod na <xref:System.Object> z programu .NET Framework.

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Typy wartości](value-types.md)
