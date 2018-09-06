---
title: Sekwencje (F#)
description: 'Dowiedz się, jak sekwencje F #, gdy masz duży, uporządkowany zbiór danych, ale nie zawsze będziesz korzystać ze wszystkich elementów.'
ms.date: 05/16/2016
ms.openlocfilehash: cfe8d1e350a8ac46b7700c12aa84d250f8b35855
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776451"
---
# <a name="sequences"></a>Sekwencje

> [!NOTE]
Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

A *sekwencji* logicznej serii elementów jest jeden typ. Sekwencje są szczególnie przydatne, gdy masz duży, uporządkowany zbiór danych, ale nie planujesz korzystać ze wszystkich elementów. Sekwencja poszczególne elementy są obliczane tylko jako wymagane, dlatego sekwencji może zapewnić lepszą wydajność niż lista w sytuacjach, w którym nie wszystkie elementy są używane. Sekwencje są reprezentowane przez `seq<'T>` typ, który jest aliasem dla `System.Collections.Generic.IEnumerable`. W związku z tym, dowolny typ .NET Framework, który implementuje `System.IEnumerable` może służyć jako sekwencja. [Seq — moduł](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) zapewnia obsługę manipulacje obejmujące sekwencji.

## <a name="sequence-expressions"></a>Wyrażenia sekwencyjne

A *sekwencji wyrażeń* jest na wyrażenie obliczane do sekwencji. Wyrażenia sekwencji może zająć wiele formularzy. Najprostsza forma określa zakres. Na przykład `seq { 1 .. 5 }` tworzy sekwencję która zawiera pięć elementów, łącznie z punktami końcowymi 1 i 5. Można również określić przyrostowa (lub dekrementacji) między dwoma okresami double. Na przykład poniższy kod tworzy sekwencję wielokrotności 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Wyrażenia sekwencyjne składają się z wyrażeń języka F #, które generują wartości sekwencji. Mogą używać `yield` — słowo kluczowe do produkcji wartości, które stają się częścią sekwencji.

Poniżej znajduje się przykład.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Możesz użyć `->` operator zamiast `yield`, w którym to przypadku można pominąć `do` — słowo kluczowe, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Poniższy kod generuje listę par współrzędnych wraz z indeks do tablicy, która reprezentuje siatki.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if` Wyrażenie użyte w sekwencji jest filtrem. Na przykład, aby wygenerować sekwencji tylko liczb pierwszych, przy założeniu, że masz funkcji `isprime` typu `int -> bool`, w następujący sposób utworzenia sekwencji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Kiedy używasz `yield` lub `->` w iteracji każdej iteracji oczekuje się, aby wygenerować pojedynczy element sekwencji. Jeśli każda iteracja tworzy sekwencję elementów, użyj `yield!`. W takiej sytuacji elementy wygenerowane w każdej iteracji są łączone w celu utworzenia ostatniej sekwencji.

Można połączyć wiele wyrażeń w to wyrażenie sekwencji. Elementy wygenerowane przez każde wyrażenie są połączone ze sobą. Aby uzyskać przykład zobacz sekcję "Przykłady" w tym temacie.

## <a name="examples"></a>Przykłady

W pierwszym przykładzie użyto wyrażenia sekwencji, zawierający iteracji, filtr i wydajności do generowania tablicy. Ten kod wyświetla sekwencję liczb pierwszych od 1 do 100 konsoli.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Poniższy kod używa `yield` Aby utworzyć tabelę mnożenia, która składa się z krotek trzech elementów, składających się z dwóch czynników i produkt.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

W poniższym przykładzie pokazano użycie `yield!` połączyć poszczególnych sekwencje na jednym ostatniej sekwencji. W tym przypadku sekwencji dla każdego poddrzewo w drzewie binarnym są łączone w funkcji cykliczne, aby wygenerować ostateczny sekwencji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Korzystanie z sekwencji

Sekwencje obsługują wiele tych samych funkcjach jak [Wyświetla](lists.md). Sekwencje obsługuje również operacje, takie jak grupowanie, a wciąż dochodzą nowe, za pomocą funkcji generowania klucza. Sekwencje również obsługę funkcji bardziej zróżnicowane wyodrębnianie podciągów.

Wiele typów danych, takich jak list, tablic, zestawy i map są niejawnie sekwencje, ponieważ są one przeliczalne kolekcje. Funkcja, która wykonuje sekwencję, jak argument działa ze wszystkimi F # typy danych, oprócz dowolnego typu danych .NET Framework, który implementuje `System.Collections.Generic.IEnumerable<'T>`. Natomiast to do funkcji, która przyjmuje listę jako argument, który przyjmuje tylko listy. Typ `seq<'T>` jest skrótem typu dla `IEnumerable<'T>`. Oznacza to, że dowolny typ, który implementuje ogólnego `System.Collections.Generic.IEnumerable<'T>`, która obejmuje tablic, list, ustawia i map w F #, a także większość typów programu .NET Framework kolekcji, jest zgodna z `seq` typu i może służyć wszędzie tam, gdzie oczekuje sekwencji.

## <a name="module-functions"></a>Funkcje modułu

[Seq — moduł](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) w [Microsoft.fsharp.Collections — przestrzeń nazw](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) zawiera funkcje do pracy z sekwencji. Funkcje te działają z listy, tablice, mapy i zestawy, ponieważ wszystkie te typy są wyliczalny i może być traktowana jako sekwencje.

## <a name="creating-sequences"></a>Tworzenie sekwencji

Można utworzyć sekwencji, za pomocą wyrażenia sekwencji, zgodnie z opisem w poprzedniej sekcji, lub za pomocą niektórych funkcji.

Utworzysz pustą sekwencją za pomocą [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), lub możesz utworzyć sekwencję tylko jeden element określonej za pomocą [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

Możesz użyć [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) utworzenia sekwencji, dla której elementy są tworzone za pomocą funkcji, które należy podać. Możesz także udostępnić o rozmiarze sekwencji. Ta funkcja jest podobnie jak [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), z tą różnicą, że elementy nie są tworzone, dopóki iterację sekwencji. Poniższy kod ilustruje sposób korzystania z `Seq.init`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

Dane wyjściowe są

```
0 10 20 30 40
```

Za pomocą [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) i [Seq.ofList&#60;t&#62; funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), można tworzyć sekwencje z tablicami i listami. Jednak możesz również przeprowadzić konwersję tablicami i listami sekwencji za pomocą operatora rzutowania. Obu tych technik przedstawiono w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

Za pomocą [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), należy utworzyć sekwencję z słabo typizowaną kolekcji, takie jak te zdefiniowane `System.Collections`. Takie kolekcje słabo typizowaną mają typ elementu `System.Object` i wyliczane są przy użyciu niepodstawowy `System.Collections.Generic.IEnumerable&#96;1` typu. Poniższy kod ilustruje sposób korzystania z `Seq.cast` przekonwertować `System.Collections.ArrayList` do sekwencji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

Można zdefiniować nieograniczony sekwencji za pomocą [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) funkcji. Taką sekwencję podasz funkcja, która generuje każdego elementu z indeksu elementu. Ze względu na obliczanie z opóźnieniem; możliwe są nieskończone sekwencji elementy są tworzone zgodnie z potrzebami przez wywołanie funkcji, które określisz. Poniższy przykład kodu tworzy sekwencję nieskończonej przemienne serii odwrotności kwadratów liczb całkowitych kolejnych liczb, w tym przypadku zmiennoprzecinkowych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[SEQ.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generuje sekwencję przez funkcję obliczeń, który przyjmuje stan i przekształca je w celu wygenerowania każdego kolejnego elementu w sekwencji. Stan to po prostu wartość, która jest używana do obliczenia każdego elementu i można zmienić, ponieważ każdy element jest kolumną obliczaną. Drugi argument `Seq.unfold` jest to wartość początkowa, który służy do uruchomienia sekwencji. `Seq.unfold` używa typu opcji stanu, co pozwala na zakończenie sekwencji, zwracając `None` wartość. Poniższy kod pokazuje dwa przykłady sekwencji, `seq1` i `fib`, które są generowane przez `unfold` operacji. Pierwsza strona, `seq1`, jest po prostu prosty sekwencję cyfr liczącą do 100. Druga Strona, `fib`, używa `unfold` do obliczenia sekwencji Fibonacci. Ponieważ każdy element w sekwencji Fibonacci to suma poprzednich dwóch liczb Fibonacci, wartość stanu jest spójną kolekcją, która składa się z poprzednich dwóch liczb w sekwencji. Wartość początkowa to `(1,1)`, najpierw dwóch liczb w sekwencji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

Dane wyjściowe wyglądają następująco:

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Poniższy kod jest przykładem, który używa wielu funkcji modułu sekwencji, które są opisane tutaj, aby wygenerować i obliczanie wartości nieskończonej sekwencji. Kod może potrwać kilka minut.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Wyszukiwanie i znajdowanie elementów

Sekwencje obsługuje funkcje dostępne z listami: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [ SEQ.Pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), i [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Wersje tych funkcji, które są dostępne dla sekwencji ocenić sekwencji tylko do elementu, który jest przeszukiwany dla. Aby uzyskać przykłady, zobacz [Wyświetla](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).

## <a name="obtaining-subsequences"></a>Uzyskiwanie podciągów

[SEQ.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) i [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) są takie jak odpowiednimi funkcjami, które są dostępne dla listy, z tą różnicą, że filtrowanie i wybierając przeprowadzona dopiero po elementy sekwencji są oceniane.

[SEQ.TRUNCATE](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) tworzy sekwencję z innej sekwencji, ale ogranicza sekwencji do określonej liczby elementów. [SEQ.Take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) tworzy nową sekwencję zawierającą określoną liczbę elementów od początku sekwencji. W przypadku mniejszej liczby elementów w sekwencji, nie należy określić, aby móc, `Seq.take` zgłasza `System.InvalidOperationException`. Różnica między `Seq.take` i `Seq.truncate` jest fakt, że `Seq.truncate` nie generuje błąd, jeśli liczba elementów, które jest mniej niż liczbę.

Poniższy kod przedstawia działanie oraz różnice między `Seq.truncate` i `Seq.take`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

Dane wyjściowe, zanim wystąpi błąd, to w następujący sposób.

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

Za pomocą [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), można określić funkcji predykatu (funkcja logiczna) i utworzenia sekwencji z innej sekwencji składają się z tych elementów w oryginalnej sekwencji, dla którego predykat jest `true`, ale Zatrzymaj przed pierwszym elementem, dla którego predykat zwraca `false`. [SEQ.SKIP](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) zwraca sekwencję pomija określoną liczbę pierwszych elementów innej sekwencji, która zwraca wszystkie pozostałe elementy. [Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) zwraca sekwencję, które pomija pierwszych elementów innej sekwencji, tak długo, jak predykat zwraca `true`, a następnie zwraca pozostałe elementy, zaczynając od pierwszego elementu, dla którego predykat zwraca `false`.

Poniższy przykład kodu ilustruje działanie oraz różnice między `Seq.takeWhile`, `Seq.skip`, i `Seq.skipWhile`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

Dane wyjściowe są następujące:

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Przekształcanie sekwencji

[SEQ.Pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) tworzy nową sekwencję, w którym kolejne elementy sekwencji wejściowych są grupowane w kolekcje.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[SEQ.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) przypomina `Seq.pairwise`, z tą różnicą, że zamiast produkujących sekwencji krotek, tworzy sekwencję tablic, które zawierają kopie sąsiadujące elementy ( *okna*) z sekwencji. Określasz liczbę sąsiadujące elementy, które mają w każdej macierzy.

Poniższy przykład kodu demonstruje użycie `Seq.windowed`. W tym przypadku liczbę elementów w oknie to 3. W przykładzie użyto `printSeq`, który jest zdefiniowany w poprzednim przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

Dane wyjściowe są następujące:

Początkowej sekwencji:

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Operacje dotyczące wielu sekwencji

[SEQ.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) i [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) dwóch lub trzech sekwencji i tworzące sekwencji krotek. Te funkcje są podobne do odpowiednich funkcji dostępnych dla [Wyświetla](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Nie ma żadnych odpowiednie funkcje, aby oddzielić jednej sekwencji w co najmniej dwóch sekwencji. Jeśli potrzebujesz tej funkcji dla sekwencji konwertowanie sekwencji do listy i użyj [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

## <a name="sorting-comparing-and-grouping"></a>Sortowanie, porównywanie i grupowanie

Obsługiwane w przypadku list funkcje sortowania, która jest również działać z sekwencji. Obejmuje to [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) i [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Te funkcje iterację całą sekwencję.

Porównanie dwóch sekwencji przy użyciu [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) funkcji. Funkcja porównuje kolejne elementy z kolei i zatrzymuje się po napotkaniu pierwszego pary nierówne. Wszelkie dodatkowe elementy nie przyczyniają się do porównania.

Poniższy kod przedstawia użycie `Seq.compareWith`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

W poprzednim kodzie tylko pierwszy element jest obliczana i zbadane, a wynikiem jest wartość -1.

[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) przyjmuje funkcja, która generuje wartość o nazwie *klucz* dla każdego elementu. Klucz jest generowany dla każdego elementu przez wywołanie tej funkcji dla każdego elementu. `Seq.countBy` Zwraca sekwencję która zawiera wartości klucza i liczbę elementów, które są generowane każdej wartości klucza.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

Dane wyjściowe są następujące:

```
(1, 34) (2, 33) (0, 33)
```

Poprzednie dane wyjściowe pokazują, że istnieją elementy 34 oryginalnej sekwencji, który klawisz 1, 33 wartości, które wygenerowały klucz 2 i 33 wartości, które wygenerowały klucz 0.

Można grupować elementy sekwencji, wywołując [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy` przyjmuje się, sekwencja i funkcję, która generuje klucz z elementu. Funkcja jest wykonywany dla każdego elementu w sekwencji. `Seq.groupBy` Zwraca sekwencję krotek, gdzie pierwszy element każda Krotka jest kluczem, a drugą jest wartość sekwencji elementów, które generują ten klucz.

Poniższy przykład kodu pokazuje użycie `Seq.groupBy` do partycjonowania sekwencji liczb z zakresu od 1 do 100 na trzy grupy, które mają różne wartości klucza, 0, 1 i 2.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

Dane wyjściowe są następujące:

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Można utworzyć sekwencji, które eliminuje zduplikowane elementy, wywołując [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Możesz też [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), który przyjmuje generowania klucza funkcję, która ma być wywoływana dla każdego elementu. Wynikowa sekwencja zawiera elementy oryginalnej sekwencji, które mają unikatowe klucze; nowsze elementy, które generuje zduplikowany klucz do wcześniejszych elementu są odrzucane.

Poniższy przykład kodu ilustruje użycie `Seq.distinct`. `Seq.distinct` obrazuje generowania sekwencji, które reprezentują binarne wartości, a następnie wskazującą, że tylko odrębnych elementach 0 i 1.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

Poniższy przykład demonstruje `Seq.distinctBy` przez uruchomienie sekwencji, która zawiera numery ujemny i dodatni i przy użyciu funkcji wartość bezwzględna jako funkcja generowania klucza. Wynikowa sekwencja nie zawiera wszystkie liczby dodatnie, które odpowiadają liczby ujemne w sekwencji, ponieważ liczbami ujemnymi pojawiają się wcześniej w sekwencji i w związku z tym są wybierane zamiast liczb dodatnich, które mają ten sam bezwzględną wartość lub klucz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Tylko do odczytu i pamięci podręcznej sekwencji

[SEQ.ReadOnly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) tworzy kopię tylko do odczytu w sekwencji. `Seq.readonly` jest przydatne, gdy masz kolekcję odczytu i zapisu, takich jak tablica, a nie chcesz modyfikować oryginalnej kolekcji. Ta funkcja może służyć do zachowania hermetyzacja danych. W poniższym przykładzie kodu jest tworzony typ, który zawiera tablicę. Właściwość udostępnia tablicy, ale zamiast zwracać tablicę, zwraca sekwencję która jest tworzona z tablicy przy użyciu `Seq.readonly`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[SEQ.Cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) tworzy składowana wersję sekwencji. Użyj `Seq.cache` w celu uniknięcia ponownej oceny sekwencji lub, jeśli wiele wątków, które za pomocą sekwencji, lecz należy się upewnić, że każdy element jest podjęte tylko jeden raz. W przypadku sekwencji, która jest używana przez wiele wątków może mieć jeden wątek, który wylicza i oblicza wartości oryginalnej sekwencji, a pozostałych wątków można użyć pamięci podręcznej sekwencji.

## <a name="performing-computations-on-sequences"></a>Wykonywanie obliczeń na sekwencje

Proste operacje arytmetyczne są podobne do tych list, takich jak [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)i tak dalej.

[SEQ.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), i [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) są takie jak odpowiednimi funkcjami, które są dostępne dla listy. Sekwencje obsługuje podzestaw pełnego odchylenia tych funkcji, który zawiera listę pomocy technicznej. Aby uzyskać więcej informacji i przykładów, zobacz [Wyświetla](lists.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
