---
title: Wprowadzenie F# do programu Visual Studio
description: Dowiedz się, F# jak korzystać z programu Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552820"
---
# <a name="get-started-with-f-in-visual-studio"></a>Wprowadzenie F# do programu Visual Studio

F#narzędzia wizualne F# są obsługiwane w środowisku IDE programu Visual Studio.

Aby rozpocząć, upewnij się, że masz [zainstalowany program Visual F#Studio z programem ](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsolowej

Jednym z najpopularniejszych projektów w programie Visual Studio jest Aplikacja konsolowa.  Oto jak to zrobić.  Po otwarciu programu Visual Studio:

1. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz **projekt**.

2. W oknie dialogowym Nowy projekt w obszarze **Szablony**powinna zostać wyświetlona wartość **Visual F#** .  Wybierz tę opcję, aby F# wyświetlić szablony.

3. Wybierz **aplikację konsolową .NET Core** lub **aplikację konsolową**.

4. Wybierz przycisk **OK** , aby utworzyć F# projekt.  Powinien być teraz widoczny F# projekt w Eksplorator rozwiązań.

## <a name="writing-your-code"></a>Pisanie kodu

Zacznijmy od zapisania najpierw kodu.  Upewnij się, że plik `Program.fs` jest otwarty, a następnie zastąp jego zawartość następującym:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

W poprzednim przykładzie kodu funkcja `square` została zdefiniowana, która pobiera dane wejściowe o nazwie `x` i mnoży ją przez siebie.  Ponieważ F# używa [wnioskowania o typie](../language-reference/type-inference.md), nie trzeba określać typu `x`.  F# Kompilator rozumie typy, w których mnożenie jest prawidłowe, i przypisuje typ do `x` w zależności od tego, jak `square` jest wywoływana.  Po umieszczeniu wskaźnika myszy na `square`należy zobaczyć następujące elementy:

```fsharp
val square: x:int -> int
```

Jest to element znany jako podpis typu funkcji.  Można go odczytać w następujący sposób: "kwadrat jest funkcją, która przyjmuje liczbę całkowitą o nazwie x i tworzy liczbę całkowitą".  Należy zauważyć, że kompilator udzielił `square` typu `int`. jest to spowodowane tym, że mnożenie nie jest ogólne dla *wszystkich* typów, ale raczej jest ogólny w przypadku zamkniętego zestawu typów.  F# Kompilator `int` wybrany w tym momencie, ale zmieni sygnaturę typu w przypadku wywołania `square` z innym typem danych wejściowych, takim jak `float`.

Inna funkcja, `main`, jest zdefiniowana z atrybutem `EntryPoint`, aby poinformować F# kompilator, że wykonanie programu powinno się uruchomić w tym miejscu.  Ta sama Konwencja jest zgodna z innymi [językami programowania w stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazane do tej funkcji i zwracany jest kod liczby całkowitej (zwykle `0`).

Jest to funkcja, która wywołuje funkcję `square` z argumentem `12`.  Następnie F# kompilator przypisuje typ `square`, które mają być `int -> int` (czyli funkcję, która pobiera `int` i tworzy `int`).  Wywołanie `printfn` jest sformatowaną funkcją drukowania, która używa ciągu formatu, podobnego do języków programowania w stylu C, parametrów, które odpowiadają określonym w ciągu formatu, a następnie drukuje wynik i nowy wiersz.

## <a name="running-your-code"></a>Uruchamianie kodu

Możesz uruchomić kod i zobaczyć wyniki, naciskając klawisz **Ctrl**+**F5**.  Spowoduje to uruchomienie programu bez debugowania i pozwala zobaczyć wyniki.  Alternatywnie możesz wybrać element menu **najwyższego poziomu w programie** Visual Studio i wybrać polecenie **Uruchom bez debugowania**.

W oknie konsoli programu Visual Studio należy teraz zobaczyć następujące elementy:

```console
12 squared is 144!
```

Nabycia!  Został utworzony pierwszy F# projekt w programie Visual Studio, a F# funkcja zapisała wyniki wywołania tej funkcji i uruchomi projekt, aby zobaczyć niektóre wyniki.

## <a name="next-steps"></a>Następne kroki

Jeśli jeszcze tego nie zrobiono, zapoznaj się [ F#z przewodnikiem ](../tour.md), który obejmuje niektóre podstawowe funkcje F# języka.  Udostępnimy przegląd niektórych możliwości programu F#i udostępniamy dużo przykładów kodu, które można skopiować do programu Visual Studio i uruchomić.  Więcej informacji na temat F# dokumentacji można znaleźć na [ F# stronie głównej witryny docs](../index.yml).

## <a name="see-also"></a>Zobacz także

- [Przewodnik po F#](../tour.md)
- [F#Dokumentacja języka](../language-reference/index.md)
- [Wnioskowanie o typie](../language-reference/type-inference.md)
- [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)
