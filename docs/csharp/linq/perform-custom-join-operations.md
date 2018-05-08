---
title: Wykonywanie niestandardowych operacji łączenia
description: Jak wykonywanie niestandardowych operacji łączenia.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: df80f4382ad5fa96fcdc41b338cbb53a3d8e6cb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="perform-custom-join-operations"></a>Wykonywanie niestandardowych operacji łączenia

W tym przykładzie przedstawiono sposób wykonywania operacji łączenia, które nie są możliwe za pomocą `join` klauzuli. W wyrażeniu zapytania `join` jest ograniczona do klauzuli i zoptymalizowane pod kątem, typ equijoins, które są najbardziej typowych operacji tworzenia sprzężenia. Wykonując sprzężenie będzie prawdopodobnie zawsze uzyskać najlepszą wydajność, za pomocą `join` klauzuli.  
  
 Jednak `join` nie można użyć klauzuli w następujących przypadkach:  
  
-   Gdy sprzężenie jest uzależniona od wyrażenia nierówności (z systemem innym niż equijoin).  
  
-   Gdy sprzężenie jest uzależniona od więcej niż jedno wyrażenie równości i nierówności.  
  
-   Jeśli użytkownik ma wprowadzić zmienną zakresu tymczasowy dla sekwencji (wewnętrzny) po prawej stronie przed operacji tworzenia sprzężenia.  
  
 Aby wykonanie sprzężeń, które nie są equijoins, można użyć wielu `from` klauzule niezależnie wprowadzenie każdego źródła danych. Następnie Zastosuj wyrażenie predykatu w `where` klauzuli do zmiennej zakresu dla każdego źródła. Wyrażenie, które również mogą mieć formę wywołania metody.  
  
> [!NOTE]
>  Nie należy mylić tego rodzaju sprzężenia niestandardowe operacji z użyciem wielu `from` klauzule można uzyskać dostępu do kolekcji wewnętrznej. Aby uzyskać więcej informacji, zobacz [klauzuli join](../language-reference/keywords/join-clause.md).  
  
## <a name="example"></a>Przykład  
 Pierwsza metoda w poniższym przykładzie przedstawiono prosty sprzężenia krzyżowego. Sprzężenia krzyżowego należy używać ostrożnie, ponieważ mogą one powodować bardzo dużych zestawów wyników. Jednak mogą być użyteczne w niektórych scenariuszach tworzenia sekwencji źródła, z którymi są uruchamiane dodatkowych zapytań.  
  
 Druga metoda tworzy sekwencję wszystkie produkty, których identyfikator kategorii znajduje się na liście Kategoria po lewej stronie. Zwróć uwagę na użycie `let` klauzuli i `Contains` metodę w celu utworzenia tablicy tymczasowej. Również istnieje możliwość utworzenia tablicy przed zapytania i eliminowania pierwszy `from` klauzuli.  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zapytanie musi zostać dołączony do dwóch sekwencji oparta na zgodności kluczy, które w przypadku sekwencji wewnętrzny (po prawej stronie), nie można uzyskać przed sam klauzuli join. Jeśli wykonano tego przyłączenia z `join` klauzuli, a następnie `Split` metoda musi zostać wywołana dla każdego elementu. Użycie wielu `from` klauzule Umożliwia zapytanie, aby uniknąć zadań wywołania metody powtórzony. Ponieważ jednak `join` jest zoptymalizowana w tym przypadku może nadal być szybciej niż przy użyciu wielu `from` klauzul. Wyniki będą się różnić w zależności od głównie koszt jest wywołanie metody.  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia zapytań LINQ](index.md)  
 [join, klauzula](../language-reference/keywords/join-clause.md)  
 [Kolejność wyników klauzuli join](order-the-results-of-a-join-clause.md)
