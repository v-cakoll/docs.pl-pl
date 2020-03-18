---
title: Ref zwraca wartości i ref locals (C# Przewodnik)
description: Dowiedz się, jak definiować i używać wartości ref return i ref local
ms.date: 04/04/2018
ms.openlocfilehash: 87a9538db60d69062f0fb48ed9683a9d4f972b91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170076"
---
# <a name="ref-returns-and-ref-locals"></a>Wartości zwracane ref i zmienne lokalne ref

Począwszy od Języka C# 7.0, C# obsługuje wartości zwracane odwołania (ref zwraca). Wartość zwracana odwołania umożliwia metody, aby zwrócić odwołanie do zmiennej, a nie wartość, z powrotem do obiektu wywołującego. Obiekt wywołujący może następnie traktować zwróconą zmienną tak, jakby została zwrócona przez wartość lub odwołanie. Obiekt wywołujący można utworzyć nową zmienną, która sama odwołuje się do zwracanej wartości, o nazwie ref local.

## <a name="what-is-a-reference-return-value"></a>Co to jest wartość zwracana odwołania?

Większość deweloperów są zaznajomieni z przekazywanie argumentu do metody wywoływanej *przez odwołanie*. Lista argumentów metody o nazwie zawiera zmienną przekazaną przez odwołanie. Wszelkie zmiany wprowadzone do jego wartości przez wywoływaną metodę są obserwowane przez obiekt wywołujący. *Wartość zwracana odwołania* oznacza, że metoda zwraca *odwołanie* (lub alias) do niektórych zmiennych. Zakres tej zmiennej musi zawierać metodę. Okres istnienia tej zmiennej musi wykraczać poza zwrot metody. Modyfikacje wartości zwracanej metody przez obiekt wywołujący są dokonywane do zmiennej, która jest zwracana przez metodę.

Deklarowanie, że metoda zwraca *wartość zwracaną odwołanie* wskazuje, że metoda zwraca alias do zmiennej. Intencją projektu jest często, że kod wywołujący powinien mieć dostęp do tej zmiennej za pośrednictwem aliasu, w tym do modyfikowania go. Wynika z tego, że metody zwracane przez odwołanie `void`nie mogą mieć typu zwracanego .

Istnieją pewne ograniczenia dotyczące wyrażenia, które metoda może zwrócić jako wartość zwracana odwołania. Ograniczenia obejmują:

- Wartość zwracana musi mieć okres istnienia, który wykracza poza wykonanie metody. Innymi słowy nie może być zmienną lokalną w metodzie, która zwraca go. Może to być wystąpienie lub statyczne pole klasy lub może to być argument przekazany do metody. Próba zwrócenia zmiennej lokalnej generuje błąd kompilatora CS8168, "Nie można zwrócić lokalnego 'obj' przez odwołanie, ponieważ nie jest ref lokalny."

- Wartość zwracana nie `null`może być literałem . Zwracanie `null` generuje błąd kompilatora CS8156, "Wyrażenie nie może być używany w tym kontekście, ponieważ nie może być zwracany przez odwołanie."

   Metoda z ref return może zwrócić alias do zmiennej, której wartość jest obecnie wartość null (uninstantiated) lub [typu wartości null](../../language-reference/builtin-types/nullable-value-types.md) dla typu wartości.

- Wartość zwracana nie może być stała, element członkowski wyliczenia, wartość zwracana według wartości z właściwości lub metody `class` lub `struct`. Naruszenie tej reguły generuje błąd kompilatora CS8156, "Wyrażenie nie może być używane w tym kontekście, ponieważ nie może być zwracany przez odwołanie."

Ponadto wartości zwracane odwołania nie są dozwolone w metodach asynchronicznej. Metoda asynchroniczna może zwrócić przed zakończeniem wykonywania, podczas gdy jego wartość zwracana jest nadal nieznany.

## <a name="defining-a-ref-return-value"></a>Definiowanie wartości zwracanej ref

Metoda zwracająca *wartość zwracaną odwołanie* musi spełniać następujące dwa warunki:

- Podpis metody zawiera [ref](../../language-reference/keywords/ref.md) słowa kluczowego przed typem zwracanego.
- Każda [instrukcja return](../../language-reference/keywords/return.md) w treści metody zawiera [ref](../../language-reference/keywords/ref.md) słowa kluczowego przed nazwą zwróconego wystąpienia.

W poniższym przykładzie przedstawiono metodę, która spełnia te `Person` warunki `p`i zwraca odwołanie do obiektu o nazwie:

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a>Zużywanie wartości zwracanej ref

Wartość zwracana ref jest aliasem do innej zmiennej w zakresie metody o nazwie. Można interpretować dowolne użycie ref return jako przy użyciu zmiennej aliases:

- Po przypisaniu jego wartości przypisuje stwierdzono, że wartość jest przypisywana do zmiennej, którą aliasuje.
- Podczas odczytywania jego wartości odczytywasz wartość zmiennej, którą aliases.
- Jeśli zwrócisz go *przez odwołanie,* zwracasz alias do tej samej zmiennej.
- Jeśli przekażesz go do innej metody *przez odwołanie,* przekazujesz odwołanie do zmiennej, którą aliasuje.
- Po wprowadzeniu [aliasu lokalnego ref](#ref-locals) wprowadzasz nowy alias do tej samej zmiennej.

## <a name="ref-locals"></a>Ref miejscowi

Załóżmy, że `GetContactInformation` metoda jest zadeklarowana jako ref return:

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

Przypisanie według wartości odczytuje wartość zmiennej i przypisuje ją do nowej zmiennej:

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

Poprzednie przypisanie deklaruje `p` jako zmienną lokalną. Jego wartość początkowa jest kopiowana `GetContactInformation`z odczytu wartości zwracanej przez . Wszelkie przyszłe przypisania nie `p` zmienią wartości zmiennej `GetContactInformation`zwróconej przez . Zmienna `p` nie jest już aliasem zwróconej zmiennej.

Deklarujesz zmienną *lokalną ref,* aby skopiować alias do oryginalnej wartości. W poniższym `p` przypisaniu jest aliasem `GetContactInformation`zmiennej zwróconej z .

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

Kolejne użycie `p` jest taka sama jak przy `GetContactInformation` `p` użyciu zmiennej zwracanej przez ponieważ jest aliasdla tej zmiennej. Zmiany, `p` aby również zmienić `GetContactInformation`zmienną zwróconą z .

Słowo `ref` kluczowe jest używane zarówno przed deklaracją zmiennej *lokalnej, jak i* przed wywołaniem metody.

Można uzyskać dostęp do wartości przez odwołanie w ten sam sposób. W niektórych przypadkach dostęp do wartości przez odwołanie zwiększa wydajność, unikając potencjalnie kosztownej operacji kopiowania. Na przykład w poniższej instrukcji pokazano, jak można zdefiniować wartość lokalną ref, która jest używana do odwoływania się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Słowo `ref` kluczowe jest używane zarówno przed deklaracją zmiennej *lokalnej, jak i* przed wartością w drugim przykładzie. Nieuwzględnienie obu `ref` słów kluczowych w deklaracji zmiennej i przypisania w obu przykładach powoduje błąd kompilatora CS8172, "Nie można zainicjować zmiennej przez odwołanie z wartością."

Przed C# 7.3 ref zmiennych lokalnych nie można ponownie przypisać do odwoływania się do innego magazynu po zainicjowaniu. Ograniczenie to zostało zniesione. W poniższym przykładzie przedstawiono ponowne przypisanie:

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 Ref zmienne lokalne muszą być nadal inicjowane, gdy są deklarowane.

## <a name="ref-returns-and-ref-locals-an-example"></a>Ref zwraca i ref locals: przykład

W poniższym `NumberStore` przykładzie zdefiniowano klasę, która przechowuje tablicę wartości całkowitych. Metoda `FindNumber` zwraca przez odwołanie pierwszy numer, który jest większy lub równy liczbie przekazywanej jako argument. Jeśli żadna liczba nie jest większa lub równa argumentowi, metoda zwraca liczbę w indeksie 0.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

Poniższy przykład wywołuje `NumberStore.FindNumber` metodę, aby pobrać pierwszą wartość, która jest większa lub równa 16. Następnie obiekt wywołujący podwaja wartość zwracaną przez metodę. Dane wyjściowe z przykładu pokazuje zmiany odzwierciedlone w wartości `NumberStore` elementów tablicy wystąpienia.

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

Bez obsługi dla wartości zwracanych odniesienia, taka operacja jest wykonywana przez zwrócenie indeksu elementu tablicy wraz z jego wartością. Obiekt wywołujący można następnie użyć tego indeksu, aby zmodyfikować wartość w wywołaniu metody oddzielne. Jednak obiekt wywołujący można również zmodyfikować indeks, aby uzyskać dostęp i ewentualnie zmodyfikować inne wartości tablicy.  

W poniższym przykładzie `FindNumber` pokazano, jak metoda może być przepisany po C# 7.3 do korzystania ref lokalnego ponownego przypisania:

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

Ta druga wersja jest bardziej efektywne z dłuższych sekwencji w scenariuszach, w których żądana liczba jest bliżej końca tablicy.

## <a name="see-also"></a>Zobacz też

- [ref — słowo kluczowe](../../language-reference/keywords/ref.md)
- [Napisz bezpieczny, wydajny kod](../../write-safe-efficient-code.md)
