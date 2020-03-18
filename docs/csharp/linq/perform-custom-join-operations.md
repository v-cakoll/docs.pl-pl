---
title: Wykonywanie operacji sprzężenia niestandardowego (LINQ w języku C#)
description: Dowiedz się, jak wykonywać niestandardowe operacje sprzężenia LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659855"
---
# <a name="perform-custom-join-operations"></a>Wykonywanie niestandardowych operacji sprzęgania

W tym przykładzie pokazano, jak wykonać operacje sprzężenia, które nie są możliwe z klauzulą. `join` W wyrażeniu `join` kwerendy klauzula jest ograniczona i zoptymalizowana dla, równorzędnych, które są zdecydowanie najbardziej typowym typem operacji sprzężenia. Podczas wykonywania równorzędne, prawdopodobnie zawsze uzyskać najlepszą `join` wydajność przy użyciu klauzuli.

Jednak że `join` klauzula ta nie może być używana w następujących przypadkach:

- Gdy sprzężenie opiera się na wyrażenie nierówności (non-equijoin).

- Gdy sprzężenie opiera się na więcej niż jednym wyrażeniu równości lub nierówności.

- Gdy trzeba wprowadzić tymczasową zmienną zakresu dla prawej strony (wewnętrznej) sekwencji przed operacją sprzężenia.

 Aby wykonać sprzężenia, które nie są równorzędne, można użyć wielu `from` klauzul, aby wprowadzić każde źródło danych niezależnie. Następnie należy zastosować wyrażenie predykatu `where` w klauzuli do zmiennej zakresu dla każdego źródła. Wyrażenie może również przybrać formę wywołania metody.

> [!NOTE]
> Nie należy mylić tego rodzaju niestandardowej operacji `from` sprzężenia z użyciem wielu klauzul, aby uzyskać dostęp do kolekcji wewnętrznych. Aby uzyskać więcej informacji, zobacz [klauzulę join .](../language-reference/keywords/join-clause.md)

## <a name="example"></a>Przykład

Pierwsza metoda w poniższym przykładzie pokazuje proste sprzężenie krzyżowe. Sprzężenia krzyżowe muszą być używane z ostrożnością, ponieważ mogą one powodować bardzo duże zestawy wyników. Jednak mogą być przydatne w niektórych scenariuszach do tworzenia sekwencji źródłowych, względem których są uruchamiane dodatkowe kwerendy.

Druga metoda tworzy sekwencję wszystkich produktów, których identyfikator kategorii znajduje się na liście kategorii po lewej stronie. Należy zwrócić uwagę `let` na `Contains` użycie klauzuli i metody do tworzenia tablicy tymczasowej. Istnieje również możliwość utworzenia tablicy przed kwerendą `from` i wyeliminowanie pierwszej klauzuli.

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a>Przykład

W poniższym przykładzie kwerenda musi łączyć dwie sekwencje oparte na pasujące klucze, które w przypadku wewnętrznej (po prawej stronie) sekwencji, nie można uzyskać przed join klauzuli, sam. Jeśli to sprzężenie `join` zostały wykonane `Split` z klauzulą, a następnie metoda musiałaby zostać wywołana dla każdego elementu. Użycie wielu `from` klauzul umożliwia kwerendy, aby uniknąć narzutów powtarzające się wywołanie metody. Jednak ponieważ `join` jest zoptymalizowany, w tym konkretnym przypadku `from` nadal może być szybsze niż przy użyciu wielu klauzul. Wyniki będą się różnić w zależności od tego, jak drogie jest wywołanie metody.

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
- [klauzula sprzężenia](../language-reference/keywords/join-clause.md)
- [Kolejność wyników klauzuli join](order-the-results-of-a-join-clause.md)
