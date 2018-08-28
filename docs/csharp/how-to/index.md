---
title: Jak artykułów (Przewodnik C#)
description: Szybkie wskazówki i przykłady kodu krótki, ukierunkowane kolekcję
ms.date: 12/20/2017
ms.openlocfilehash: db3ba1982a26097c3d69ba91493164c8f2371be9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999566"
---
# <a name="how-to-c"></a>Instrukcje (C#)

W sposób części przewodnika C# można znaleźć szybkich odpowiedzi na często zadawane pytania. W niektórych przypadkach artykuły mogą być wymienione w wielu sekcjach. Chcieliśmy były łatwo dostępne dla wielu ścieżek wyszukiwania. 

## <a name="general-c-concepts"></a>Pojęcia ogólne C#

Istnieje kilka porady i wskazówki, które są wspólne praktyki dla deweloperów języka C#.

- [Inicjowanie obiektów za pomocą inicjatora obiektów](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Dowiedz się, różnice między przekazywaniem struktury i klasy do metody](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Jak używać wyrażeń lambda](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).
- [Rozwiązać konflikty nazw typu za pomocą aliasu globalna przestrzeń nazw](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [Przeciążanie operatora użyj](../programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).
- [Implementowanie i wywołanie niestandardowej metody rozszerzenia](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Chcieć nawet języku C# programistów [użyj `My` przestrzeni nazw z VB](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [Utwórz nową metodę `enum` typu przy użyciu metody rozszerzenia](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Składowe klasy i struktury

Możesz utworzyć klasy i struktury, aby zaimplementować program. Metody te są często używane podczas zapisywania klasy lub struktury.

- [Deklarowanie właściwości zaimplementowane automatycznie](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Deklarowanie i użycie właściwości odczytu/zapisu](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Definiuj stałe](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Zastąp `ToString` metodę w celu udostępnienia danych wyjściowych ciąg](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Definiowanie właściwości abstrakcyjnych](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Użycie funkcji dokumentacji xml do dokumentowania kodu](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Jawne Implementowanie elementów interfejsu](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) zapewnienie publicznego interfejsu zwięzły.
- [Jawne Implementowanie elementów dwóch interfejsów](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Praca z kolekcjami

Te artykuły ułatwiają pracę z kolekcji danych.

- [Inicjowanie słownika przy użyciu inicjatora kolekcji](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Praca z ciągami

Ciągi są podstawowy typ danych używane do wyświetlania i manipulowania tekstem. Artykuły te przedstawiają typowe rozwiązania z ciągami.

- [Porównywanie ciągów](compare-strings.md).
- [Modyfikowanie zawartości ciągu](modify-string-contents.md).
- [Określanie, jeśli ciąg reprezentuje liczbę](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Użyj `String.Split` do rozdzielania ciągów](parse-strings-using-split.md).
- [Łączenie wielu ciągów w jeden](concatenate-multiple-strings.md).
- [Wyszukaj tekst w ciągu](search-strings.md).

## <a name="convert-between-types"></a>Konwertowanie między typami

Może być konieczne konwersji obiektu do innego typu.

- [Określanie, jeśli ciąg reprezentuje liczbę](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Konwertowanie ciągów, które reprezentują liczb szesnastkowych numer](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Konwertuj ciąg na `DateTime` ](../../standard/base-types/parsing-datetime.md).
- [Konwertowanie tablicy typu byte na liczbę całkowitą](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Konwertowanie ciągu na liczbę](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Użyj `as` i `is` bezpiecznego rzutowania na inny typ](../programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).
- [Zdefiniuj operatory konwersji dla `struct` typy](../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md).
- [Określa, czy typ jest typem wartościowym](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md).
- [Konwertowanie między typami dopuszcza wartości null i dopuszcza wartość](../programming-guide/nullable-types/using-nullable-types.md#conversion-from-a-nullable-type-to-an-underlying-type).

## <a name="equality-and-ordering-comparisons"></a>Równości i porównania porządkowania

Można utworzyć typy, które zdefiniować własne reguły dla równości lub Definiowanie fizycznych między obiektami tego typu.

- [Testowanie równości odwołań na podstawie](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Definiowanie równości na podstawie wartości dla typu](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Obsługa wyjątków

Programy platformy .NET zgłosić, że metody nie została pomyślnie ukończona swoją pracę za zgłaszanie wyjątków. W tych artykułach dowiesz się pracować z wyjątków.

- [Obsługa wyjątków za pomocą `try` i `catch` ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Oczyszczanie zasobów przy użyciu `finally` klauzule](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Odzyskiwanie z wyjątków niezgodnych ze specyfikacją CLS (Common Language Specification)](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Delegaci i zdarzenia

Delegaci i zdarzenia zapewniają możliwość przesyłania strategie, które obejmują luźno sprzężonych bloków kodu.

- [Deklarowanie, tworzenie wystąpień i używać delegatów](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Połącz obiekty delegowane multiemisji](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Zdarzenia zapewniają mechanizm do publikowania i subskrybowania powiadomień.

- [Subskrybowanie i anulowanie subskrypcji zdarzeń](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Implementowanie zdarzeniach deklarowanych w interfejsach](../programming-guide/events/how-to-implement-interface-events.md).
- [Być zgodne z zasadami .NET Framework, gdy kod publikuje zdarzenia](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Wywoływanie zdarzeń zdefiniowanych w klasach bazowych klas pochodnych](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Store wystąpień zdarzeń w słowniku](../programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md).
- [Implementowanie niestandardowych metod dostępu zdarzeń](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>Rozwiązania programu LINQ

LINQ umożliwia pisanie kodu, aby wysłać zapytanie dowolnego źródła danych, które obsługuje wzorzec wyrażenia zapytań LINQ. Następujące artykuły pomogą Ci zrozumieć wzorzec działania i pracy z różnymi źródłami danych.

- [Kwerenda dotycząca kolekcji](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Użycie wyrażeń lambda w kwerendzie](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Użyj `var` w wyrażeniach zapytań](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Zwracanie podzbiorów właściwości elementu w wyniku zapytania](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Pisanie zapytań z zaawansowanym filtrowaniem](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Sortowanie elementów źródła danych](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Sortowanie elementów na wielu kluczach](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Kontrolowanie typu projekcji](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Liczba wystąpień wartość w sekwencji źródłowej](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Obliczanie wartości pośrednich](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Scalanie danych z wielu źródeł](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Wyszukiwanie zestawu różnic między dwoma sekwencjami](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Debugowanie wyników zapytania pusty](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Dodawanie metod niestandardowych do kwerend LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Wiele wątków i przetwarzania asynchronicznego

Nowoczesne programy często używają operacji asynchronicznych. Te artykuły ułatwią informacje na temat używania tych metod.

- [Poprawa async wydajność dzięki używaniu `System.Threading.Tasks.Task.WhenAll` ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Tworzenie wielu żądania sieci web równolegle przy użyciu `async` i `await` ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Korzystanie z puli wątków](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Argumenty wiersza polecenia do programu

Zazwyczaj C# programy działają argumenty wiersza polecenia. Te artykuły nauczą Cię, jak uzyskać dostęp i przetwarzać te argumenty wiersza polecenia.

- [Pobieranie wszystkich argumentów wiersza polecenia `for` ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
- [Pobieranie wszystkich argumentów wiersza polecenia `foreach` ](../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md).
