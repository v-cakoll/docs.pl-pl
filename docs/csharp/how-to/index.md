---
title: Jak artykuły (Przewodnik C#)
description: Kolekcja krótkie wskazówki i przykłady kodu krótkie, ukierunkowanych
ms.date: 12/20/2017
ms.openlocfilehash: b8164abd84647fc9118acc6e0b84e7fd46838fe9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-c"></a>Jak (C#)

W sposób przewodniku C# można znaleźć szybkich odpowiedzi na często zadawane pytania. W niektórych przypadkach artykuły mogą być wyświetlone w wielu sekcjach. Możemy były łatwe do odnalezienia wielu ścieżek wyszukiwania. 

## <a name="general-c-concepts"></a>Koncepcje ogólne C#

Istnieje kilka porady i wskazówki, które są typowe rozwiązania developer C#.

- [Inicjowanie obiektów za pomocą inicjatora obiektów](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Dowiedz się różnic między przekazywaniem struktury i klasy do metody](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Jak używać wyrażenia lambda](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).
- [Rozwiązywanie konfliktów nazw typu za pomocą aliasu globalnej przestrzeni nazw](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [Przeładowanie operatora użyj](../programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).
- [Implementowanie i wywołanie niestandardowej metody rozszerzenia](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Możesz nawet programistów C# [użyj `My` przestrzeni nazw z VB](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [Utwórz nową metodę `enum` typu przy użyciu metod rozszerzenia](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Elementy członkowskie klasy i struktury

Możesz utworzyć, klasy i struktury do wykonania programu. Te techniki są często używane podczas zapisywania klasy lub struktury.

- [Deklarowanie właściwości zaimplementowane automatycznie](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Deklarowanie i użycie właściwości odczytu/zapisu](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Definiowanie stałych](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Zastąpienie `ToString` metodę w celu zapewnienia ciąg w danych wyjściowych](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Definiowanie właściwości abstrakcyjnych](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Użycie funkcji dokumentacji xml do dokumentów kodu](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Jawne Implementowanie elementów interfejsu](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) do zachowania zwięzły publicznego interfejsu.
- [Jawne Implementowanie elementów dwóch interfejsów](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Praca z kolekcjami

Te artykuły ułatwiają pracę z kolekcji danych.

- [Inicjowanie słownika przy użyciu inicjatora kolekcji](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).
- [Dostęp do wszystkich elementów w kolekcji przy użyciu `foreach` ](../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).

## <a name="strings"></a>ciągi

Ciągi to podstawowy typ danych używany do wyświetlania lub modyfikowania tekstu. Te artykuły pokazują typowe rozwiązania z ciągami.

- [Porównywanie ciągów](compare-strings.md).
- [Modyfikowanie zawartości ciągu](modify-string-contents.md).
- [Określanie, czy ciąg reprezentuje liczbę](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Użyj `String.Split` do rozdzielania ciągów](parse-strings-using-split.md).
- [Łączenie wielu ciągów w jednym](concatenate-multiple-strings.md).
- [Wyszukaj tekst w ciągu](search-strings.md).

## <a name="convert-between-types"></a>Konwertowanie typów

Konieczne może być konwersji obiektu do innego typu.

- [Określanie, czy ciąg reprezentuje liczbę](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Konwertowanie ciągów, które reprezentują szesnastkowe numer](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Konwertowanie ciągu do `DateTime` ](../../standard/base-types/parsing-datetime.md).
- [Konwertowanie tablicy typu byte na liczbę całkowitą](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Konwertowanie ciągu na liczbę](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Użyj `as` i `is` można bezpiecznie rzutowany na inny typ](../programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).
- [Zdefiniuj operatory konwersji dla `struct` typów](../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md).
- [Określa, czy typem jest typ wartości null](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md).
- [Konwertowanie typów wartości null i nie dopuszcza wartości null](../programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).

## <a name="equality-and-ordering-comparisons"></a>Równość i porównania porządkowania

Może tworzyć typy, które definiować własne zasady równości lub zdefiniuj kolejność fizyczną między obiekty tego typu.

- [Testowanie równości odwołania na](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Definiowanie wartości na podstawie równości dla typu](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Obsługa wyjątków

Programy .NET raport, że metody nie ukończył pracy przez zgłaszanie wyjątków. W tych artykułach dowiesz się pracować z wyjątków.

- [Obsługa wyjątków za pomocą `try` i `catch` ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Oczyszczanie zasobów przy użyciu `finally` klauzule](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Odzyskiwanie ze specyfikacją CLS (Common Language Specification) wyjątki](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Delegaci i zdarzenia

Delegaci i zdarzenia zapewniają możliwość strategie, których dotyczą luźno powiązane bloków kodu.

- [Deklarowanie, tworzenie wystąpień i używać delegatów](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Łączenie obiektów delegowanych multiemisji](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Zdarzenia udostępniają mechanizm umożliwiający publikowanie lub subskrypcja notyfikacji.

- [Subskrybowanie i anulowanie subskrypcji zdarzeń](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Wdrożenie w zdarzeniach deklarowanych w interfejsach](../programming-guide/events/how-to-implement-interface-events.md).
- [Być zgodne z zasadami .NET Framework, gdy kod publikuje zdarzenia](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Wywoływanie zdarzeń zdefiniowanych w klasach podstawowych z klas pochodnych](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Przechowywania wystąpień zdarzeń w słowniku](../programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md).
- [Implementowanie niestandardowych metod dostępu zdarzeń](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>Wskazówki LINQ

LINQ umożliwia pisanie kodu do badania wszystkie źródła danych, które obsługuje wzorzec wyrażenia zapytań LINQ. Te artykuły pomogą lepiej poznać wzorce i pracować z różnych źródeł danych.

- [Kwerenda dotycząca kolekcji](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Użycie wyrażeń lambda w kwerendzie](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Użyj `var` w wyrażeniach zapytań](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Zwracanie podzbiorów właściwości elementu w wyniku zapytania](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Pisać zapytania za pomocą filtrowania złożonych](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Sortowanie elementów źródła danych](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Sortowanie elementów na wielu kluczy](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Kontrolowanie typu projekcji](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Liczba wystąpień wartości w sekwencji źródłowej](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Obliczania wartości pośrednich](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Scalanie danych z wielu źródeł](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Znajdowanie różnicy pomiędzy dwoma sekwencji](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Debugowanie wyników zapytania pusty](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Dodawanie metod niestandardowych do kwerend LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Wiele wątków i przetwarzania asynchronicznego

Nowoczesne programy często używają operacji asynchronicznych. Te artykuły ułatwią Dowiedz się za pomocą tych metod.

- [Poprawy async wydajności przy użyciu `System.Threading.Tasks.Task.WhenAll` ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Tworzenie wielu żądania sieci web równolegle `async` i `await` ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Korzystanie z puli wątków](../programming-guide/concepts/threading/how-to-use-a-thread-pool.md).

## <a name="command-line-args-to-your-program"></a>Argumenty wiersza polecenia do programu

Najczęściej programów C# ma argumenty wiersza polecenia. Te artykuły omawiające dostępu i przetworzenie tych argumentów wiersza polecenia.

- [Pobierz wszystkie argumenty wiersza polecenia z `for` ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
- [Pobierz wszystkie argumenty wiersza polecenia z `foreach` ](../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md).
