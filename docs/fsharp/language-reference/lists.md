---
title: Listy (F#)
description: 'Więcej informacji na temat list języka F #, uporządkowany i niezmienne szeregu elementów tego samego typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 60e7edb56bdf498e3ba51aff028d8564eb68d0f1
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532785"
---
# <a name="lists"></a>Listy

> [!NOTE]
Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

Na liście w F # jest uporządkowany i niezmienne szereg elementów tego samego typu. Aby wykonywać podstawowe operacje na listach, należy użyć funkcji w [lista modułów](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

## <a name="creating-and-initializing-lists"></a>Tworzenie i Inicjowanie listy

Aby zdefiniować listę, należy jawnie listę elementów, oddzielone średnikami i ujęte w nawiasy kwadratowe, jak pokazano w następującym wierszu kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Możesz również umieścić podziały wierszy między elementami, w którym to przypadku średnikami są opcjonalne. Jego składni może spowodować czytelność kodu, gdy wyrażenia inicjowania elementu są dłuższe lub gdy chcesz dołączyć komentarz dla każdego elementu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Normalnie wszystkie elementy listy muszą być tego samego typu. Wyjątek stanowi, listy, w której elementy są określane jako typu podstawowego, może mieć elementów, które są typy pochodne. Dlatego poniżej przedstawiono dopuszczalne, ponieważ oba `Button` i `CheckBox` dziedziczyć `Control`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Można również definiować listy elementów za pomocą zakres wskazywany przez liczb całkowitych rozdzielonych operatora zakresu (`..`), jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Pusta lista jest określana przez parę nawiasów kwadratowych pustą między nimi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Umożliwia utworzenie listy, można użyć wyrażenia sekwencji. Zobacz [wyrażenia sekwencji](sequences.md#sequence-expressions) Aby uzyskać więcej informacji. Na przykład poniższy kod tworzy listę kwadratów liczb całkowitych z zakresu od 1 do 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Operatory do pracy z listy

Można dołączyć elementy do listy przy użyciu `::` — operator (wad). Jeśli `list1` jest `[2; 3; 4]`, poniższy kod tworzy `list2` jako `[100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Można łączyć ze sobą list, które mają niezgodne typy przy użyciu `@` operatora, jak w poniższym kodzie. Jeśli `list1` jest `[2; 3; 4]` i `list2` jest `[100; 2; 3; 4 ]`, ten kod tworzy `list3` jako `[2; 3; 4; 100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

W dostępnych funkcji w celu wykonywania operacji na listach [lista modułów](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

Ponieważ listy języka F # są niezmienne, wszystkie operacje modyfikowania wygenerować nowe listy zamiast modyfikowania istniejących list.

List w języku F # są implementowane jako pojedynczo połączoną list, które oznacza, że operacje, do których dostęp tylko nagłówek listy O(1), a dostęp do elementu jest O (*n*).

## <a name="properties"></a>Właściwości

Typ listy obsługuje następujące właściwości:

|Właściwość|Typ|Opis|
|--------|----|-----------|
|[główny](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|Pierwszy element.|
|[pusty](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Właściwość statyczna, która zwraca pustą listę odpowiedniego typu.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` Jeśli lista nie zawiera elementów.|
|[Element](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|Element wskazywany przez określony indeks (liczony od zera).|
|[Długość](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Liczba elementów.|
|[Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|Lista bez pierwszego elementu.|
Poniżej przedstawiono kilka przykładów użycia tych właściwości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Korzystanie z list

Programowanie przy użyciu list umożliwia wykonywanie złożonych operacji z małą ilością kodu. W tej sekcji opisano typowe operacje na listach, które są istotne dla programowania funkcjonalnego.

### <a name="recursion-with-lists"></a>Rekursja przy użyciu list

Listy są dostosowane do cyklicznego technikach programowania. Należy wziąć pod uwagę operacji, które należy wykonać dla każdego elementu listy. Możesz zrobić to rekursywnie według działających na nagłówek listy, a następnie przekazywanie ogona listę, która jest mniejsza listę, która składa się z oryginalnej listy bez pierwszego elementu, z powrotem na następny poziom rekursji.

Aby napisać funkcję cykliczne, możesz użyć operatora wad (`::`) w dopasowywania do wzorca, który umożliwia rozdzielenie nagłówek listy z zakończeniem.

W poniższym przykładzie kodu pokazano, jak na potrzeby dopasowywania do wzorca implementacji funkcji recursive, który wykonuje operacje na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Powyższy kod działa dobrze w przypadku małych list, ale w przypadku większych list można przepełnienia stosu. Poniższy kod poprawia na ten kod przy użyciu argumentu akumulatora, to standardowa metoda do pracy z funkcji rekursywnych. Użycie argumentu akumulatora sprawia, że cyklicznego tail funkcji, co pozwoli zaoszczędzić miejsce na stosie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

Funkcja `RemoveAllMultiples` jest funkcją cykliczne, która przyjmuje dwie listy. Pierwsza lista zawiera liczby, w których wielokrotności zostaną usunięte, a druga lista to lista, z którego chcesz usunąć numery. Kod w poniższym przykładzie funkcja ta cykliczne, aby wyeliminować wszystkich innych iloczyn liczb z listy, pozostawiając listy liczb pierwszych, w wyniku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Dane wyjściowe wyglądają następująco:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Funkcje modułu

[Lista modułów](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) oferuje funkcje, których dostęp do elementów listy. Head element jest najszybszy i najłatwiejszy w celu uzyskania dostępu do. Użyj właściwości [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) lub funkcji modułu [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). Tail listy mieli dostęp za pomocą [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) właściwości lub [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) funkcji. Aby znaleźć element według indeksu, należy użyć [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) funkcji. `List.nth` przechodzi przez listę. Dlatego jest O (*n*). Jeśli kod używa `List.nth` często, warto rozważyć użycie tablicy zamiast listy. Element w tablicach jest O(1).

### <a name="boolean-operations-on-lists"></a>Operacji logicznych na listach

[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) funkcji określa, czy lista ma żadnych elementów.

[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) funkcja ma zastosowanie Boolean testów elementów listy i zwraca `true` Jeśli każdy element spełnia testu. [List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) są podobne, ale działa na kolejne pary elementów w dwie listy.

Poniższy przykład demonstruje użycie `List.exists`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

Dane wyjściowe wyglądają następująco:

```
For list [0; 1; 2; 3], contains zero is true
```

W poniższym przykładzie pokazano użycie `List.exists2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

Dane wyjściowe wyglądają następująco:

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

Możesz użyć [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) Jeśli chcesz sprawdzić, czy wszystkie elementy z listy spełniają warunek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

Dane wyjściowe wyglądają następująco:

```
true
false
```

Podobnie [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) Określa, czy wszystkie elementy w odpowiedniej pozycji w dwie listy spełniają wyrażenie logiczne, które obejmuje każdej pary elementów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

Dane wyjściowe wyglądają następująco:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Operacje sortowania na listach

[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), i [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) funkcje sortować listy. Określa funkcję sortowania, której te trzy funkcje do użycia. `List.sort` używa domyślnego porównania rodzajowego. Ogólne porównanie używa operatorów globalnych na podstawie porównania rodzajowego funkcji do porównywania wartości. Działa wydajnie wiele różnych typów elementów, takich jak proste typy liczbowe, krotek, rekordy, związki dyskryminowane, list, tablic i dowolny typ, który implementuje `System.IComparable`. Dla typami, które implementują `System.IComparable`, używa porównania rodzajowego `System.IComparable.CompareTo()` funkcji. Porównania rodzajowego również współdziała z ciągami, ale używa niezależnych od kultury sortowania. Nie można używać porównania rodzajowego na nieobsługiwane typy, takie jak typy funkcji. Ponadto wydajność porównania rodzajowego domyślny jest najlepszym rozwiązaniem dla małych typów strukturalnych. dla większych ze strukturą typów, które muszą być porównywane i posortowane często, rozważ zaimplementowanie `System.IComparable` i wydajne implementację `System.IComparable.CompareTo()` metody.

`List.sortBy` przyjmuje funkcję, która zwraca wartość, która jest używana jako kryterium sortowania i `List.sortWith` przyjmuje funkcją porównywania jako argument. Te ostatnie dwie funkcje są przydatne podczas pracy z typami, które nie obsługują porównywania lub kiedy porównanie wymaga bardziej złożonej semantykę porównania, tak jak w przypadku ciągów kultury.

W poniższym przykładzie pokazano użycie `List.sort`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

Dane wyjściowe wyglądają następująco:

```
[-2; 1; 4; 5; 8]
```

W poniższym przykładzie pokazano użycie `List.sortBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

Dane wyjściowe wyglądają następująco:

```
[1; -2; 4; 5; 8]
```

Następny przykład demonstruje użycie `List.sortWith`. W tym przykładzie niestandardową funkcję porównywania `compareWidgets` służy do porównywania najpierw jedno pole typu niestandardowego oraz gdy następnie inne wartości pierwszego pola są równe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

Dane wyjściowe wyglądają następująco:

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Operacji wyszukiwania na listach

Wiele operacji wyszukiwania są obsługiwane w przypadku list. Najprostszy, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umożliwia znalezienie pierwszego elementu, który odpowiada określony warunek.

Poniższy przykład kodu demonstruje użycie `List.find` można znaleźć pierwszy numer, który można podzielić przez 5 na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

Wynik wynosi 5.

Jeśli najpierw musi zostać przekształcone elementy, wywołaj [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)używającą funkcji zwraca opcję i szuka pierwszej opcji wartość, która jest `Some(x)`. Zamiast zwracać element `List.pick` zwraca wynik `x`. Jeśli nie zostanie znaleziony, `List.pick` zgłasza `System.Collections.Generic.KeyNotFoundException`. Poniższy kod przedstawia użycie `List.pick`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

Dane wyjściowe wyglądają następująco:

```
"b"
```

Inna grupa operacji wyszukiwania [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) i powiązane funkcje zwracają wartość opcji. `List.tryFind` Funkcja zwraca pierwszy element listy, który spełnia warunek, jeśli taki element istnieje, ale wartość opcji `None` w przeciwnym razie. Zmiana [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) zwraca indeks elementu, jeśli został znaleziony, a nie samego elementu. Te funkcje zostały zilustrowane w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

Dane wyjściowe wyglądają następująco:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Operacje arytmetyczne na listach

Typowe operacje arytmetyczne, takie jak Suma i średnia są wbudowane w [lista modułów](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Do pracy z [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), typ elementu listy musi obsługiwać `+` operatora i mieć wartość zero. Wszystkie wbudowane typy arytmetyczne spełniają te warunki. Aby pracować z [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musi obsługiwać dzielenia bez reszty, co wyklucza typy całkowite, ale pozwala uzyskać punktu zmiennoprzecinkowego. [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) i [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) funkcje biorą funkcję, jako parametr, a wyniki tej funkcji są używane do obliczania wartości dla sumy lub średniej.

Poniższy przykład demonstruje użycie `List.sum`, `List.sumBy`, i `List.average`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

Dane wyjściowe są `1.000000`.

Poniższy kod przedstawia użycie `List.averageBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

Dane wyjściowe są `5.5`.

### <a name="lists-and-tuples"></a>Listy i kolekcje

List, które zawierają krotek mogą być zmieniane według kodu pocztowego i Rozpakuj funkcji. Te funkcje połączyć dwie listy pojedynczych wartości na jednej liście krotek lub rozdzielić jeden listą spójnych kolekcji na dwie listy pojedynczych wartości. Najprostsze [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) funkcja przyjmuje dwie listy pojedynczych elementów i tworzy jedną listę par spójnej kolekcji. Inna wersja [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), przyjmuje trzy listy pojedynczych elementów i tworzy jednej liście krotek, które mają trzy elementy. Poniższy przykład kodu demonstruje użycie `List.zip`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

Dane wyjściowe wyglądają następująco:

```
[(1, -1); (2, -2); (3; -3)]
```

Poniższy przykład kodu demonstruje użycie `List.zip3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

Dane wyjściowe wyglądają następująco:

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Odpowiedni Rozpakuj wersji [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) i [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), wykonaj listę krotek i zwrócić listy w spójnej kolekcji, w których pierwsza lista zawiera wszystkie elementy, które zostały po raz pierwszy w każda krotka i druga lista zawiera drugi element każdego krotki i tak dalej.

Poniższy przykład kodu demonstruje użycie [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

Dane wyjściowe wyglądają następująco:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Poniższy przykład kodu demonstruje użycie [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

Dane wyjściowe wyglądają następująco:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Wykonywanie operacji na liście elementów

Język F # obsługuje różnych operacji na elementach listy. To najprostszy [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), co umożliwia wywoływanie funkcji dla każdego elementu listy. Zmiany obejmują [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), która umożliwia wykonywanie operacji na elementy z dwóch list [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), który przypomina `List.iter` z tą różnicą, że indeks każdy element jest przekazywany jako argument do funkcji, która jest wywoływana dla każdego elementu i [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), który jest kombinacją funkcji `List.iter2` i `List.iteri`. Poniższy przykładowy kod przedstawia te funkcje.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

Dane wyjściowe wyglądają następująco:

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

Innym często używanych funkcji, która przekształca elementów listy jest [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), co umożliwia zastosowanie funkcji do każdego elementu listy i umieścić wszystkie wyniki w nowej listy. [List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) i [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) są zmiany, które przyjmują wielu listach. Można również użyć [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) i [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), jeśli oprócz elementu, funkcja musi być przekazywany indeks każdego elementu. Jedyną różnicą między `List.mapi2` i `List.mapi` jest fakt, że `List.mapi2` współpracuje z dwoma listami. W poniższym przykładzie pokazano [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

Dane wyjściowe wyglądają następująco:

```
[2; 3; 4]
```

Poniższy przykład pokazuje użycie `List.map2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

Dane wyjściowe wyglądają następująco:

```
[5; 7; 9]
```

Poniższy przykład pokazuje użycie `List.map3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

Dane wyjściowe wyglądają następująco:

```
[7; 10; 13]
```

Poniższy przykład pokazuje użycie `List.mapi`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

Dane wyjściowe wyglądają następująco:

```
[1; 3; 5]
```

Poniższy przykład pokazuje użycie `List.mapi2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

Dane wyjściowe wyglądają następująco:

```
[0; 7; 18]
```

[List.Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) przypomina `List.map`, z tą różnicą, że każdy element tworzy listę te listy są łączone do ostatecznej listy. W poniższym kodzie każdego elementu listy generuje trzech liczb. Te są wszystkie zebrane na jednej liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

Dane wyjściowe wyglądają następująco:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Można również użyć [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), która przyjmuje warunek logiczny i tworzy nową listę, która składa się tylko z elementów, które spełniają dany warunek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

Wynikowa lista jest `[2; 4; 6]`.

Kombinację mapy i filtrowanie [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) pozwala na przekształcanie i wybrać elementy w tym samym czasie. `List.choose` stosuje funkcję, która zwraca opcję do każdego elementu listy, a następnie zwraca nową listę wyników dla elementów, gdy funkcja zwraca wartość opcji `Some`.

Poniższy przykład demonstruje użycie `List.choose` wybrać wyrazy wielkimi literami spoza listy słów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

Dane wyjściowe wyglądają następująco:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Wykonywanie operacji na wielu listach

Listy można łączyć ze sobą. Aby połączyć dwie listy w jedną, użyj [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). Aby dołączyć więcej niż dwie listy, należy użyć [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Zwijania i operacji skanowania

Niektóre operacje listy obejmują wzajemnych zależności między wszystkie elementy z listy. Operacje zwijania i skanowania są podobne do `List.iter` i `List.map` , wywołaj funkcję dla każdego elementu, ale operacje te zapewniają dodatkowy parametr o nazwie *akumulatora* , niesie ze sobą informacje za pośrednictwem obliczenie.

Użyj `List.fold` do wykonywania obliczeń na liście.

Poniższy przykład kodu demonstruje użycie [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) Aby wykonywać różne operacje.

Lista, o ile; akumulatora `acc` jest wartością, która jest przekazywany w trakcie wykonywania obliczeń. Pierwszy argument przyjmuje akumulatora i elementu listy i zwraca tymczasowy wynik obliczeń dla tego elementu listy. Drugi argument jest wartością początkową akumulatora.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

Wersje tych funkcji, które mają cyfrę w nazwie funkcji działać na więcej niż jednej listy. Na przykład [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) wykonuje obliczenia na dwóch list.

W poniższym przykładzie pokazano użycie `List.fold2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` i [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) różnią się w tym `List.fold` zwraca końcowa wartość dodatkowy parametr, ale `List.scan` zwraca listę wartości pośrednich (wraz z końcowej) z dodatkowym parametrem.

Odmiana odwrotnej każda z tych funkcji obejmuje na przykład [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), który różni się w kolejności, w których, o ile listy i kolejność argumentów. Ponadto `List.fold` i `List.foldBack` mają zmian, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) i [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), które wymagają dwie listy o równej długości. Funkcja, który jest wykonywany dla każdego elementu umożliwia wykonanie akcji odpowiednie elementy obu list. Typów elementów z dwóch list może różnić się, jak w poniższym przykładzie, w której ilości transakcji dla banku, zawiera jedną listę, a inne listy zawiera typ transakcji: depozytu lub wycofania.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

Na potrzeby obliczeń, takich jak Suma `List.fold` i `List.foldBack` mają ten sam efekt, ponieważ wynik nie zależy od kolejności przechodzenia. W poniższym przykładzie `List.foldBack` służy do dodawania elementów na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

W poniższym przykładzie zwracany do przykładu koncie bankowym. Tym razem zostanie dodany nowy typ transakcji: obliczenie zainteresowania. Saldo końcowe zależy od teraz rzędu kilku transakcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

Funkcja [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) jest nieco, takich jak `List.fold` i `List.scan`, z tą różnicą, że zamiast wokół oddzielne akumulatora `List.reduce` przyjmuje funkcję, która przyjmuje dwa argumenty typu elementu zamiast tylko jednego i jeden z tych argumentów pełniącego funkcję akumulatora, co oznacza przechowuje pośrednich wynik obliczenia. `List.reduce` rozpoczyna się od działających na pierwszych dwóch list elementów, a następnie używa wynik operacji oraz następnego elementu. Ponieważ nie ma osobnych akumulatora, który ma swój własny typ `List.reduce` mogą być używane zamiast `List.fold` tylko gdy akumulatora i typ elementu ma tego samego typu. Poniższy przykład demonstruje użycie `List.reduce`. `List.reduce` zgłasza wyjątek, jeśli nie ma żadnych elementów listy.

W poniższym kodzie pierwsze wywołanie do wyrażenia lambda podano argumentów, 2 i 4 i zwróci wynik 6, a następne wywołanie podano argumentów, 6 i 10, więc 16.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Konwertowanie pomiędzy listy i inne typy kolekcji

`List` Moduł zapewnia funkcje do konwersji do i z sekwencji i tablic. Aby dokonać konwersji do i z sekwencji, użyj [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) lub [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). Aby dokonać konwersji do lub z tablicy, należy użyć [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) lub [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).

### <a name="additional-operations"></a>Dodatkowe operacje

Dla informacji na temat dodatkowych operacji na listach, zobacz temat odwołanie do biblioteki [Collections.list — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
- [Sekwencje](sequences.md)
- [Tablice](arrays.md)
- [Opcje](options.md)
