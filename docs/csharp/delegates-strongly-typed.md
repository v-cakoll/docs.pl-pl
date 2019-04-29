---
title: Silnie Typizowanych obiektów delegowanych
description: Dowiedz się, jak korzystać z ogólnymi typami delegatów do deklarowania typów niestandardowych podczas tworzenia funkcji wymagających delegatów.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646663"
---
# <a name="strongly-typed-delegates"></a>Silnie Typizowanych obiektów delegowanych

[Poprzednie](delegate-class.md)

W poprzednim artykule pokazano, Utwórz delegata określonych typów przy użyciu `delegate` — słowo kluczowe. 

Klasa abstrakcyjna delegata zapewnienia infrastruktury dla luźne powiązania i wywołania. Konkretne typy delegatów stać się bardziej użyteczne założeń i wymuszanie bezpieczeństwa typu dla metody, które są dodawane do listy wywołań obiektu delegowanego. Kiedy używasz `delegate` — słowo kluczowe i określić typ delegata konkretnych, kompilator generuje tych metod.

W praktyce może to prowadzić do tworzenie typów nowe delegowanie, zawsze, gdy potrzebujesz podpisu inną metodę. Tej pracy można pobrać tedious po pewnym czasie. Każdej nowej funkcji wymaga nowych typów obiektów delegowanych.

Na szczęście nie jest to konieczne. Framework .NET Core zawiera kilka typów, które można wykorzystać w każdym przypadku, gdy potrzebujesz przekazać typów. Są to [ogólny](programming-guide/generics/index.md) definicji, dzięki czemu można zadeklarować dostosowań, gdy będziesz potrzebować nowego deklaracje metody. 

Jest to pierwsza z tych typów <xref:System.Action> typu i kilka zmian:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

`in` Modyfikator na argument typu ogólnego zostało omówione w artykule na KOWARIANCJA.

Brak odmian `Action` delegata, które zawierają argumenty do 16, takie jak <xref:System.Action%6016>.
Jest ważne, że te definicje używać różnych argumenty ogólne dla każdego z podanych argumentów delegata: Który zapewnia maksymalną elastyczność. Argumenty metody nie muszą być jednak może być tego samego typu.

Użyj jednej z `Action` typów dla dowolnego typu delegata, który ma zwracać typ void.

Środowisko zawiera także kilka ogólnymi typami delegatów, które umożliwiają typami delegatów, które zwracają wartości:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

`out` Modyfikatora w wyniku argument typu ogólnego zostało omówione w artykule na KOWARIANCJA.

Brak odmian `Func` delegowanie z maksymalnie 16 argumenty wejściowe, takie jak <xref:System.Func%6017>.
Typ wyniku jest zawsze ostatnim parametrze typu we wszystkich `Func` deklaracji, zgodnie z Konwencją.

Użyj jednej z `Func` typów dla dowolnego typu delegata, która nie zwraca wartości.

Istnieje również specjalne <xref:System.Predicate%601> 
Typ dla pełnomocnika, który zwraca wartość typu single testu:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Należy zauważyć, że dla każdego `Predicate` typ, strukturalnie równoważne `Func` typ istnieje na przykład:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Myślisz, że te dwa typy są równoważne. Nie są one.
Te dwie zmienne nie mogą być używane zamiennie. Zmienna typu nie można przypisać innego typu. C# Typu system używa nazwy zdefiniowanych typów, nie struktury.

Wszystkie te typ delegata, który definicje w bibliotece programu .NET Core oznacza, że nie musisz zdefiniować nowy typ delegata dla żadnych nowych funkcji możesz utworzyć, których wymaga delegatów. Te definicje ogólny powinien zapewnić wszystkich delegata typów, które są potrzebne w większości sytuacji. Można po prostu utworzyć wystąpienie jednego z następujących typów z parametrami typu wymagane. W przypadku algorytmów, które mogą być wykonane na ogólny te delegaty może służyć jako typów ogólnych. 

To powinno zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć, aby pracować z delegatów.

W następnym artykule przedstawimy kilka typowych wzorców do pracy z delegatów w praktyce.

[Next](delegates-patterns.md)
