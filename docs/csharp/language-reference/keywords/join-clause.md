---
title: Klauzula join (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: a868c52cf753b1e4285586ec41c1993f519299d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289402"
---
# <a name="join-clause-c-reference"></a>Klauzula join (odwołanie w C#)
`join` Klauzuli przydaje się do kojarzenia elementów z sekwencje innego źródła, które nie mają bezpośredniego relacji w modelu obiektów. Jedynym wymaganiem jest to, że elementy w każdym źródle udostępniać niektóre wartości, które można porównywać pod względem równości. Na przykład dystrybutora żywności może mieć listy dostawców określonego produktu oraz listę kupujący. A `join` klauzuli można na przykład, aby utworzyć listę dostawców i kupujący tego produktu, którzy są w taki sam określić region.  
  
 A `join` klauzuli przyjmuje dwóch sekwencji źródła jako dane wejściowe. Elementów w każdej kolejny musi być albo zawiera właściwości, które można porównać do odpowiadającej właściwości w innych sekwencji. `join` Klauzuli porównuje równość określone klucze za pomocą specjalnych `equals` — słowo kluczowe. Dołącza wszystkie wykonywane przez `join` klauzuli są equijoins. Kształt danych wyjściowych `join` klauzuli zależy od określonego typu wykonywanego sprzężenia. Poniżej przedstawiono trzy typów sprzężeń najczęściej:  
  
-   sprzężenie wewnętrzne  
  
-   Łączenie grupowe  
  
-   Lewe sprzężenie zewnętrzne  
  
## <a name="inner-join"></a>Sprzężenie wewnętrzne  
 W poniższym przykładzie przedstawiono prosty equijoin wewnętrzny. To zapytanie daje płaski sekwencji "Nazwa produktu / kategorii" pary. W wielu elementów pojawi się ten sam ciąg kategorii. Jeśli element na podstawie `categories` nie posiada odpowiadającego `products`, tej kategorii nie będą widoczne w wynikach.  
  
 [!code-csharp[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: wykonania sprzężenia wewnętrznego](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).  
  
## <a name="group-join"></a>Łączenie grupowe  
 A `join` klauzuli z `into` wyrażenie jest nazywany sprzężenia grupy.  
  
 [!code-csharp[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]  
  
 Łączenie grupowe tworzy sekwencję wyników hierarchicznych, co umożliwia skojarzenie elementy sekwencji źródłowej po lewej stronie z jednego lub więcej elementów pasujących w sekwencji źródłowej po prawej stronie. Sprzężenia grupy nie ma odpowiednika w warunków relacyjnych; jest zasadniczo sekwencję tablice obiektów.  
  
 Jeśli nie z sekwencji prawo źródłowej znaleziono elementów do dopasowania elementu w źródle po lewej stronie `join` klauzuli utworzy pustą tablicę dla tego elementu. W związku z tym sprzężenia grupy jest nadal zasadniczo sprzężenie wewnętrzne z tą różnicą, że sekwencji wyniki są zorganizowane w grupy.  
  
 Wybranie tylko wyniki sprzężenia grupy uzyskują dostęp do elementów, ale nie można zidentyfikować odpowiadających na klucz. W związku z tym jest zazwyczaj bardziej użyteczna wybrać wyniki sprzężenia grupy do nowego typu, który ma także nazwę klucza, jak pokazano w poprzednim przykładzie.  
  
 Oczywiście umożliwia także wyniku w sprzężeniu grupy jako generator innego podzapytania:  
  
 [!code-csharp[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: wykonaj pogrupowane sprzężenia](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).  
  
## <a name="left-outer-join"></a>Zewnętrzne lewego sprzężenia  
 W lewe sprzężenie zewnętrzne zwracane są wszystkie elementy w sekwencji źródłowej po lewej stronie, nawet jeśli w prawej sekwencji żadnych zgodnych elementów. Aby wykonać lewe sprzężenie zewnętrzne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], użyj `DefaultIfEmpty` metody w połączeniu z sprzężenia grupy, aby określić domyślny element po prawej stronie, aby wygenerować, jeśli element po lewej stronie nie ma żadnych wyników. Można użyć `null` jako wartość domyślną dla wszystkich odwołań typ, lub można określić typ domyślny zdefiniowane przez użytkownika. W poniższym przykładzie przedstawiono domyślne zdefiniowane przez użytkownika typu:  
  
 [!code-csharp[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: wykonaj lewej strony sprzężenia zewnętrzne](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).  
  
## <a name="the-equals-operator"></a>Operator równości  
 A `join` klauzuli wykonuje sprzężenie. Innymi słowy można tylko podstawowy dopasowań na równość dwa klucze. Inne rodzaje porównań, takie jak "większe niż" lub "nie równa się" nie są obsługiwane. Aby wyjaśnić, czy wszystkie sprzężenia equijoins, `join` używa klauzuli `equals` słowa kluczowego zamiast `==` operatora. `equals` — Słowo kluczowe można używać tylko w `join` klauzuli i różni się od `==` operatora w jednym ze sposobów ważne. Z `equals`, po lewej stronie klucza zużywa sekwencji źródło zewnętrzne i wewnętrzne źródło wykorzystuje prawidłowy klucz. Źródło zewnętrzne jest tylko w zakresie po lewej stronie `equals` i sekwencji wewnętrzny źródłowej znajduje się tylko w zakresie po prawej stronie.  
  
## <a name="non-equijoins"></a>Z systemem innym niż Equijoins  
 Nie equijoins, cross sprzężenia i innych niestandardowych operacji łączenia można wykonać za pomocą wielu `from` klauzule niezależnie wprowadzenie nowego sekwencji do zapytania. Aby uzyskać więcej informacji, zobacz [porady: wykonaj operacje Join niestandardowe](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="joins-on-object-collections-vs-relational-tables"></a>Sprzężenia w kolekcji obiektów, a tabel relacyjnych  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytania, sprzężenia operacje są wykonywane w kolekcji obiektów. Obiekt kolekcji nie może być "przyłączony" w taki sam sposób, jak dwóch tabel relacyjnych. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], jawne `join` tylko jest wymagana, gdy dwie sekwencje źródła nie jest powiązana w żadnej z relacji. Podczas pracy z [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], tabele klucza obcego są reprezentowane w modelu obiektów jako właściwości tabeli podstawowej. Na przykład w bazie danych Northwind tabeli klienta ma relacji klucza obcego z tabeli zamówienia. Podczas mapowania tabele w modelu obiektów, klasa klienta ma właściwości zleceń, który zawiera kolekcję zleceń skojarzonych z klientem. W efekcie sprzężenie już przeprowadzono dla Ciebie.  
  
 Aby uzyskać więcej informacji o wykonywanie zapytań w powiązanych tabel w kontekście [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], zobacz [porady: relacje bazy danych mapy](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
## <a name="composite-keys"></a>Klucze złożone  
 Można przetestować równości wiele wartości, przy użyciu klucza złożonego. Aby uzyskać więcej informacji, zobacz [porady: sprzęganie za pomocą kluczy złożonych](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md). Klucze złożone mogą być również używane w `group` klauzuli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład porównuje wyniki sprzężenie wewnętrzne, sprzężenia grupy i lewe sprzężenie zewnętrzne w tym samym źródle danych przy użyciu tych samych kluczy dopasowania. Niektóre dodatkowe kodu jest dodawana do te przykłady, aby wyjaśnić wyniki w oknie konsoli.  
  
 [!code-csharp[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]  
  
## <a name="remarks"></a>Uwagi  
 A `join` klauzula nie poprzedza `into` jest przekształcana na <xref:System.Linq.Enumerable.Join%2A> wywołania metody. A `join` klauzuli, w którym następuje `into` jest translacji <xref:System.Linq.Enumerable.GroupJoin%2A> wywołania metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe zapytania (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Operacje połączone](../../programming-guide/concepts/linq/join-operations.md)  
 [group, klauzula](../../../csharp/language-reference/keywords/group-clause.md)  
 [Porady: wykonanie lewych sprzężeń zewnętrznych](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Porady: wykonanie sprzężeń wewnętrznych](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Porady: wykonanie sprzężeń grupowanych](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Porady: kolejność wyników klauzuli Join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Porady: sprzęganie za pomocą kluczy złożonych](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Porady: Instalacja przykładowych baz danych](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
