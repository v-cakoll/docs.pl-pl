---
title: Rozpoczynanie pracy z usługą F# w programie Visual Studio
description: Dowiedz się, jak używać F# z programem Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 020e5d32b3aa5d5a2195c19d70d8fe684fbd56ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331913"
---
# <a name="get-started-with-f-in-visual-studio"></a>Rozpoczynanie pracy z usługą F# w programie Visual Studio

F#a wizualizacja F# narzędzi są obsługiwane w środowisku IDE programu Visual Studio.

Aby rozpocząć, upewnij się, że [zainstalowany program Visual Studio za pomocą F# ](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsoli

Jednym z najprostszych projektów w programie Visual Studio jest aplikacji konsoli.  Oto jak to zrobić.  Po otwarciu programu Visual Studio:

1. Na **pliku** menu wskaż **New**, a następnie wybierz **projektu**.

2. W nowym projekcie okno dialogowe, w obszarze **szablony**, powinien zostać wyświetlony **Visual F#** .  Wybierz, aby wyświetlić F# szablonów.

3. Wybierz opcję **.NET Core w aplikacji Konsolowej** lub **aplikacja Konsolowa**.

3. Wybierz **OK** przycisk, aby utworzyć F# projektu!  Powinien zostać wyświetlony F# projekt w Eksploratorze rozwiązań.

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

Można uruchomić kod i wyświetlić wyniki, naciskając klawisz **Ctrl**+**F5**.  To uruchamia program bez debugowania i pozwala wyświetlić wyniki.  Alternatywnie można wybrać **debugowania** menu najwyższego poziomu elementu w programie Visual Studio i wybierz polecenie **Rozpocznij bez debugowania**.

Powinien zostać wyświetlony wypisywane w oknie konsoli programu Visual Studio pojawiające się następujące czynności:

```
12 squared is 144!
```

Gratulacje!  Utworzono pierwszej F# projektu w programie Visual Studio zapisywane F# funkcji drukowania wyniki wywołania funkcji i uruchom projekt, aby wyświetlać pewnych wyników.

## <a name="next-steps"></a>Następne kroki

Jeśli jeszcze nie, zapoznaj się z [Przewodnik po przykładzie F# ](../tour.md), które obejmują niektóre z podstawowych funkcji F# języka.  Uzyskasz przegląd możliwości F#oraz podać przykłady wystarczającą ilość kodu, które można skopiować do programu Visual Studio i uruchamiać.  Dostępne są także kilka wspaniałych zasobów zewnętrznych, można użyć, pokazywane w [ F# przewodnik](../index.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik po F#](../tour.md)
- [F#Dokumentacja języka](../language-reference/index.md)
- [Wnioskowanie o typie](../language-reference/type-inference.md)
- [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)
