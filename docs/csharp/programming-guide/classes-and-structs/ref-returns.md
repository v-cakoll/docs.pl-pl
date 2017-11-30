---
title: "Wartości zwracane ref i ref zmienne lokalne (Przewodnik C#)"
description: "Dowiedz się, jak zdefiniować i użyć zwracane ref i wartości lokalnej ref"
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 18cf7a4b-29f0-4b14-85b8-80af754aabd8
ms.openlocfilehash: 1d8fb092b578602b5d4f791a3fd14f47dfae1ba6
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="ref-returns-and-ref-locals"></a>Zwraca ref i zmienne lokalne ref

Począwszy od C# 7, C# obsługuje zwracanych wartości odwołanie (ref zwraca). Odwołanie zwracać wartość umożliwia metodę przywrócić odwołania do obiektu, a nie wartość, obiekt wywołujący. Obiekt wywołujący możliwość Traktuj zwrócony obiekt zwrócony tak, jakby zwrócono według wartości lub według odwołania. Wartość zwracana przez odwołanie, czy element wywołujący obsługuje jako odwołanie, a nie wartość jest zmienna lokalna ref.

## <a name="what-is-a-reference-return-value"></a>Co to jest wartością zwracaną odwołania?

Deweloperzy większość zapoznali się z przekazywaniem argumentu metody wywołane *przez odwołanie*. Argument wywołaną metodę się, że lista zawiera wartości przekazywane przez odwołanie, a wszelkie zmiany wprowadzone do jego wartości przez metodę o nazwie są zwracane do obiektu wywołującego. A *odwołania do wartości zwracanej* odwrotny:

- Wywołana metoda zwracanej wartości, zamiast argument przekazany do niej, to odwołanie.

- Obiekt wywołujący, zamiast wywołaną metodę można zmodyfikować wartość zwrócona przez metodę.

- Zamiast zmiany do argumentu, które zostaną odzwierciedlone w stan obiektu na element wywołujący zmiany w wartości zwracanej przez metodę przez obiekt wywołujący zostaną odzwierciedlone w stan obiektu, którego metoda została wywołana.

Odwołanie zwracane wartości można utworzyć mniejszych kodu, a także zezwala na udostępnianie tylko poszczególnych elementów danych, takich jak elementu tablicy interesujące do obiektu wywołującego obiektu. Zmniejsza to prawdopodobieństwo wywołującego przypadkowo zmodyfikuje stan obiektu.

Istnieją pewne ograniczenia na wartość, która może zwracać metoda jako wartości zwracane odwołanie. Należą do nich następujące elementy:

- Wartość zwrotna nie może być `void`. Podjęto próbę zdefiniowania metody z `void` wartości zwracanej odwołanie generuje błąd kompilatora CS1547, "W tym kontekście nie można użyć słowa kluczowego"void"."
 
- Wartość zwrotna nie może być zmienną lokalną w metodzie, która zwraca musi mieć zakres, w którym znajduje się poza metodę, która zwraca go. Można instancji lub pola statycznego w klasie lub może być argument przekazany do metody. Próby zwracać zmiennej lokalnej generuje błąd kompilatora CS8168, "nie może zwracać lokalnego"obj"przez odwołanie, ponieważ nie jest zmienna lokalna ref."

- Wartość zwrotna nie może być `null`. Podjęto próbę zwracać `null` generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."

   Jeśli metodę o ref zwracany musi zwracać wartość null, albo może zwracać wartości null (bez wystąpień) dla typu odwołania lub [typ dopuszczający wartość null](../nullable-types/index.md) dla typu wartości.
 
- Wartość zwrotna nie może być stałą, elementu członkowskiego wyliczenia lub właściwości `class` lub `struct`. Próba zwrócić te generuje błąd kompilatora CS8156 "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."

Ponadto ponieważ może zwracać metodę asynchroniczną, zanim zakończy wykonywanie, gdy jego wartość zwracana jest nadal nieznany, odwołanie zwracane wartości są niedozwolone w metodach asynchronicznych.
 
## <a name="defining-a-ref-return-value"></a>Definiowanie wartości zwracanej ref

Zdefiniuj ref wartości zwracanej przez dodanie [ref](../../language-reference/keywords/ref.md) — słowo kluczowe na zwracany typ sygnatury metody. Na przykład następująca sygnatura wskazuje, że `GetContactInformation` właściwość zwraca odwołanie do `Person` obiektu do obiektu wywołującego:

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

Ponadto nazwa obiektu zwracaną przez każdy [zwracać](../../language-reference/keywords/return.md) instrukcji w treści metody musi być poprzedzona [ref](../../language-reference/keywords/ref.md) — słowo kluczowe. Na przykład następująca `return` zwraca instrukcji `Person` obiektu o nazwie `p` przez odwołanie:

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a>Korzystanie z wartością zwracaną ref

Obiekt wywołujący może obsłużyć ref wartości zwracanej w jeden z dwóch sposobów:

- Jako wartość zwykłej zwrócony przez wartości z metody. Obiekt wywołujący można zignorować, że zwracana wartość jest wartością zwracaną odwołania. W takim przypadku wszelkie zmiany wprowadzone do wartości zwróconej przez wywołanie metody nie są odzwierciedlane w stanie nazwie typu. Zwrócona wartość jest typem wartości, wszelkie zmiany wprowadzone do wartości zwróconej przez wywołanie metody nie są odzwierciedlane w stanie nazwie typu.

- Wartość zwracana jako odwołanie. Obiekt wywołujący musi definiować zmiennej, do której przypisany jest zwracana wartość odwołanie jako [lokalnej typu ref](#ref-local), a wartość zwrócona przez wywołanie metody wszelkie zmiany zostaną odzwierciedlone w stanie typu o nazwie. 

## <a name="ref-locals"></a>Zmienne lokalne REF

Do obsługi wartość zwracaną odwołanie jako odwołanie, wywołujący musi deklarować wartość *lokalnej typu ref* za pomocą `ref` — słowo kluczowe. Na przykład, jeśli wartość zwracana przez `Person.GetContactInfomation` metody ma być używane jako odwołanie, a nie wartość, wywołanie metody ma postać:

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Należy pamiętać, że `ref` słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wywołaniem metody. Błąd zawiera zarówno `ref` słów kluczowych w deklaracji zmiennej i przypisania powoduje błąd kompilatora CS8172, "nie można zainicjować zmiennej dostępnej przez odwołanie o wartości." 
 
Kolejne zmiany do `Person` odzwierciedlone w obiekcie zwracanym przez metodę `contacts` obiektu.

Jeśli `p` nie jest zdefiniowany jako zmienna lokalna ref przy użyciu `ref` — słowo kluczowe, wszelkie zmiany wprowadzone do `p` przez obiekt wywołujący nie są uwzględniane w `contacts` obiektu.
 
## <a name="ref-returns-and-ref-locals-an-example"></a>Zwraca ref i zmienne lokalne ref: przykład

W poniższym przykładzie zdefiniowano `NumberStore` klasy, która przechowuje tablicę wartości będące liczbami całkowitymi. `FindNumber` Metoda zwraca wartość przez odwołanie pierwsza liczba, która jest większa lub równa liczbie przekazanego jako argument. Jeśli żadna liczba jest większa niż lub równy argumentowi, metoda zwraca numer indeksu 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

Następujące przykładowe wywołania `NumberStore.FindNumber` metoda pobierania pierwsza wartość, która jest większa niż lub równa 16. Obiekt wywołujący następnie podwaja wartość zwrócona przez metodę. Jak dane wyjściowe w przykładzie pokazano, ta zmiana ta jest uwzględniana w wartości elementów tablicy `NumberStore` wystąpienia.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

Takie działanie bez obsługi zwracanych wartości odwołania, zwykle odbywa się zwracając indeks elementu tablicy wraz z jego wartość. Obiekt wywołujący następnie można użyć tego indeksu można zmodyfikować wartości w wywołaniu metody oddzielne. Jednak wywołującego można również zmodyfikować indeks dostępu i możliwie zmodyfikować inne wartości w tablicy.  
 
## <a name="see-also"></a>Zobacz także

[REF — słowo kluczowe](../../language-reference/keywords/ref.md)
