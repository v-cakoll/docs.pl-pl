---
title: Rozpoczynanie pracy z usługą F# w programie Visual Studio dla komputerów Mac
description: Dowiedz się, jak używać F# z programem Visual Studio dla komputerów Mac.
ms.date: 07/03/2018
ms.openlocfilehash: a6997f139d7e6c5fdf77878442db0b0b75b3d727
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331874"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Rozpoczynanie pracy z usługą F# w programie Visual Studio dla komputerów Mac

F#a wizualizacja F# narzędzi są obsługiwane w programie Visual Studio dla komputerów Mac w środowisku IDE. Upewnij się, że masz [Visual Studio for Mac zainstalowane](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsoli

Jednym z najprostszych projektów w programie Visual Studio dla komputerów Mac jest aplikacji konsoli.  Oto jak to zrobić.  Po otwarciu programu Visual Studio dla komputerów Mac:

1. Na **pliku** menu wskaż **nowe rozwiązanie**.

2. W oknie dialogowym Nowy projekt istnieją 2 różnych szablonów dla aplikacji konsoli.  Jest węzłem Other -> .NET, który jest przeznaczony dla .NET Framework.  Ten szablon jest w ramach platformy .NET Core -> Aplikacja, która jest przeznaczony dla platformy .NET Core.  Albo szablonu powinny działać na potrzeby tego artykułu.

3. W obszarze aplikacji konsoli, zmień C# do F# w razie potrzeby.  Wybierz **dalej** przycisk umożliwiający przenoszenie do przodu!  

4. Nadaj projektowi nazwę, a następnie wybierz odpowiednie opcje dla aplikacji.  Powiadomienia w okienku podglądu, aby stronie ekranu, pokazujące strukturę katalogu, który zostanie utworzony w oparciu o wybrane opcje.  

5. Kliknij przycisk **Utwórz**.  Powinien zostać wyświetlony F# projekt w Eksploratorze rozwiązań.

## <a name="writing-your-code"></a>Pisanie kodu

Zacznijmy napisanie kodu.  Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym kodem:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

W poprzednim przykładzie kodu funkcji `square` zdefiniowano, który przyjmuje dane wejściowe o nazwie `x` i mnożona przez siebie.  Ponieważ F# używa [wnioskowanie o typie](../language-reference/type-inference.md), typ `x` nie muszą być określone.  F# Kompilator rozpoznaje typy, których mnożenie jest prawidłowy i przypisze typu `x` zależnie od `square` jest wywoływana.  Po umieszczeniu wskaźnika myszy nad `square`, powinny pojawić się następujące:

```
val square: x:int -> int
```

Jest to, co jest nazywane podpisu typu funkcji.  Mogą być odczytywane następująco: "Kwadratu jest funkcją, która przyjmuje liczbą całkowitą o nazwie x i tworzy całkowitą".  Należy zauważyć, że kompilator nadaje `square` `int` typu teraz — jest to spowodowane mnożenie nie jest ogólna między *wszystkich* typów, ale raczej jest ogólny w zestawie zamknięte typy.  F# Kompilatora pobrane `int` tej punkt, ale skoryguje sygnatura typu Jeśli wywołasz `square` przy użyciu innego typu danych wejściowych, takich jak `float`.

Inną funkcję, `main`, jest zdefiniowany, który zostanie nadany `EntryPoint` atrybutu, aby poinformować F# powinny zacząć kompilator, że wykonywanie programu.  Jest zgodna z tej samej Konwencji co inne [języków programowania stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazywane do tej funkcji i zostanie zwrócony kod liczby całkowitej (zazwyczaj `0`).

Znajduje się w tej funkcji, które nazywamy `square` funkcji z argumentem `12`.  F# Kompilatora następnie przypisuje typ `square` jako `int -> int` (oznacza to, że funkcja, która przyjmuje `int` i tworzy `int`).  Wywołanie `printfn` jest sformatowany funkcję drukowania, który używa formatu ciągu, podobny do języków programowania w stylu języka C, parametry, które odnoszą się do tych określonych w ciągu formatu, a następnie drukuje wyniki i nowy wiersz.

## <a name="running-your-code"></a>Uruchamianie kodu

Można uruchomić kod i wyświetlić wyniki, klikając **Uruchom** menu najwyższego poziomu i następnie **Rozpocznij bez debugowania**.  To spowoduje Uruchom program bez debugowania i pozwala wyświetlić wyniki.

Powinien zostać wyświetlony wypisywane w oknie konsoli, które program Visual Studio for Mac pojawiające się następujące czynności:

```
12 squared is 144!
```

Gratulacje!  Utworzono pierwszej F# projektu w programie Visual Studio dla komputerów Mac, zapisywane F# funkcji drukowania wyniki wywołania funkcji i uruchom projekt, aby wyświetlać pewnych wyników.

## <a name="using-f-interactive"></a>Za pomocą F# interaktywne

Jedną z najlepszych funkcji wizualizacji F# narzędzi w programie Visual Studio dla komputerów Mac jest F# okna interaktywnego.  Pozwala ona do wysłania kodu do procesu, w którym można wywołać ten kod i interaktywnie wyświetlić wynik.

Aby zacząć z niego korzystać, wyróżnij `square` funkcję zdefiniowaną w kodzie.  Przejdź do menu **Edytuj** menu najwyższego poziomu.  Następnie wybierz pozycję **Wyślij zaznaczenie do F# Interactive**.  To wykonuje kod w F# okna interaktywnego.  Alternatywnie, kliknij zaznaczenie prawym przyciskiem myszy i wybierz polecenie **Wyślij zaznaczenie do F# Interactive**.  Powinien zostać wyświetlony F# okna interaktywnego pojawiają się z następującymi w nim:

```
>

val square : x:int -> int

>
```

Pokazuje to taki sam podpis funkcji dla `square` funkcji, tak aby był wyświetlany po najechaniu za pośrednictwem funkcji.  Ponieważ `square` teraz jest zdefiniowany w F# interakcyjny proces, można wywołać go z różnymi wartościami:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

To wykonuje funkcję, łączy wynik pod nową nazwą `it`i wyświetla typ i wartość `it`.  Należy pamiętać, że musi kończyć się każdy wiersz z `;;`.  Jest to jak F# Interactive wie, po zakończeniu wywołania funkcji.  Można również definiować nowe funkcje w F# interakcyjne:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Powyższe definiuje nową funkcję `isOdd`, która przyjmuje `int` i sprawdza, czy jest nieparzysta!  Możesz wywołać tę funkcję, aby zobaczyć zwróceniem przy użyciu różnych danych wejściowych.  Można wywołać funkcji w ramach wywołania funkcji:

```
> isOdd (square 15);;
val it : bool = true
```

Można również użyć [operatora potoku — przekazywanie](../language-reference/symbol-and-operator-reference/index.md) do potoku wartość w dwie funkcje:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

Operator do przodu potoku i innych zostały omówione w kolejnych samouczkach.

Jest to tylko programistyczne do co można zrobić za pomocą F# interakcyjne.  Aby dowiedzieć się więcej, zapoznaj się z [interaktywne programowanie za pomocą F# ](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Następne kroki

Jeśli jeszcze nie, zapoznaj się z [Przewodnik po przykładzie F# ](../tour.md), które obejmują niektóre z podstawowych funkcji F# języka.  Uzyskasz przegląd możliwości F#oraz podać przykłady wystarczającą ilość kodu, które można skopiować do programu Visual Studio dla komputerów Mac i uruchom.  Dostępne są także kilka wspaniałych zasobów zewnętrznych, można użyć, pokazywane w [ F# przewodnik](../index.md).

## <a name="see-also"></a>Zobacz także

- [Visual F#](../index.md)
- [Przewodnik po F#](../tour.md)
- [F#Dokumentacja języka](../language-reference/index.md)
- [Wnioskowanie o typie](../language-reference/type-inference.md)
- [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)
