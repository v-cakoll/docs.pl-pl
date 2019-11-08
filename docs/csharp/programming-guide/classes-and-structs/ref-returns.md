---
title: Wartości zwracane ref i lokalne elementy ref (C# przewodnik)
description: Dowiedz się, jak definiować i używać lokalnych wartości zwrotnych i ref
ms.date: 04/04/2018
ms.openlocfilehash: 7ade422b5b3805ef2e1f487252a98fb85cdfe70c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736819"
---
# <a name="ref-returns-and-ref-locals"></a>Wartości zwracane ref i zmienne lokalne ref

Począwszy od C# 7,0, C# obsługuje zwracane wartości odwołania (zwroty ref). Wartość zwracana przez odwołanie umożliwia metodzie zwracanie odwołania do zmiennej, a nie wartości, z powrotem do obiektu wywołującego. Obiekt wywołujący może następnie traktować zwracaną zmienną, tak jakby była zwracana przez wartość lub przez odwołanie. Obiekt wywołujący może utworzyć nową zmienną, która sama jest odwołaniem do zwracanej wartości o nazwie ref Local.

## <a name="what-is-a-reference-return-value"></a>Co to jest zwrócona wartość odwołania?

Większość deweloperów zna przekazywanie argumentu do wywoływanej metody *przez odwołanie*. Lista argumentów wywoływanej metody zawiera zmienną przekazaną przez odwołanie. Wszystkie zmiany wprowadzone do jego wartości przez wywołaną metodę są obserwowane przez obiekt wywołujący. *Wartość zwracana przez odwołanie* oznacza, że metoda zwraca *odwołanie* (lub alias) do pewnej zmiennej. Zakres tej zmiennej musi zawierać metodę. Okres istnienia tej zmiennej musi przekraczać wartość zwracaną przez metodę. Modyfikacje wartości zwracanej metody przez obiekt wywołujący są wprowadzane do zmiennej, która jest zwracana przez metodę.

Deklarowanie, że metoda zwraca *odwołanie* do zwracanej wartości wskazuje, że metoda zwraca alias do zmiennej. Zamiarem projektowania często jest to, że kod wywołujący powinien mieć dostęp do tej zmiennej za pomocą aliasu, w tym do modyfikowania. Wynika to z tego, że metody zwracające przez odwołanie nie mogą mieć zwracanego typu `void`.

Istnieją pewne ograniczenia dotyczące wyrażenia, które Metoda może zwrócić jako wartość zwracana przez odwołanie. Ograniczenia obejmują:

- Wartość zwracana musi mieć okres istnienia wykraczający poza wykonywanie metody. Innymi słowy, nie może być zmienną lokalną w metodzie, która zwraca ją. Może to być wystąpienie lub statyczne pole klasy albo argument przeszedł do metody. Próba zwrócenia zmiennej lokalnej powoduje wygenerowanie błędu kompilatora CS8168, "nie można zwrócić lokalnego elementu" obj "przez odwołanie, ponieważ nie jest to lokalne odwołanie".

- Zwracana wartość nie może być literałem `null`. Zwracanie `null` generuje błąd kompilatora CS8156 "wyrażenie nie może być używane w tym kontekście, ponieważ może nie zostać zwrócone przez odwołanie".

   Metoda ze zwróceniem ref może zwracać alias do zmiennej, której wartość jest obecnie wartością null (niebędącą wystąpieniem) lub [typem wartości null](../../language-reference/builtin-types/nullable-value-types.md) dla typu wartości.

- Zwracana wartość nie może być stałą, składową wyliczenia, wartością zwracaną przez wartość z właściwości lub metodą `class` lub `struct`. Naruszenie tej reguły powoduje wygenerowanie błędu kompilatora CS8156, "nie można użyć wyrażenia w tym kontekście, ponieważ może ono nie zostać zwrócone przez odwołanie".

Dodatkowo odwołania do zwracanych wartości nie są dozwolone w metodach asynchronicznych. Metoda asynchroniczna może zostać zwrócona przed zakończeniem wykonywania, podczas gdy jej wartość zwracana jest nadal nieznana.

## <a name="defining-a-ref-return-value"></a>Definiowanie wartości zwracanej ref

Metoda zwracająca *wartość zwracaną przez odwołanie* musi spełniać następujące dwa warunki:

- Podpis metody zawiera słowo kluczowe [ref](../../language-reference/keywords/ref.md) przed typem zwracanym.
- Każda instrukcja [Return](../../language-reference/keywords/return.md) w treści metody zawiera słowo kluczowe [ref](../../language-reference/keywords/ref.md) przed nazwą zwracanego wystąpienia.

Poniższy przykład przedstawia metodę, która spełnia te warunki i zwraca odwołanie do obiektu `Person` o nazwie `p`:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Zużywanie referencyjnej wartości zwracanej

Zwracana wartość Ref jest aliasem innej zmiennej w zakresie wywołanej metody. Można interpretować dowolne użycie Return ref jako przy użyciu zmiennej aliasu IT:

- Po przypisaniu jego wartości przypisujesz wartość do zmiennej aliasu IT.
- Podczas odczytywania wartości, odczytywana jest wartość zmiennej aliasu IT.
- Jeśli zwracasz ją *przez odwołanie*, zwracasz alias do tej samej zmiennej.
- Jeśli przekażesz go do innej metody *przez odwołanie*, przekazujesz odwołanie do zmiennej aliasu IT.
- Po wprowadzeniu aliasu [lokalnego ref](#ref-locals) należy utworzyć nowy alias do tej samej zmiennej.

## <a name="ref-locals"></a>Odwołania lokalne

Załóżmy, że metoda `GetContactInformation` jest zadeklarowana jako Return ref:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Przypisanie przez wartość odczytuje wartość zmiennej i przypisuje ją do nowej zmiennej:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Poprzednie przypisanie deklaruje `p` jako zmienną lokalną. Jego początkowa wartość jest kopiowana z odczytywania wartości zwracanej przez `GetContactInformation`. Wszelkie przyszłe przypisania do `p` nie zmienią wartości zmiennej zwracanej przez `GetContactInformation`. Zmienna `p` nie jest już aliasem zwracanej zmiennej.

Zadeklaruj zmienną *lokalną ref* , aby skopiować alias do oryginalnej wartości. W poniższym przypisaniu `p` jest aliasem zmiennej zwracanej z `GetContactInformation`.

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Kolejne użycie `p` jest taka sama jak przy użyciu zmiennej zwracanej przez `GetContactInformation`, ponieważ `p` jest aliasem dla tej zmiennej. Zmiany w `p` również zmieniają zmienną zwróconą z `GetContactInformation`.

Słowo kluczowe `ref` jest używane przed deklaracją zmiennej lokalnej *i* przed wywołaniem metody. 

Możesz uzyskać dostęp do wartości przez odwołanie w ten sam sposób. W niektórych przypadkach uzyskanie dostępu do wartości przez odwołanie zwiększa wydajność poprzez uniknięcie potencjalnie kosztownej operacji kopiowania. Na przykład poniższa instrukcja pokazuje, jak jedna z nich może definiować wartość lokalna ref, która jest używana do odwoływania się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Słowo kluczowe `ref` jest używane przed deklaracją zmiennej lokalnej *i* przed wartością w drugim przykładzie. Nie można uwzględnić obydwu `ref` słów kluczowych w deklaracji zmiennej i przypisaniu w obu przykładach skutkuje błędem kompilatora CS8172 ". 

Przed C# 7,3, nie można ponownie przypisać odwołań do zmiennych lokalnych w celu odwoływania się do innego magazynu po zainicjowaniu. To ograniczenie zostało usunięte. W poniższym przykładzie przedstawiono ponowne przypisanie:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Po zadeklarowaniu należy nadal inicjować zmienne lokalne ref.

## <a name="ref-returns-and-ref-locals-an-example"></a>Zwroty ref i lokalne elementy ref: przykład

W poniższym przykładzie zdefiniowano klasę `NumberStore`, która przechowuje tablicę wartości całkowitych. Metoda `FindNumber` zwraca przez odwołanie do pierwszej liczby, która jest większa lub równa liczbie przesłanej jako argument. Jeśli żadna liczba nie jest większa lub równa argumentowi, metoda zwraca liczbę w indeksie 0. 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Poniższy przykład wywołuje metodę `NumberStore.FindNumber`, aby pobrać pierwszą wartość, która jest większa lub równa 16. Obiekt wywołujący następnie podwaja wartość zwróconą przez metodę. Dane wyjściowe z przykładu przedstawiają zmianę odzwierciedloną w wartości elementów tablicy wystąpienia `NumberStore`.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Bez obsługi wartości zwracanych odwołań, taka operacja jest wykonywana przez zwrócenie indeksu elementu tablicy wraz z jego wartością. Obiekt wywołujący może następnie użyć tego indeksu do zmodyfikowania wartości w osobnym wywołaniu metody. Jednak obiekt wywołujący może także zmodyfikować indeks, aby uzyskać dostęp do innych wartości tablicy i prawdopodobnie je zmodyfikować.  

Poniższy przykład pokazuje, jak można ponownie napisać metodę `FindNumber` po C# 7,3 do użycia lokalnego ponownego przypisania odwołania:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Ta druga wersja jest wydajniejsza z dłuższymi sekwencjami w scenariuszach, w których liczba poszukiwanych elementów jest bliżej końca tablicy.

## <a name="see-also"></a>Zobacz także

- [ref — słowo kluczowe](../../language-reference/keywords/ref.md)
- [Zapisz bezpieczny wydajny kod](../../write-safe-efficient-code.md)
