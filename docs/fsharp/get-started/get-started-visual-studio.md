---
title: Wprowadzenie F# do programu Visual Studio
description: Dowiedz się, F# jak korzystać z programu Visual Studio.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337348"
---
# <a name="get-started-with-f-in-visual-studio"></a>Wprowadzenie F# do programu Visual Studio

F#narzędzia wizualne F# są obsługiwane w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.

Aby rozpocząć, upewnij się, że masz [zainstalowany program Visual F# Studio z obsługą techniczną](install-fsharp.md#install-f-with-visual-studio).

## <a name="create-a-console-application"></a>Tworzenie aplikacji konsolowej

Jednym z najpopularniejszych projektów w programie Visual Studio jest Aplikacja konsolowa. Oto jak utworzyć:

1. Open Visual Studio 2019.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wybierz **F#** z listy język.

4. Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

5. Na stronie **Konfiguruj nowy projekt** wprowadź nazwę w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   Program Visual Studio tworzy nowy F# projekt. Można go wyświetlić w oknie Eksplorator rozwiązań.

## <a name="write-the-code"></a>Tworzenie kodu

Zacznijmy od pisania kodu. Upewnij się, że plik `Program.fs` jest otwarty, a następnie zastąp jego zawartość następującym:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Poprzedni przykład kodu definiuje funkcję o nazwie `square`, która przyjmuje dane wejściowe o nazwie `x` i mnoży ją przez siebie. Ponieważ F# używa [wnioskowania o typie](../language-reference/type-inference.md), nie trzeba określać typu `x`. F# Kompilator rozumie typy, w których mnożenie jest prawidłowe, i przypisuje typ do `x` w zależności od tego, jak `square` jest wywoływana. Po umieszczeniu wskaźnika myszy na `square`należy zobaczyć następujące elementy:

```fsharp
val square: x:int -> int
```

Jest to element znany jako podpis typu funkcji. Można go odczytać w następujący sposób: "kwadrat jest funkcją, która przyjmuje liczbę całkowitą o nazwie x i tworzy liczbę całkowitą". Kompilator nadał teraz `square` typ `int`; wynika to z faktu, że mnożenie nie jest ogólne dla *wszystkich* typów, ale raczej do zamkniętego zestawu typów. F# Kompilator dostosowuje podpis typu w przypadku wywołania `square` z innym typem danych wejściowych, takim jak `float`.

Inna funkcja, `main`, jest zdefiniowana z atrybutem `EntryPoint`. Ten atrybut informuje kompilator F# , że wykonanie programu powinno zacząć się w tym miejscu. Ta sama Konwencja jest zgodna z innymi [językami programowania w stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazane do tej funkcji i zwracany jest kod liczby całkowitej (zwykle `0`).

Znajduje się w funkcji punktu wejścia, `main`, że wywoływana jest funkcja `square` z argumentem `12`. Następnie F# kompilator przypisuje typ `square` do `int -> int` (to jest funkcja, która pobiera `int` i tworzy `int`). Wywołanie `printfn` jest sformatowaną funkcją drukowania, która używa ciągu formatu i drukuje wynik (i nowy wiersz). Ciąg formatu, podobny do języków programowania w stylu C, ma parametry (`%d`) odpowiadające argumentom, które są do niego przekazane, w tym przypadku `12` i `(square 12)`.

## <a name="run-the-code"></a>Uruchamianie kodu

Możesz uruchomić kod i zobaczyć wyniki, naciskając klawisz **Ctrl**+**F5**. Alternatywnie można wybrać **debugowanie** > **rozpocząć bez debugowania** z paska menu najwyższego poziomu. Spowoduje to uruchomienie programu bez debugowania.

Następujące dane wyjściowe są drukowane do okna konsoli, który został otwarty przez program Visual Studio:

```console
12 squared is: 144!
```

Gratulacje! Utworzono pierwszy F# projekt w programie Visual Studio, zapisał F# funkcję, która oblicza i drukuje wartość i uruchamia projekt, aby zobaczyć wyniki.

## <a name="next-steps"></a>Następne kroki

Jeśli jeszcze tego nie zrobiono, zapoznaj się [ F#z przewodnikiem ](../tour.md), który obejmuje niektóre podstawowe funkcje F# języka. Zawiera przegląd niektórych możliwości F# i większość przykładów kodu, które można skopiować do programu Visual Studio i uruchomić.

> [!div class="nextstepaction"]
> [Przewodnik po F#](../tour.md)

## <a name="see-also"></a>Zobacz także

- [F#Dokumentacja języka](../language-reference/index.md)
- [Wnioskowanie o typie](../language-reference/type-inference.md)
- [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)
