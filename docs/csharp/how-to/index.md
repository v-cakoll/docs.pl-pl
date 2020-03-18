---
title: Jak artykuły (C# Przewodnik)
description: Zbiór szybkich wskazówek i krótkich, ukierunkowanych próbek kodu
ms.date: 12/20/2017
ms.openlocfilehash: e6cb657726b82a1710bbcd596fe48037b5c26352
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399323"
---
# <a name="how-to-c"></a>Jak (C#)

W sekcji Jak przewodnik po języku C#można znaleźć szybkie odpowiedzi na często zadawane pytania. W niektórych przypadkach artykuły mogą być wymienione w wielu sekcjach. Chcieliśmy, aby były łatwe do znalezienia dla wielu ścieżek wyszukiwania.

## <a name="general-c-concepts"></a>Ogólne pojęcia języka C#

Istnieje kilka wskazówek i wskazówek, które są typowe praktyki dewelopera Języka C#:

- [Inicjowanie obiektów przy użyciu inicjatora obiektów](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Poznaj różnice między przekazywaniem struktury a klasą do metody](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Użyj przeciążenia operatora](../language-reference/operators/operator-overloading.md).
- [Implementowanie i wywoływanie niestandardowej metody rozszerzenia](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Nawet programiści języka C# mogą chcieć [użyć przestrzeni `My` nazw z języka Visual Basic.](../programming-guide/namespaces/how-to-use-the-my-namespace.md)
- [Utwórz nową metodę `enum` dla typu przy użyciu metod rozszerzenia](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Członkowie klasy i struktury

Tworzenie klas i struktur do zaimplementowania programu. Techniki te są powszechnie używane podczas pisania klas lub struktur.

- [Deklaruj właściwości zaimplementowane automatycznie](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Deklaruj i użyj właściwości odczytu/zapisu](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Zdefiniuj stałe](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Zastąp `ToString` metodę, aby zapewnić dane wyjściowe ciągu](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Zdefiniuj właściwości abstrakcyjne](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Użyj funkcji dokumentacji xml, aby udokumentować kod](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Jawnie implementuj elementy członkowskie interfejsu,](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) aby zachować zwięzły interfejs publiczny.
- [Jawnie implementuj elementy członkowskie dwóch interfejsów](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Praca z kolekcjami

Te artykuły ułatwiają pracę z kolekcjami danych.

- [Inicjuj słownik z inicjatora kolekcji](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Praca z ciągami

Ciągi są podstawowym typem danych używanym do wyświetlania lub manipulowania tekstem. Te artykuły wykazują typowe praktyki z ciągami.

- [Porównaj ciągi](compare-strings.md)znaków .
- [Modyfikowanie zawartości ciągu](modify-string-contents.md).
- [Określ, czy ciąg reprezentuje liczbę](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Służy `String.Split` do oddzielania ciągów](parse-strings-using-split.md).
- [Połącz wiele ciągów w jeden](concatenate-multiple-strings.md).
- [Wyszukiwanie tekstu w ciągu](search-strings.md).

## <a name="convert-between-types"></a>Konwertowanie między typami

Może być konieczne przekonwertowanie obiektu na inny typ.

- [Określ, czy ciąg reprezentuje liczbę](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Konwertuj między ciągami reprezentującymi liczby szesnastkowe a liczbą](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Konwertowanie ciągu `DateTime`na plik ](../../standard/base-types/parsing-datetime.md).
- [Konwertowanie tablicy bajtów na int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Konwertowanie ciągu na liczbę](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Użyj dopasowania wzorców, `as` operatorów i `is` bezpiecznie rzutować na inny typ](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).
- [Zdefiniuj konwersje typu niestandardowego](../language-reference/operators/user-defined-conversion-operators.md).
- [Określ, czy typ jest typem wartości nullable](../language-reference/builtin-types/nullable-value-types.md#how-to-identify-a-nullable-value-type).
- [Konwersja między typami wartości nullable i non-nullable](../language-reference/builtin-types/nullable-value-types.md#conversion-from-a-nullable-value-type-to-an-underlying-type).

## <a name="equality-and-ordering-comparisons"></a>Równość i porządkowanie porównań

Można utworzyć typy, które definiują własne reguły równości lub zdefiniować naturalną kolejność między obiektami tego typu.

- [Test równości opartej na odniesieniach](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Definiowanie równości opartej na wartości dla typu](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Obsługa wyjątków

Programy .NET zgłaszają, że metody nie zakończyły się pomyślnie ich pracy, zgłaszając wyjątki. W tych artykułach dowiesz się pracować z wyjątkami.

- [Obsługa wyjątków `try` `catch`przy użyciu i ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Oczyszczanie zasobów `finally` przy użyciu klauzul](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Odzyskiwanie z wyjątków innych niż CLS (Common Language Specification).](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md)

## <a name="delegates-and-events"></a>Delegaci i wydarzenia

Delegatów i zdarzenia zapewniają możliwość dla strategii, które obejmują luźno sprzętych bloków kodu.

- [Deklaruj, tworzy jonów i używaj delegatów](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Połącz delegatów multiemisji](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Zdarzenia zapewniają mechanizm publikowania lub subskrybowania powiadomień.

- [Subskrybuj i anuluj subskrypcję wydarzeń.](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
- [Implementowanie zdarzeń zadeklarowanych w interfejsach](../programming-guide/events/how-to-implement-interface-events.md).
- [Są zgodne z wytycznymi programu .NET Framework, gdy kod publikuje zdarzenia](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Podnieść zdarzenia zdefiniowane w klasach podstawowych z klas pochodnych](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Zaimplementuj niestandardowe akcesory zdarzeń](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>Praktyki LINQ

LINQ umożliwia pisanie kodu do kwerendy dowolnego źródła danych, który obsługuje wzorzec wyrażenia kwerendy LINQ. Te artykuły pomagają zrozumieć wzorzec i pracować z różnymi źródłami danych.

- [Zapytanie do kolekcji](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Użyj wyrażeń lambda w kwerendzie](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Użyj `var` w wyrażeniach kwerend .](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Zwraca podzestawy właściwości elementu z kwerendy](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Napisz zapytania ze złożonym filtrowaniem](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Sortuj elementy źródła danych](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Sortuj elementy na wielu klawiszach](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Sterować typem projekcji](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Zliczanie wystąpień wartości w sekwencji źródłowej](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Oblicz wartości pośrednie](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Scalanie danych z wielu źródeł](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Znajdź różnicę między dwiema sekwencjami](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Debuguj puste wyniki kwerendy](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Dodaj metody niestandardowe do zapytań LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Wiele wątków i przetwarzanie asynchroniczne

Nowoczesne programy często używają operacji asynchronicznych. Te artykuły pomogą Ci nauczyć się korzystać z tych technik.

- [Zwiększ wydajność asynchroniczną przy użyciu programu `System.Threading.Tasks.Task.WhenAll` ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Należy tworzyć wiele `async` żądań `await`sieci Web równolegle przy użyciu i ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Użyj puli wątków](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Args wiersza polecenia do programu

Zazwyczaj programy Języka C# mają argumenty wiersza polecenia. Artykuły te uczą dostępu i przetwarzania tych argumentów wiersza polecenia.

- [Pobierz wszystkie argumenty `for`wiersza polecenia za pomocą pliku ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
