---
title: Listy (F#)
description: 'Dowiedz się więcej na temat języka F # list, uporządkowany i modyfikować szereg elementów tego samego typu.'
ms.date: 05/16/2016
ms.openlocfilehash: ea86b3ca94c6414bf5ab60406452f3604838075a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="lists"></a>Listy

> [!NOTE]
Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

Na liście w F # jest uporządkowany i modyfikować szereg elementów tego samego typu. Aby wykonywać podstawowe operacje na listach, użyj funkcji w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).


## <a name="creating-and-initializing-lists"></a>Tworzenie i Inicjowanie listy
Aby zdefiniować listę, należy jawnie wyświetlania się elementy, oddzielając je średnikami i ujęte w nawiasy kwadratowe, jak pokazano w następującym wierszu kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Można również wprowadzić podziałów między elementami, w którym to przypadku średniki są opcjonalne. Ostatnie składni może spowodować czytelność kodu, gdy wyrażenia inicjowania elementów są dłuższe lub gdy chcesz dołączyć komentarz dla każdego elementu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Zwykle wszystkie elementy listy muszą być tego samego typu. Wyjątkiem jest listy, w jakiej elementy są określane jako typu podstawowego, może mieć elementów, które są typów pochodnych. W związku z tym następujące jest dopuszczalne, ponieważ zarówno `Button` i `CheckBox` pochodzi od `Control`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Można również definiować listy elementów za pomocą zakres wskazywany przez liczb całkowitych rozdzielonych operatora zakresu (`..`), jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Pusta lista jest określana przez parę nawiasy kwadratowe bez żadnych składników między nimi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Umożliwia utworzenie listy, można użyć wyrażenia sekwencji. Zobacz [wyrażenia sekwencji](sequences.md#sequence-expressions) Aby uzyskać więcej informacji. Na przykład poniższy kod tworzy listę kwadratów liczb całkowitych od 1 do 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Operatory do pracy z listy
Możesz dołączyć elementy do listy przy użyciu `::` — operator (wad). Jeśli `list1` jest `[2; 3; 4]`, poniższy kod tworzy `list2` jako `[100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Można połączyć listy, które mają niezgodne typy przy użyciu `@` operatora, zgodnie z poniższym kodem. Jeśli `list1` jest `[2; 3; 4]` i `list2` jest `[100; 2; 3; 4 ]`, ten kod tworzy `list3` jako `[2; 3; 4; 100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Funkcje do wykonywania operacji na listach są dostępne w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

Ponieważ listy w języku F # są niezmienne, wszystkie operacje modyfikowania wygenerować nowe listy zamiast modyfikowania istniejących list.

Listy w F # są zaimplementowane jako list połączonych pojedynczo, co oznacza, że operacje, które uzyskują dostęp tylko head listy są O(1), i dostęp do elementu jest O (*n*).


## <a name="properties"></a>Właściwości
Typ listy obsługuje następujące właściwości:

|Właściwość|Typ|Opis|
|--------|----|-----------|
|[HEAD](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|Pierwszy element.|
|[pusty](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Właściwości statyczne, która zwraca pustą listę odpowiedniego typu.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` Jeśli na liście nie ma żadnych elementów.|
|[Element](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|Element pod określony indeks (liczony od zera).|
|[długość](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Liczba elementów.|
|[Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|Lista bez pierwszego elementu.|
Poniżej przedstawiono kilka przykładów użycia tych właściwości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a>Używanie list
Programowanie przy użyciu list umożliwia wykonywanie złożonych operacji z małej ilości kodu. W tej sekcji opisano typowe operacje na listach, które są ważne dla programowanie funkcjonalne.


### <a name="recursion-with-lists"></a>Rekursja z listy
Listy są dostosowane do cyklicznego technik programowania. Należy wziąć pod uwagę operacji, które należy wykonać dla każdego elementu listy. Można nie tego rekursywnie działających na head listy, a następnie przekazywanie tail listy, czyli listę mniejszych, która składa się z oryginalnej listy bez pierwszy element, z powrotem na następny poziom rekursji.

Aby napisać funkcję rekursywną, możesz użyć operatora wad (`::`) w dopasowania wzorca, który umożliwia head listy z końcowego fragmentu.

Poniższy przykład kodu pokazuje, jak na potrzeby dopasowywania do wzorca implementacji funkcji cyklicznej, która wykonuje operacje na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Poprzedni kod działa dobrze w przypadku małych list, ale większych list można przepełnienia stosu. Poniższy kod poprawia dla tego kodu za pomocą argumentu akumulatora standardowa metoda do pracy z funkcjami cyklicznego. Użycie argumentu akumulatora sprawia, że funkcję z rekursją ogonową, która zapisuje miejsca na stosie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

Funkcja `RemoveAllMultiples` to funkcja cykliczne, która ma dwie listy. Pierwsza lista może zawierać cyfry, w których wielokrotności zostaną usunięte, a druga lista znajduje się lista, z którego mają zostać usunięte liczby. Kod w poniższym przykładzie funkcja tego cyklicznego wyeliminowanie wszystkich innych niż — pierwszych liczb z listy, pozostawiając listę liczb pierwszych w wyniku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Wynik jest następujący:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Moduł funkcji
[Modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) udostępnia funkcje, które uzyskują dostęp do elementów listy. Head element jest najszybszym i najprostszym dostępu do. Użyj właściwości [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) lub funkcji modułu [list.HEAD —](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). Tail listy mogą korzystać za pomocą [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) właściwości lub [list.tail —](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) funkcji. Aby znaleźć element przez indeks, użyj [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) funkcji. `List.nth` listy są przesyłane za pośrednictwem. Dlatego jest O (*n*). Jeśli używa Twój kod `List.nth` często, warto rozważyć użycie tablicy zamiast listy. Dostęp do elementu w tablicach jest O(1).


### <a name="boolean-operations-on-lists"></a>Operacji logicznych na listach
[List.IsEmpty —](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) funkcji określa, czy lista ma żadnych elementów.

[List.EXISTS —](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) wartość logiczna ma zastosowanie funkcja testów elementów listy i zwraca `true` Jeśli dowolny element spełnia testu. [List.exists2 —](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) jest podobny, ale działa na kolejnych pary elementów listy.

Poniższy kod przedstawia użycie `List.exists`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

Wynik jest następujący:

```
For list [0; 1; 2; 3], contains zero is true
```

W poniższym przykładzie pokazano użycie `List.exists2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

Wynik jest następujący:

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

Można użyć [list.ForAll —](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) Jeśli chcesz sprawdzić, czy wszystkie elementy z listy spełniają warunek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

Wynik jest następujący:

```
true
false
```

Podobnie [list.forall2 —](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) Określa, czy wszystkie elementy w odpowiednich miejscach w dwie listy spełniają wyrażenie logiczne, która obejmuje każda para elementów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

Wynik jest następujący:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Sortowanie na listach
[List.sort —](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [list.sortby —](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), i [list.sortwith —](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) funkcje sortować listy. Funkcja sortowania określa, która z tych trzech funkcji do użycia. `List.sort` korzysta z domyślnego ogólnego porównania. Porównanie ogólnego używa operatorów globalnych na podstawie ogólnego porównanie funkcji do porównywania wartości. Działa wydajnie wiele różnych typów elementów, takich jak proste typy liczbowe, krotek rekordów, rozłączne, list, tablic i dowolnego typu, który implementuje `System.IComparable`. Dla typów które implementują `System.IComparable`, używa standardowego porównania `System.IComparable.CompareTo()` funkcji. Porównanie ogólnego również działa z ciągów, ale używa sortowania niezależne od kultury. Porównanie ogólnych nie powinien być używany w nieobsługiwanych typów, takie jak typy funkcji. Ponadto wydajność domyślnym porównaniem ogólnego jest najlepsze dla małych typów strukturalnych. dla większych strukturalnych typów, które muszą być porównywane i sortowane często, rozważ zaimplementowanie `System.IComparable` i wydajne implementacja `System.IComparable.CompareTo()` metody.

`List.sortBy` pobiera funkcję, która zwraca wartość, która jest używana jako kryterium sortowania i `List.sortWith` przyjmuje jako argument funkcji porównania. Te dwie funkcje te ostatnie są przydatne podczas pracy z typami, które nie obsługują porównywania lub kiedy porównanie wymaga bardziej złożonej semantykę porównania, tak jak w przypadku ciągi kultury aware.

W poniższym przykładzie pokazano użycie `List.sort`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

Wynik jest następujący:

```
[-2; 1; 4; 5; 8]
```

W poniższym przykładzie pokazano użycie `List.sortBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

Wynik jest następujący:

```
[1; -2; 4; 5; 8]
```

W następnym przykładzie pokazano użycie `List.sortWith`. W tym przykładzie funkcja porównywania niestandardowych `compareWidgets` służy do porównywania najpierw jedno pole typu niestandardowego oraz gdy następnie inne wartości pierwszego pola są takie same.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

Wynik jest następujący:

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Operacje wyszukiwania na listach
Wiele operacji wyszukiwania są obsługiwane dla listy. Najprostsza, [list.Find —](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umożliwia znalezienie pierwszy element, który odpowiada dany warunek.

Poniższy przykład kodu pokazuje użycie `List.find` można znaleźć pierwszego liczba, która jest podzielna przez 5 na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

Wynik wynosi 5.

Jeśli najpierw musi zostać przekształcone elementy, wywołanie [list.Pick —](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)używającą funkcja zwraca opcję i wygląda pierwszej opcji wartość, która jest `Some(x)`. Zamiast zwracać elementu `List.pick` zwraca wynik `x`. Jeśli nie zostanie znaleziony, `List.pick` zgłasza `System.Collections.Generic.KeyNotFoundException`. Poniższy kod przedstawia użycie `List.pick`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

Wynik jest następujący:

```
"b"
```

Innej grupy operacji wyszukiwania [list.tryfind —](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) i powiązane funkcje zwracają wartość opcji. `List.tryFind` Funkcja zwraca pierwszy element listy, która spełnia warunek, jeśli taki element istnieje, ale wartość opcji `None` , jeśli nie. Zmiana [list.tryfindindex —](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) zwraca indeks elementu, jeśli został znaleziony, a nie samego elementu. Te funkcje zostały przedstawione w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

Wynik jest następujący:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Operacje arytmetyczne na listach
Typowe operacje arytmetyczne, takie jak sum i średniej są wbudowane w [modułu listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Aby pracować z [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), musi obsługiwać typ elementu listy `+` operatora i mieć wartość zero. Wszystkie wbudowanych typów arytmetycznych spełnia te warunki. Aby pracować z [list.AVERAGE —](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musi obsługiwać dzielenia bez reszty, co wyklucza typy całkowite, ale pozwala na liczby zmiennoprzecinkowe typy punktów. [List.sumby —](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) i [list.averageby —](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) funkcje pobierać funkcji jako parametr, a wyniki tej funkcji są używane do obliczania wartości sum lub średnia.

Poniższy kod przedstawia użycie `List.sum`, `List.sumBy`, i `List.average`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

Dane wyjściowe `1.000000`.

Poniższy kod przedstawia użycie `List.averageBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

Dane wyjściowe `5.5`.


### <a name="lists-and-tuples"></a>Listy i spójnych kolekcji
Listy zawierające krotek może manipulować zip i Rozpakuj funkcji. Te funkcje Połącz dwie listy pojedynczych wartości na jednej liście krotek lub podzielić jedną listę krotek na dwóch list z jednej wartości. Najprostszą [list.zip —](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) funkcja przyjmuje dwa listę elementów jednego i tworzy jedną listę par spójnej kolekcji. Inna wersja [list.zip3 —](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), przyjmuje trzy listę elementów jednego i tworzy jedną listę krotek, które mają trzy elementy. Poniższy przykład kodu pokazuje użycie `List.zip`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

Wynik jest następujący:

```
[(1, -1); (2, -2); (3; -3)]
```

Poniższy przykład kodu pokazuje użycie `List.zip3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

Wynik jest następujący:

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Odpowiednie Rozpakuj wersje, [list.Unzip —](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) i [list.unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), wykonaj listę krotek i zwróć list w spójnej kolekcji, których pierwsza lista zawiera wszystkie elementy, które zostały po raz pierwszy w każdej krotki i druga lista zawiera drugi element każda krotka i tak dalej.

Poniższy przykład kodu pokazuje użycie [list.Unzip —](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

Wynik jest następujący:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Poniższy przykład kodu pokazuje użycie [list.unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

Wynik jest następujący:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Na liście elementów
F # obsługuje wiele operacji na liście elementów. Najprostszą jest [list.ITER —](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), co umożliwia wywołać funkcję dla każdego elementu listy. Zmiany obejmują [list.iter2 —](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), który umożliwia wykonywanie operacji w elementach dwie listy [list.iteri —](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), czyli jak `List.iter` z tą różnicą, że indeks każdego elementu jest przekazywany jako argument do funkcji, która jest wywoływana dla każdego elementu i [list.iteri2 —](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), który jest kombinacją funkcji `List.iter2` i `List.iteri`. Poniższy przykład kodu pokazuje tych funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

Wynik jest następujący:

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

Inną funkcję często używanych, który przekształca elementów listy jest [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), dzięki czemu można zastosować funkcji do każdego elementu listy i wszystkie wyniki do nowej listy. [List.map2 —](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) i [list.map3 —](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) są zmiany, które przyjmują wielu list. Można również użyć [list.MAPI —](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) i [list.mapi2 —](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), jeśli oprócz elementu, funkcja musi być przekazywany indeks każdego elementu. Jedyną różnicą między `List.mapi2` i `List.mapi` jest to, że `List.mapi2` współpracuje z listy. Poniższy przykład przedstawia [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

Wynik jest następujący:

```
[2; 3; 4]
```

W poniższym przykładzie przedstawiono użycie `List.map2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

Wynik jest następujący:

```
[5; 7; 9]
```

W poniższym przykładzie przedstawiono użycie `List.map3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

Wynik jest następujący:

```
[7; 10; 13]
```

W poniższym przykładzie przedstawiono użycie `List.mapi`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

Wynik jest następujący:

```
[1; 3; 5]
```

W poniższym przykładzie przedstawiono użycie `List.mapi2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

Wynik jest następujący:

```
[0; 7; 18]
```

[List.Collect —](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) przypomina `List.map`, z wyjątkiem, że każdy element tworzy listę i te listy są połączone w listą końcową. W poniższym kodzie każdego elementu listy generuje trzech cyfr. Te są wszystkie zebrane na jednej liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

Wynik jest następujący:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Można również użyć [list.filter —](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), która przyjmuje warunek typu Boolean i tworzy nową listę, która zawiera tylko elementy, które spełniają dany warunek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

Wynikowa lista jest `[2; 4; 6]`.

Kombinację mapy i Filtruj [list.Choose —](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) pozwala na przekształcanie i wybierz elementy w tym samym czasie. `List.choose` stosuje funkcję, która zwraca opcji do każdego elementu listy i zwraca nową listę wyników dla elementów, gdy funkcja zwraca wartość opcji `Some`.

Poniższy kod przedstawia użycie `List.choose` aby zaznaczyć pisanymi wielkimi literami wyrazy poza listę słów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

Wynik jest następujący:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Korzysta z wielu list
Listy można łączyć ze sobą. Aby przyłączyć się do jednego dwie listy, użyj [list.append —](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). Aby dołączyć więcej niż dwie listy, użyj [list.concat —](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a>Składanie i operacji skanowania
Niektóre operacje listy obejmują zależności między wszystkie elementy z listy. Operacje złożenia i skanowania są podobne do `List.iter` i `List.map` , wywołaj funkcję dla każdego elementu, ale te operacje zapewnia dodatkowy parametr o nazwie *akumulatora* który przenosi informacje za pomocą obliczenia.

Użyj `List.fold` do przeprowadzenia obliczeń na listę.

Poniższy przykład kodu pokazuje użycie [list.fold —](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) do wykonywania różnych operacji.

Lista jest przesunięta; akumulatora `acc` to wartość, która jest przekazywane w trakcie wykonywania obliczeń. Pierwszy argument akumulatora i elementu listy i zwraca wynik tymczasowe obliczeń dla tego elementu listy. Drugi argument jest wartością początkową akumulatora.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

Wersje te funkcje, które mają cyfrę w nazwie funkcji działać na więcej niż jedną listę. Na przykład [list.fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) wykonuje obliczenia na dwie listy.

W poniższym przykładzie pokazano użycie `List.fold2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` i [list.Scan —](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) różnią się w tym `List.fold` zwraca końcowa wartość dodatkowy parametr, ale `List.scan` zwraca listę wartości pośrednich (wraz z końcowej) z dodatkowym parametrem.

Każda z tych funkcji obejmuje odwrotnej zmiany, na przykład [list.foldback —](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), który różni się w kolejności, w której przecina listy i kolejność argumentów. Ponadto `List.fold` i `List.foldBack` ma zmian, [list.fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) i [list.foldback2 —](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), które wymagają dwie listy o równej długości. Funkcja wykonująca na każdym elemencie może być wykonanie akcji odpowiednie elementy obu list. Typy elementu dwie listy mogą być różne, jak w poniższym przykładzie, w której jedna lista zawiera kwoty transakcji dla konta bankowego, i inne lista zawiera typ transakcji: złożenia lub wycofania.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

Do obliczenia, takich jak podsumowania `List.fold` i `List.foldBack` mają ten sam efekt, ponieważ wynik nie zależy od rzędu przechodzenie. W poniższym przykładzie `List.foldBack` służy do dodawania elementów na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

Poniższy przykład zwraca przykład konta bankowego. Teraz zostanie dodany nowy typ transakcji: Obliczanie odsetek. Saldo końcowe zależy od teraz rzędu transakcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

Funkcja [list.Reduce —](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) jest nieco jak `List.fold` i `List.scan`, ale zamiast przekazywanie wokół oddzielne akumulatora, `List.reduce` przyjmuje funkcję, która przyjmuje dwa argumenty typu zamiast elementu tylko jeden, a jeden z tych argumentów działa jako akumulatora, co oznacza przechowuje pośredni wynikiem obliczenia. `List.reduce` rozpoczyna się od działających na pierwszych dwóch listy elementów, a następnie używa wynik operacji wraz z następnym elementem. Ponieważ nie jest osobnym akumulatora, który ma swój własny typ `List.reduce` można użyć zamiast `List.fold` tylko gdy akumulatora i typ elementu być tego samego typu. Poniższy kod przedstawia użycie `List.reduce`. `List.reduce` zgłasza wyjątek, jeśli nie ma żadnych elementów listy.

W poniższym kodzie pierwsze wywołanie w celu wyrażenia lambda podano argumenty 2 i 4 i zwraca 6 i następnego wywołania podano argumenty, 6, 10, dlatego 16.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a>Konwertowanie pomiędzy listy i inne typy kolekcji
`List` Moduł zapewnia funkcje do konwertowania do i z tablic i sekwencji. Aby dokonać konwersji do lub z sekwencją, użyj [list.toseq —](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) lub [list.ofseq —](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). Aby dokonać konwersji do lub z tablicy, należy użyć [list.toarray —](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) lub [list.ofarray —](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).


### <a name="additional-operations"></a>Dodatkowe operacje
Informacje dodatkowe operacje na listach, zobacz temat odwołanie do biblioteki [Collections.list — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Typy F#](fsharp-types.md)

[Sekwencje](sequences.md)

[Tablice](arrays.md)

[Opcje](options.md)
