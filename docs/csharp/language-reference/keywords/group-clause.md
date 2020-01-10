---
title: Klauzula grupy — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713470"
---
# <a name="group-clause-c-reference"></a>group — Klauzula (odwołanie w C#)

Klauzula `group` zwraca sekwencję obiektów <xref:System.Linq.IGrouping%602>, które zawierają zero lub więcej elementów, które pasują do wartości klucza dla grupy. Na przykład można grupować sekwencję ciągów zgodnie z pierwszą literą w każdym ciągu. W tym przypadku pierwsza litera jest kluczem i ma typ [char](../builtin-types/char.md)i jest przechowywana we właściwości `Key` każdego <xref:System.Linq.IGrouping%602> obiektu. Kompilator wnioskuje typ klucza.

Możesz zakończyć wyrażenie zapytania z klauzulą `group`, jak pokazano w następującym przykładzie:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Jeśli chcesz wykonać dodatkowe operacje zapytań dla każdej grupy, możesz określić tymczasowy identyfikator przy użyciu słowa kluczowego [into](into.md) . Gdy używasz `into`, musisz kontynuować zapytania i ostatecznie zakończyć je za pomocą instrukcji `select` lub innej klauzuli `group`, jak pokazano na poniższym fragmencie fragmentu:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Dokładniejsze przykłady użycia `group` z i bez `into` są podane w przykładowej sekcji tego artykułu.

## <a name="enumerating-the-results-of-a-group-query"></a>Wyliczanie wyników zapytania grupy

Ponieważ obiekty <xref:System.Linq.IGrouping%602> utworzone przez zapytanie `group` są zasadniczo listą list, należy użyć zagnieżdżonej pętli [foreach](foreach-in.md) , aby uzyskać dostęp do elementów w każdej grupie. Pętla zewnętrzna wykonuje iterację na klucze grupy, a pętla wewnętrzna wykonuje iterację nad każdym elementem w samej grupie. Grupa może mieć klucz, ale nie elementy. Poniżej znajduje się pętla `foreach`, która wykonuje zapytanie w poprzednim przykładzie kodu:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Typy kluczy

Klucze grup mogą być dowolnego typu, takich jak ciąg, wbudowany typ liczbowy lub zdefiniowany przez użytkownika typ nazwany lub typ anonimowy.

### <a name="grouping-by-string"></a>Grupowanie według ciągu

W poprzednich przykładach kodu użyto `char`. Zamiast tego można określić klucz ciągu, na przykład pełną nazwę:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Grupowanie według wartości logicznej

W poniższym przykładzie pokazano użycie wartości logicznej dla klucza w celu podzielenia wyników na dwie grupy. Należy zauważyć, że wartość jest generowana przez Podwyrażenie w klauzuli `group`.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Grupowanie według zakresu liczbowego

W następnym przykładzie używane jest wyrażenie do tworzenia liczbowych kluczy grup reprezentujących zakres percentylu. Zwróć uwagę na użycie metody [Let](let-clause.md) jako wygodnej lokalizacji do przechowywania wyniku wywołania metody, tak aby nie trzeba było wywoływać metodę dwa razy w klauzuli `group`. Aby uzyskać więcej informacji o sposobie bezpiecznego używania metod w wyrażeniach zapytań, zobacz temat [Obsługa wyjątków w wyrażeniach zapytań](../../linq/handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Grupowanie według kluczy złożonych

Użyj klucza złożonego, gdy chcesz grupować elementy zgodnie z więcej niż jednym kluczem. Można utworzyć klucz złożony przy użyciu typu anonimowego lub nazwanego typu w celu przechowywania elementu klucza. W poniższym przykładzie Załóżmy, że Klasa `Person` została zadeklarowana z elementami członkowskimi o nazwie `surname` i `city`. Klauzula `group` powoduje utworzenie oddzielnej grupy dla każdego zestawu osób o tej samej nazwie i o tej samej miejscowości.

```csharp
group person by new {name = person.surname, city = person.city};
```

Użyj nazwanego typu, jeśli musisz przekazać zmienną zapytania do innej metody. Utwórz specjalną klasę przy użyciu wstępnie wdrożonych właściwości kluczy, a następnie zastąp metody <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A>. Można również użyć struktury, w tym przypadku nie trzeba przesłonić tych metod. Aby uzyskać więcej informacji, zobacz [jak zaimplementować uproszczoną klasę z zaimplementowanymi właściwościami](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) i [jak wykonywać zapytania dotyczące zduplikowanych plików w drzewie katalogów](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Ten ostatni artykuł zawiera przykład kodu, który demonstruje sposób użycia klucza złożonego z nazwanym typem.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje standardowy wzorzec służący do porządkowania danych źródłowych do grup, gdy żadna dodatkowa logika kwerendy nie zostanie zastosowana do grup. Jest to nazywane grupowaniem bez kontynuacji. Elementy w tablicy ciągów są pogrupowane według ich pierwszej litery. Wynikiem zapytania jest typ <xref:System.Linq.IGrouping%602>, który zawiera publiczną właściwość `Key` typu `char` oraz kolekcję <xref:System.Collections.Generic.IEnumerable%601>, która zawiera wszystkie elementy w grupowaniu.

Wynikiem klauzuli `group` jest sekwencja sekwencji. W związku z tym, aby uzyskać dostęp do poszczególnych elementów w każdej zwróconej grupie, Użyj zagnieżdżonej pętli `foreach` wewnątrz pętli, która iteruje klucze grupy, jak pokazano w poniższym przykładzie.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak wykonać dodatkową logikę dla grup po ich utworzeniu przy użyciu *kontynuacji* `into`. Aby uzyskać więcej informacji, zobacz [do](into.md). Poniższy przykład wysyła zapytanie do każdej grupy, aby wybrać tylko te, których wartość klucza jest samodzielna.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Uwagi

W czasie kompilacji klauzule `group` są tłumaczone na wywołania metody <xref:System.Linq.Enumerable.GroupBy%2A>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [Słowa kluczowe zapytania](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
- [Tworzenie grupy zagnieżdżonej](../../linq/create-a-nested-group.md)
- [Grupowanie wyników zapytania](../../linq/group-query-results.md)
- [Wykonanie podzapytania w operacji grupowania](../../linq/perform-a-subquery-on-a-grouping-operation.md)
