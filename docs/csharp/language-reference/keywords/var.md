---
title: WARIANCJA C# — odwołanie
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712887"
---
# <a name="var-c-reference"></a>var (odwołanie w C#)

Począwszy od programu C# Visual 3,0, zmienne, które są zadeklarowane w zakresie metody, mogą mieć niejawny "typ" `var`. Niejawnie wpisana zmienna lokalna jest silnie wpisana, tak jakby zadeklarowano typ samodzielnie, ale kompilator określa typ. Następujące dwie deklaracje `i` są funkcjonalnie równoważne:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach zapytań LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dwa wyrażenia zapytania. W pierwszym wyrażeniu użycie `var` jest dozwolone, ale nie jest wymagane, ponieważ typ wyniku zapytania można jawnie określić jako `IEnumerable<string>`. Jednak w drugim wyrażeniu `var` zezwala na zbieranie anonimowych typów, a nazwa tego typu jest niedostępna z wyjątkiem samego kompilatora. Użycie `var` eliminuje wymóg tworzenia nowej klasy dla wyniku. Należy zauważyć, że w przykładzie #2 Zmienna iteracji `foreach` `item` musi również być wpisana niejawnie.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Jawnie wpisane zmienne lokalne](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
