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
ms.openlocfilehash: dee11c1ab754e515c69f330a5919776cbcb1e775
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871692"
---
# <a name="join-clause-c-reference"></a>Klauzula join (odwołanie w C#)

`join` Klauzuli przydaje się do kojarzenia elementów z sekwencji innego źródła, które nie mają bezpośredniego relacji w modelu obiektów. Jedynym wymaganiem jest, że elementy w każdym źródle udostępniać niektóre wartości, które mogą być porównywane pod kątem równości. Na przykład dystrybutora żywności może mieć listy dostawców określonego produktu oraz listę kupujący. A `join` klauzuli może służyć, na przykład, aby utworzyć listę dostawców i kupujący tego produktu, którzy są w taki sam określony region.

A `join` klauzuli przyjmuje dwóch źródłowych sekwencji jako dane wejściowe. Elementów w każdej sekwencji musi być albo zawiera właściwości, które można porównać do odpowiadającą właściwość w innych sekwencji. `join` Klauzuli porównuje klucze określonego pod kątem równości przy użyciu specjalnych `equals` — słowo kluczowe. Wszystkie sprzężenia, wykonywane przez `join` klauzuli są equijoins. Kształt danych wyjściowych `join` klauzuli zależy od określonego typu sprzężenia wykonywana. Poniżej przedstawiono trzy najbardziej powszechne typy join:

- Sprzężenie wewnętrzne

- Łączenie grupowe

- Lewe sprzężenie zewnętrzne

## <a name="inner-join"></a>Sprzężenie wewnętrzne

Poniższy przykład pokazuje prosty equijoin wewnętrznego. To zapytanie tworzy prostych sekwencji "Nazwa produktu / category" pary. Ten sam ciąg kategorii będą wyświetlane w wielu elementów. Jeśli element z `categories` nie ma odpowiadającego `products`, tej kategorii będą widoczne w wynikach.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Aby uzyskać więcej informacji, zobacz [wykonanie sprzężeń wewnętrznych](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Łączenie grupowe

A `join` klauzula `into` wyrażenie jest wywoływane sprzężenie grupy.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Sprzężenie grupy tworzy sekwencję wyniku hierarchicznego, który kojarzy elementów w sekwencji źródłowej po lewej stronie z co najmniej jeden zgodnych elementów w sekwencji źródłowej po prawej stronie. Sprzężenie grupy nie ma odpowiednika w relacyjnego kategoriach; jest zasadniczo sekwencję tablic obiektów.

Jeśli odpowiadający element w źródle po lewej stronie znajdują się żadnych elementów z sekwencji źródłowej prawo `join` klauzuli dadzą pustą tablicę dla tego elementu. Dlatego sprzężenie grupy jest nadal zasadniczo sprzężenie wewnętrzne różnicą, że kolejność wyniku są zorganizowane w grupy.

Wybranie tylko wyniki sprzężenie grupy uzyskują dostęp do elementów, ale nie może zidentyfikować są zgodne na klucz. Dlatego jest zazwyczaj bardziej użyteczna, wybrać wyniki sprzężenie grupy do nowego typu, który ma również nazwę klucza, jak pokazano w poprzednim przykładzie.

Oczywiście, umożliwia również wynikiem sprzężenia grupy jako generator innego podzapytania:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Aby uzyskać więcej informacji, zobacz [wykonaj pogrupowane sprzężeń](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Lewe sprzężenie zewnętrzne

Lewego sprzężenia zewnętrznego wszystkie elementy w sekwencji źródłowej po lewej stronie zostaną zwrócone, nawet jeśli w prawej sekwencji żadnych zgodnych elementów. Aby wykonać lewe sprzężenie zewnętrzne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], użyj `DefaultIfEmpty` metody w połączeniu z sprzężenie grupy, aby określić domyślny element po prawej stronie, do produkcji, jeśli element po lewej stronie nie ma żadnych dopasowań. Możesz użyć `null` jako wartość domyślna w przypadku dowolnego odwołania do typu, lub można określić typ domyślny zdefiniowanych przez użytkownika. W poniższym przykładzie pokazano zdefiniowane przez użytkownika domyślny typ:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Aby uzyskać więcej informacji, zobacz [wykonaj Lewe sprzężenia zewnętrzne](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>Operator równości

A `join` klauzuli wykonuje sprzężenie. Innymi słowy możesz to zrobić tylko podstawowy dopasowań na równość dwa klucze. Innych rodzajów porównań, takie jak "większe niż" lub "nie równa się" nie są obsługiwane. Aby wyjaśnić, czy wszystkie sprzężeń equijoins, `join` używa klauzuli `equals` słowa kluczowego zamiast `==` operatora. `equals` — Słowo kluczowe można używać tylko w `join` klauzuli i różni się od `==` operatora w jednym ze sposobów ważne. Za pomocą `equals`Strzałka w lewo zużywa sekwencji źródło zewnętrzne i Strzałka w prawo zużywa typu inner source. Źródło zewnętrzne jest tylko do zakresu po lewej stronie `equals` i sekwencji źródłowej wewnętrzny jest tylko w zakresie po prawej stronie.

## <a name="non-equijoins"></a>Inne niż equijoins

Można wykonać innych niż equijoins, sprzężeń i innych niestandardowych operacji łączenia za pomocą wielu `from` klauzul, aby wprowadzić nowy sekwencje niezależnie do zapytania. Aby uzyskać więcej informacji, zobacz [wykonywanie niestandardowych operacji łączenia](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Sprzężenia w kolekcji obiektów w porównaniu z tabelami relacyjnymi

W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenie zapytania, sprzężenia operacje są wykonywane w kolekcji obiektów. Obiekt kolekcji nie może być "łączone" w taki sam sposób, jak dwie tabele relacyjne. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], jawna `join` klauzule są tylko wymagane w przypadku dwóch źródłowych sekwencji nie są powiązane przez żadnych relacji. Podczas pracy z [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], tabel kluczy obcych są reprezentowane w modelu obiektu jako właściwości tabeli podstawowej. Na przykład w bazie danych Northwind tabeli klientów ma relacji klucza obcego z tabeli zamówienia. Kiedy mapujesz tabele do modelu obiektu klasy klienta ma właściwość zamówienia, który zawiera kolekcję zleceń skojarzonych z tym klientem. W efekcie sprzężenia już przeprowadzono dla Ciebie.

Aby uzyskać więcej informacji na temat wykonywania zapytań w tabelach pokrewnych w kontekście [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], zobacz [jak: relacje bazy danych mapy](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Klucze złożone

Możesz przetestować pod kątem równości wielu wartości przy użyciu klucza złożonego. Aby uzyskać więcej informacji, zobacz [sprzęganie za pomocą kluczy złożonych](../../linq/join-by-using-composite-keys.md). Klucze złożone, które mogą być również używane w `group` klauzuli.

## <a name="example"></a>Przykład

W poniższym przykładzie porównano wynikiem sprzężenia wewnętrznego, łączenie grupy i lewe sprzężenie zewnętrzne na te same źródła danych przy użyciu tych samych kluczy dopasowania. Dodatkowy kod jest dodawany do tych przykładów, aby wyjaśnić, wyniki w oknie konsoli.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Uwagi

A `join` klauzula, która nie jest zakończony znakiem `into` jest tłumaczony na <xref:System.Linq.Enumerable.Join%2A> wywołania metody. A `join` klauzula, która następuje `into` jest tłumaczony <xref:System.Linq.Enumerable.GroupJoin%2A> wywołania metody.

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
- [Operacje połączone](../../programming-guide/concepts/linq/join-operations.md)
- [group, klauzula](group-clause.md)
- [Wykonywanie lewych sprzężeń zewnętrznych](../../linq/perform-left-outer-joins.md)
- [Wykonywanie sprzężeń wewnętrznych](../../linq/perform-inner-joins.md)
- [Wykonywanie sprzężeń grupowanych](../../linq/perform-grouped-joins.md)
- [Kolejność wyników klauzuli join](../../linq/order-the-results-of-a-join-clause.md)
- [Sprzęganie za pomocą kluczy złożonych](../../linq/join-by-using-composite-keys.md)
- [Zgodne systemy bazy danych dla programu Visual Studio](/visualstudio/data-tools/installing-database-systems-tools-and-samples)