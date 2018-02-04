---
title: "Wartości zwracane ref i ref zmienne lokalne (Przewodnik C#)"
description: "Dowiedz się, jak zdefiniować i użyć zwracane ref i wartości lokalnej ref"
author: rpetrusha
ms.author: ronpet
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: a74563c0d24b6cd2a2fa8534787f078f3cc92674
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="ref-returns-and-ref-locals"></a>Zwraca ref i zmienne lokalne ref

Począwszy od C# 7, C# obsługuje zwracanych wartości odwołanie (ref zwraca). Odwołanie zwracać wartość umożliwia metodę przywrócić odwołania do zmiennej, a nie wartość, obiekt wywołujący. Obiekt wywołujący możliwość traktować zwrócony zmiennej tak, jakby zwrócono według wartości lub według odwołania. Obiekt wywołujący może utworzyć nową zmienną, która jest elementem odwołania do zwrócona wartość ref o nazwie lokalnej.

## <a name="what-is-a-reference-return-value"></a>Co to jest wartością zwracaną odwołania?

Deweloperzy większość zapoznali się z przekazywaniem argumentu metody wywołane *przez odwołanie*. Argument wywołaną metodę się, że lista zawiera zmienną przekazywane przez odwołanie, a wszelkie zmiany wprowadzone do jego wartości przez metodę o nazwie są przestrzegane przez obiekt wywołujący. A *odwołania do wartości zwracanej* oznacza, że metoda zwraca *odwołania* (lub alias) do niektórych zmiennej którego zakres obejmuje metodę i którego okres istnienia muszą być rozszerzane poza zwracany metody. Do wartości zwracanej przez metodę przez obiekt wywołujący się zmiany do zmiennej, który jest zwracany przez metodę.

Deklarowanie metody zwracające *odwołania zwracana wartość* wskazuje, że ta metoda zwraca alias do zmiennej. Celem projektu jest często, że kod wywołujący powinien mieć dostęp do tej zmiennej za pomocą aliasu, w tym do jej modyfikowania. Wynika, że metody zwracanie przez odwołanie nie może mieć typ zwracany `void`.

Istnieją pewne ograniczenia na wyrażenie, które może zwracać metoda jako wartości zwracane odwołanie. Należą do nich następujące elementy:

- Zwracana wartość musi mieć okresu istnienia, która wykracza poza wykonywanie metody. Innymi słowy nie może być zmienną lokalną w metodzie, która zwraca go. Można instancji lub pola statycznego w klasie lub może być argument przekazany do metody. Próby zwracać zmiennej lokalnej generuje błąd kompilatora CS8168, "nie może zwracać lokalnego"obj"przez odwołanie, ponieważ nie jest zmienna lokalna ref."

- Wartość zwrotna nie może być literał `null`. Podjęto próbę zwracać `null` generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."

   Metody z ref zwracany alias można było powrócić do zmiennej, którego wartość jest obecnie wartość null (bez wystąpień) lub [typ dopuszczający wartość null](../nullable-types/index.md) dla typu wartości.
 
- Wartość zwrotna nie może być stałą, elementu członkowskiego wyliczenia, wartość zwracana przez wartości z właściwości lub metody `class` lub `struct`. Próba zwrócić te generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."

Ponadto ponieważ może zwracać metodę asynchroniczną, zanim zakończy wykonywanie, gdy jego wartość zwracana jest nadal nieznany, odwołanie zwracane wartości są niedozwolone w metodach asynchronicznych.
 
## <a name="defining-a-ref-return-value"></a>Definiowanie wartości zwracanej ref

Zdefiniuj ref wartości zwracanej przez dodanie [ref](../../language-reference/keywords/ref.md) — słowo kluczowe na zwracany typ sygnatury metody. Na przykład następująca sygnatura wskazuje, że `GetContactInformation` właściwość zwraca odwołanie do `Person` obiektu do obiektu wywołującego:

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

Ponadto nazwa obiektu zwracaną przez każdy [zwracać](../../language-reference/keywords/return.md) instrukcji w treści metody musi być poprzedzona [ref](../../language-reference/keywords/ref.md) — słowo kluczowe. Na przykład następująca `return` instrukcja zwraca odwołanie do `Person` obiektu o nazwie `p`:

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>Korzystanie z wartością zwracaną ref

Ref zwracać wartość jest alias do innej zmiennej w zakresie wywołaną metodę. Można odnaleźć żadnego użycie ref zwracany jako przy użyciu zmiennej go aliasy:

- Po przypisaniu jej wartość są przypisywanie wartości do zmiennej go aliasów.
- Podczas czytania wartość odczytywania wartości zmiennej go aliasów.
- Jeśli powraca *przez odwołanie* alias jest zwracany do tej samej zmiennej.
- W przypadku przekazania do innej metody *przez odwołanie* przekazywane odwołanie do zmiennej go aliasów.
- Po dokonaniu [lokalnej typu ref](#ref-local) aliasu, możesz wprowadzić nowy alias tę samą zmienną.


## <a name="ref-locals"></a>Zmienne lokalne REF

Załóżmy `GetContactInformation` metoda jest zadeklarowana jako wartości ref zwrotu:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Przypisania przez wartość odczytuje wartość zmiennej i przypisuje go do nowej zmiennej:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Deklaruje poprzedniego przypisania `p` jako zmiennej lokalnej. Swojej wartości początkowej zostanie skopiowana ze odczytywania wartości zwróconej przez `GetContactInformation`. Przyszłe przydziały w celu `p` nie zmieni się wartość zmiennej zwrócony przez `GetContactInformation`. Zmienna `p` nie jest już alias do zmiennej zwracane.

Należy zadeklarować *lokalnej typu ref* zmiennej, aby skopiować alias do oryginalnej wartości. W następujących przypisania `p` jest alias do zmiennej zwrócony z `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Użycie kolejnych `p` jest taka sama jak przy użyciu zmiennej zwrócony przez `GetContactInformation` ponieważ `p` jest aliasu dla tej zmiennej. Zmienia się na `p` również zmienić zmiennej zwrócony z `GetContactInformation`.

Należy pamiętać, że `ref` słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wywołaniem metody. Błąd zawiera zarówno `ref` słów kluczowych w deklaracji zmiennej i przypisania powoduje błąd kompilatora CS8172, "nie można zainicjować zmiennej dostępnej przez odwołanie o wartości." 
 
## <a name="ref-returns-and-ref-locals-an-example"></a>Zwraca ref i zmienne lokalne ref: przykład

W poniższym przykładzie zdefiniowano `NumberStore` klasy, która przechowuje tablicę wartości będące liczbami całkowitymi. `FindNumber` Metoda zwraca wartość przez odwołanie pierwsza liczba, która jest większa lub równa liczbie przekazanego jako argument. Jeśli żadna liczba jest większa niż lub równy argumentowi, metoda zwraca numer indeksu 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

Następujące przykładowe wywołania `NumberStore.FindNumber` metoda pobierania pierwsza wartość, która jest większa niż lub równa 16. Obiekt wywołujący następnie podwaja wartość zwrócona przez metodę. Jak dane wyjściowe w przykładzie pokazano, ta zmiana ta jest uwzględniana w wartości elementów tablicy `NumberStore` wystąpienia.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

Takie działanie bez obsługi zwracanych wartości odwołania, zwykle odbywa się zwracając indeks elementu tablicy wraz z jego wartość. Obiekt wywołujący następnie można użyć tego indeksu można zmodyfikować wartości w wywołaniu metody oddzielne. Jednak wywołującego można również zmodyfikować indeks dostępu i możliwie zmodyfikować inne wartości w tablicy.  
 
## <a name="see-also"></a>Zobacz także

[ref keyword](../../language-reference/keywords/ref.md)
