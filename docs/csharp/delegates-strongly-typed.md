---
title: Delegaty o jednoznacznie określonym typie
description: Dowiedz się, jak używać ogólnych typów delegatów do deklarowania typów niestandardowych podczas tworzenia funkcji wymagającej delegatów.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 798e8b597389bc99d10e587ec417a4e717f28abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146206"
---
# <a name="strongly-typed-delegates"></a>Delegaty o jednoznacznie określonym typie

[Wstecz](delegate-class.md)

W poprzednim artykule widać, że tworzysz określone `delegate` typy delegatów przy użyciu słowa kluczowego.

Abstrakcyjne Delegate klasy zapewniają infrastrukturę dla luźne sprzężenia i wywołania. Konkretne typy delegatów stają się znacznie bardziej przydatne, obejmując i wymuszając bezpieczeństwo typów dla metod, które są dodawane do listy wywołania dla obiektu delegata. Korzystając ze `delegate` słowa kluczowego i zdefiniować konkretny typ delegata, kompilator generuje te metody.

W praktyce prowadzi to do tworzenia nowych typów delegatów, gdy potrzebujesz podpisu innej metody. Ta praca może stać się nużące po jakauroku. Każda nowa funkcja wymaga nowych typów delegatów.

Na szczęście nie jest to konieczne. Struktura .NET Core zawiera kilka typów, które można ponownie użyć, gdy potrzebujesz typów delegatów. Są to definicje [ogólne,](programming-guide/generics/index.md) dzięki czemu można zadeklarować dostosowania, gdy potrzebujesz deklaracji nowych metod.

Pierwszym z tych typów <xref:System.Action> jest typ i kilka odmian:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

Modyfikator `in` na argument typu ogólnego jest omówione w artykule na kowariancji.

Istnieją odmiany delegata, `Action` które zawierają do 16 <xref:System.Action%6016>argumentów, takich jak .
Ważne jest, aby te definicje używać różnych argumentów ogólnych dla każdego z argumentów delegata: To daje maksymalną elastyczność. Argumenty metody nie muszą być, ale mogą być tego samego typu.

Użyj jednego `Action` z typów dla dowolnego typu delegata, który ma typ zwracany unieważnienia.

Struktura zawiera również kilka typów delegatów ogólnych, które można użyć dla typów delegatów, które zwracają wartości:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

Modyfikator `out` argumentu wynikowego typu ogólnego jest omówiony w artykule na kowariancję.

Istnieją odmiany delegata `Func` z maksymalnie 16 argumentami <xref:System.Func%6017>wejściowymi, takimi jak .
Typ wyniku jest zawsze ostatni parametr typu `Func` we wszystkich deklaracjach, zgodnie z konwencją.

Użyj jednego `Func` z typów dla dowolnego typu delegata, który zwraca wartość.

Istnieje również wyspecjalizowana<xref:System.Predicate%601>
typ pełnomocnika, który zwraca test na pojedynczą wartość:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Można zauważyć, że `Predicate` dla każdego typu `Func` istnieje typ strukturalnie równoważny Na przykład:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Można by pomyśleć, że te dwa typy są równoważne. Nie są.
Te dwie zmienne nie mogą być używane zamiennie. Zmiennej jednego typu nie można przypisać drugiego typu. System typu C# używa nazw zdefiniowanych typów, a nie struktury.

Wszystkie te definicje typów delegatów w bibliotece .NET Core powinny oznaczać, że nie trzeba definiować nowego typu delegata dla każdej nowej funkcji, która wymaga delegatów. Te definicje ogólne powinny zawierać wszystkie typy delegatów, których potrzebujesz w większości sytuacji. Można po prostu utworzyć wystąpienia jednego z tych typów z wymaganymi parametrami typu. W przypadku algorytmów, które mogą być ogólne, tych delegatów mogą służyć jako typy ogólne.

Powinno to zaoszczędzić czas i zminimalizować liczbę nowych typów, które należy utworzyć w celu pracy z delegatów.

W następnym artykule zobaczysz kilka typowych wzorców do pracy z delegatami w praktyce.

[Dalej](delegates-patterns.md)
