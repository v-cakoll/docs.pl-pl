---
title: var — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: a523e575f14c88ea385bf115f0b07f54190499a5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633202"
---
# <a name="var-c-reference"></a>var (odwołanie w C#)

Począwszy od Visual C# 3.0, zmienne, które są zadeklarowane w zakresie metoda może mieć niejawne "type" `var`. Niejawnie wpisane zmiennej lokalnej jest jednoznacznie określone typy, tak jak w przypadku możesz typu była zadeklarowana, ale kompilator Określa typ. Poniższe dwie deklaracje `i` są funkcjonalnie równoważne:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach zapytań LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dwa wyrażenia zapytania. W pierwszym wyrażeniu użytkowania `var` jest dozwolone, ale nie jest wymagana, ponieważ typ wyniku zapytania może być jawnie wyrażona jako `IEnumerable<string>`. Jednak w drugim wyrażeniu `var` umożliwia wynik, który ma być kolekcją typów anonimowych, i nazwę tego typu nie jest dostępny z wyjątkiem kompilatorowi sam. Korzystanie z `var` eliminuje konieczność Utwórz nową klasę dla wyniku. Należy pamiętać, że w przykładzie 2, `foreach` zmiennej iteracyjnej `item` również musi być wpisana niejawnie.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Jawnie wpisane zmienne lokalne](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
