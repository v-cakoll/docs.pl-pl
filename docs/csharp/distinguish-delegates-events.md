---
title: Wyróżniające się obiekty delegowane i zdarzenia
description: Zapoznaj się z różnicą między delegatami i zdarzeniami oraz kiedy korzystać z każdej z tych funkcji platformy .NET Core.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: ff90af1d2b1a92f06eed58228f8e8ca5ff6b93ca
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037320"
---
# <a name="distinguishing-delegates-and-events"></a>Wyróżniające się obiekty delegowane i zdarzenia

[Ubiegł](modern-events.md)

Deweloperzy, którzy są nowością dla platformy .NET Core, często podejmują decyzje dotyczące projektowania na podstawie `delegates` i projektu opartego na `events`. Jest to trudne koncepcje, ponieważ dwie funkcje języka są bardzo podobne. Zdarzenia są nawet kompilowane przy użyciu obsługi języka dla delegatów. 

Obie te funkcje oferują scenariusz późnego wiązania: włączają scenariusze, w których składnik komunikuje się, wywołując metodę, która jest znana tylko w czasie wykonywania. Obsługują one metody jednego i wielu subskrybentów. Może to być nazywane singlecast i obsługą multiemisji. Obie te funkcje obsługują podobną składnię do dodawania i usuwania programów obsługi. Na koniec, podnoszenie poziomu zdarzenia i wywołanie delegata używa dokładnie tej samej składni wywołania metody. Obsługują one również tę samą składnię metody `Invoke()` do użycia z operatorem `?.`.

W przypadku wszystkich tych podobieństw można łatwo mieć problemy z ustaleniem, kiedy należy używać tego programu.

## <a name="listening-to-events-is-optional"></a>Nasłuchiwanie zdarzeń jest opcjonalne

Najważniejszym zagadnieniem przy określaniu, które funkcje języka mają być używane, jest to, czy musi być dołączonym subskrybentem. Jeśli kod musi wywoływać kod dostarczony przez subskrybenta, należy użyć projektu opartego na delegatach. Jeśli kod może zakończyć całą pracę bez wywoływania subskrybentów, należy użyć projektu opartego na zdarzeniach. 

Rozważ przykłady skompilowane w tej sekcji. Kod utworzony przy użyciu `List.Sort()` musi mieć funkcję porównującą, aby poprawnie sortować elementy. Zapytania LINQ muszą zostać dostarczone z delegatami w celu ustalenia, jakie elementy mają być zwracane. Oba używane projekty skompilowane z delegatami.

Rozważ zdarzenie `Progress`. Raportuje postęp zadania.
Zadanie kontynuuje działanie niezależnie od tego, czy istnieją odbiorniki.
`FileSearcher` jest kolejnym przykładem. Nadal będzie można wyszukiwać i znajdować wszystkie pliki, które zostały uzyskane, nawet jeśli nie załączono żadnych subskrybentów zdarzeń.
Formanty środowiska użytkownika nadal działają poprawnie, nawet jeśli nie ma subskrybentów nasłuchujących zdarzeń. Oba używają projektów opartych na zdarzeniach.

## <a name="return-values-require-delegates"></a>Wartości zwracane wymagają delegatów

Innym zagadnieniem jest prototyp metody dla metody delegata. Jak widać, delegatów używanych dla zdarzeń wszystkie mają typ zwracany void. Zobaczysz również, że istnieją idiomy do tworzenia programów obsługi zdarzeń, które przekazują informacje z powrotem do źródeł zdarzeń przez modyfikowanie właściwości obiektu argumentu zdarzenia. Chociaż te idiomy pracują, nie są tak naturalne jak zwracanie wartości z metody.

Należy zauważyć, że te dwa heurystyke mogą często być obecne: Jeśli metoda Delegate zwraca wartość, prawdopodobnie będzie to miało wpływ na algorytm.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Detektory zdarzeń często mają dłuższe okresy istnienia 

Jest to nieco słabsze uzasadnienie. Jednak można stwierdzić, że projekty oparte na zdarzeniach są bardziej naturalne, gdy źródło zdarzeń będzie w długim czasie podnieść zdarzenia. Przykłady tego elementu można zobaczyć w przypadku formantów środowiska użytkownika w wielu systemach. Po zasubskrybowaniu zdarzenia Źródło zdarzenia może zgłosić zdarzenia przez cały okres istnienia programu.
(Możesz anulować subskrypcję zdarzeń, gdy nie są już potrzebne.)

Kontrast, który ma wiele projektów opartych na delegatach, gdzie delegat jest używany jako argument do metody i delegat nie jest używany po powrocie tej metody.

## <a name="evaluate-carefully"></a>Dokładnie Oceń

Powyższe uwagi nie są regułami twardymi i szybkimi. Zamiast tego przedstawiają wskazówki, które mogą pomóc zdecydować, który wybór jest najlepszy dla danego użycia. Ze względu na to, że są podobne, można nawet prototypować i zastanowić się, że będzie bardziej naturalna współpraca z nimi. Oba obsługują również scenariusze późnego wiązania. Użyj tego, który komunikuje się z projektem najlepiej.
