---
title: Wykonywanie niestandardowych operacji łączenia (LINQ w C#)
description: Dowiedz się, jak wykonać niestandardowych operacji łączenia LINQ w C#.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: a0e08396c006f68949357c50a28b3b0982f0dd83
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866679"
---
# <a name="perform-custom-join-operations"></a>Wykonywanie niestandardowych operacji łączenia

W tym przykładzie pokazano, jak wykonywanie operacji łączenia, które nie są możliwe dzięki `join` klauzuli. W wyrażeniu zapytania `join` klauzula jest ograniczona do i zoptymalizowane pod kątem, equijoins, które są najbardziej typowe rodzaj operacji tworzenia sprzężenia. Wykonując sprzężenie będzie prawdopodobnie zawsze uzyskać najlepszą wydajność, za pomocą `join` klauzuli.

Jednak `join` nie można używać klauzuli w następujących przypadkach:

- Gdy sprzężenia jest uzależniona na wyrażeniu nierówności (innych niż equijoin).

- Gdy sprzężenia jest uzależniona na więcej niż jedno wyrażenie równości lub nierówności.

- Gdy trzeba wprowadzić zmienną zakresu tymczasowy dla sekwencji po prawej stronie (wewnętrzny) przed wykonaniem operacji dołączania.

 Do wykonania sprzężenia, które nie są equijoins, możesz użyć wielu `from` klauzule niezależnie wprowadzenie każdego źródła danych. Następnie Zastosuj wyrażenie predykatu w `where` klauzuli do zmiennej zakresu dla każdego źródła. Wyrażenie może również mieć postać wywołania metody.

> [!NOTE]
> Nie należy mylić tego rodzaju operacji tworzenia sprzężenia niestandardowe z użyciem wielu `from` klauzul do dostępu do kolekcji wewnętrznego. Aby uzyskać więcej informacji, zobacz [klauzuli join](../language-reference/keywords/join-clause.md).

## <a name="example"></a>Przykład

Pierwsza metoda w poniższym przykładzie przedstawiono prosty sprzężenie krzyżowe. Sprzężenia krzyżowego należy używać ostrożnie, ponieważ mogą one powodować bardzo dużych zestawów wyników. Jednakże mogą być użyteczne w niektórych scenariuszach tworzenia źródłowych sekwencji, wobec których są uruchamiane dodatkowe zapytania.

Druga metoda generuje sekwencję wszystkie produkty, których identyfikator kategorii znajduje się na liście kategorii po lewej stronie. Zwróć uwagę na użycie `let` klauzuli i `Contains` metodę, aby utworzyć tablicę tymczasową. Również jest możliwe, aby utworzyć tablicę przed zapytania i wyeliminować pierwszy `from` klauzuli.

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a>Przykład

W poniższym przykładzie zapytanie należy przyłączyć dwie sekwencje oparta na zgodności kluczy, które w przypadku sekwencji wewnętrzny (prawa strona), nie można uzyskać przed klauzuli join, sam. Jeśli wykonano to połączenie przy użyciu `join` klauzuli, a następnie `Split` metody musi być wywoływana dla każdego elementu. Korzystanie z wielu `from` klauzule Umożliwia zapytanie, aby uniknąć obciążenie związane z wywołania metody powtórzony. Jednak ponieważ `join` jest zoptymalizowana w tym konkretnym przypadku nadal może być szybsze niż użycie wielu `from` klauzul. Wyniki będą się różnić w zależności przede wszystkim na sposób kosztownych jest wywołanie metody.

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)  
- [join, klauzula](../language-reference/keywords/join-clause.md)  
- [Kolejność wyników klauzuli join](order-the-results-of-a-join-clause.md)  