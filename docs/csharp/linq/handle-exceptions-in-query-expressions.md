---
title: Obsługa wyjątków w wyrażeniach zapytań (LINQ w C#)
description: Informacje o sposobie obsługi wyjątków w wyrażeniach zapytań LINQ w C#.
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 5ad98565a74a96ac18829eb87f13eb398aa72967
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528476"
---
# <a name="handle-exceptions-in-query-expressions"></a>Obsługa wyjątków w wyrażeniach zapytań

Istnieje możliwość wywołać dowolną metodę w kontekście wyrażenia zapytania. Jednak zaleca się unikać wywołaniem jakiejkolwiek jego metody w wyrażeniu zapytania, które można utworzyć efekt uboczny, takich jak modyfikowanie zawartości źródła danych lub zostanie zgłoszony wyjątek. W tym przykładzie pokazano, jak można uniknąć zgłaszania wyjątków, po wywołaniu metody w wyrażeniu zapytania bez naruszania ogólne wytyczne .NET na obsługę wyjątków. Stan tych wytycznych można przechwytywać określony wyjątek, jeśli zrozumiesz, dlaczego jest zgłaszany w danym kontekście. Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące wyjątków](../../standard/exceptions/best-practices-for-exceptions.md).

W ostatnim przykładzie pokazano sposób obsługi tych przypadków, gdy należy zgłosić wyjątek podczas wykonywania zapytania.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób przenoszenia kodu poza wyrażeniem zapytania obsługi wyjątków. Jest to możliwe tylko wtedy, gdy metoda nie zależy od żadnych zmiennych lokalnych do zapytania.

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a>Przykład

W niektórych przypadkach może być najlepsze odpowiedzi na wyjątek, który jest zgłaszany w obrębie zapytania natychmiast zatrzymać wykonywanie zapytań. Poniższy przykład przedstawia sposób obsługi wyjątków, które może być wyrzucanych z wewnątrz treść zapytania. Przyjęto założenie, że `SomeMethodThatMightThrow` potencjalnie może spowodować wyjątek, który wymaga wykonywania zapytania, aby zatrzymać.

Należy pamiętać, że `try` otacza bloku `foreach` pętli i nie zapytanie. Jest to spowodowane `foreach` pętli to punkt, w którym faktycznie wykonać zapytania. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)  
