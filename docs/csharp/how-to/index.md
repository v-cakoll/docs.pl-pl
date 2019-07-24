---
title: Instrukcje (C# przewodnik)
description: Kolekcja szybkich porad i krótkich, ukierunkowanych przykładów kodu
ms.date: 12/20/2017
ms.openlocfilehash: 09e39e3c9bea5d4b9240039e37d2a5998fe1ebf8
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400735"
---
# <a name="how-to-c"></a>Instrukcje (C#)

W sekcji C# jak można znaleźć szybkie odpowiedzi na często zadawane pytania. W niektórych przypadkach artykuły mogą być wymienione w wielu sekcjach. Chcemy je łatwo znaleźć dla wielu ścieżek wyszukiwania.

## <a name="general-c-concepts"></a>Pojęcia C# ogólne

Istnieje kilka porad i wskazówek, które są typowymi C# rozwiązaniami programistycznymi.

- [Inicjowanie obiektów za pomocą inicjatora obiektów](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Zapoznaj się z różnicami między przekazywaniem struktury a klasą do metody](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Rozwiązywanie konfliktów nazw typów przy użyciu globalnego aliasu przestrzeni nazw](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [Użyj przeciążenia operatora](../language-reference/operators/operator-overloading.md).
- [Implementowanie i wywoływanie niestandardowej metody rozszerzenia](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Nawet C# programiści mogą chcieć [ `My` użyć przestrzeni nazw w języku VB](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [Utwórz `enum` nową metodę dla typu przy użyciu metod rozszerzających](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Elementy członkowskie klasy i struktury

Tworzysz klasy i struktury w celu zaimplementowania programu. Te techniki są często używane podczas pisania klas lub struktur.

- [Zadeklaruj zaimplementowane właściwości](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Zadeklaruj i Użyj właściwości odczytu/zapisu](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Zdefiniuj stałe](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Zastąp metodę, aby zapewnić ciąg wyjściowy. `ToString` ](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)
- [Zdefiniuj właściwości abstrakcyjne](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Użyj funkcji dokumentacji XML, aby udokumentować swój kod](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Jawnie Implementuj elementy członkowskie interfejsu](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) , aby zapewnić zwięzły interfejs publiczny.
- [Jawne implementowanie elementów członkowskich dwóch interfejsów](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Praca z kolekcjami

Te artykuły ułatwiają współpracę z kolekcjami danych.

- [Inicjowanie słownika z inicjatorem kolekcji](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Praca z ciągami

Ciągi są podstawowym typem danych używanym do wyświetlania lub manipulowania tekstem. W tych artykułach przedstawiono typowe praktyki dotyczące ciągów.

- [PORÓWNAJ ciągi](compare-strings.md).
- [Zmodyfikuj zawartość ciągu](modify-string-contents.md).
- [Ustal, czy ciąg reprezentuje liczbę](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [ Użyj`String.Split` , aby oddzielić ciągi](parse-strings-using-split.md).
- [Połącz wiele ciągów w jeden](concatenate-multiple-strings.md).
- [Wyszukaj tekst w ciągu](search-strings.md).

## <a name="convert-between-types"></a>Konwertuj między typami

Może być konieczne przekonwertowanie obiektu na inny typ.

- [Ustal, czy ciąg reprezentuje liczbę](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Konwertuj między ciągami, które reprezentują liczby szesnastkowe i liczbę](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Konwertuj ciąg na `DateTime` ](../../standard/base-types/parsing-datetime.md).
- [Konwertuj tablicę bajtów na](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)liczbę całkowitą.
- [Konwertuje ciąg na liczbę](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Użyj `as` dopasowania wzorca `is` i operatorów, aby bezpiecznie rzutować do innego typu](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).
- [Zdefiniuj konwersje typów niestandardowych](../language-reference/operators/user-defined-conversion-operators.md).
- [Ustal, czy typ jest typem wartości null](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md).
- [Konwersja pomiędzy typami wartości null i](../programming-guide/nullable-types/using-nullable-types.md#conversion-from-a-nullable-type-to-an-underlying-type)niedopuszczających wartości null.

## <a name="equality-and-ordering-comparisons"></a>Porównania równości i określania kolejności

Można utworzyć typy, które definiują własne reguły równości lub definiują naturalne porządkowanie między obiektami tego typu.

- [Test pod kątem równości odwołań](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Zdefiniuj równość na podstawie wartości dla typu](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Obsługa wyjątków

Programy .NET zgłaszają, że metody nie ukończyły pracy przez wyrzucanie wyjątków. W tych artykułach dowiesz się, jak korzystać z wyjątków.

- [Obsługa wyjątków przy `try` użyciu `catch`i ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Oczyszczanie zasobów `finally` przy użyciu klauzul](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [Odzyskaj z wyjątków nienależących do CLS (Common Language Specification)](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Obiekty delegowane i zdarzenia

Obiekty delegowane i zdarzenia zapewniają możliwość tworzenia strategii obejmujących luźno sprzężone bloki kodu.

- [Deklarowanie, Tworzenie wystąpień i używanie delegatów](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Połącz delegatów multiemisji](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Zdarzenia udostępniają mechanizm publikowania lub subskrybowania powiadomień.

- [Subskrybowanie i anulowanie subskrypcji zdarzeń](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Implementuj zdarzenia zadeklarowane w interfejsach](../programming-guide/events/how-to-implement-interface-events.md).
- Jest [to zgodne z wytycznymi .NET Framework, gdy kod publikuje zdarzenia](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Wywołaj zdarzenia zdefiniowane w klasach bazowych z klas pochodnych](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Implementowanie niestandardowych metod dostępu do zdarzeń](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>Wskazówki dotyczące LINQ

LINQ umożliwia pisanie kodu w celu zbadania dowolnego źródła danych, które obsługuje wzorzec wyrażenia zapytania LINQ. Te artykuły ułatwiają zrozumienie wzorca i pracy z różnymi źródłami danych.

- [Kwerenda kolekcji](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Użycie wyrażeń lambda w zapytaniu](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [ Użyj`var` w wyrażeniach zapytania](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Zwraca podzbiory właściwości elementów z zapytania](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Zapisuj zapytania ze złożonym filtrowaniem](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Sortuj elementy źródła danych](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Sortuj elementy dla wielu kluczy](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Kontrolowanie typu projekcji](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Liczenie wystąpień wartości w sekwencji źródłowej](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Oblicz wartości pośrednie](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Scalanie danych z wielu źródeł](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [Znajdź różnicę między dwiema sekwencjami](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Debuguj puste wyniki zapytania](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [Dodaj niestandardowe metody do zapytań LINQ](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Wiele wątków i przetwarzanie asynchroniczne

Nowoczesne programy często używają operacji asynchronicznych. Te artykuły ułatwią naukę korzystania z tych technik.

- [Zwiększenie wydajności asynchronicznej `System.Threading.Tasks.Task.WhenAll`przy użyciu programu ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Równoległe wykonywanie wielu żądań sieci Web `async` przy `await`użyciu i ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Użyj puli wątków](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Argumenty wiersza polecenia dla programu

Zazwyczaj C# programy mają argumenty wiersza polecenia. Te artykuły uczyją się, jak uzyskać dostęp do tych argumentów wiersza polecenia i ich przetworzyć.

- [Pobierz wszystkie argumenty wiersza polecenia z `for` ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
