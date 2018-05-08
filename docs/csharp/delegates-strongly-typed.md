---
title: Jednoznacznie delegatów
description: Dowiedz się, jak użycie ogólnych typów delegata w celu zadeklarowania typów niestandardowych podczas tworzenia funkcji wymagających delegatów.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strongly-typed-delegates"></a>Jednoznacznie delegatów

[Poprzednie](delegate-class.md)

W poprzednim artykule widać, utworzyć delegata określonych typów za pomocą `delegate` — słowo kluczowe. 

Abstrakcyjna klasa delegata zapewnia infrastrukturę luźne powiązanie i wywołania. Konkretne typy delegata staną się bardziej użyteczne obejmującego i wymuszanie bezpieczeństwa typu dla metody, które są dodawane do listy wywołania obiektu delegowanego. Jeśli używasz `delegate` — słowo kluczowe i typ delegata konkretnych, kompilator generuje tych metod.

W praktyce może to prowadzić do tworzenia nowego obiektu delegowanego typów przy każdym podpisu innej metody. Tę pracę można pobrać niewygodny po pewnym czasie. Co nowa funkcja wymaga nowych typów delegata.

Thankfully nie jest to konieczne. Framework .NET Core zawiera kilka typów, które można wykorzystać w każdym przypadku, gdy należy przekazać typów. Są to [ogólnego](programming-guide/generics/index.md) definicje, mogą zadeklarować dostosowań, gdy będziesz potrzebować nowej deklaracje metody. 

Pierwsza z tych typów jest <xref:System.Action> typu i kilka zmian:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

`in` Modyfikator na argumentu typu ogólnego zostało opisane w artykule na KOWARIANCJA.

Brak zmian `Action` delegata, który będzie zawierać do 16 argumenty, takich jak <xref:System.Action%6016>.
Należy pamiętać, że te definicje używać różnych argumentów ogólnych dla każdego z argumentami delegata: który zapewnia elastyczność maksymalna. Argumenty metody nie muszą być, ale może być tego samego typu.

Użyj jednej z `Action` typy dla dowolnego typu delegata, który został zwrócony typ void.

Struktura obejmuje również kilka ogólnych typów delegata używane dla typów delegowanych, które zwracają wartości:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

`out` Modyfikatora w wyniku argumentu typu ogólnego zostało opisane w artykule na KOWARIANCJA.

Brak zmian `Func` delegować z maksymalnie 16 argumenty wejściowe, takie jak <xref:System.Func%6017>.
Typ wyniku jest zawsze ostatniego parametru typu we wszystkich `Func` deklaracje przez Konwencję.

Użyj jednej z `Func` typy dla dowolnego typu delegata, która zwraca wartość.

Istnieje również specjalne <xref:System.Predicate%601> typ delegata, która zwraca pojedynczą wartość testu:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Należy zauważyć, że dla każdego `Predicate` typu, strukturę równoważne `Func` typ istnieje na przykład:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Wydaje się, że te dwa typy są równoważne. Nie są one.
Te dwie zmienne nie może być używane zamiennie. Zmienna typu nie można przypisać innego typu. System typów języka C# korzysta z nazw określonych typów nie struktury.

Wszystkie te typu delegata, który definicje w bibliotece programu .NET Core oznacza, że nie trzeba zdefiniować nowy typ delegata żadnych nowych funkcji tworzenia wymaganych obiektów delegowanych. Te definicje ogólnego powinien zawierać wszystkie delegata typy, które są potrzebne w większości sytuacji. Można po prostu utworzyć wystąpienie jednego z następujących typów z parametrami typu wymagane. W przypadku algorytmy, które można podjąć ogólnego te obiekty delegowane może służyć jako typów ogólnych. 

To powinno zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć w celu zapewnienia ich współdziałania z obiektów delegowanych.

W artykule pojawi się kilka typowych wzorców do pracy z delegatów w praktyce.

[Next](delegates-patterns.md)
