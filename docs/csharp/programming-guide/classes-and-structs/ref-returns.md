---
title: Wartości zwracane ref i ref zmienne lokalne (Przewodnik C#)
description: Dowiedz się, jak zdefiniować i użyć zwracane ref i wartości lokalnej ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 98c58d083cb806a92e28c1c9d27effa1124fd153
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ref-returns-and-ref-locals"></a>Zwraca ref i zmienne lokalne ref

Począwszy od wersji 7.0 C#, C# obsługuje zwracanych wartości odwołanie (ref zwraca). Odwołanie zwracać wartość umożliwia metodę przywrócić odwołania do zmiennej, a nie wartość, obiekt wywołujący. Obiekt wywołujący możliwość traktować zwrócony zmiennej tak, jakby zwrócono według wartości lub według odwołania. Obiekt wywołujący może utworzyć nową zmienną, która jest elementem odwołania do zwrócona wartość ref o nazwie lokalnej.

## <a name="what-is-a-reference-return-value"></a>Co to jest wartością zwracaną odwołania?

Deweloperzy większość zapoznali się z przekazywaniem argumentu metody wywołane *przez odwołanie*. Lista argumentów wywołaną metodę zawiera zmienną przekazywana przez odwołanie. Wszelkie zmiany wprowadzone przez metodę o nazwie jej wartość są przestrzegane przez obiekt wywołujący. A *odwołania do wartości zwracanej* oznacza, że metoda zwraca *odwołania* (lub alias) do niektórych zmiennej. Zakres zmiennej musi zawierać metodę. Okres istnienia tej zmiennej musi wykraczać poza zwracany metody. Do wartości zwracanej przez metodę przez obiekt wywołujący się zmiany do zmiennej, który jest zwracany przez metodę.

Deklarowanie metody zwracające *odwołania zwracana wartość* wskazuje, że ta metoda zwraca alias do zmiennej. Celem projektu jest często, że kod wywołujący powinien mieć dostęp do tej zmiennej za pomocą aliasu, w tym do jej modyfikowania. Wynika, że metody zwracanie przez odwołanie nie może mieć typ zwracany `void`.

Istnieją pewne ograniczenia na wyrażenie, które może zwracać metoda jako wartości zwracane odwołanie. Ograniczenia obejmują:

- Zwracana wartość musi mieć okresu istnienia, która wykracza poza wykonywanie metody. Innymi słowy nie może być zmienną lokalną w metodzie, która zwraca go. Można instancji lub pola statycznego w klasie lub może być argument przekazany do metody. Próby zwracać zmiennej lokalnej generuje błąd kompilatora CS8168, "nie może zwracać lokalnego"obj"przez odwołanie, ponieważ nie jest zmienna lokalna ref."

- Wartość zwrotna nie może być literał `null`. Zwracanie `null` generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."

   Metody z ref zwracany alias można było powrócić do zmiennej, którego wartość jest obecnie wartość null (bez wystąpień) lub [typ dopuszczający wartość null](../nullable-types/index.md) dla typu wartości.
 
- Wartość zwrotna nie może być stałą, elementu członkowskiego wyliczenia, wartość zwracana przez wartości z właściwości lub metody `class` lub `struct`. Naruszenie ta zasada generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."

Ponadto odwołanie zwracać wartości nie są dozwolone w metodach asynchronicznych. Zanim zakończy wykonywanie, gdy jego wartość zwracana jest nadal nieznany, mogą zwracać metody asynchronicznej.
 
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
- Jeśli powraca *przez odwołanie*, jest zwracany alias do tej samej zmiennej.
- W przypadku przekazania do innej metody *przez odwołanie*, jest przekazywany odwołanie do zmiennej go aliasów.
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

`ref` Słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wywołaniem metody. 

Dostępne wartości przez odwołanie w taki sam sposób. W niektórych przypadkach dostępu do wartość przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne. Na przykład następująca instrukcja pokazuje, jak jedną można zdefiniować wartości lokalnej ref, służący do odwołać się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

`ref` Słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wartością w drugim przykładzie. Błąd zawiera zarówno `ref` słów kluczowych w deklaracji zmiennej i przydziałów w obu przykłady powoduje błąd kompilatora CS8172, "nie można zainicjować zmiennej dostępnej przez odwołanie o wartości." 

Przed C# 7.3 zmienne lokalne ref nie były ponownie przypisywane do odwołuje się do innego magazynu zostały już zainicjowane. Ograniczenia zostały usunięte. W poniższym przykładzie przedstawiono ponownego przypisania:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Zmienna lokalna REF nadal musi zostać zainicjowany, jeśli są deklarowane jako.

## <a name="ref-returns-and-ref-locals-an-example"></a>Zwraca ref i zmienne lokalne ref: przykład

W poniższym przykładzie zdefiniowano `NumberStore` klasy, która przechowuje tablicę wartości będące liczbami całkowitymi. `FindNumber` Metoda zwraca wartość przez odwołanie pierwsza liczba, która jest większa lub równa liczbie przekazanego jako argument. Jeśli żadna liczba jest większa niż lub równy argumentowi, metoda zwraca numer indeksu 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Następujące przykładowe wywołania `NumberStore.FindNumber` metoda pobierania pierwsza wartość, która jest większa niż lub równa 16. Obiekt wywołujący następnie podwaja wartość zwrócona przez metodę. Dane wyjściowe z przykładu zawierają zmiany zostaną uwzględnione w wartości elementów tablicy `NumberStore` wystąpienia.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Bez obsługi odwołanie zwracane wartości takie działanie jest wykonywane przez zwrócenie indeks elementu tablicy wraz z jego wartość. Obiekt wywołujący następnie można użyć tego indeksu można zmodyfikować wartości w wywołaniu metody oddzielne. Jednak wywołującego można również zmodyfikować indeks dostępu i możliwie zmodyfikować inne wartości w tablicy.  

W poniższym przykładzie przedstawiono sposób `FindNumber` metody może ulegną po 7.3 C# do użycia lokalnego ponownego przypisania ref:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Ta druga wersja jest bardziej wydajny dłużej sekwencja w scenariuszach, w których liczba poszukiwane jest zbliżonej do końca tablicy.

## <a name="see-also"></a>Zobacz także

[ref keyword](../../language-reference/keywords/ref.md)  
[Semantykę odwołania z typami wartości](../../../csharp/reference-semantics-with-value-types.md)
