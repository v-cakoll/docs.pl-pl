---
title: Sekwencje
description: Dowiedz się, F# jak używać sekwencji, gdy masz dużą uporządkowaną kolekcję danych, ale niekoniecznie używać wszystkich elementów.
ms.date: 11/04/2019
ms.openlocfilehash: 34e03f1cead0a9f678f637afcb6c8397ef7572bc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971446"
---
# <a name="sequences"></a>Sekwencje

> [!NOTE]
> Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

*Sekwencja* jest logiczną serią wszystkich elementów jednego typu. Sekwencje są szczególnie przydatne w przypadku dużej, uporządkowanej kolekcji danych, ale niekoniecznie używać wszystkich elementów. Poszczególne elementy sekwencji są obliczane tylko w razie potrzeby, dlatego sekwencja może zapewnić lepszą wydajność niż lista w sytuacjach, w których nie wszystkie elementy są używane. Sekwencje są reprezentowane przez typ `seq<'T>`, który jest aliasem dla <xref:System.Collections.Generic.IEnumerable%601>. W związku z tym każdy typ .NET, który implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>, może być używany jako sekwencja. [Moduł SEQ](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) zapewnia obsługę operacji dla operacji związanych z sekwencjami.

## <a name="sequence-expressions"></a>Wyrażenia sekwencji

*Wyrażenie sekwencji* jest wyrażeniem, którego wynikiem jest sekwencja. Wyrażenia sekwencji mogą przyjmować wiele form. Najprostsza forma określa zakres. Na przykład `seq { 1 .. 5 }` tworzy sekwencję zawierającą pięć elementów, w tym punkty końcowe 1 i 5. Możesz również określić przyrost (lub zmniejszany) między dwoma podwójnymi kropkami. Na przykład poniższy kod tworzy sekwencję wielokrotności 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Wyrażenia sekwencji składają się z F# wyrażeń, które tworzą wartości sekwencji. Można również programowo generować wartości:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Poprzedni przykład używa operatora `->`, który umożliwia określenie wyrażenia, którego wartość stanie się częścią sekwencji. `->` można używać tylko wtedy, gdy każda część kodu, który następuje po zwraca wartość.

Alternatywnie możesz określić słowo kluczowe `do` z opcjonalnymi `yield`, które są następujące:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Poniższy kod generuje listę par współrzędnych wraz z indeksem do tablicy, która reprezentuje siatkę. Należy zauważyć, że pierwsze wyrażenie `for` wymaga określenia `do`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

Wyrażenie `if` użyte w sekwencji jest filtrem. Na przykład, aby wygenerować sekwencję tylko liczb pierwszych, przy założeniu, że masz funkcję `isprime` typu `int -> bool`, Konstruuj sekwencję w następujący sposób.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Jak wspomniano wcześniej, w tym miejscu `do` jest wymagane, ponieważ nie ma `else` gałęzi, która przechodzi z `if`em. Jeśli spróbujesz użyć `->`, zostanie wyświetlony komunikat o błędzie informujący, że nie wszystkie gałęzie zwracają wartość.

## <a name="the-yield-keyword"></a>Słowo kluczowe `yield!`

Czasami może być konieczne dołączenie sekwencji elementów do innej sekwencji. Aby dołączyć sekwencję w innej sekwencji, należy użyć słowa kluczowego `yield!`:

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

Innym sposobem na zastanawianie się `yield!` jest to, że spłaszcza sekwencję wewnętrzną, a następnie dołącza ją w sekwencji zawierającej.

Gdy `yield!` jest używany w wyrażeniu, wszystkie pozostałe pojedyncze wartości muszą używać słowa kluczowego `yield`:

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

Określenie tylko `x` w poprzednim przykładzie spowoduje wygenerowanie żadnych wartości przez sekwencję.

## <a name="examples"></a>Przykłady

W pierwszym przykładzie używane jest wyrażenie sekwencji zawierające iterację, filtr i wartość Yield do wygenerowania tablicy. Ten kod drukuje sekwencję numerów pierwszych z zakresu od 1 do 100 w konsoli programu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Poniższy przykład tworzy tabelę mnożenia, która składa się z krotek trzech elementów, z których każdy składa się z dwóch czynników i produktu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

Poniższy przykład ilustruje użycie `yield!` do łączenia poszczególnych sekwencji w jedną końcową sekwencję. W takim przypadku sekwencje dla każdego poddrzewa w drzewie binarnym są łączone w funkcji cyklicznej, aby utworzyć ostateczną sekwencję.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Używanie sekwencji

Sekwencje obsługują wiele takich samych funkcji, jak [listy](lists.md). Sekwencje obsługują również operacje, takie jak grupowanie i zliczanie przy użyciu funkcji generujących klucze. Sekwencje obsługują również bardziej różnorodne funkcje wyodrębniania podsekwencji.

Wiele typów danych, takich jak listy, tablice, zestawy i mapy, to niejawne sekwencje, ponieważ są wyliczalnymi kolekcjami. Funkcja, która przyjmuje sekwencję jako argument, działa z dowolnym wspólnym F# typem danych, oprócz dowolnego typu danych platformy .NET, który implementuje `System.Collections.Generic.IEnumerable<'T>`. W przeciwieństwie do funkcji, która przyjmuje listę jako argument, który może przyjmować tylko listy. Typ `seq<'T>` jest skrótem typu dla `IEnumerable<'T>`. Oznacza to, że każdy typ implementujący ogólne `System.Collections.Generic.IEnumerable<'T>`, który obejmuje tablice, listy, zestawy i mapy w F#, a także większość typów kolekcji .NET, jest zgodny z typem `seq` i może być używany wszędzie tam, gdzie jest oczekiwana sekwencja.

## <a name="module-functions"></a>Funkcje modułu

[Moduł SEQ](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) w [przestrzeni nazw Microsoft. FSharp. Collections](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) zawiera funkcje do pracy z sekwencjami. Te funkcje działają również z listami, tablicami, mapami i zestawami, ponieważ wszystkie te typy są wyliczalne i dlatego mogą być traktowane jako sekwencje.

## <a name="creating-sequences"></a>Tworzenie sekwencji

Sekwencje można tworzyć przy użyciu wyrażeń sekwencji, jak opisano wcześniej lub korzystając z określonych funkcji.

Można utworzyć pustą sekwencję przy użyciu [SEQ. Empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)lub można utworzyć sekwencję tylko jednego określonego elementu przy użyciu [SEQ. singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

Za pomocą [SEQ. init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) można utworzyć sekwencję, dla której elementy są tworzone za pomocą podania funkcji. Możesz również podać rozmiar sekwencji. Ta funkcja jest tak samo jak [list. init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), z tą różnicą, że elementy nie są tworzone, dopóki nie przeprowadzisz iteracji przez sekwencję. Poniższy kod ilustruje sposób używania `Seq.init`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

Dane wyjściowe to

```console
0 10 20 30 40
```

Za pomocą [SEQ. ofArray —](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) i [SEQ. ofList —&#60;&#62; ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), można tworzyć sekwencje z tablic i list. Można jednak skonwertować tablice i listy na sekwencje przy użyciu operatora rzutowania. W poniższym kodzie przedstawiono obie techniki.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

Za pomocą [SEQ. Cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)można utworzyć sekwencję z niejednoznacznie wpisanej kolekcji, takiej jak te zdefiniowane w `System.Collections`. Takie kolekcje o nieokreślonych typach mają typ elementu `System.Object` i są wyliczane przy użyciu nieogólnego typu `System.Collections.Generic.IEnumerable&#96;1`. Poniższy kod ilustruje użycie `Seq.cast` do przekonwertowania `System.Collections.ArrayList` na sekwencję.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

Można zdefiniować nieskończone sekwencje przy użyciu funkcji [SEQ. initInfinite —](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) . Dla takiej sekwencji można dostarczyć funkcję, która generuje każdy element z indeksu elementu. Nieskończone sekwencje są możliwe z powodu oceny z opóźnieniem; elementy są tworzone zgodnie z wymaganiami, wywołując funkcję, którą określisz. Poniższy przykład kodu tworzy nieskończoną sekwencję liczb zmiennoprzecinkowych, w tym przypadku przemienny szereg reciprocals kwadratów kolejnych liczb całkowitych.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[SEQ. unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generuje sekwencję z funkcji obliczeniowej, która przyjmuje stan i przekształca ją w celu utworzenia każdego kolejnego elementu w sekwencji. Stan to tylko wartość, która jest używana do obliczenia każdego elementu i może ulec zmianie, gdy każdy element jest obliczany. Drugi argument `Seq.unfold` jest wartością początkową, która jest używana do uruchomienia sekwencji. `Seq.unfold` używa typu opcji dla stanu, który umożliwia zakończenie sekwencji poprzez zwrócenie wartości `None`. Poniższy kod przedstawia dwa przykłady sekwencji, `seq1` i `fib`, które są generowane przez operację `unfold`. Pierwsza, `seq1`, to prosta sekwencja z liczbami do 20. Drugi `fib`, używa `unfold` do obliczania sekwencji Fibonacci. Ponieważ każdy element w sekwencji Fibonacci jest sumą poprzednich dwóch liczb Fibonacci, wartość stanu jest krotką, która składa się z poprzednich dwóch liczb w sekwencji. Wartość początkowa to `(1,1)`, pierwsze dwie liczby w sekwencji.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

Dane wyjściowe są następujące:

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Poniższy kod to przykład, który używa wielu funkcji modułu sekwencji opisanych tutaj do generowania i obliczania wartości nieskończonych sekwencji. Uruchomienie kodu może potrwać kilka minut.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Wyszukiwanie i znajdowanie elementów

Funkcje obsługi sekwencji dostępne dla list: [SEQ. Exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [SEQ. exists2 —](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [SEQ. Find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [SEQ. FindIndex —](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [SEQ. pobranie](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [SEQ. tryFind —](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)i [SEQ. tryFindIndex —](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Wersje tych funkcji, które są dostępne dla sekwencji, ocenią sekwencję tylko do elementu, który jest wyszukiwany. Aby zapoznać się z przykładami, zobacz [listy](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).

## <a name="obtaining-subsequences"></a>Uzyskiwanie podsekwencji

[SEQ. Filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) i [SEQ. Choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) przypomina odpowiadające im funkcje, które są dostępne dla list, z tą różnicą, że filtrowanie i wybór nie występują do momentu obliczenia elementów sekwencji.

[SEQ. Truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) tworzy sekwencję z innej sekwencji, ale ogranicza sekwencję do określonej liczby elementów. [SEQ. Take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) tworzy nową sekwencję zawierającą tylko określoną liczbę elementów na początku sekwencji. Jeśli w sekwencji znajduje się mniej elementów niż określono do wykonania, `Seq.take` zgłasza `System.InvalidOperationException`. Różnica między `Seq.take` i `Seq.truncate` polega na tym, że `Seq.truncate` nie wygenerował błędu, jeśli liczba elementów jest mniejsza niż określona liczba.

Poniższy kod przedstawia zachowanie i różnice między `Seq.truncate` i `Seq.take`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

Dane wyjściowe przed wystąpieniem błędu są następujące.

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

Korzystając z [SEQ. TakeWhile —](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), można określić funkcję predykatu (funkcję logiczną) i utworzyć sekwencję z innej sekwencji składającej się z tych elementów oryginalnej sekwencji, dla której predykat jest `true`, ale zatrzymać przed pierwszym elementem dla który predykat zwraca `false`. [SEQ. Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) zwraca sekwencję, która pomija określoną liczbę pierwszych elementów w innej sekwencji i zwraca pozostałe elementy. [SEQ. SkipWhile —](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) zwraca sekwencję, która pomija pierwsze elementy innej sekwencji, tak długo, jak predykat zwraca `true`, a następnie zwraca pozostałe elementy, rozpoczynając od pierwszego elementu, dla którego predykat zwraca `false`.

Poniższy przykład kodu ilustruje zachowanie i różnice między `Seq.takeWhile`, `Seq.skip`i `Seq.skipWhile`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

Dane wyjściowe są następujące:

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Przekształcanie sekwencji

[SEQ. parowania](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) tworzy nową sekwencję, w której kolejne elementy sekwencji wejściowej są pogrupowane w krotki.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

[SEQ. Windowd](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) przypomina `Seq.pairwise`, z tą różnicą, że zamiast tworzenia sekwencji krotek tworzy sekwencję tablic zawierających kopie sąsiadujących elementów ( *okna*) z sekwencji. Należy określić liczbę sąsiadujących elementów, które mają być w każdej tablicy.

Poniższy przykład kodu demonstruje użycie `Seq.windowed`. W takim przypadku liczba elementów w oknie to 3. W przykładzie jest używany `printSeq`, który jest zdefiniowany w poprzednim przykładzie kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

Dane wyjściowe są następujące:

Sekwencja początkowa:

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Operacje z wieloma sekwencjami

[SEQ. zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) i [SEQ. zip3 —](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) mają dwie lub trzy sekwencje i tworzą sekwencję krotek. Te funkcje są podobne do odpowiednich funkcji dostępnych dla [list](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Nie ma odpowiedniej funkcjonalności do oddzielenia jednej sekwencji na dwie lub więcej sekwencji. Jeśli potrzebujesz tej funkcji dla sekwencji, przekonwertuj sekwencję na listę i użyj funkcji [list. Rozpakuj](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

## <a name="sorting-comparing-and-grouping"></a>Sortowanie, porównywanie i grupowanie

Funkcje sortowania obsługiwane dla list również działają z sekwencjami. Obejmuje to [SEQ. Sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) i [SEQ. SortBy —](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Te funkcje iterą przez całą sekwencję.

Można porównać dwie sekwencje przy użyciu funkcji [SEQ. CompareWith —](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) . Funkcja porównuje kolejne elementy z kolei i przerywa, gdy napotka on pierwszą nierówną parę. Wszelkie dodatkowe elementy nie przyczyniają się do porównania.

Poniższy kod przedstawia użycie `Seq.compareWith`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

W poprzednim kodzie tylko pierwszy element jest obliczany i sprawdzany, a wynik to-1.

[SEQ. countBy —](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) pobiera funkcję, która generuje wartość o nazwie *Key* dla każdego elementu. Dla każdego elementu jest generowany klucz, wywołując tę funkcję dla każdego elementu. `Seq.countBy` następnie zwraca sekwencję zawierającą wartości klucza oraz liczbę elementów, które wygenerowały każdą wartość klucza.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

Dane wyjściowe są następujące:

```console
(1, 34) (2, 33) (0, 33)
```

Poprzednie dane wyjściowe pokazują, że wystąpiły 34 elementy oryginalnej sekwencji, która wygenerowała wartości Key 1, 33, które wygenerowały klucz 2 i 33 wartości, które wygenerowały klucz 0.

Elementy sekwencji można grupować przez wywołanie [SEQ. GroupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy` przyjmuje sekwencję i funkcję, która generuje klucz z elementu. Funkcja jest wykonywana na każdym elemencie sekwencji. `Seq.groupBy` zwraca sekwencję krotek, gdzie pierwszy element każdej krotki jest kluczem, a drugi to sekwencja elementów, które tworzą ten klucz.

Poniższy przykład kodu ilustruje użycie `Seq.groupBy` do partycjonowania sekwencji liczb z 1 do 100 w trzech grupach, które mają odrębne wartości klucza 0, 1 i 2.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

Dane wyjściowe są następujące:

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Można utworzyć sekwencję, która eliminuje zduplikowane elementy przez wywołanie [SEQ. DISTINCT](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Można też użyć [SEQ. distinctBy —](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), który pobiera funkcję generującą klucz do wywołania dla każdego elementu. Utworzona sekwencja zawiera elementy oryginalnej sekwencji, które mają unikatowe klucze; późniejsze elementy, które generują zduplikowany klucz do wcześniejszego elementu, są odrzucane.

Poniższy przykład kodu ilustruje sposób używania `Seq.distinct`. `Seq.distinct` jest przedstawiany przez generowanie sekwencji, które reprezentują liczby binarne, a następnie pokazują, że jedyne różne elementy to 0 i 1.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

Poniższy kod ilustruje `Seq.distinctBy`, rozpoczynając od sekwencji zawierającej liczbę ujemną i dodatnią i używając funkcji wartości bezwzględnej jako funkcji generującej klucz. Wynikowa sekwencja nie zawiera wszystkich liczb dodatnich, które odpowiadają liczbom ujemnym w sekwencji, ponieważ liczby ujemne występują wcześniej w sekwencji i w związku z tym są wybierane zamiast liczb dodatnich, które mają te same bezwzględne wartość lub klucz.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Sekwencje ReadOnly i buforowane

[SEQ. ReadOnly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) tworzy kopię sekwencji tylko do odczytu. `Seq.readonly` jest przydatne, gdy masz kolekcję do odczytu i zapisu, taką jak tablica, i nie chcesz modyfikować oryginalnej kolekcji. Ta funkcja może służyć do zachowywania hermetyzacji danych. W poniższym przykładzie kodu zostanie utworzony typ zawierający tablicę. Właściwość uwidacznia tablicę, ale zamiast zwracać tablicę, zwraca sekwencję utworzoną z tablicy przy użyciu `Seq.readonly`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[SEQ. cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) tworzy przechowywaną wersję sekwencji. Użyj `Seq.cache`, aby uniknąć ponownej oceny sekwencji lub jeśli masz wiele wątków, które używają sekwencji, ale musisz się upewnić, że każdy element jest poddany działaniu tylko raz. Jeśli masz sekwencję, która jest używana przez wiele wątków, możesz mieć jeden wątek, który wylicza i oblicza wartości dla oryginalnej sekwencji, a pozostałe wątki mogą używać sekwencji w pamięci podręcznej.

## <a name="performing-computations-on-sequences"></a>Wykonywanie obliczeń na sekwencjach

Proste operacje arytmetyczne są podobne do tych list, takich jak [SEQ. Average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [SEQ. sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [SEQ. averageBy —](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [SEQ. sumBy —](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)i tak dalej.

[SEQ. złożenie](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [SEQ. Zmniejsz](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)i [SEQ. Scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) przypomina odpowiednie funkcje, które są dostępne dla list. Sekwencje obsługują podzestaw pełnych wariantów tych funkcji, które obsługują listę. Aby uzyskać więcej informacji i przykładów, zobacz [listy](lists.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
