---
title: Wyróżniające się obiekty delegowane i zdarzenia
description: Różnice między delegaci i zdarzenia i kiedy należy używać każdego z tych funkcji platformy .NET Core.
ms.date: 06/20/2016
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.openlocfilehash: 2f9c26519d93314f4991829191723df5426b23b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646647"
---
# <a name="distinguishing-delegates-and-events"></a>Wyróżniające się obiekty delegowane i zdarzenia

[Poprzednie](modern-events.md)

Deweloperzy, które są często jesteś nowym użytkownikiem platformy .NET Core mieć trudności podczas podejmowania decyzji o między projektu na podstawie `delegates` i projekty na podstawie `events`. Jest to koncepcja trudne, ponieważ funkcje językowe dwa są bardzo podobne. Zdarzenia nawet są tworzone przy użyciu języka pomocy technicznej dla obiektów delegowanych. 

Oferują scenariusza późne powiązania: umożliwiają one scenariusze, w którym składnik komunikuje się przez wywołanie metody, która jest znane tylko w czasie wykonywania. Obsługiwane są też obu metod pojedynczych i wielu subskrybentów. Może się okazać tej obsługi są nazywane singlecast i multiemisji. Obie obsługują podobnej składni umożliwiającą Dodawanie i usuwanie programów obsługi. Na koniec podnoszenie zdarzenia i wywoływać metodę delegata Użyj dokładnie tej samej składni wywołania metody. Oba nawet obsługują te same `Invoke()` składni metody do użytku z programem `?.` operatora.

Za pomocą tych podobieństwa jest łatwe do problemów z ustaleniem, kiedy je stosować.

## <a name="listening-to-events-is-optional"></a>Nasłuchiwanie zdarzeń jest opcjonalne

Najważniejsze brany pod uwagę przy określaniu funkcji języka jest lub nie musi być subskrybentem dołączone. Jeśli kod musi wywoływać kod dostarczonych przez subskrybenta, należy użyć projektu, oparte na delegatach. Jeśli Twój kod może wykonać swoją pracę bez wywoływania żadnych subskrybentów, należy użyć projektu na podstawie zdarzeń. 

Należy wziąć pod uwagę przykłady utworzone w tej sekcji. Kod zostanie skompilowany przy użyciu `List.Sort()` należy zachować szczególną funkcję porównującą aby można było poprawnie sortować elementy. Zapytania LINQ, należy podać przy użyciu delegatów w celu ustalenia, jakie elementy do zwrócenia. Jest używany zarówno projektu utworzonych za pomocą obiektów delegowanych.

Należy wziąć pod uwagę `Progress` zdarzeń. Wysyła raporty postęp zadania.
Zadania w dalszym ciągu kontynuować informację określającą, czy istnieją żadnych odbiorników.
`FileSearcher` Jest inny przykład. Będzie on nadal wyszukiwania i znajdowania wszystkich plików, które zostały poszukiwane, nawet w przypadku subskrybentów zdarzeń dołączonych.
Kontrolki interfejsu użytkownika nadal działają poprawnie, nawet wtedy, gdy istnieją żadnych subskrybentów nasłuchiwanie zdarzenia. Obie używają projekty na podstawie zdarzeń.

## <a name="return-values-require-delegates"></a>Wartości zwracane wymagają delegatów

Kolejna kwestia jest związana prototypu metody, które mają swoje metody delegata. Jak wiesz, delegatów, używane dla wszystkich zdarzeń ma zwracać typ void. Również wiesz, że nie istnieją idiomy do tworzenia programów obsługi zdarzeń, które przekazują informacje do źródła zdarzeń przez modyfikowanie właściwości obiektu argumentu zdarzenia. Podczas tych idiomy będą działać, nie są one jako naturalnego jako zwracanie wartości z metody.

Zwróć uwagę, że te dwa algorytmy heurystyczne mogą często być obecne jednocześnie: Jeśli Twoje metody delegata zwróci wartość, prawdopodobnie będzie miało wpływ algorytm w jakiś sposób.

## <a name="event-listeners-often-have-longer-lifetimes"></a>Odbiorniki zdarzeń często mają dłuższe okresy istnienia 

Jest to nieco mniejsze uzasadnienie. Jednak może się okazać oparte na zdarzeniach projekty są bardziej naturalne, gdy źródło zdarzenia będą wywoływanie zdarzeń w długim okresie czasu. Widać to przykłady formantów interfejsu użytkownika w wielu systemach. Gdy zasubskrybujesz zdarzenia, źródło zdarzenia mogą zgłaszać zdarzenia w okresie istnienia programu.
(Możesz anulować subskrypcję zdarzenia, gdy nie są już potrzebne.)

Natomiast, o wiele projektów opartych na delegacie, gdy obiekt delegowany jest używana jako argument do metody, i delegata nie jest używana, po powrocie z tej metody.

## <a name="evaluate-carefully"></a>Dokładnie oceń

Powyższe zagadnienia, nie są reguły trudny i szybkie. Zamiast tego stanowią one wskazówki, które mogą pomóc zdecydować, rozwiązanie jest najlepsze dla określonego użycia. Ponieważ są one podobne, można nawet prototypu zarówno i należy wziąć pod uwagę będzie stosować bardziej naturalne chcesz pracować. Obie obsługują scenariusze późne powiązania dobrze. Użyj przepływu, który komunikuje się projektu najlepsze.
