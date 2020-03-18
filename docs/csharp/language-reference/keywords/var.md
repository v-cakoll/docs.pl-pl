---
title: var - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712887"
---
# <a name="var-c-reference"></a>var (odwołanie w C#)

Począwszy od języka Visual C# 3.0 zmienne, które są zadeklarowane w zakresie metody może mieć niejawne "typ" `var`. Niejawnie wpisane zmiennej lokalnej jest silnie wpisany tak, jakby zadeklarowano typ samodzielnie, ale kompilator określa typ. Następujące dwie deklaracje `i` są funkcjonalnie równoważne:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach kwerend LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono dwa wyrażenia kwerendy. W pierwszym wyrażeniu `var` użycie jest dozwolone, ale nie jest wymagane, ponieważ typ wyniku `IEnumerable<string>`kwerendy można wyraźnie podać jako . Jednak w drugim wyrażeniu `var` umożliwia wynik jest kolekcją typów anonimowych, a nazwa tego typu nie jest dostępna z wyjątkiem samego kompilatora. Użycie `var` eliminuje wymóg, aby utworzyć nową klasę dla wyniku. Należy zauważyć, że `foreach` w przykładzie `item` #2 zmienna iteracji musi być również wpisywany niejawnie.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Jawnie wpisana zmienna lokalna](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
