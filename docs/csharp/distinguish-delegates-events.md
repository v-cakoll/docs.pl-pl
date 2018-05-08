---
title: Wyróżniającą delegaci i zdarzenia
description: Różnice między delegaci i zdarzenia i kiedy należy używać każdego z tych funkcji .NET Core.
ms.date: 06/20/2016
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 2f9c26519d93314f4991829191723df5426b23b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="distinguishing-delegates-and-events"></a>Wyróżniającą delegaci i zdarzenia

[Poprzednie](modern-events.md)

Deweloperzy, które są nowe dla platformy .NET Core często mieć trudności podczas podejmowania decyzji o między projekt na podstawie `delegates` i projekty na podstawie `events`. Jest to pojęcie trudne, ponieważ język dwie funkcje są bardzo podobne. Zdarzenia nawet utworzonym przy użyciu Obsługa języka dla obiektów delegowanych. 

Oferują scenariusza późne powiązania: umożliwiają one scenariuszy, w którym składnik komunikuje się przez wywołanie metody, która jest znane tylko w czasie wykonywania. Oba obsługuje subskrybenta pojedynczych i wielu metod. Może się okazać ta obsługa dalej singlecast i multiemisji. Oba obsługuje składni podobne do dodawania i usuwania programów obsługi. Na koniec wywoływanie zdarzeń i wywoływać metodę delegata należy użyć dokładnie tego samego Składnia wywołania metody. Nawet w przypadku obu obsługują takie same `Invoke()` składni metody do użycia z `?.` operatora.

Z tych podobieństwa jest łatwa do określania, kiedy należy używać problemów.

## <a name="listening-to-events-is-optional"></a>Nasłuchiwanie zdarzeń jest opcjonalne

Najważniejsze uwagę przy określaniu funkcji języka jest czy musi być dołączony subskrybenta. Jeśli kod musi wywoływać kod dostarczonych przez subskrybenta, należy użyć projektu, na podstawie delegatów. Jeśli kod może wykonać wszystkie pracę bez wywoływania żadnych subskrybentów, należy użyć projektu, na podstawie zdarzeń. 

Należy wziąć pod uwagę przykłady wbudowanych w tej sekcji. Kod zostały utworzone przy użyciu `List.Sort()` muszą mieć funkcję porównującą aby prawidłowo sortowania elementów. Zapytania LINQ musi być zasilane delegatów w celu ustalenia, jakie elementy do zwrócenia. Używany zarówno projektu skompilowanych przy użyciu delegatów.

Należy wziąć pod uwagę `Progress` zdarzeń. Raporty postęp zadania.
Zadanie będzie nadal występować kontynuować, czy istnieją wszystkie obiekty nasłuchujące.
`FileSearcher` Inny przykład. Czy nadal wyszukiwanie i Znajdź wszystkie pliki, które zostały poszukiwane, nawet w przypadku subskrybentów zdarzeń dołączony.
Formanty UX nadal działa poprawnie, nawet wtedy, gdy nie ma żadnych subskrybentów nasłuchiwanie zdarzeń. Oba używają projekty na podstawie zdarzeń.

## <a name="return-values-require-delegates"></a>Wartości zwracane wymagają delegatów

Kolejnym zagadnieniem są prototypu — metoda, która ma dla metodę delegata. Jak przedstawiono, delegatów, używanych na potrzeby wszystkich zdarzeń ma zwrócony typ void. Zapoznaniu się również, czy idioms można utworzyć procedury obsługi zdarzeń, które przekazują informacje do źródła zdarzeń przez modyfikowanie właściwości obiektu argument zdarzenia. Podczas pracy te idioms, nie są one jak fizyczną jako zwracanie wartości z metody.

Powiadomienie, że te dwa algorytmy heurystyczne często może zarówno być obecne: Jeśli metodę delegata zwróci wartość, prawdopodobnie wpłyną algorytmu w określony sposób.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Odbiorniki zdarzeń często mają dłuższe okresy istnienia 

Jest to uzasadnienie nieco mniejsze. Jednak może się okazać projekty oparte na zdarzeniu są bardziej naturalne, gdy źródło zdarzenia będą wywoływanie zdarzeń w długim okresie czasu. Spowoduje to przykłady formantów interfejsu użytkownika w wielu systemach. Po zasubskrybowaniu zdarzenie źródło zdarzenia mogą zgłaszać zdarzenia w okresie istnienia program.
(Możesz anulować subskrypcję zdarzenia, gdy nie jest już potrzebne.)

Natomiast który o wiele projektów na podstawie delegata, w którym delegata jest używany jako argument do metody, a delegat nie jest używany po powrocie z tej metody.

## <a name="evaluate-carefully"></a>Dokładnie oceń

Powyższe zagadnienia nie są reguły twardym i szybki. Zamiast tego reprezentują wskazówki, które mogą pomóc zdecydować, rozwiązanie jest najlepsze dla konkretnego użycie. Ponieważ są one podobne, możesz nawet prototypu zarówno i należy wziąć pod uwagę będzie bardziej naturalne do pracy z. Obie również obsługiwać scenariusze późne powiązania. Użyj ten, który komunikuje się projekt najlepiej.
