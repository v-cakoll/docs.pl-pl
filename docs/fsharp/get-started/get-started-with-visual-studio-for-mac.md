---
title: Rozpoczynanie pracy F# z usługą w Visual Studio dla komputerów Mac
description: Dowiedz się, F# jak korzystać z programu z Visual Studio dla komputerów Mac.
ms.date: 07/03/2018
ms.openlocfilehash: cd45ab9c59cef76e4bf85a93f39d8e2ee063d200
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552368"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Rozpoczynanie pracy F# z usługą w Visual Studio dla komputerów Mac

F#narzędzia wizualne F# są obsługiwane w Visual Studio dla komputerów Mac IDE. Upewnij się, że [zainstalowano Visual Studio dla komputerów Mac](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsolowej

Jednym z najpopularniejszych projektów w Visual Studio dla komputerów Mac jest Aplikacja konsolowa.  Oto jak to zrobić.  Gdy Visual Studio dla komputerów Mac jest otwarty:

1. W menu **plik** wskaż polecenie **nowe rozwiązanie**.

2. W oknie dialogowym Nowy projekt istnieją 2 różne szablony dla aplikacji konsolowej.  Istnieje jedna pod innymi > .NET, która jest przeznaczona dla .NET Framework.  Drugi szablon jest objęty aplikacją .NET Core->, która jest przeznaczona dla platformy .NET Core.  Każdy szablon powinien zadziałał na potrzeby tego artykułu.

3. W obszarze aplikacja konsoli, C# w F# razie potrzeby, przejdź do programu.  Wybierz przycisk **dalej** , aby przejść do przodu!  

4. Nadaj projektowi nazwę, a następnie wybierz odpowiednie opcje dla aplikacji.  Zwróć uwagę, że okienko podglądu z boku ekranu spowoduje wyświetlenie struktury katalogów, która zostanie utworzona na podstawie wybranych opcji.  

5. Kliknij przycisk **Utwórz**.  Powinien być teraz widoczny F# projekt w Eksplorator rozwiązań.

## <a name="writing-your-code"></a>Pisanie kodu

Zacznijmy od zapisania najpierw kodu.  Upewnij się, że plik `Program.fs` jest otwarty, a następnie zastąp jego zawartość następującym:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

W poprzednim przykładzie kodu funkcja `square` została zdefiniowana, która pobiera dane wejściowe o nazwie `x` i mnoży ją przez siebie.  Ponieważ F# używa [wnioskowania o typie](../language-reference/type-inference.md), nie trzeba określać typu `x`.  F# Kompilator rozumie typy, w których mnożenie jest prawidłowe, i przypisuje typ do `x` w zależności od tego, jak `square` jest wywoływana.  Po umieszczeniu wskaźnika myszy na `square`należy zobaczyć następujące elementy:

```console
val square: x:int -> int
```

Jest to element znany jako podpis typu funkcji.  Można go odczytać w następujący sposób: "kwadrat jest funkcją, która przyjmuje liczbę całkowitą o nazwie x i tworzy liczbę całkowitą".  Należy zauważyć, że kompilator udzielił `square` typu `int`. jest to spowodowane tym, że mnożenie nie jest ogólne dla *wszystkich* typów, ale raczej jest ogólny w przypadku zamkniętego zestawu typów.  F# Kompilator `int` wybrany w tym momencie, ale zmieni sygnaturę typu w przypadku wywołania `square` z innym typem danych wejściowych, takim jak `float`.

Inna funkcja, `main`, jest zdefiniowana z atrybutem `EntryPoint`, aby poinformować F# kompilator, że wykonanie programu powinno się uruchomić w tym miejscu.  Ta sama Konwencja jest zgodna z innymi [językami programowania w stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazane do tej funkcji i zwracany jest kod liczby całkowitej (zwykle `0`).

Jest to funkcja, która wywołuje funkcję `square` z argumentem `12`.  Następnie F# kompilator przypisuje typ `square`, które mają być `int -> int` (czyli funkcję, która pobiera `int` i tworzy `int`).  Wywołanie `printfn` jest sformatowaną funkcją drukowania, która używa ciągu formatu, podobnego do języków programowania w stylu C, parametrów, które odpowiadają określonym w ciągu formatu, a następnie drukuje wynik i nowy wiersz.

## <a name="running-your-code"></a>Uruchamianie kodu

Możesz uruchomić kod i zobaczyć wyniki, klikając polecenie **Uruchom** w menu najwyższego poziomu, a następnie **uruchamiając bez debugowania**.  Spowoduje to uruchomienie programu bez debugowania i umożliwi wyświetlenie wyników.

W oknie konsoli powinna zostać wyświetlona następująca wartość, która Visual Studio dla komputerów Mac zdjęte:

```console
12 squared is 144!
```

Nabycia!  Został utworzony pierwszy F# projekt w Visual Studio dla komputerów Mac, zapisanie F# funkcji Wydrukowano wyniki wywołania tej funkcji i Uruchom projekt, aby zobaczyć niektóre wyniki.

## <a name="using-f-interactive"></a>Używanie F# interaktywne

Jedną z najlepszych funkcji narzędzi wizualnych F# w Visual Studio dla komputerów Mac jest okno F# interaktywne.  Umożliwia wysyłanie kodu do procesu, w którym można wywołać ten kod i interaktywnie zobaczyć wynik.

Aby rozpocząć korzystanie z niego, zaznacz funkcję `square` zdefiniowaną w kodzie.  Następnie kliknij pozycję **Edytuj** w menu najwyższego poziomu.  Następnie wybierz pozycję **Wyślij zaznaczenie F# do opcji interaktywny**.  Spowoduje to wykonanie kodu w oknie F# interaktywnym.  Alternatywnie możesz kliknąć prawym przyciskiem myszy zaznaczenie i wybrać polecenie **Wyślij zaznaczenie do F# opcji interaktywny**.  Powinno zostać wyświetlone okno F# interaktywne z następującym w nim:

```console
>

val square : x:int -> int

>
```

Jest to ta sama sygnatura funkcji dla funkcji `square`, która została wcześniej umieszczona po umieszczeniu wskaźnika myszy nad funkcją.  Ponieważ `square` jest teraz zdefiniowany w procesie F# interaktywnym, można wywołać go z różnymi wartościami:

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Wykonuje funkcję, wiąże wynik z nową nazwą `it`i wyświetla typ i wartość `it`.  Należy pamiętać, że każdy wiersz należy zakończyć `;;`.  Jest to sposób F# interaktywny wie, gdy wywołanie funkcji zostało zakończone.  Możesz również definiować nowe funkcje w F# trybie interaktywnym:

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Powyższe definiuje nową funkcję, `isOdd`, która przyjmuje `int` i sprawdza, czy jest nieparzysta.  Możesz wywołać tę funkcję, aby zobaczyć, co zwraca z innymi danymi wejściowymi.  Można wywoływać funkcje w ramach wywołań funkcji:

```console
> isOdd (square 15);;
val it : bool = true
```

Można również użyć [operatora przekazywania potoków](../language-reference/symbol-and-operator-reference/index.md) , aby przekierować wartość do dwóch funkcji:

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

Operator przekazujący przekazanie dalej i inne są omówione w kolejnych samouczkach.

To tylko możliwość wypróbowania innowacyjnego, co możesz zrobić z F# interaktywną.  Aby dowiedzieć się więcej, zapoznaj się [z programowaniem interaktywnym przy użyciu programu F# ](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Następne kroki

Jeśli jeszcze tego nie zrobiono, zapoznaj się [ F#z przewodnikiem ](../tour.md), który obejmuje niektóre podstawowe funkcje F# języka.  Udostępnimy przegląd niektórych możliwości programu F#i udostępniamy dużo przykładów kodu, które można skopiować do Visual Studio dla komputerów Mac i uruchamiać.  Istnieją również pewne doskonałe zasoby zewnętrzne, których można użyć w [ F# przewodniku](../index.yml).

## <a name="see-also"></a>Zobacz także

- [F#prowadzą](../index.yml)
- [Przewodnik po F#](../tour.md)
- [F#Dokumentacja języka](../language-reference/index.md)
- [Wnioskowanie o typie](../language-reference/type-inference.md)
- [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)
