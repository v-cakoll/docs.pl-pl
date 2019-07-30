---
title: Listy
description: Dowiedz F# się więcej na temat list, uporządkowanej, niemodyfikowalnej serii elementów tego samego typu.
ms.date: 05/16/2016
ms.openlocfilehash: e8c4a464306cfedfd36a4685507684d3a1a97a2e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630732"
---
# <a name="lists"></a>Listy

> [!NOTE]
> Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

Lista w F# jest uporządkowaną, niemodyfikowalną serią elementów tego samego typu. Aby wykonać podstawowe operacje na listach, użyj funkcji w [module list](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

## <a name="creating-and-initializing-lists"></a>Tworzenie i Inicjowanie list

Możesz zdefiniować listę, jawnie wymieniając elementy, oddzielając je średnikami i ujęte w nawiasy kwadratowe, jak pokazano w poniższym wierszu kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Można również umieścić podziały wierszy między elementami, w tym przypadku średniki są opcjonalne. Druga składnia może spowodować bardziej czytelny kod, gdy wyrażenia inicjowania elementu są dłuższe lub jeśli chcesz dołączyć komentarz dla każdego elementu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Zwykle wszystkie elementy listy muszą być tego samego typu. Wyjątek polega na tym, że lista, w której elementy są określone jako typ podstawowy może mieć elementy, które są typami pochodnymi. W związku z tym następujące elementy są dopuszczalne `Button` , `CheckBox` ponieważ obie `Control`i pochodzą od.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Można również zdefiniować elementy listy przy użyciu zakresu wskazywanego przez liczby całkowite oddzielone operatorem zakresu (`..`), jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Pusta lista jest określana przez parę nawiasów kwadratowych, w których nie ma niczego między nimi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Możesz również użyć wyrażenia sekwencji, aby utworzyć listę. Aby uzyskać więcej informacji, zobacz [wyrażenia sekwencji](sequences.md#sequence-expressions) . Na przykład poniższy kod tworzy listę kwadratów liczb całkowitych z zakresu od 1 do 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Operatory pracy z listami

Możesz dołączyć elementy do listy za pomocą `::` operatora (wady). Jeśli `list1` `list2` `[100; 2; 3; 4]`jest `[2; 3; 4]`, poniższy kod tworzy jako.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Można łączyć listy z zgodnymi typami przy użyciu `@` operatora, jak w poniższym kodzie. Jeśli `list1` jest `[2; 3; 4]` i ma`list2` ,ten`list3` kod tworzy jako .`[2; 3; 4; 100; 2; 3; 4]` `[100; 2; 3; 4]`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Funkcje do wykonywania operacji na listach są dostępne w [module list](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

Ponieważ listy w F# są niezmienne, wszelkie operacje modyfikacji generują nowe listy zamiast modyfikować istniejące.

Listy w F# programie są implementowane jako odrębnie połączone listy, co oznacza, że operacje, które uzyskują dostęp tylko do nagłówka listy, mają wartość o (1), a dostęp do elementów to o (*n*).

## <a name="properties"></a>Właściwości

Typ listy obsługuje następujące właściwości:

|Właściwość|Typ|Opis|
|--------|----|-----------|
|[MTP](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|Pierwszy element.|
|[pusty](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Właściwość statyczna zwracająca pustą listę odpowiedniego typu.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true`Jeśli lista nie zawiera żadnych elementów.|
|[Element](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|Element o określonym indeksie (liczony od zera).|
|[Długość](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Liczba elementów.|
|[Drugorzędn](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|Lista bez pierwszego elementu.|

Poniżej przedstawiono kilka przykładów użycia tych właściwości.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Korzystanie z list

Programowanie za pomocą list umożliwia wykonywanie złożonych operacji przy użyciu niewielkiej ilości kodu. W tej sekcji opisano typowe operacje na listach, które są ważne dla programowania funkcjonalnego.

### <a name="recursion-with-lists"></a>Rekursja z listami

Listy są jednoznacznie dostosowane do technik programowania cyklicznego. Należy wziąć pod uwagę operację, która musi zostać wykonana dla każdego elementu listy. Można to zrobić cyklicznie, działając na początku listy, a następnie przekazując ogon listy, czyli mniejszą listę, która składa się z oryginalnej listy bez pierwszego elementu, z powrotem do następnego poziomu rekursji.

Aby napisać taką funkcję cykliczną, należy użyć operatora wad (`::`) we wzorcu dopasowywania, który umożliwia rozdzielenie nagłówka listy od ogona.

Poniższy przykład kodu pokazuje, jak używać dopasowywania wzorców do implementowania funkcji cyklicznej, która wykonuje operacje na liście.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Poprzedni kod działa dobrze w przypadku małych list, ale dla większych list może przekroczyć stos. Poniższy kod Ulepsza ten kod przy użyciu argumentu akumulowana, standardowej techniki pracy z funkcjami cyklicznymi. Użycie argumentu akumulowana powoduje cykliczne zakończenie funkcji, która zapisuje przestrzeń stosu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

Funkcja `RemoveAllMultiples` jest funkcją cykliczną, która przyjmuje dwie listy. Pierwsza lista zawiera numery, których wielokrotność zostanie usunięta, a druga lista to lista, z której mają zostać usunięte liczby. W poniższym przykładzie kod używa tej funkcji cyklicznej, aby wyeliminować wszystkie niepodstawowe numery z listy, pozostawiając w wyniku listę numerów pierwszych.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Wynik jest następujący:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Funkcje modułu

[Moduł list](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) zawiera funkcje, które uzyskują dostęp do elementów listy. Element główny jest najszybszy i najłatwiejszy do uzyskania dostępu. Użyj właściwości [głównego](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) lub listy funkcji modułu [.](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2) Można uzyskać dostęp do ogona listy za pomocą właściwości [tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) lub funkcji [list. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) . Aby znaleźć element według indeksu, użyj funkcji [list. n](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) . `List.nth`przechodzi listę. W związku z tym to O (*n*). Jeśli kod jest często `List.nth` używany, warto rozważyć użycie tablicy zamiast listy. Dostęp do elementów w tablicach ma (1).

### <a name="boolean-operations-on-lists"></a>Operacje logiczne na listach

Funkcja [list. IsEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) określa, czy lista zawiera dowolne elementy.

Funkcja [list. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) stosuje test logiczny do elementów listy i zwraca `true` , jeśli którykolwiek element spełnia testy. [List. exists2 —](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) jest podobny, ale działa na kolejnych parach elementów na dwóch listach.

Poniższy kod ilustruje użycie `List.exists`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

Wynik jest następujący:

```
For list [0; 1; 2; 3], contains zero is true
```

Poniższy przykład ilustruje użycie `List.exists2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

Wynik jest następujący:

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

Możesz użyć [list. ForAll](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) , jeśli chcesz sprawdzić, czy wszystkie elementy listy spełniają warunek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

Wynik jest następujący:

```
true
false
```

Podobnie, [list. forall2 —](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) określa, czy wszystkie elementy w odpowiednich pozycjach na dwóch listach spełniają wyrażenie logiczne, które obejmuje każdą parę elementów.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

Wynik jest następujący:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Operacje sortowania na listach

Listy sortowania list [. Sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [list. SortBy —](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)oraz [list. sortWith —](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) . Funkcja sortowania określa, które z tych trzech funkcji mają być używane. `List.sort`używa domyślnego porównania ogólnego. Porównanie ogólne używa operatorów globalnych opartych na funkcji porównania generycznej do porównywania wartości. Wydajnie współpracuje z szeroką gamą typów elementów, takimi jak proste typy liczbowe, krotki, rekordy, związki rozłączne, listy, tablice i dowolny typ, który implementuje `System.IComparable`. Dla typów, które `System.IComparable`implementują, porównanie ogólne `System.IComparable.CompareTo()` używa funkcji. Porównanie ogólne działa również z ciągami, ale używa niezależnej od kultury kolejności sortowania. Porównania generycznego nie należy używać w przypadku nieobsługiwanych typów, takich jak typy funkcji. Ponadto wydajność domyślnego porównania ogólnego jest Najlepsza dla małych typów strukturalnych; w przypadku większych typów strukturalnych, które muszą być porównywane i sortowane często `System.IComparable` , należy rozważyć zaimplementowanie i `System.IComparable.CompareTo()` zapewnienie wydajnej implementacji metody.

`List.sortBy`przyjmuje funkcję zwracającą wartość, która jest używana jako kryterium sortowania i `List.sortWith` pobiera funkcję porównania jako argument. Te ostatnie dwie funkcje są przydatne podczas pracy z typami, które nie obsługują porównania, lub gdy porównanie wymaga bardziej złożonej semantyki porównania, tak jak w przypadku ciągów z obsługą kultury.

Poniższy przykład ilustruje użycie `List.sort`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

Wynik jest następujący:

```
[-2; 1; 4; 5; 8]
```

Poniższy przykład ilustruje użycie `List.sortBy`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

Wynik jest następujący:

```
[1; -2; 4; 5; 8]
```

W następnym przykładzie pokazano użycie `List.sortWith`. W tym przykładzie funkcja `compareWidgets` porównywania niestandardowego służy do pierwszego porównania jednego pola typu niestandardowego, a następnie drugiego, gdy wartości pierwszego pola są równe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

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

Dla list są obsługiwane liczne operacje wyszukiwania. Najprostszy, [list. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umożliwia znalezienie pierwszego elementu, który jest zgodny z danym warunkiem.

Poniższy przykład kodu demonstruje użycie `List.find` programu w celu znalezienia pierwszego numeru, który jest podzielny przez 5 na liście.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

Wynik to 5.

Jeśli elementy muszą zostać przekształcone w pierwszej kolejności, wywołaj [listę. pobranie](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), która pobiera funkcję, która zwraca opcję, i szuka pierwszej wartości opcji, która jest `Some(x)`. Zamiast zwracać element, `List.pick` zwraca wynik. `x` Jeśli nie zostanie znaleziony pasujący element `List.pick` , `System.Collections.Generic.KeyNotFoundException`zgłosi. Poniższy kod ilustruje użycie `List.pick`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

Wynik jest następujący:

```
"b"
```

Inna grupa operacji wyszukiwania, [list. tryFind —](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) i powiązanych funkcji, zwracają wartość opcji. Funkcja zwraca pierwszy element listy, który spełnia warunek, jeśli taki element istnieje, ale wartość `None` opcji, jeśli nie. `List.tryFind` Lista wariacji [. tryFindIndex —](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) zwraca indeks elementu, jeśli został znaleziony, a nie sam element. Te funkcje są zilustrowane w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

Wynik jest następujący:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Operacje arytmetyczne na listach

Typowe operacje arytmetyczne, takie jak sum i Average, są wbudowane w [moduł listy](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Aby można było korzystać z [list. sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), typ elementu listy musi obsługiwać `+` operatora i mieć wartość zerową. Wszystkie wbudowane typy arytmetyczne spełniają te warunki. Aby można było korzystać z [listy. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musi obsługiwać dzielenie bez reszty, która wyklucza typy całkowite, ale pozwala na używanie zmiennoprzecinkowych typów. Funkcje [list. sumBy —](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) i [list. averageBy —](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) przyjmują funkcję jako parametr, a wyniki tej funkcji są używane do obliczania wartości sum lub średniej.

Poniższy kod ilustruje użycie `List.sum`, `List.sumBy`, i `List.average`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

Dane wyjściowe to `1.000000`.

Poniższy kod ilustruje użycie `List.averageBy`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

Dane wyjściowe to `5.5`.

### <a name="lists-and-tuples"></a>Listy i krotki

Listy zawierające krotki mogą być przetwarzane przy użyciu funkcji zip i rozpakowania. Te funkcje łączą dwie listy pojedynczych wartości w jedną listę spójnych kolekcji lub dzielą jedną listę krotek na dwie listy pojedynczych wartości. Najprostsza funkcja [list. zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) przyjmuje dwie listy pojedynczych elementów i tworzy pojedynczą listę par krotek. Inna wersja, [list. zip3 —](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), pobiera trzy listy pojedynczych elementów i tworzy pojedynczą listę spójnych kolekcji, które mają trzy elementy. Poniższy przykład kodu demonstruje użycie `List.zip`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

Wynik jest następujący:

```
[(1, -1); (2, -2); (3; -3)]
```

Poniższy przykład kodu demonstruje użycie `List.zip3`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

Wynik jest następujący:

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Odpowiednie wersje rozpakować, [list. rozpakować](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) i [list. unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), przyjmują listy krotek i listy zwracane w spójnej kolekcji, gdzie pierwsza lista zawiera wszystkie elementy, które wcześniej znajdowały się w każdej kolekcji, a druga lista zawiera drugi element każdego Krotka i tak dalej.

Poniższy przykład kodu demonstruje użycie [list.](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)rozpakowywanie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

Wynik jest następujący:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Poniższy przykład kodu demonstruje użycie [list. unzip3 —](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

Wynik jest następujący:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Działa na elementach listy

F#obsługuje różne operacje na elementach listy. Najprostszą jest [Lista. ITER](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), która umożliwia wywoływanie funkcji dla każdego elementu listy. Wariacje obejmują [list. iter2 —](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), które umożliwiają wykonywanie operacji na elementach dwóch list, [list. iteri —](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), `List.iter` które przypominają, że indeks każdego elementu jest przenoszona jako argument do funkcji, która jest wywoływana dla każdego element oraz [list. iteri2 —](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), który jest kombinacją funkcji `List.iter2` i. `List.iteri` Poniższy przykład kodu ilustruje te funkcje.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

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

Inna często używana funkcja, która przekształca elementy listy to [list. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), która umożliwia zastosowanie funkcji do każdego elementu listy i umieszczenie wszystkich wyników w nowej liście. [List. MAP2 —](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) i [list. map3 —](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) są odmianami, które pobierają wiele list. Można również użyć [list. MAPI](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) i [list. mapi2 —](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), jeśli oprócz elementu, funkcja musi zostać przeniesiona indeks każdego elementu. Jedyną różnicą między `List.mapi2` i `List.mapi` jest to `List.mapi2` , że program współpracuje z dwiema listami. Poniższy przykład ilustruje [list. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

Wynik jest następujący:

```
[2; 3; 4]
```

W poniższym przykładzie pokazano użycie `List.map2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

Wynik jest następujący:

```
[5; 7; 9]
```

W poniższym przykładzie pokazano użycie `List.map3`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

Wynik jest następujący:

```
[7; 10; 13]
```

W poniższym przykładzie pokazano użycie `List.mapi`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

Wynik jest następujący:

```
[1; 3; 5]
```

W poniższym przykładzie pokazano użycie `List.mapi2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

Wynik jest następujący:

```
[0; 7; 18]
```

[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) `List.map`przypomina, z tą różnicą, że każdy element tworzy listę i wszystkie te listy są łączone w ostateczną listę. W poniższym kodzie każdy element listy generuje trzy liczby. Wszystkie te dane są zbierane w jednej liście.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

Wynik jest następujący:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Można również użyć [list. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), który przyjmuje warunek logiczny i tworzy nową listę, która składa się tylko z elementów, które spełniają określony warunek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

Lista `[2; 4; 6]`wyników.

Kombinacja map i filtru, [list. Choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) umożliwia przekształcanie i zaznaczanie elementów w tym samym czasie. `List.choose`stosuje funkcję, która zwraca opcję do każdego elementu listy i zwraca nową listę wyników dla elementów, gdy funkcja zwraca wartość `Some`opcji.

Poniższy kod ilustruje użycie `List.choose` do zaznaczania wersalików wyrazów z listy wyrazów.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

Wynik jest następujący:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Działa na wielu listach

Listy można łączyć ze sobą. Aby dołączyć dwie listy do jednej, użyj [list. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). Aby dołączyć więcej niż dwie listy, użyj [list. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Operacje składania i skanowania

Niektóre operacje na listach obejmują wzajemne zależności między wszystkimi elementami listy. Operacje składania i skanowania są podobne `List.iter` i `List.map` w przypadku wywołania funkcji dla każdego elementu, ale te operacje zapewniają dodatkowy parametr o nazwie *akumulowana* , który przenosi informacje za pomocą obliczeń.

Służy `List.fold` do wykonywania obliczeń na liście.

Poniższy przykład kodu demonstruje użycie [list. zgięcie](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) do wykonywania różnych operacji.

Lista jest przesunięta; akumulacja `acc` jest wartością, która jest przenoszona wraz z przeprowadzeniem obliczeń. Pierwszy argument przyjmuje wartość akumulowana i element list i zwraca pośredni wynik obliczeń dla tego elementu listy. Drugi argument jest początkową wartością akumulowana.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

Wersje tych funkcji, które mają cyfrę w nazwie funkcji, działają na więcej niż jednej liście. Na przykład, [list. fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) wykonuje obliczenia na dwóch listach.

Poniższy przykład ilustruje użycie `List.fold2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold`and [list. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) różni się, `List.fold` która zwraca końcową wartość dodatkowego parametru, ale `List.scan` zwraca listę wartości pośrednich (wraz z wartością końcową) dodatkowego parametru.

Każda z tych funkcji zawiera odwrotną odmianę, na przykład [list. foldBack —](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), która różni się w kolejności, w jakiej jest przesunięty listy, i kolejności argumentów. Ponadto `List.fold` i`List.foldBack` mają różne odmiany, [list. fold2 —](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) i [list. foldBack2 —](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), które pobierają dwie listy o równej długości. Funkcja, która jest wykonywana dla każdego elementu, może użyć odpowiednich elementów obu list do wykonania pewnej akcji. Typy elementów dwóch list mogą być różne, jak w poniższym przykładzie, w którym jedna lista zawiera kwoty transakcji dla konta bankowego, a druga lista zawiera typ transakcji: kaucja lub wycofanie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

W przypadku obliczeń, takich jak `List.fold` suma `List.foldBack` i ma ten sam skutek, ponieważ wynik nie zależy od kolejności przechodzenia. W poniższym przykładzie `List.foldBack` jest używany do dodawania elementów na liście.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

Poniższy przykład zwraca dane do przykładu konta bankowego. Tym razem zostanie dodany nowy typ transakcji: Obliczanie odsetek. Saldo końcowe jest teraz zależne od kolejności transakcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

Lista funkcji [. Redukcja](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) jest nieco taka sama `List.fold` jak `List.scan`i, z tą różnicą, że zamiast przechodzenia do `List.reduce` innego akumulowana, przyjmuje funkcję, która przyjmuje dwa argumenty typu elementu zamiast jednego z nich. argumenty pełnią rolę akumulowana, co oznacza, że przechowuje pośredni wynik obliczeń. `List.reduce`zaczyna się od działania pierwszego z dwóch elementów listy, a następnie używa wyniku operacji wraz z następnym elementem. Ponieważ nie istnieje oddzielny obiekt, który ma własny typ, może `List.reduce` być używany `List.fold` zamiast tylko wtedy, gdy obiekt, który ma ten sam typ i typ elementu. Poniższy kod ilustruje użycie `List.reduce`. `List.reduce`zgłasza wyjątek, jeśli podana lista nie zawiera żadnych elementów.

W poniższym kodzie, pierwsze wywołanie do wyrażenia lambda otrzymuje argumenty 2 i 4 i zwraca 6, a następne wywołanie otrzymuje argumenty 6 i 10, więc wynik wynosi 16.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Konwertowanie między listami i innymi typami kolekcji

`List` Moduł zawiera funkcje do konwersji do i z obu sekwencji i tablic. Aby przekonwertować sekwencję na lub z sekwencji, użyj [list. toSeq —](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) lub [list. ofSeq —](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). Aby przekonwertować na tablicę lub z niej, użyj [list. ToArray —](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) lub [list. ofArray —](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).

### <a name="additional-operations"></a>Dodatkowe operacje

Aby uzyskać informacje na temat dodatkowych operacji na listach, zobacz temat Dokumentacja biblioteki [kolekcje. list](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
- [Sekwencje](sequences.md)
- [Tablice](arrays.md)
- [Opcje](options.md)
