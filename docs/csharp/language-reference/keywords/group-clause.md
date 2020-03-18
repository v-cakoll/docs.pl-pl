---
title: klauzula grupy — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713470"
---
# <a name="group-clause-c-reference"></a>group — Klauzula (odwołanie w C#)

Klauzula `group` zwraca sekwencję <xref:System.Linq.IGrouping%602> obiektów, które zawierają zero lub więcej elementów, które pasują do wartości klucza dla grupy. Na przykład można grupować sekwencję ciągów zgodnie z pierwszą literą w każdym ciągu. W takim przypadku pierwsza litera jest kluczem i ma [znak](../builtin-types/char.md)typu i jest przechowywana we `Key` właściwości każdego <xref:System.Linq.IGrouping%602> obiektu. Kompilator wywnioskuje typ klucza.

Wyrażenie kwerendy można zakończyć `group` klauzulą, jak pokazano w poniższym przykładzie:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Jeśli chcesz wykonać dodatkowe operacje kwerendy dla każdej grupy, możesz określić tymczasowy identyfikator za pomocą słowa kluczowego [w](into.md) kontekście. Użycie `into`należy kontynuować kwerendę, a następnie zakończyć ją `select` instrukcją `group` lub inną klauzulą, jak pokazano w poniższym fragmencie:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Pełniejsze przykłady użycia `group` z i `into` bez znajdują się w sekcji Przykład tego artykułu.

## <a name="enumerating-the-results-of-a-group-query"></a>Wyliczanie wyników kwerendy grupowej

Ponieważ <xref:System.Linq.IGrouping%602> obiekty tworzone `group` przez kwerendę są zasadniczo listę list, należy użyć zagnieżdżonych [foreach](foreach-in.md) pętli, aby uzyskać dostęp do elementów w każdej grupie. Zewnętrzna pętla itere nad kluczami grupy, a wewnętrzna pętla iteuje nad każdym elementem w samej grupie. Grupa może mieć klucz, ale nie ma elementów. Poniżej przedstawiono `foreach` pętlę, która wykonuje kwerendę w poprzednich przykładach kodu:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Typy kluczy

Klucze grupy mogą być dowolnym typem, takim jak ciąg, wbudowany typ liczbowy lub zdefiniowany przez użytkownika nazwany typ lub typ anonimowy.

### <a name="grouping-by-string"></a>Grupowanie według ciągów

W poprzednich przykładach `char`kodu użyto pliku . Zamiast tego można łatwo określić klucz ciągu, na przykład pełne nazwisko:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Grupowanie według bool

W poniższym przykładzie przedstawiono użycie wartości bool dla klucza, aby podzielić wyniki na dwie grupy. Należy zauważyć, że wartość jest tworzona `group` przez wyrażenie podrzędne w klauzuli.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Grupowanie według zakresu liczbowego

W następnym przykładzie użyto wyrażenia do utworzenia kluczy grupy numerycznej, które reprezentują zakres percentyla. Należy zwrócić uwagę na użycie [let](let-clause.md) jako dogodną lokalizację do przechowywania wyniku wywołania metody, dzięki czemu nie trzeba wywołać metodę dwa razy w klauzuli. `group` Aby uzyskać więcej informacji na temat bezpiecznego używania metod w wyrażeniach kwerend, zobacz [Obsługa wyjątków w wyrażeniach kwerend .](../../linq/handle-exceptions-in-query-expressions.md)

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Grupowanie według kluczy złożonych

Klucz złożony należy użyć, aby pogrupować elementy zgodnie z więcej niż jednym kluczem. Klucz złożony można utworzyć przy użyciu typu anonimowego lub nazwanego typu do przechowywania elementu klucza. W poniższym przykładzie załóżmy, że `Person` klasa `surname` `city`została zadeklarowana z członkami o nazwie i . Klauzula `group` powoduje utworzenie oddzielnej grupy dla każdego zestawu osób o tym samym nazwisku i tym samym mieście.

```csharp
group person by new {name = person.surname, city = person.city};
```

Użyj nazwanego typu, jeśli zmienna kwerendy musi zostać przekazana innej metodzie. Utwórz specjalną klasę przy użyciu właściwości implementowane automatycznie dla <xref:System.Object.Equals%2A> kluczy, a następnie zastąpić i <xref:System.Object.GetHashCode%2A> metody. Można również użyć struktury, w którym to przypadku nie trzeba ściśle zastąpić te metody. Aby uzyskać więcej informacji, zobacz [Jak zaimplementować klasę lekką z właściwościami zaimplementowanymi automatycznie](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) i Jak [wysyłać zapytania o zduplikowane pliki w drzewie katalogów](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Ten ostatni artykuł zawiera przykład kodu, który pokazuje, jak używać klucza złożonego o nazwanym typie.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono standardowy wzorzec do porządkowania danych źródłowych w grupy, gdy do grup nie jest stosowana żadna dodatkowa logika kwerendy. Nazywa się to grupowaniem bez kontynuacji. Elementy w tablicy ciągów są grupowane według ich pierwszej litery. Wynik kwerendy jest <xref:System.Linq.IGrouping%602> typem, który `Key` zawiera `char` właściwość <xref:System.Collections.Generic.IEnumerable%601> publiczną typu i kolekcji, która zawiera każdy element w grupowaniu.

Wynik `group` klauzuli jest sekwencja sekwencji. W związku z tym, aby uzyskać dostęp do `foreach` poszczególnych elementów w każdej zwróconej grupy, należy użyć pętli zagnieżdżonej wewnątrz pętli, która iteruje klucze grupy, jak pokazano w poniższym przykładzie.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak wykonać dodatkową logikę na grupach po ich utworzeniu, przy użyciu *kontynuacji* z . `into` Aby uzyskać więcej informacji, zobacz [w](into.md). Poniższy przykład wysyła kwerendy każdej grupy, aby wybrać tylko te, których wartość klucza jest samogłoska.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Uwagi

W czasie kompilacji `group` klauzule są tłumaczone <xref:System.Linq.Enumerable.GroupBy%2A> na wywołania metody.

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [Słowa kluczowe zapytania](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
- [Tworzenie grupy zagnieżdżonej](../../linq/create-a-nested-group.md)
- [Grupowanie wyników zapytania](../../linq/group-query-results.md)
- [Wykonywanie podzapytania w operacji grupowania](../../linq/perform-a-subquery-on-a-grouping-operation.md)
