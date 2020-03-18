---
title: Obsługa wyjątków w wyrażeniach kwerendy (LINQ w języku C#)
description: Dowiedz się, jak obsługiwać wyjątki w wyrażeniach kwerend LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688504"
---
# <a name="handle-exceptions-in-query-expressions"></a>Obsługa wyjątków w wyrażeniach zapytań

Istnieje możliwość wywołania dowolnej metody w kontekście wyrażenia kwerendy. Jednak zaleca się, aby uniknąć wywoływania dowolnej metody w wyrażeniu kwerendy, które można utworzyć efekt uboczny, takich jak modyfikowanie zawartości źródła danych lub zgłaszanie wyjątku. W tym przykładzie pokazano, jak uniknąć wywoływania wyjątków podczas wywoływania metod w wyrażeniu zapytania bez naruszania ogólnych wytycznych .NET dotyczących obsługi wyjątków. Te wytyczne stwierdzają, że dopuszczalne jest, aby przechwycić określony wyjątek, gdy rozumiesz, dlaczego jest generowany w danym kontekście. Aby uzyskać więcej informacji, zobacz [Najważniejsze wskazówki dotyczące wyjątków](../../standard/exceptions/best-practices-for-exceptions.md).

W ostatnim przykładzie pokazano, jak obsługiwać te przypadki, gdy należy zgłosić wyjątek podczas wykonywania kwerendy.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak przenieść kod obsługi wyjątków poza wyrażenie kwerendy. Jest to możliwe tylko wtedy, gdy metoda nie zależy od żadnych zmiennych lokalnych do kwerendy.

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a>Przykład

W niektórych przypadkach najlepszą odpowiedzią na wyjątek, który jest generowany z poziomu kwerendy może być natychmiastowe zatrzymanie wykonywania kwerendy. W poniższym przykładzie pokazano, jak obsługiwać wyjątki, które mogą być generowane z wewnątrz treści kwerendy. Załóżmy, że `SomeMethodThatMightThrow` potencjalnie może spowodować wyjątek, który wymaga wykonania kwerendy, aby zatrzymać.

Należy zauważyć, że `try` blok `foreach` otacza pętlę, a nie samą kwerendę. Jest to `foreach` spowodowane pętli jest punkt, w którym kwerenda jest faktycznie wykonywana. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do zapytań LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
