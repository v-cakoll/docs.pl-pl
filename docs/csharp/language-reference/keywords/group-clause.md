---
title: Group — klauzula - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 6c28f9f4cdcb2ec2d84f299dddb13dc821c1739a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238172"
---
# <a name="group-clause-c-reference"></a>group — Klauzula (odwołanie w C#)

`group` Klauzula zwraca sekwencję <xref:System.Linq.IGrouping%602> obiektów zawierających zero lub więcej elementów, które odpowiadają wartości klucza dla grupy. Na przykład można pogrupować sekwencją ciągów, zgodnie z pierwszą literę każdego ciągu. W takim przypadku pierwsza litera jest kluczem i ma typ [char](char.md)i jest przechowywany w `Key` właściwości każdego <xref:System.Linq.IGrouping%602> obiektu. Kompilator wnioskuje typ klucza.

Możesz zakończyć wyrażeniu zapytania z `group` klauzuli, jak pokazano w poniższym przykładzie:

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

Jeśli chcesz wykonać operacje zapytań dodatkowe w każdej grupie, należy określić identyfikator tymczasowy, za pomocą [do](into.md) kontekstowego słowa kluczowego. Kiedy używasz `into`, należy kontynuować z zapytaniem, a po pewnym czasie Zakończ ją albo `select` instrukcji lub innego `group` klauzuli, jak pokazano w poniższym fragmencie:

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

Bardziej kompletne przykłady stosowania `group` z lub bez `into` znajdują się w sekcji przykład tego artykułu.

## <a name="enumerating-the-results-of-a-group-query"></a>Wyliczanie wyników zapytania grupy

Ponieważ <xref:System.Linq.IGrouping%602> obiekty utworzone przez `group` zapytania są zasadniczo listę list, korzystając z zagnieżdżonej [foreach](foreach-in.md) pętli, aby mieć dostęp do elementów w każdej grupie. Zewnętrzna pętla wykonuje iterację na klucze grupy, a wewnętrzną pętlę iteruje przez każdy element w samej grupy. Grupa może mieć klucza, ale żadne elementy. Poniżej przedstawiono `foreach` pętli, która wykonuje zapytanie w poprzednich przykładach kodu:

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>Typy kluczy

Klucze grupy mogą być dowolnego typu, takie jak ciąg, wbudowanego typu liczbowego lub zdefiniowanej przez użytkownika o nazwie typu lub typu anonimowego.

### <a name="grouping-by-string"></a>Grupowanie według ciągu

W poprzednich przykładach kodu używany `char`. Klucza typu ciąg można łatwo określono zamiast tego, na przykład Pełna nazwa ostatnich:

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>Grupowanie według bool

Poniższy przykład pokazuje użycie wartość bool klawisz aby podzielić wyniki na dwie grupy. Należy pamiętać, że wartość jest generowany przez Podwyrażenie w `group` klauzuli.

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>Grupowanie według zakresu liczbowego

W następnym przykładzie użyto wyrażenia, aby utworzyć klucze grupy numeryczne, które reprezentują zakres percentyl. Zwróć uwagę na użycie [umożliwiają](let-clause.md) jako wygodną lokalizację do przechowywania metodę wywołania wynik, dzięki czemu nie trzeba wywoływać metodę dwa razy w `group` klauzuli. Aby uzyskać więcej informacji o tym, jak bezpiecznie używać metod w wyrażeniach zapytań, zobacz [jak: Obsługa wyjątków w wyrażeniach zapytań](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>Grupowanie według kluczy złożonych

Umożliwia grupowanie elementów według więcej niż jeden klucz za pomocą klucza złożonego. Klucz złożony możesz utworzyć przy użyciu typu anonimowego lub typem nazwanym do przechowywania klucza elementu. W poniższym przykładzie przyjęto założenie, że klasa `Person` został zadeklarowany za pomocą elementów członkowskich o nazwie `surname` i `city`. `group` Klauzuli powoduje, że ma zostać utworzony dla każdego zestawu osób z tej samej nazwisko i tym samym mieście osobnej grupy.

```csharp
group person by new {name = person.surname, city = person.city};
```

Jeśli zmienna zapytania musi pomyślnie przejść do innej metody, należy użyć typu nazwanego. Utwórz klasę specjalnych kluczy przy użyciu automatycznie implementowanych właściwości, a następnie zastąpić <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody. Można również użyć struktury, w którym to przypadku ściśle trzeba zastąpić te metody. Aby uzyskać więcej informacji, zobacz [jak: Implementowanie klasy Lightweight przy użyciu automatycznie implementowanych właściwości](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) i [jak: Zapytanie o zduplikowane pliki w drzewie katalogu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Ostatni artykuł zawiera przykładowy kod, który demonstruje sposób skorzystania z kluczem złożonym z typem nazwanym.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje standardowego wzorca porządkowania danych źródłowych w grupach, stosowania logiki nie dodatkowych zapytania do grup. Jest to grupa bez kontynuacji. Elementy w tablicy ciągów są pogrupowane według ich pierwszą literę. Wynik zapytania jest <xref:System.Linq.IGrouping%602> typu, który zawiera publiczny `Key` właściwości typu `char` i <xref:System.Collections.Generic.IEnumerable%601> kolekcji, która zawiera każdy element na grupowanie.

Wynik `group` klauzula jest sekwencji. W związku z tym, aby uzyskać dostęp do poszczególnych elementów w każdej grupie zwrócone, użyj zagnieżdżoną `foreach` pętli wewnątrz pętli, który iteruje po klucze grupy, jak pokazano w poniższym przykładzie.

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono sposób wykonywania dodatkowej logiki w grupach, po ich utworzeniu, za pomocą *kontynuacji* z `into`. Aby uzyskać więcej informacji, zobacz [do](into.md). Poniższy przykład wysyła zapytanie do każdej grupy, aby wybrać tylko te, których wartość klucza jest samogłosek.

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>Uwagi

W czasie kompilacji `group` klauzule są tłumaczone na wywołania <xref:System.Linq.Enumerable.GroupBy%2A> metody.

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
