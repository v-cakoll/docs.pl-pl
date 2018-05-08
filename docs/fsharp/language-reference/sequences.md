---
title: Sekwencje (F#)
description: 'Dowiedz się, jak używać F #, gdy masz duży, uporządkowanych zbierania danych, ale nie zawsze powinien korzystać ze wszystkich elementów.'
ms.date: 05/16/2016
ms.openlocfilehash: ebebec3a69fd0f4fb8e3ad8d554541fa1cc8945e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sequences"></a>Sekwencje

> [!NOTE]
Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

A *sekwencji* to zbiór logiczny elementy tylko jeden typ. Sekwencje są szczególnie przydatne, gdy ma dużą, uporządkowanych zbierania danych, ale nie zawsze będzie korzystać ze wszystkich elementów. Sekwencja poszczególne elementy są obliczane tylko jako wymagana, więc sekwencję może zapewnić lepszą wydajność niż lista w sytuacjach, w którym nie wszystkie elementy są używane. Sekwencje są reprezentowane przez `seq<'T>` typu, który jest aliasem dla `System.Collections.Generic.IEnumerable`. W związku z tym dowolnego typu .NET Framework, który implementuje `System.IEnumerable` mogą być używane jako sekwencję. [Seq — moduł](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) zapewnia obsługę manipulacje obejmujące sekwencji.

## <a name="sequence-expressions"></a>Wyrażenia sekwencji
A *wyrażenia sekwencji* jest wyrażenie obliczane do sekwencji. Wyrażenia sekwencji może zająć wiele formularzy. Najprostsza forma określa zakres. Na przykład `seq { 1 .. 5 }` tworzy sekwencję, która zawiera pięć elementów, w tym punkty końcowe 1 do 5. Można również określić inkrementacji (lub zmniejszyć) między dwoma okresami dwa razy. Na przykład poniższy kod tworzy sekwencję wielokrotności 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Sekwencja wyrażeń składają się z F # wyrażeń, które powodują powstanie wartości sekwencji. Mogą używać `yield` — słowo kluczowe do tworzenia wartości, która staje się częścią sekwencji.

Poniżej przedstawiono przykład.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Można użyć `->` operator zamiast `yield`, w takim przypadku można pominąć `do` — słowo kluczowe, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Poniższy kod generuje listę pary współrzędnych wraz z indeksu do tablicy, która reprezentuje siatki.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if` Wyrażenie użyte w sekwencji jest filtrem. Na przykład, aby wygenerować sekwencję tylko liczb pierwszych, przy założeniu, że funkcja `isprime` typu `int -> bool`, w następujący sposób utworzenia sekwencji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Jeśli używasz `yield` lub `->` w iteracji, powinien wygenerować pojedynczego elementu sekwencji każdej iteracji. Jeśli w każdej iteracji tworzy sekwencję elementów, użyj `yield!`. W takim przypadku elementy generowane w każdej iteracji są łączone wygenerowało końcowego sekwencji.

Można połączyć wiele wyrażeń w wyrażenia sekwencji. Elementy generowane przez każde wyrażenie są połączone ze sobą. Na przykład zobacz sekcję "Przykłady" w tym temacie.

## <a name="examples"></a>Przykłady
Pierwszym przykładzie użyto wyrażenia sekwencji, zawierający iteracji, filtr i wydajności, aby wygenerować tablicy. Ten kod wyświetla sekwencję liczb pierwszych od 1 do 100 konsoli.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Poniższy kod używa `yield` do utworzenia tabeli mnożenia składający się z krotek trzy elementy, każdy zawiera dwa składniki i produktu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

W poniższym przykładzie pokazano użycie `yield!` połączyć poszczególnych sekwencji do pojedynczego ciągu końcowego. W takim przypadku sekwencji dla każdego poddrzewo w drzewa binarnego są łączone w funkcji cyklicznej wygenerowało końcowego sekwencji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]
    
## <a name="using-sequences"></a>Przy użyciu sekwencji
Sekwencje obsługuje wiele funkcji [wymieniono](lists.md). Sekwencje również obsługiwać operacji, takich jak grupowanie i Zliczanie przy użyciu funkcji generowania klucza. Sekwencje również obsługę bardziej różnorodnych funkcji wyodrębniania podciągów.

Wiele typów danych, takich jak list, tablic, zestawów i map są niejawnie sekwencji, ponieważ są to wyliczalny kolekcji. Funkcja, która przyjmuje sekwencję jako argument działa ze wszystkimi F # typy danych, oprócz do dowolnego typu danych .NET Framework, który implementuje `System.Collections.Generic.IEnumerable<'T>`. Natomiast to funkcji pobierającej listę jako argument, który przyjmuje tylko list. Typ `seq<'T>` skrótu typu `IEnumerable<'T>`. Oznacza to, że dowolnego typu, który implementuje ogólnego `System.Collections.Generic.IEnumerable<'T>`, która obejmuje tablic, list, ustawia i map w F #, a także większości .NET Framework typy kolekcji, jest zgodna z `seq` wpisz i mogą być używane wszędzie tam, gdzie oczekiwano sekwencji.


## <a name="module-functions"></a>Moduł funkcji
[Seq — moduł](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) w [Microsoft.fsharp.Collections — przestrzeń nazw](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) zawiera nowe funkcje do pracy z sekwencji. Te funkcje pracować z list, tablic, map i również zestawów, ponieważ wszystkie te typy są wyliczalny i może być traktowana jako sekwencji.


## <a name="creating-sequences"></a>Tworzenie sekwencji
Można tworzyć sekwencje przy użyciu wyrażenia sekwencji, jak opisano wcześniej lub przy użyciu określonych funkcji.

Pustej sekwencji można tworzyć przy użyciu [SEQ.Empty —](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), lub można utworzyć sekwencję tylko jednego elementu określonego za pomocą [SEQ.Singleton —](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

Można użyć [SEQ.init —](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) do utworzenia sekwencji, dla którego elementy są tworzone za pomocą funkcji podane. Możesz także udostępnić o rozmiarze sekwencji. Ta funkcja jest tak jak [list.init —](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), z wyjątkiem, że elementy nie są tworzone, aż iterację sekwencji. Poniższy kod przedstawia użycie `Seq.init`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

Dane wyjściowe

```
0 10 20 30 40
```

Za pomocą [SEQ.ofarray —](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) i [SEQ.oflist —&#60;'T&#62; funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), można tworzyć sekwencje z tablicami i listami. Jednak możesz również przekonwertować tablicami i listami sekwencji za pomocą operatora rzutowania. Obie techniki przedstawiono w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

Za pomocą [SEQ.CAST —](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), należy utworzyć sekwencję z lekko typu kolekcji, takie jak te zdefiniowane `System.Collections`. Takie kolekcje typizowanych lekko ma typu elementu `System.Object` i są wyliczane przy użyciu nieogólnego `System.Collections.Generic.IEnumerable&#96;1` typu. Poniższy kod przedstawia użycie `Seq.cast` przekonwertować `System.Collections.ArrayList` w sekwencji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

Nieskończone sekwencji można zdefiniować za pomocą [SEQ.initinfinite —](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) funkcji. Takie sekwencji musisz podać funkcję, która generuje każdy element na podstawie indeks elementu. Nieskończone sekwencje są możliwe ze względu na obliczanie leniwe; elementy są tworzone zgodnie z potrzebami przez wywołanie funkcji, który określisz. Poniższy przykład kodu tworzy sekwencja nieskończona zmiennej ilości numery punktu, w tym przypadku przemiennych serii odwrotności kwadratów liczb całkowitych kolejne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[SEQ.unfold —](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generuje sekwencję z funkcji obliczeń, która przyjmuje stanie i przekształceniu go do produkcji każdego kolejnego elementu w sekwencji. Stan jest tylko wartość, która jest używana do obliczania każdy element i można zmienić, ponieważ każdy element jest obliczana. Drugi argument `Seq.unfold` jest to wartość początkowa, który służy do uruchomienia sekwencji. `Seq.unfold` używa typu opcji dla stanu, co pozwala na zakończenie sekwencji zwracając `None` wartość. Poniższy kod przedstawia dwa przykłady sekwencji, `seq1` i `fib`, które są generowane przez `unfold` operacji. Pierwsza strona, `seq1`, jest tylko proste sekwencja z cyfr liczącą do 100. Druga Strona, `fib`, używa `unfold` do obliczenia Fibonacci sekwencji. Ponieważ każdy element w sekwencji Fibonacci to suma poprzednich dwóch liczb Fibonacci, wartość stanu jest krotka składająca się z poprzednich dwóch liczb w sekwencji. Jest to wartość początkowa `(1,1)`, najpierw dwóch liczb w sekwencji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

Wynik jest następujący:

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Następujący kod jest przykładem korzystania z wielu funkcji modułu sekwencji opisanych tutaj, aby wygenerować i służą do obliczania wartości nieskończone sekwencji. Kod może potrwać kilka minut.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]
    
## <a name="searching-and-finding-elements"></a>Wyszukiwanie i wyszukiwanie elementów
Sekwencje obsługuje funkcje dostępne przy użyciu list: [SEQ.EXISTS —](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [SEQ.exists2 —](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [SEQ.Find —](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [SEQ.findindex —](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [ SEQ.Pick —](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [SEQ.tryfind —](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), i [SEQ.tryfindindex —](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Wersje tych funkcji, które są dostępne dla sekwencji ocenić sekwencji tylko do elementu, który jest przeszukiwany dla. Aby uzyskać przykłady, zobacz [wymieniono](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).


## <a name="obtaining-subsequences"></a>Uzyskiwanie podciągów
[SEQ.filter —](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) i [SEQ.Choose —](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) są takie jak odpowiednie funkcje, które są dostępne dla listy, z tą różnicą, że filtrowanie i wybierając przeprowadzona dopiero po elementy sekwencji są oceniane.

[SEQ.TRUNCATE —](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) tworzy sekwencję z innej sekwencji, lecz ogranicza sekwencji do określonej liczby elementów. [SEQ.Take —](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) tworzy nową sekwencję, zawierający tylko określoną liczbę elementów od początku sekwencji. W przypadku mniejszej liczby elementów w sekwencji niż określać podjęcie, `Seq.take` zgłasza `System.InvalidOperationException`. Różnica między `Seq.take` i `Seq.truncate` jest to, że `Seq.truncate` nie generuje błędu, jeśli liczba elementów jest mniej niż liczbę.

Poniższy kod przedstawia zachowania i różnice między `Seq.truncate` i `Seq.take`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

Dane wyjściowe, zanim wystąpi błąd, wygląda następująco.

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

Za pomocą [SEQ.takewhile —](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), można określić predykatu funkcji (funkcja logiczna) i utworzysz sekwencję z innej sekwencji składają się z tych elementów oryginalnej sekwencji, dla którego jest predykatu `true`, ale stop przed pierwszym elementem, dla którego predykat zwraca `false`. [SEQ.SKIP —](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) zwraca sekwencję pomija określoną liczbę pierwszych elementów innej sekwencji i zwraca wszystkie pozostałe elementy. [SEQ.skipwhile —](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) zwraca sekwencję pomijające pierwszych elementów innej sekwencji tak długo, jak predykat zwraca `true`, a następnie zwraca wszystkie pozostałe elementy, rozpoczynając od pierwszego elementu, dla którego predykat zwraca `false`.

Poniższy przykładowy kod przedstawia zachowania oraz różnice między `Seq.takeWhile`, `Seq.skip`, i `Seq.skipWhile`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

Dane wyjściowe są następujące:

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Przekształcanie sekwencji
[SEQ.Pairwise —](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) tworzy nową sekwencję, w którym sekwencja wejściowa kolejnych elementów są zgrupowane w krotek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[SEQ.windowed —](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) przypomina `Seq.pairwise`, ale zamiast produkujących sekwencji krotek, tworzy sekwencję tablic, które zawierają kopie elementy sąsiednie ( *okna*) z sekwencji. Możesz określić liczbę elementy sąsiednie, który ma w każdej macierzy.

Poniższy przykład kodu pokazuje użycie `Seq.windowed`. W takim przypadku liczba elementów w oknie to 3. W przykładzie użyto `printSeq`, która jest zdefiniowana w poprzednim przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

Dane wyjściowe są następujące:

Początkowa sekwencja:

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Operacje przy użyciu wielu sekwencji
[SEQ.zip —](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) i [SEQ.zip3 —](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) dwóch lub trzech sekwencji i tworzące sekwencji spójnych kolekcji. Te funkcje są podobne do odpowiedniej funkcji dostępnych dla [wymieniono](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Nie ma żadnych odpowiednich funkcji Rozdziel sekwencji jednej do dwóch lub więcej sekwencji. Należy ta funkcja sekwencji przekonwertować sekwencji do listy i użyj [list.Unzip —](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).


## <a name="sorting-comparing-and-grouping"></a>Sortowanie, porównanie i grupowania
Obsługiwane w przypadku list funkcje sortowania również współpracować z sekwencji. Obejmuje to [SEQ.sort —](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) i [SEQ.sortby —](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Te funkcje iterację całej sekwencji.

Porównanie dwóch sekwencji przy użyciu [SEQ.comparewith —](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) funkcji. Funkcja z kolei porównuje kolejnych elementów i przerywa działanie po napotkaniu pierwszego nierówne pary. Wszelkie dodatkowe elementy nie przyczyniają się do porównania.

Poniższy kod przedstawia użycie `Seq.compareWith`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

W poprzednim kodzie tylko pierwszy element jest obliczana i zbadane, a wynikiem jest wartość -1.

[SEQ.countby —](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) przyjmuje funkcję, która generuje wartość o nazwie *klucza* dla każdego elementu. Klucz jest generowany dla każdego elementu przez wywołanie tej funkcji na każdym elemencie. `Seq.countBy` Zwraca sekwencję, która zawiera wartości klucza, a liczba Liczba elementów wygenerowanych każdej wartości klucza.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

Dane wyjściowe są następujące:

```
(1, 34) (2, 33) (0, 33)
```

Dane wyjściowe poprzedniego pokazuje wystąpiły 34 elementy oryginalnej sekwencji wytworzonego klucz 1, 33 wartości, które tworzone klucz 2 i 33 wartości, które tworzone klucza 0.

W przypadku grupowania elementów sekwencji przez wywołanie metody [SEQ.groupby —](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy` pobiera sekwencję i funkcję, która generuje klucz w elemencie. Funkcja jest wykonywane dla każdego elementu w sekwencji. `Seq.groupBy` Zwraca sekwencję krotek, gdzie pierwszy element poszczególne krotki jest kluczem, a drugą jest wartość sekwencję elementów, które powodują powstanie tego klucza.

W poniższym przykładzie pokazano sposób użycia `Seq.groupBy` do partycjonowania sekwencji liczb od 1 do 100 na trzy grupy, które mają różne wartości klucza, 0, 1 i 2.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

Dane wyjściowe są następujące:

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Można utworzyć sekwencji, która eliminuje zduplikowane elementy przez wywołanie metody [SEQ.DISTINCT —](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Możesz też użyć [SEQ.distinctby —](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), który przyjmuje generowania klucza funkcję można wywołać dla każdego elementu. Wynikowa sekwencja zawiera elementy oryginalnej sekwencji, które miały unikatowe klucze; nowsze elementy, które tworzy zduplikowany klucz do elementu wcześniejszych zostaną odrzucone.

W poniższym przykładzie przedstawiono użycie `Seq.distinct`. `Seq.distinct` przedstawiono generowania sekwencji, które reprezentują binarne wartości, a następnie wskazującą, że tylko odrębnych elementach 0 i 1.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

Poniższy kod przedstawia `Seq.distinctBy` przez uruchomienie z sekwencją liczb ujemnych i dodatnich i jak funkcja generowania klucza przy użyciu funkcji wartość bezwzględna. Wynikowa sekwencja nie zawiera wszystkich dodatnie odpowiadające liczby ujemne w sekwencji, ponieważ liczby ujemne znajdują się wcześniej w kolejności i w związku z tym wybrano zamiast dodatnie, który ma tego samego bezwzględne wartość lub klucz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]
    
## <a name="readonly-and-cached-sequences"></a>Tylko do odczytu i pamięci podręcznej sekwencji
[SEQ.ReadOnly —](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) tworzy kopię tylko do odczytu w sekwencji. `Seq.readonly` jest przydatne, gdy masz kolekcję odczytu i zapisu, takich jak tablicy, i nie chcesz zmodyfikować oryginalnej kolekcji. Ta funkcja umożliwia zachowanie hermetyzacji danych. W poniższym przykładzie jest tworzony typ zawierający tablicę. Właściwość udostępnia tablicy, ale zamiast zwracać tablicy, zwraca sekwencję, która jest tworzona na podstawie tablicy przy użyciu `Seq.readonly`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[SEQ.Cache —](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) tworzy przechowywanej wersji sekwencji. Użyj `Seq.cache` można uniknąć ponownej oceny sekwencji lub, jeśli masz wiele wątków używających sekwencję, ale należy upewnić się, że każdy element reagować jest tylko jeden raz. Jeśli masz sekwencji, który jest używany przez wiele wątków może mieć jeden wątek, który wylicza i oblicza wartości oryginalnej sekwencji, a pozostałe wątki można użyć pamięci podręcznej sekwencji.


## <a name="performing-computations-on-sequences"></a>Wykonywanie obliczeń na sekwencji
Proste operacje arytmetyczne są podobne do tych list, takich jak [SEQ.AVERAGE —](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [SEQ.sum —](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [SEQ.averageby —](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [SEQ.sumby —](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)i tak dalej.

[SEQ.fold —](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [SEQ.Reduce —](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), i [SEQ.Scan —](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) są takie jak odpowiednie funkcje, które są dostępne dla listy. Sekwencje obsługuje podzestawie pełnego odchylenia tych funkcji, który zawiera obsługiwane. Aby uzyskać dodatkowe informacje i przykłady, zobacz [wymieniono](lists.md).

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Typy F#](fsharp-types.md)
