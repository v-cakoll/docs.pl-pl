---
title: Wartości zwracane ref i zmienne lokalne ref (Przewodnik C#)
description: Dowiedz się, jak zdefiniować i zastosować zwracane ref i wartości lokalnych typu ref
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: 6399079e17a53ac5bf283eaa5c799964360350f4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146069"
---
# <a name="ref-returns-and-ref-locals"></a>Wartości zwracane ref i zmienne lokalne ref

Począwszy od języka C# 7.0, C# obsługuje wartości zwracane odwołanie (ref zwraca). Odwołanie zwracana wartość umożliwia metodę przywrócić odwołania do zmiennej, a nie wartość, obiekt wywołujący. Obiekt wywołujący możliwość traktować zwrócone zmiennej tak, jakby zostały zwrócone, przez wartość lub przez odwołanie. Obiekt wywołujący, można utworzyć nową zmienną, która sama jest odwołaniem do wartości zwracane ref o nazwie lokalnej.

## <a name="what-is-a-reference-return-value"></a>Co to jest zwracana wartość odniesienia?

Większość programistów zaczynasz przekazywanie argumentu metody o nazwie *przez odwołanie*. Listy argumentów o nazwie metody zawiera zmienną przekazywany przez odwołanie. Wszelkie zmiany wprowadzone do jego wartości przez metodę o nazwie są przestrzegane przez obiekt wywołujący. A *odwoływać się do wartości zwracanej* oznacza, że metoda zwraca *odwołania* (lub aliasem) do niektórych zmiennej. Tę zmienną zakresu musi zawierać metodę. Okres istnienia tej zmiennej musi wykraczać poza zwrotu metody. Do metody wartości zwracanej przez obiekt wywołujący modyfikacje wprowadza do zmiennej, która jest zwracana przez metodę.

Deklarowanie, metoda zwraca *odwoływać się do wartości zwracanej* wskazuje, że metoda zwraca alias do zmiennej. Celem projektu jest często, że kod wywołujący powinni mieć dostęp do tej zmiennej za pomocą aliasu, włączając go zmodyfikować. Wynika, że metody zwracanie przez odwołanie nie może mieć typ zwracany `void`.

Istnieją pewne ograniczenia na wyrażenie, które metoda może zwracać jako odwołanie do wartości zwracanej. Ograniczenia obejmują:

- Zwracana wartość musi mieć okresu istnienia, który wykracza poza wykonywanie metody. Innymi słowy nie może być zmienną lokalną w metodzie, która zwraca go. Może to być wystąpienia lub pole statyczne klasy lub może być argument przekazany do metody. Podjęto próbę zwracanych zmienną lokalną generuje błąd kompilatora CS8168, "nie może zwrócić lokalnego"obj"przez odwołanie, ponieważ nie jest zmienna lokalna ref."

- Zwracana wartość nie może być literał `null`. Zwracanie `null` generuje błąd kompilatora CS8156, "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."

   Metoda z zwracane ref może zwracać alias do zmiennej, którego wartość jest obecnie wartość null (bez wystąpień) lub [typu dopuszczającego wartość null](../nullable-types/index.md) dla typu wartości.
 
- Zwracana wartość nie może być stała, elementu członkowskiego wyliczenia, wartość zwracana przez wartość właściwości lub metody `class` lub `struct`. Naruszenie tej zasady generuje błąd kompilatora CS8156, "nie można użyć wyrażenia w tym kontekście, ponieważ nie mogą być zwrócone przez odwołanie."

Ponadto odwołania zwracanych wartości nie są dozwolone w metodach async. Metoda asynchroniczna może zwracać, zanim zakończy wykonywanie, gdy jego wartość zwracana jest nadal nieznany.
 
## <a name="defining-a-ref-return-value"></a>Definiowanie wartości zwracane ref

Metoda, która zwraca *odwoływać się do wartości zwracanej* musi spełniać następujące dwa warunki:

- Podpis metody zawiera [ref](../../language-reference/keywords/ref.md) — słowo kluczowe przed zwracanym typem.
- Każdy [zwracają](../../language-reference/keywords/return.md) instrukcja w treści metody zawiera [ref](../../language-reference/keywords/ref.md) — słowo kluczowe przed nazwą zwracanego wystąpienia.

W poniższym przykładzie pokazano metodę, która spełnia te warunki i zwraca odwołanie do `Person` obiektu o nazwie `p`:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Korzystanie z wartością zwracaną ref

Odwołania zwracana wartość jest alias do innej zmiennej w zakresie wywoływanej metody. Może interpretować jakiekolwiek użycie zwracane ref, używając zmiennej go aliasy:

- Po przypisaniu jej wartość są przypisywania wartości do zmiennej go aliasów.
- Podczas odczytywania wartości odczytujesz wartość zmiennej go aliasów.
- Jeśli przywrócić go *przez odwołanie*, alias jest zwracany do tej samej zmiennej.
- W przypadku przekazania do innej metody *przez odwołanie*, kończy się sukcesem odwołania do zmiennej go aliasów.
- Po ustawieniu [odwołanie lokalne](#ref-locals) alias, należy wprowadzić nowy alias tę samą zmienną.


## <a name="ref-locals"></a>Zmienne lokalne REF

Załóżmy `GetContactInformation` metody jest zadeklarowany jako ref zwracany:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Przypisania przez wartość odczytuje wartość zmiennej, a następnie przypisuje go do nowej zmiennej:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Deklaruje poprzedniego przypisania `p` jako zmienna lokalna. Wartość początkowa jest kopiowany z odczytywania wartości zwracanej przez `GetContactInformation`. Wszystkie przyszłe przypisania do `p` nie zmieni się wartość zmiennej zwrócony przez `GetContactInformation`. Zmienna `p` nie jest już aliasem do zmiennej, zwracany.

Możesz deklarować *odwołanie lokalne* zmiennej, aby skopiować alias do oryginalnej wartości. W następujących przypisaniu `p` alias dla zmiennej zwróciło `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Kolejne użycie `p` jest taka sama jak za pomocą zmiennej zwrócony przez `GetContactInformation` ponieważ `p` jest aliasem dla tej zmiennej. Zmienia się na `p` również zmienić zmienną zwróciło `GetContactInformation`.

`ref` Słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wywołaniem metody. 

Dostępne wartości przez odwołanie, w taki sam sposób. W niektórych przypadkach uzyskiwanie dostępu do wartości przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne. Na przykład następująca instrukcja pokazuje, jak jeden można zdefiniować wartości lokalnej ref, służący do odwoływać się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

`ref` Słowo kluczowe jest używane zarówno przed deklaracji zmiennej lokalnej *i* przed wartością w drugim przykładzie. Niepodanie zarówno `ref` słów kluczowych w deklaracji zmiennej i przydziałów w obu przykładach skutkuje błąd kompilatora CS8172, "nie można zainicjować zmiennej o wartości przez odwołanie." 

Przed C# 7.3 zmienne lokalne ref nie można ponownie przypisać do odwoływania się do innego magazynu zostały już zainicjowane. Tego ograniczenia zostały usunięte. Poniższy przykład przedstawia ponowne przypisanie:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Zmienne lokalne REF nadal musi być inicjowana, gdy są one zgłoszone.

## <a name="ref-returns-and-ref-locals-an-example"></a>Wartości zwracane ref i zmienne lokalne ref: przykład

W poniższym przykładzie zdefiniowano `NumberStore` klasę, która przechowuje tablicę wartości całkowitych. `FindNumber` Metoda zwraca wartość przez odwołanie pierwsza liczba, która jest większa lub równa liczbie przekazywany jako argument. Jeśli żadna liczba nie jest większa lub równa wartości argumentu, metoda zwraca numer indeksu 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Poniższy przykład wywołuje `NumberStore.FindNumber` metodę, która pobierze pierwszą wartość, która jest większa niż lub równe 16. Obiekt wywołujący podwaja się następnie wartość zwracana przez metodę. Dane wyjściowe z przykładu przedstawia zmiany zostaną uwzględnione w wartości elementów tablicy `NumberStore` wystąpienia.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Bez obsługi wartości zwracane odwołanie taka operacja jest wykonywana przez zwraca indeks elementu tablicy, wraz z jego wartość. Obiekt wywołujący do modyfikowania wartości w wywołaniu metody oddzielne, następnie można użyć tego indeksu. Jednak obiekt wywołujący, można również zmodyfikować indeks, aby uzyskać dostęp i możliwie zmodyfikować pozostałe wartości w tablicy.  

W poniższym przykładzie pokazano sposób, w jaki `FindNumber` metody, które można dopasować po języka C# 7.3 do użycia lokalnego ponowne przypisanie atrybutu ref:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Ta druga wersja jest bardziej wydajne, za pomocą sekwencji dłużej w scenariuszach, gdzie numer poszukiwane jest bliżej końca tablicy.

## <a name="see-also"></a>Zobacz także

- [ref keyword](../../language-reference/keywords/ref.md)  
- [Pisanie kodu efektywne bezpieczne](../../write-safe-efficient-code.md)
