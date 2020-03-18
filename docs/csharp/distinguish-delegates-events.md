---
title: Wyróżniające się obiekty delegowane i zdarzenia
description: Poznaj różnicę między delegatami i zdarzeniami oraz czas korzystania z każdej z tych funkcji programu .NET Core.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 04738ac2dd82da9c577e88598d0bb737a93333c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146181"
---
# <a name="distinguishing-delegates-and-events"></a>Wyróżniające się obiekty delegowane i zdarzenia

[Wstecz](modern-events.md)

Deweloperzy, którzy są nowicjuszami w platformie .NET `delegates` Core często mają `events`trudności przy podejmowaniu decyzji między projektem opartym na projekcie na podstawie . Jest to trudne pojęcie, ponieważ dwie cechy języka są bardzo podobne. Zdarzenia są nawet tworzone przy użyciu obsługi języka dla delegatów.

Oba oferują scenariusz późnego wiązania: umożliwiają scenariusze, w których składnik komunikuje się, wywołując metodę, która jest znana tylko w czasie wykonywania. Obsługują one zarówno pojedyncze i wiele metod subskrybenta. Może się to znaleźć, o którym mowa w trybie singlecast i multiemisji. Oba obsługują podobną składnię do dodawania i usuwania programów obsługi. Na koniec wywoływania zdarzenia i wywoływania delegata użyć dokładnie tej samej składni wywołania metody. Oba obsługują nawet `Invoke()` tę samą składnię metody do użycia z operatorem. `?.`

Przy tych wszystkich podobieństwach łatwo jest mieć problemy z określeniem, kiedy użyć którego.

## <a name="listening-to-events-is-optional"></a>Słuchanie zdarzeń jest opcjonalne

Najważniejszą kwestią przy określaniu, której funkcji języka użyć, jest to, czy musi istnieć załączony subskrybent. Jeśli kod musi wywołać kod podany przez subskrybenta, należy użyć projektu opartego na delegatów. Jeśli kod może zakończyć całą swoją pracę bez wywoływania subskrybentów, należy użyć projektu na podstawie zdarzeń.

Należy wziąć pod uwagę przykłady utworzone w tej sekcji. Kod utworzony przy `List.Sort()` użyciu musi mieć funkcję porównania w celu prawidłowego sortowania elementów. Zapytania LINQ muszą być dostarczane z delegatów w celu określenia, jakie elementy do zwrócenia. Oba używane projekt zbudowany z delegatów.

Rozważmy `Progress` zdarzenie. Raportuje postęp y w zadaniu.
Zadanie jest kontynuowane, niezależnie od tego, czy istnieją odbiorniki.
Jest `FileSearcher` to kolejny przykład. To nadal szukać i znaleźć wszystkie pliki, które były poszukiwane, nawet bez abonentów zdarzeń dołączone.
Formanty ux nadal działają poprawnie, nawet jeśli nie ma subskrybentów słuchających zdarzeń. Obaj używają projektów opartych na wydarzeniach.

## <a name="return-values-require-delegates"></a>Zwracanie wartości wymaga delegatów

Inną kwestią jest prototyp metody, który chcesz dla metody delegata. Jak widać, delegaci używane do zdarzeń wszystkie mają typ powrotu void. Zaobserwowano również, że istnieją idiomy do tworzenia programów obsługi zdarzeń, które przekazują informacje z powrotem do źródeł zdarzeń poprzez modyfikowanie właściwości obiektu argumentu zdarzenia. Podczas gdy te idiomy działają, nie są tak naturalne, jak zwracanie wartości z metody.

Należy zauważyć, że te dwa heurystyki często mogą być obecne: Jeśli metoda delegata zwraca wartość, prawdopodobnie wpłynie na algorytm w jakiś sposób.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Detektory zdarzeń często mają dłuższe okresy istnienia

Jest to nieco słabsze uzasadnienie. Jednak może się okazać, że projekty oparte na zdarzeniach są bardziej naturalne, gdy źródło zdarzeń będzie podnosić zdarzenia przez długi okres czasu. Można zobaczyć przykłady tego dla formantów UX w wielu systemach. Po zasubskrybowania zdarzenia, źródło zdarzenia może wywołać zdarzenia w całym okresie istnienia programu.
(Możesz zrezygnować ze zdarzeń, gdy nie są już potrzebne).

Kontrast, że z wielu projektów opartych na delegata, gdzie delegat jest używany jako argument do metody, a delegat nie jest używany po tej metody zwraca.

## <a name="evaluate-carefully"></a>Dokładnie oceniaj

Powyższe rozważania nie są trudne i szybkie zasady. Zamiast tego reprezentują wskazówki, które mogą pomóc w podjęciu decyzji, który wybór jest najlepszy dla danego użycia. Ponieważ są one podobne, można nawet prototyp zarówno, i zastanowić się, które byłoby bardziej naturalne do pracy. Oba obsługują scenariusze późnego wiązania dobrze. Użyj tego, który najlepiej komunikuje swój projekt.
