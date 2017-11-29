---
title: "group — Klauzula (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a2f67b2c90e1cced92d6fc7d47768b58bf155360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="group-clause-c-reference"></a>group — Klauzula (odwołanie w C#)
`group` Klauzula zwraca sekwencji <xref:System.Linq.IGrouping%602> obiektów zawierających zero lub więcej elementów, które odpowiadają wartości klucza dla grupy. Na przykład można grupować sekwencję ciągi zgodnie z pierwszej litery każdego ciągu. W takim przypadku pierwszą literę jest klucz i ma typ [char](../../../csharp/language-reference/keywords/char.md)i są przechowywane w `Key` właściwości każdego <xref:System.Linq.IGrouping%602> obiektu. Kompilator wnioskuje typ klucza.  
  
 Możesz zakończyć wyrażeniu zapytania z `group` klauzuli, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 Jeśli chcesz wykonać operacje kwerend dodatkowe w każdej grupie, można określić identyfikator tymczasowy przy użyciu [do](../../../csharp/language-reference/keywords/into.md) kontekstowe słowo kluczowe. Jeśli używasz `into`, należy kontynuować z zapytaniem, a ostatecznie Zakończ ją przy użyciu jednej `select` instrukcji lub innym `group` klauzuli, jak pokazano w poniższym fragmencie:  
  
 [!code-csharp[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 Więcej ukończyć przykłady stosowania `group` z włączonymi i wyłączonymi `into` znajdują się w sekcji przykład tego tematu.  
  
## <a name="enumerating-the-results-of-a-group-query"></a>Wyliczanie wyników zapytania grupy  
 Ponieważ <xref:System.Linq.IGrouping%602> obiekty utworzone przez `group` zapytania są zasadniczo listę list, należy użyć zagnieżdżoną [foreach](../../../csharp/language-reference/keywords/foreach-in.md) pętli dostęp do elementów w każdej grupie. Zewnętrzne pętli wykonuje iterację na klucze grupy, a wewnętrzny pętli przechodzi przez każdego elementu w samej grupy. Grupa może mieć klucza, ale nie elementy. Poniżej przedstawiono `foreach` pętli, które wykonuje zapytanie w poprzednich przykładach kodu:  
  
 [!code-csharp[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## <a name="key-types"></a>Typy kluczy  
 Klucze grupy mogą być dowolnego typu, takie jak ciąg, wbudowanego typu liczbowego lub zdefiniowane przez użytkownika o nazwie lub typu anonimowego.  
  
### <a name="grouping-by-string"></a>Grupowanie według ciągu  
 W poprzednich przykładach kodu używany `char`. Klucz ciągu można łatwo zostały określone, na przykład Pełna nazwa ostatniego:  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### <a name="grouping-by-bool"></a>Grupowanie według wartości logicznej  
 Poniższy przykład przedstawia użycie wartości bool klucza do dzielenia wyników na dwie grupy. Należy pamiętać, że wartość jest generowany przez wyrażenia podrzędnego w `group` klauzuli.  
  
 [!code-csharp[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### <a name="grouping-by-numeric-range"></a>Grupowanie według zakresu numerycznego  
 W następnym przykładzie użyto wyrażenia do tworzenia kluczy grupy liczbowego, reprezentujące procentowy zakres. Zwróć uwagę na użycie [let](../../../csharp/language-reference/keywords/let-clause.md) jako wygodną lokalizację do przechowywania metodę wywołania wyników, dzięki czemu nie trzeba wywołać metodę dwa razy w `group` klauzuli. Należy pamiętać, również w `group` klauzuli, aby uniknąć wyjątek "dzielenie przez zero" kod sprawdza do upewnij się, że student średnią wartość zero. Aby uzyskać więcej informacji na temat bezpiecznego używania metod w wyrażeniach zapytań, zobacz [porady: obsługa wyjątków w wyrażeniach kwerend](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).  
  
 [!code-csharp[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### <a name="grouping-by-composite-keys"></a>Grupowanie według kluczy złożonych  
 Umożliwia grupowanie elementów według więcej niż jednego klucza, należy użyć klucza złożonego. Tworzysz złożonych kluczy przy użyciu typu anonimowego lub typ nazwany do przechowywania klucza elementu. W poniższym przykładzie przyjęto założenie, że klasa `Person` została zadeklarowana z elementami członkowskimi o nazwie `surname` i `city`. `group` Klauzuli powoduje osobnej grupy dla każdego zestawu osób z tej samej nazwie ostatniego i tego samego miasta.  
  
```csharp  
group person by new {name = person.surname, city = person.city};  
```  
  
 Użyj typu nazwanego, jeśli należy przekazać do zmiennej zapytania do innej metody. Utwórz klasę specjalne przy użyciu automatycznie implementowanych właściwości kluczy, a następnie zastąpić <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody. Umożliwia także struktury, w tym przypadku nie ściśle masz zastąpić tych metod. Aby uzyskać więcej informacji, zobacz [porady: Implementowanie klasy Lightweight przy użyciu właściwości Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) i [porady: zapytanie o zduplikowane pliki w drzewie katalogu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md). Ostatnie temat zawiera przykładowy kod, który demonstruje sposób użycia klucza złożonego z nazwanym typem.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono standardowe wzorzec porządkowania źródło danych w grupach, gdy logiki nie dodatkowe zapytania jest stosowany do grup. Jest to grupa bez utrzymania. Elementy w tablicy ciągów są pogrupowane według ich pierwszą literę. Wynik kwerendy jest <xref:System.Linq.IGrouping%602> typu, który zawiera publicznego `Key` właściwości typu `char` i <xref:System.Collections.Generic.IEnumerable%601> kolekcji zawierającej każdego elementu w grupowaniu.  
  
 Wynik `group` klauzuli jest sekwencją sekwencji. W związku z tym, aby uzyskać dostęp do poszczególnych elementów w każdej grupie zwrócone, użyj zagnieżdżoną `foreach` pętli wewnątrz pętli, który iteruje po klucze grupy, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak wykonać dodatkową logikę w grupach, po ich utworzeniu, za pomocą *kontynuacji* z `into`. Aby uzyskać więcej informacji, zobacz [do](../../../csharp/language-reference/keywords/into.md). Poniższy przykład wysyła zapytanie do każdej grupy, aby wybrać tylko te, których wartości klucza jest samogłoskę.  
  
 [!code-csharp[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## <a name="remarks"></a>Uwagi  
 W czasie kompilacji `group` klauzule są przetłumaczyć wywołań <xref:System.Linq.Enumerable.GroupBy%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.IGrouping%602>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.Enumerable.ThenBy%2A>  
 <xref:System.Linq.Enumerable.ThenByDescending%2A>  
 [Słowa kluczowe zapytania (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Porady: tworzenie grup zagnieżdżonych](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [Porady: grupowanie wyników kwerendy](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [Porady: wykonanie podzapytania w operacji grupowania](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
