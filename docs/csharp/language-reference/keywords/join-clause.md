---
title: klauzula sprzężenia — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: 8e52e9db241392b67818b7316767dd97bd38432a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713407"
---
# <a name="join-clause-c-reference"></a>Klauzula join (odwołanie w C#)

Klauzula `join` jest przydatna do kojarzenia elementów z różnych sekwencji źródłowych, które nie mają bezpośredniej relacji w modelu obiektu. Jedynym wymaganiem jest to, że elementy w każdym źródle mają pewną wartość, którą można porównać dla równości. Na przykład dystrybutor żywności może mieć listę dostawców określonego produktu i listę kupujących. Klauzula `join` może służyć, na przykład, aby utworzyć listę dostawców i nabywców tego produktu, którzy są w tym samym określonym regionie.

Klauzula `join` przyjmuje dwie sekwencje źródłowe jako dane wejściowe. Elementy w każdej sekwencji musi być lub zawierać właściwość, która może być porównywana z odpowiednią właściwość w innej sekwencji. Klauzula `join` porównuje określone klucze równości przy `equals` użyciu specjalnego słowa kluczowego. Wszystkie sprzężenia wykonywane `join` przez klauzulę są równoważne. Kształt danych wyjściowych `join` klauzuli zależy od określonego typu sprzężenia, które wykonujesz. Oto trzy najczęściej spotykane typy sprzężenia:

- Sprzężenie wewnętrzne

- Dołączanie do grupy

- Lewe sprzężenie zewnętrzne

## <a name="inner-join"></a>Sprzężenie wewnętrzne

W poniższym przykładzie przedstawiono prosty wewnętrzny przyłączyć. To zapytanie tworzy płaską sekwencję par "nazwa produktu / kategoria". Ten sam ciąg kategorii pojawi się w wielu elementach. Jeśli element `categories` z nie `products`ma dopasowania , tej kategorii nie pojawi się w wynikach.

[!code-csharp[cscsrefQueryKeywords#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#24)]

Aby uzyskać więcej informacji, zobacz [Wykonywanie sprzężeń wewnętrznych](../../linq/perform-inner-joins.md).

## <a name="group-join"></a>Dołączanie do grupy

Klauzula `join` z `into` wyrażeniem jest nazywany sprzężenia grupy.

[!code-csharp[cscsrefQueryKeywords#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#25)]

Sprzężenie grupy tworzy hierarchiczną sekwencję wyników, która kojarzy elementy w lewej sekwencji źródłowej z co najmniej jednym pasującym elementem w prawej sekwencji źródłowej po prawej stronie. Dołączanie do grupy nie ma odpowiednika w kategoriach relacyjnych; jest to zasadniczo sekwencja tablic obiektów.

Jeśli żadne elementy z prawej sekwencji źródłowej nie zostaną `join` znalezione tak, aby pasowały do elementu w lewym źródle, klauzula spowoduje wygenerowanie pustej tablicy dla tego elementu. W związku z tym sprzężenia grupy jest nadal w zasadzie wewnętrznej równołączyć z tą różnicą, że sekwencja wyników jest zorganizowana w grupy.

Jeśli po prostu wybierzesz wyniki sprzężenia grupy, możesz uzyskać dostęp do elementów, ale nie możesz zidentyfikować klucza, który pasują do nich. W związku z tym jest ogólnie bardziej przydatne, aby wybrać wyniki połączenia grupy do nowego typu, który ma również nazwę klucza, jak pokazano w poprzednim przykładzie.

Można również, oczywiście, użyć wyniku sprzężenia grupy jako generator innej podkwerendy:

[!code-csharp[cscsrefQueryKeywords#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#26)]

Aby uzyskać więcej informacji, zobacz [Wykonywanie sprzężeń grupowanych](../../linq/perform-grouped-joins.md).

## <a name="left-outer-join"></a>Lewe sprzężenie zewnętrzne

W lewym sprzężeniu zewnętrznym wszystkie elementy w lewej sekwencji źródłowej są zwracane, nawet jeśli żadne pasujące elementy znajdują się w odpowiedniej kolejności. Aby wykonać sprzężenie zewnętrzne lewe `DefaultIfEmpty` w LINQ, należy użyć metody w połączeniu z sprzężenia grupy, aby określić domyślny element po prawej stronie do produkcji, jeśli element po lewej stronie nie ma dopasowania. Jako wartość `null` domyślną można użyć jako wartości domyślnej dla dowolnego typu odwołania lub można określić typ domyślny zdefiniowany przez użytkownika. W poniższym przykładzie wyświetlany jest typ domyślny zdefiniowany przez użytkownika:

[!code-csharp[cscsrefQueryKeywords#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#27)]

Aby uzyskać więcej informacji, zobacz [Wykonywanie sprzężeń zewnętrznych .](../../linq/perform-left-outer-joins.md)

## <a name="the-equals-operator"></a>Operator równych sobie

Klauzula `join` wykonuje przyłączyć. Innymi słowy można tylko oprzeć dopasowania na równości dwóch kluczy. Inne rodzaje porównań, takie jak "większe niż" lub "nie równa się" nie są obsługiwane. Aby wyjaśnić, że wszystkie sprzężenia `join` są równorzędne, klauzula używa słowa kluczowego `equals` zamiast `==` operatora. Słowo `equals` kluczowe może być `join` używane tylko w klauzuli i różni się od `==` operatora w jeden ważny sposób. Z `equals`, lewy klucz zużywa sekwencję źródła zewnętrznego, a prawy klucz zużywa źródło wewnętrzne. Zewnętrzne źródło znajduje się tylko w `equals` zakresie po lewej stronie, a sekwencja źródła wewnętrznego znajduje się tylko w zakresie po prawej stronie.

## <a name="non-equijoins"></a>Nierównowatki

Można wykonywać non-joinjoins, sprzężenia krzyżowego i innych `from` operacji sprzężenia niestandardowego przy użyciu wielu klauzul do wprowadzania nowych sekwencji niezależnie do kwerendy. Aby uzyskać więcej informacji, zobacz [Wykonywanie operacji sprzężenia niestandardowego](../../linq/perform-custom-join-operations.md).

## <a name="joins-on-object-collections-vs-relational-tables"></a>Sprzężenia w kolekcjach obiektów a tabele relacyjne

W wyrażeniu kwerendy LINQ operacje sprzężenia są wykonywane w kolekcjach obiektów. Kolekcje obiektów nie mogą być "połączone" w dokładnie taki sam sposób, jak dwie tabele relacyjne. W LINQ `join` jawne klauzule są wymagane tylko wtedy, gdy dwie sekwencje źródłowe nie są powiązane przez żadną relację. Podczas pracy [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]z , tabele kluczy obcych są reprezentowane w modelu obiektu jako właściwości tabeli podstawowej. Na przykład w bazie danych Northwind tabela Customer ma relację klucza obcego z tabelą Zamówienia. Podczas mapowania tabel do modelu obiektu, Customer klasy ma Orders właściwość, która zawiera kolekcję zamówień skojarzonych z tym klientem. W efekcie sprzężenie zostało już wykonane dla Ciebie.

Aby uzyskać więcej informacji na temat wykonywania zapytań w powiązanych tabelach [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]w kontekście , zobacz [Jak: Mapowanie relacji bazy danych](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).

## <a name="composite-keys"></a>Klawisze kompozytowe

Można przetestować pod kątem równości wielu wartości przy użyciu klucza złożonego. Aby uzyskać więcej informacji, zobacz [Dołączanie przy użyciu kluczy złożonych](../../linq/join-by-using-composite-keys.md). Klucze złożone mogą być `group` również używane w klauzuli.

## <a name="example"></a>Przykład

W poniższym przykładzie porównano wyniki sprzężenia wewnętrznego, sprzężenia grupy i sprzężenia zewnętrznego w tym samym źródle danych przy użyciu tych samych pasujących kluczy. Niektóre dodatkowe kodu jest dodawany do tych przykładów, aby wyjaśnić wyniki na wyświetlaczu konsoli.

[!code-csharp[cscsrefQueryKeywords#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Join.cs#23)]

## <a name="remarks"></a>Uwagi

Klauzula, `join` która nie `into` jest następnie <xref:System.Linq.Enumerable.Join%2A> jest tłumaczone na wywołanie metody. Klauzula, `join` która `into` następuje jest <xref:System.Linq.Enumerable.GroupJoin%2A> tłumaczone na wywołanie metody.

## <a name="see-also"></a>Zobacz też

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
