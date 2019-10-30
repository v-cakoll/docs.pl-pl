---
title: Delegaty o jednoznacznie określonym typie
description: Dowiedz się, jak używać typów delegatów ogólnych do deklarowania typów niestandardowych podczas tworzenia funkcji wymagającej delegatów.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: efdbef39d0e6bf2f07cde2c9621cec173e921752
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037359"
---
# <a name="strongly-typed-delegates"></a>Delegaty o jednoznacznie określonym typie

[Ubiegł](delegate-class.md)

W poprzednim artykule przedstawiono tworzenie określonych typów delegatów za pomocą słowa kluczowego `delegate`. 

Abstrakcyjna klasa delegatów zapewnia infrastrukturę do swobodnego sprzęgania i wywoływania. Konkretne typy delegatów stają się znacznie bardziej przydatne poprzez stosowanie i wymuszanie bezpieczeństwa typów dla metod, które są dodawane do listy wywołań dla obiektu delegowanego. Gdy używasz słowa kluczowego `delegate` i zdefiniujesz konkretny typ delegata, kompilator generuje te metody.

W tej sytuacji może to spowodować utworzenie nowych typów delegatów, gdy będzie potrzebna inna sygnatura metody. To działanie może uzyskać żmudnym po upływie czasu. Każda nowa funkcja wymaga nowych typów delegatów.

Thankfully, nie jest to konieczne. .NET Core Framework zawiera kilka typów, których można użyć, gdy potrzebne są typy delegatów. Są to definicje [Ogólne](programming-guide/generics/index.md) , dzięki czemu można deklarować dostosowania, gdy potrzebne są nowe deklaracje metody. 

Pierwszy z tych typów jest typem <xref:System.Action> i kilka wariantów:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

Modyfikator `in` dla argumentu typu ogólnego jest pokryty w artykule dotyczącym kowariancji.

Istnieją różne odmiany delegata `Action`, które zawierają do 16 argumentów, takich jak <xref:System.Action%6016>.
Ważne jest, aby te definicje używały różnych argumentów ogólnych dla każdego z argumentów delegata: zapewnia maksymalną elastyczność. Argumenty metody nie muszą być, ale mogą być tego samego typu.

Użyj jednego z typów `Action` dla dowolnego typu delegata, który ma zwracany typ void.

Struktura zawiera również kilka ogólnych typów delegatów, których można użyć dla typów delegatów, które zwracają wartości:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

Modyfikator `out` dla argumentu typu ogólnego wyniku jest pokryty w artykule dotyczącym kowariancji.

Istnieją różne odmiany delegata `Func` z maksymalnie 16 argumentami wejściowymi, takimi jak <xref:System.Func%6017>.
Typ wyniku jest zawsze ostatnim parametrem typu we wszystkich deklaracjach `Func` według Konwencji.

Użyj jednego z typów `Func` dla dowolnego typu delegata, który zwraca wartość.

Istnieje również wyspecjalizowana <xref:System.Predicate%601> 
typ delegata, który zwraca test dla pojedynczej wartości:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Można zauważyć, że dla dowolnego typu `Predicate` istnieje strukturalnie odpowiedni typ `Func` na przykład:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Te dwa typy mogą być uważane za równoważne. Nie są.
Te dwie zmienne nie mogą być używane zamiennie. Zmienna jednego typu nie może być przypisana do innego typu. System C# typów używa nazw zdefiniowanych typów, a nie struktury.

Wszystkie te definicje typów delegatów w bibliotece .NET Core powinny oznaczać, że nie trzeba definiować nowego typu delegata dla każdej nowej funkcji, którą tworzysz, która wymaga delegatów. Te definicje ogólne powinny podawać wszystkie typy delegatów, które są potrzebne w większości sytuacji. Można po prostu utworzyć wystąpienie jednego z tych typów z wymaganymi parametrami typu. W przypadku algorytmów, które mogą być generyczne, te Delegaty mogą być używane jako typy ogólne. 

Powinno to zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć w celu pracy z delegatami.

W następnym artykule zobaczysz kilka typowych wzorców do pracy z delegatami w ćwiczeniu.

[Next](delegates-patterns.md)
