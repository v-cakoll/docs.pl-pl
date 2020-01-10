---
title: klauzula Join — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 8e52e9db241392b67818b7316767dd97bd38432a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713407"
---
# <a name="join-clause-c-reference"></a>Klauzula join (odwołanie w C#)

Klauzula `join` jest przydatna do kojarzenia elementów z różnych sekwencji źródłowych, które nie mają bezpośredniej relacji w modelu obiektów. Jedyny wymóg polega na tym, że elementy w poszczególnych źródłach mają pewną wartość, którą można porównać pod kątem równości. Na przykład dystrybutor żywności może mieć listę dostawców określonego produktu i listę kupujących. Klauzula `join` może być używana na przykład w celu utworzenia listy dostawców i nabywców tego produktu, którzy znajdują się w tym samym określonym regionie.

Klauzula `join` przyjmuje dwie sekwencje źródłowe jako dane wejściowe. Elementy w każdej sekwencji muszą być albo zawierać właściwość, którą można porównać z odpowiednią właściwością w innej sekwencji. Klauzula `join` porównuje określone klucze dla równości przy użyciu słowa kluczowego `equals` specjalnego. Wszystkie sprzężenia wykonywane przez klauzulę `join` są equijoins. Kształt danych wyjściowych klauzuli `join` zależy od określonego typu dołączania. Poniżej przedstawiono trzy Najczęstsze typy sprzężeń:

- Sprzężenie wewnętrzne

- Dołącz do grupy

- Lewe sprzężenie zewnętrzne

## <a name="inner-join"></a>Sprzężenie wewnętrzne

W poniższym przykładzie przedstawiono proste wewnętrzne equijoin. To zapytanie tworzy płaską sekwencję par "Nazwa produktu/kategoria". Ten sam ciąg kategorii będzie wyświetlany w wielu elementach. Jeśli element z `categories` nie ma pasujących `products`, Ta kategoria nie zostanie wyświetlona w wynikach.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Aby uzyskać więcej informacji, zobacz [wykonywanie sprzężeń wewnętrznych](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Dołącz do grupy

Klauzula `join` z wyrażeniem `into` jest nazywana przyłączaniem do grupy.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Przyłączenie do grupy tworzy hierarchiczną sekwencję wyników, która kojarzy elementy w sekwencji z lewej strony z co najmniej jednym zgodnymi elementami w sekwencji źródłowej po prawej stronie. Przyłączanie do grupy nie ma odpowiedników w warunkach relacyjnych; zasadniczo jest to sekwencja tablic obiektów.

Jeśli nie zostaną znalezione żadne elementy z prawej sekwencji źródłowej pasujące do elementu w lewym źródle, klauzula `join` będzie generować pustą tablicę dla tego elementu. W związku z tym, przyłączenie do grupy jest nadal zasadniczo wewnętrznym equijoin, z tą różnicą, że sekwencja wyników jest zorganizowana w grupy.

Jeśli po prostu wybierzesz wyniki przyłączenia do grupy, możesz uzyskać dostęp do tych elementów, ale nie możesz zidentyfikować klucza, na którym są one zgodne. W związku z tym zwykle bardziej przydatne jest wybranie wyników sprzężenia grupy na nowy typ, który ma również nazwę klucza, jak pokazano w poprzednim przykładzie.

Oczywiście można również użyć wyniku sprzężenia grupy jako generatora innego podzapytania:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Aby uzyskać więcej informacji, zobacz [wykonywanie sprzężeń zgrupowanych](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Lewe sprzężenie zewnętrzne

W lewym sprzężeniu zewnętrznym są zwracane wszystkie elementy w sekwencji po lewej stronie, nawet jeśli żadne zgodne elementy nie są w odpowiedniej kolejności. Aby wykonać lewe sprzężenie zewnętrzne w LINQ, użyj metody `DefaultIfEmpty` w połączeniu z przyłączaniem do grupy, aby określić domyślny element po prawej stronie, który ma zostać użyty, jeśli element po lewej stronie nie ma dopasowań. Można użyć `null` jako wartości domyślnej dla dowolnego typu odwołania lub można określić typ domyślny zdefiniowany przez użytkownika. W poniższym przykładzie jest pokazywany typ domyślny zdefiniowany przez użytkownika:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Aby uzyskać więcej informacji, zobacz [przełączenie do lewego sprzężenia zewnętrznego](../../linq/perform-left-outer-joins.md).

## <a name="the-equals-operator"></a>Operator równości

Klauzula `join` wykonuje equijoin. Innymi słowy, można uzyskać tylko podstawowe dopasowania dotyczące równości dwóch kluczy. Inne typy porównania, takie jak "większe niż" lub "not Equals", nie są obsługiwane. Aby wyczyścić, że wszystkie sprzężenia są equijoins, klauzula `join` używa słowa kluczowego `equals` zamiast operatora `==`. Słowo kluczowe `equals` może być używane tylko w klauzuli `join` i różni się od operatora `==` w jeden ważny sposób. W przypadku `equals`lewy klucz zużywa zewnętrzną sekwencję źródłową, a prawy klucz korzysta ze źródła wewnętrznego. Zewnętrzne źródło znajduje się tylko w zakresie po lewej stronie `equals`, a wewnętrzna sekwencja źródłowa jest tylko w zakresie po prawej stronie.

## <a name="non-equijoins"></a>Nie equijoins

Za pomocą wielu klauzul `from`, aby wprowadzać nowe sekwencje niezależnie do zapytania, można wykonywać operacje inne niż equijoins, sprzężenia krzyżowego i inne niestandardowe czynności Join. Aby uzyskać więcej informacji, zobacz [wykonywanie niestandardowych operacji łączenia](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Sprzężenia na kolekcjach obiektów a tabelach relacyjnych

W wyrażeniu zapytania LINQ operacje Join są wykonywane w ramach kolekcji obiektów. Kolekcje obiektów nie mogą być połączone w taki sam sposób jak dwie tabele relacyjne. W LINQ jawne klauzule `join` są wymagane tylko wtedy, gdy dwie sekwencje źródłowe nie są powiązane z żadną relacją. Podczas pracy z [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]tabele kluczy obcych są reprezentowane w modelu obiektów jako właściwości tabeli podstawowej. Na przykład w bazie danych Northwind tabela Customer zawiera relację klucza obcego z tabelą Orders. Po zmapowaniu tabel do modelu obiektów Klasa Customer ma właściwość Orders, która zawiera kolekcję zamówień skojarzonych z tym klientem. W efekcie połączenie zostało już wykonane.

Aby uzyskać więcej informacji o wysyłaniu zapytań między powiązanymi tabelami w kontekście [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], zobacz [How to: map Relationships Database](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Klucze złożone

Możesz sprawdzić równość wielu wartości przy użyciu klucza złożonego. Aby uzyskać więcej informacji, zobacz [sprzęganie za pomocą kluczy złożonych](../../linq/join-by-using-composite-keys.md). Klucze złożone mogą być również używane w klauzuli `group`.

## <a name="example"></a>Przykład

Poniższy przykład porównuje wyniki sprzężenia wewnętrznego, sprzężenie grupy i lewe sprzężenie zewnętrzne w tych samych źródłach danych przy użyciu tych samych pasujących kluczy. Do tych przykładów zostanie dodany dodatkowy kod, aby wyjaśnić wyniki wyświetlane w konsoli.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Uwagi

Klauzula `join`, która nie następuje po `into`, jest tłumaczona na wywołanie metody <xref:System.Linq.Enumerable.Join%2A>. Klauzula `join`, do której następuje `into`, jest tłumaczona na wywołanie metody <xref:System.Linq.Enumerable.GroupJoin%2A>.

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
- [Zgodne systemy baz danych dla programu Visual Studio](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
