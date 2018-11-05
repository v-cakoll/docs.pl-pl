---
title: Rozpoczynanie pracy z usługą F# w programie Visual Studio
description: 'Dowiedz się, jak używać języka F # za pomocą programu Visual Studio.'
ms.date: 07/03/2018
ms.openlocfilehash: 3dac8466501338873aeb308ceac9274a7934a8a9
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43872854"
---
# <a name="get-started-with-f-in-visual-studio"></a>Rozpoczynanie pracy z usługą F# w programie Visual Studio

Język F # i narzędzi Visual F # są obsługiwane w środowisku IDE programu Visual Studio.

Aby rozpocząć, upewnij się, że [programu Visual Studio z F #](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsoli

Jednym z najprostszych projektów w programie Visual Studio jest aplikacji konsoli.  Oto jak to zrobić.  Po otwarciu programu Visual Studio:

1. Na **pliku** menu wskaż **New**, a następnie wybierz **projektu**.

2.  W nowym projekcie okno dialogowe, w obszarze **szablony**, powinien zostać wyświetlony **Visual F #**.  Wybierz tę opcję, aby wyświetlić szablony języka F #.

3. Wybierz opcję **.NET Core w aplikacji Konsolowej** lub **aplikacja Konsolowa**.

3. Wybierz **OK** przycisk, aby utworzyć projekt języka F #!  Powinien zostać wyświetlony projektu języka F # w Eksploratorze rozwiązań.

## <a name="writing-your-code"></a>Pisanie kodu

Zacznijmy napisanie kodu.  Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym kodem:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

W poprzednim przykładzie kodu funkcji `square` zdefiniowano, który przyjmuje dane wejściowe o nazwie `x` i mnożona przez siebie.  Ponieważ F # używa [wnioskowanie o typie](../language-reference/type-inference.md), typ `x` nie muszą być określone.  Kompilator F # rozumie typów, gdzie mnożenie jest nieprawidłowy i spowoduje przypisanie typu `x` zależnie od `square` jest wywoływana.  Po umieszczeniu wskaźnika myszy nad `square`, powinny pojawić się następujące:

```
val square: x:int -> int
```

Jest to, co jest nazywane podpisu typu funkcji.  Może zostać odczytany następująco: "kwadratu jest funkcją, która przyjmuje liczbą całkowitą o nazwie x i tworzy całkowitą".  Należy zauważyć, że kompilator nadaje `square` `int` typu teraz — jest to spowodowane mnożenie nie jest ogólna między *wszystkich* typów, ale raczej jest ogólny w zestawie zamknięte typy.  Kompilator F # pobrane `int` tej punkt, ale skoryguje sygnatura typu Jeśli wywołasz `square` przy użyciu innego typu danych wejściowych, takich jak `float`.

Inną funkcję, `main`, jest zdefiniowany, który zostanie nadany `EntryPoint` powinny zacząć atrybutu, aby poinformować kompilator F # wykonanie tego programu.  Jest zgodna z tej samej Konwencji co inne [języków programowania stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazywane do tej funkcji i zostanie zwrócony kod liczby całkowitej (zazwyczaj `0`).

Znajduje się w tej funkcji, które nazywamy `square` funkcji z argumentem `12`.  Kompilator F # następnie przypisuje typ `square` jako `int -> int` (oznacza to, że funkcja, która przyjmuje `int` i tworzy `int`).  Wywołanie `printfn` jest sformatowany funkcję drukowania, który używa formatu ciągu, podobny do języków programowania w stylu języka C, parametry, które odnoszą się do tych określonych w ciągu formatu, a następnie drukuje wyniki i nowy wiersz.

## <a name="running-your-code"></a>Uruchamianie kodu

Można uruchomić kod i wyświetlić wyniki, naciskając klawisz **Ctrl**+**F5**.  To uruchamia program bez debugowania i pozwala wyświetlić wyniki.  Alternatywnie można wybrać **debugowania** menu najwyższego poziomu elementu w programie Visual Studio i wybierz polecenie **Rozpocznij bez debugowania**.

Powinien zostać wyświetlony wypisywane w oknie konsoli programu Visual Studio pojawiające się następujące czynności:

```
12 squared is 144!
```

Gratulacje!  Utworzeniu pierwszego projektu F # w programie Visual Studio, napisane, że funkcja języka F # drukowany wyników wywołania tej funkcji i uruchom projekt, aby wyświetlać pewnych wyników.

## <a name="next-steps"></a>Następne kroki

Jeśli jeszcze nie, zapoznaj się z [samouczek programu F #](../tour.md), które obejmują niektóre z podstawowych funkcji języka F #.  Spowoduje przedstawienie niektórych funkcji języka F # i udostępnić przykłady kodu wystarczającą, które można skopiować do programu Visual Studio i uruchamiać.  Dostępne są także kilka wspaniałych zasobów zewnętrznych, można użyć, pokazywane w [Podręcznik języka F #](../index.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik po F#](../tour.md)
- [Dokumentacja języka F #](../language-reference/index.md)
- [Wnioskowanie o typie](../language-reference/type-inference.md)
- [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)
