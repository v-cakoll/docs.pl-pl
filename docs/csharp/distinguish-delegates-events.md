---
title: Wyróżniające się obiekty delegowane i zdarzenia
description: Dowiedz się, jak różnica między delegatami a zdarzeniami i kiedy korzystać z każdej z tych funkcji .NET Core.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 4179330fe5e88da5d5034a150a057f63e31b178b
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588257"
---
# <a name="distinguishing-delegates-and-events"></a>Wyróżniające się obiekty delegowane i zdarzenia

[Wstecz](modern-events.md)

Deweloperzy, którzy są nowicjuszami w platformie .NET `delegates` Core, często `events`mają trudności z podejmowaniem decyzji między projektem opartym na projekcie a projektem opartym na . Jest to trudna koncepcja, ponieważ dwie funkcje językowe są bardzo podobne. Zdarzenia są nawet tworzone przy użyciu obsługi języka dla delegatów.

Obie oferują scenariusz późnego wiązania: umożliwiają one scenariusze, w których składnik komunikuje się, wywołując metodę, która jest znana tylko w czasie wykonywania. Obsługują one zarówno pojedyncze, jak i wiele metod subskrybenta. Może się okazać, że jest to określane jako obsługa pojedynczej emisji i multiemisji. Obie obsługują podobną składnię do dodawania i usuwania programów obsługi. Na koniec wywoływanie zdarzenia i wywoływanie delegata używa dokładnie tej samej składni wywołania metody. Nawet obie obsługują `Invoke()` tę samą składnię `?.` metody do użytku z operatorem.

Z tych wszystkich podobieństw, łatwo jest mieć problemy z określeniem, kiedy używać, które.

## <a name="listening-to-events-is-optional"></a>Słuchanie zdarzeń jest opcjonalne

Najważniejszą kwestią przy określaniu funkcji języka do użycia jest to, czy musi istnieć dołączony subskrybent. Jeśli kod musi wywołać kod dostarczony przez subskrybenta, należy użyć projektu opartego na delegatów. Jeśli kod można wykonać całą swoją pracę bez wywoływania żadnych subskrybentów, należy użyć projektu opartego na zdarzeniach.

Należy wziąć pod uwagę przykłady zbudowane podczas tej sekcji. Kod, który `List.Sort()` został utworzony przy użyciu musi mieć funkcję porównywarki w celu prawidłowego sortowania elementów. Zapytania LINQ muszą być dostarczane z delegatów w celu określenia, jakie elementy do zwrócenia. Oba jednych i drugich używały projektu zbudowanego z delegatami.

Należy `Progress` wziąć pod uwagę zdarzenie. Raportuje postępy w realizacji zadania.
Zadanie w dalszym ciągu postępować, czy istnieją żadnych odbiorników.
Jest `FileSearcher` to kolejny przykład. Nadal przeszukiwałby i wyszukiwał wszystkie pliki, które były poszukiwane, nawet bez dołączanych subskrybentów zdarzeń.
Kontrolki środowiska użytkownika nadal działają poprawnie, nawet jeśli nie ma subskrybentów słuchających zdarzeń. Obaj używają wzorów opartych na wydarzeniach.

## <a name="return-values-require-delegates"></a>Wartości zwracane wymagają delegatów

Inną kwestią jest prototyp metody, który chcesz dla metody delegata. Jak widać, delegatów używanych dla zdarzeń wszystkie mają typ zwrotu void. Widać również, że istnieją idiomy do tworzenia programów obsługi zdarzeń, które przekazują informacje z powrotem do źródeł zdarzeń poprzez modyfikowanie właściwości obiektu argumentu zdarzenia. Podczas gdy te idiomy działają, nie są tak naturalne, jak zwracanie wartości z metody.

Należy zauważyć, że te dwie heurystyki często mogą być zarówno obecny: Jeśli metoda delegat zwraca wartość, prawdopodobnie wpłynie na algorytm w jakiś sposób.

## <a name="events-have-private-invocation"></a>Zdarzenia mają prywatne wywołanie

Klasy inne niż ten, w którym zawiera się zdarzenie, można tylko dodawać i usuwać detektory zdarzeń; tylko klasa zawierająca zdarzenie może wywołać zdarzenie. Zdarzenia są zazwyczaj członkami klasy publicznej.
Dla porównania delegatów są często przekazywane jako parametry i przechowywane jako członków klasy prywatnej, jeśli są one przechowywane w ogóle.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Detektory zdarzeń często mają dłuższe okresy istnienia

Jest to nieco słabsze uzasadnienie. Jednak może się okazać, że projekty oparte na zdarzeniach są bardziej naturalne, gdy źródło zdarzeń będzie wywoływać zdarzenia przez długi okres czasu. Można zobaczyć przykłady tego dla formantów ux w wielu systemach. Po zasubskrybowaniu zdarzenia źródło zdarzeń może zgłaszać zdarzenia przez cały okres istnienia programu.
(Możesz zrezygnować z subskrypcji wydarzeń, gdy nie są już potrzebne).

Kontrast, że z wielu projektów opartych na pełnomocnika, gdzie delegat jest używany jako argument do metody, a delegat nie jest używany po tej metody zwraca.

## <a name="evaluate-carefully"></a>Oceń uważnie

Powyższe rozważania nie są twarde i szybkie zasady. Zamiast tego stanowią one wskazówki, które pomogą Ci zdecydować, który wybór jest najlepszy dla danego użycia. Ponieważ są one podobne, można nawet prototyp zarówno, i rozważyć, które byłyby bardziej naturalne do pracy z. Obie dobrze obsługują scenariusze późnego wiązania. Użyj tego, który najlepiej komunikuje swój projekt.
