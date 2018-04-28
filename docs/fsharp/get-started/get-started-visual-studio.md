---
title: 'Rozpoczynanie pracy z F # w programie Visual Studio'
description: 'Dowiedz się, jak używać F # za pomocą programu Visual Studio.'
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 29e24f755e6d97c4b31c0d01b254bf90cf77bf17
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-in-visual-studio"></a>Rozpoczynanie pracy z F # w programie Visual Studio

F # i narzędzia Visual F # są obsługiwane w programie Visual Studio IDE.  Aby rozpocząć, należy [pobierania programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), jeśli nie jest jeszcze.  W tym artykule wykorzystano program Visual Studio 2017 Community Edition, ale może użyć F # z wersją wybranych przez użytkownika.

## <a name="installing-f"></a>Instalowanie F # #

Jeśli po raz pierwszy jest pobranie Visual Studio, najpierw zainstaluje Instalator programu Visual Studio.  Zainstaluj wszelkie wersje programu Visual Studio 2017 z Instalatora. Jeśli masz już zainstalowany, kliknij przycisk **Modyfikuj**.

Następnie wyświetlona lista obciążeń. Można zainstalować F # za pomocą dowolnej z następujących obciążenia:

|Obciążenie|Akcja|
|--------|------|
| Programowanie wieloplatformowych .NET core | Żadna akcja - F # jest instalowany domyślnie |
| ASP.NET i sieć web development | Żadna akcja - F # jest instalowany domyślnie |
| Programowanie Azure | Żadna akcja - F # jest instalowany domyślnie |
| Programowanie przenośnych z platformą .NET | Żadna akcja - F # jest instalowany domyślnie |
| Aplikacje do analizy i przetwarzania danych | Żadna akcja - F # jest instalowany domyślnie |
| .NET — rozwój pulpitu | Wybierz **obsługi pulpitu języka F #** z prawej |
| Magazynowanie i przetwarzanie danych | Wybierz **obsługi pulpitu języka F #** z prawej |

Następnie kliknij przycisk **Modyfikuj** w prawej dolnej.  Spowoduje to zainstalowanie wszystko, co jest wybrane.  Następnie możesz otworzyć programu Visual Studio 2017 z obsługą języka F #, klikając **uruchamianie**.

## <a name="creating-a-console-application"></a>Tworzenie aplikacji konsoli

Jednym z najprostszych projekty w programie Visual Studio jest aplikacji konsoli.  Oto jak to zrobić.  Po otwarciu programu Visual Studio:

1. Na **pliku** menu wskaż **nowy**, a następnie wybierz pozycję **projektu**.

2.  W nowy projekt okna dialogowego, w obszarze **szablony**, powinny pojawić się **Visual F #**.  Wybierz tę opcję, aby wyświetlić szablony F #.

3. Wybierz opcję **.NET Core aplikacji konsoli** lub **aplikacji konsoli**.

3. Wybierz **OK** przycisk, aby utworzyć projekt F #!  Powinna zostać wyświetlona projektów F # w Eksploratorze rozwiązań.

## <a name="writing-your-code"></a>Pisanie kodu

Rozpocznijmy pisząc kodu.  Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym kodem:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

W poprzednim przykładzie kodu funkcji `square` zdefiniowano, który przyjmuje danych wejściowych o nazwie `x` i mnożona przez samego siebie.  Ponieważ F # używa [wnioskowanie o typie](../language-reference/type-inference.md), typ `x` nie muszą być określone.  Kompilator języka F # rozumie typy, których mnożenia jest prawidłowy i przypisze typu na `x` zależy od `square` jest wywoływana.  Jeśli w ustawieniu kursora `square`, należy znaleźć w następujących tematach:

```
val square: x:int -> int
```

Jest to określane jako podpis typu funkcji.  Mogą być odczytywane następująco: "kwadratowa jest funkcją, która przyjmuje liczbą całkowitą o nazwie x i tworzy całkowitą".  Należy pamiętać, że kompilator nadać `square` `int` typu teraz — jest to ponieważ mnożenie nie jest rodzajowa między *wszystkie* typów, ale raczej jest rodzajowy zamkniętego zestawu typów.  Kompilator języka F # pobrane `int` dla tego punktu, ale dostosuje podpis typu połączeń `square` z innym typem wejściowych, takich jak `float`.

Innej funkcji, `main`, jest zdefiniowany, który zostanie nadany `EntryPoint` powinny zacząć atrybutu, sprawdzić kompilator języka F #, wykonanie tego programu.  Wynika z tej samej Konwencji, jak inne [języków programowania w stylu języka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą zostać przekazane do tej funkcji i zostanie zwrócony kod liczba całkowita (zazwyczaj `0`).

W tej funkcji, które nazywamy `square` funkcji z argumentem `12`.  Kompilator języka F # następnie przypisuje typ `square` jako `int -> int` (to znaczy funkcję, która przyjmuje `int` i tworzy `int`).  Wywołanie `printfn` jest sformatowany funkcję drukowania, który używa formatu ciągu, podobnie jak języków programowania w stylu języka C, parametry, które odpowiadają na określone w ciągu formatu, a następnie drukuje wyniki i znakiem nowego wiersza.

## <a name="running-your-code"></a>Wykonywanie kodu użytkownika

Można uruchomić kod i wyświetlić wyniki naciskając **ctrl-f5**.  To spowoduje uruchomienie programu bez debugowania i służy do wyświetlenia wyników.  Alternatywnie można wybrać **debugowania** menu najwyższego poziomu elementu w programie Visual Studio i wybierz polecenie **uruchomić bez debugowania**.

Powinien zostać wyświetlony poniższy wypisywane w oknie konsoli, które tam pojawi Visual Studio:

```
12 squared is 144!
```

Gratulacje!  Utworzeniu pierwszego projektu F # w programie Visual Studio, zapisywać funkcja F # drukowane wyników wywołania tej funkcji i uruchom projekt, aby wyświetlać pewnych wyników.

## <a name="using-f-interactive"></a>Przy użyciu interakcyjne F #

Jednym z najlepszych funkcji programu Visual F # narzędzi w programie Visual Studio jest okno interaktywne F #.  Umożliwia ona wysłania kodu do procesu, gdy wywołanie kodu i interakcyjnie zobaczyć wynik.

Aby rozpocząć używanie go, zaznacz `square` funkcji zdefiniowanej w kodzie.  Następnie przytrzymać **Alt** i naciśnij **Enter**.  Wykonuje kod okno interaktywne F #.  Powinny pojawić się F # Interactive okna są wyświetlane następujące w niej:

```
>

val square : x:int -> int

>
```

Ta operacja wyświetla tę samą sygnaturę funkcji dla `square` funkcji, który został wcześniej wyświetlony po aktywowany przez funkcję.  Ponieważ `square` jest teraz zdefiniowana w proces narzędzia F # Interactive, można wywołać ją z różnymi wartościami:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

To wykonuje funkcję, wiąże wynik na nową nazwę `it`i wyświetla typ i wartość `it`.  Należy pamiętać, że należy zakończyć każdego wiersza `;;`.  Jest to, jak F # Interactive wie, po zakończeniu wywołania funkcji.  Istnieje także możliwość zdefiniowania nowych funkcji w F # Interactive:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Powyższy kod definiuje nową funkcję, `isOdd`, która przyjmuje `int` i sprawdza, czy jest nieparzysta! Możesz wywołać tę funkcję, aby sprawdzić, jakie zwraca z różnych danych wejściowych.  Można wywołać funkcji w ramach wywołania funkcji:

```
> isOdd (square 15);;
val it : bool = true
```

Można również użyć [operatora potoku następny](../language-reference/symbol-and-operator-reference/index.md) do potoku wartość do dwie funkcje:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

Operator do przodu potoku i inne, znajdują się w kolejnych samouczkach.

Jest to tylko glimpse do czego z F # Interactive. Aby dowiedzieć się więcej, zapoznaj się [interakcyjne programowania w języku F #](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Następne kroki

Jeśli nie jest jeszcze, zapoznaj się [samouczek programu F #](../tour.md), która obejmuje niektóre podstawowe funkcje języka F #.  Zostanie zawiera przegląd niektórych funkcji języka F # i zapewnić wystarczającą przykłady, które można skopiować do programu Visual Studio i uruchomić.  Są także niektóre dużą zasobów zewnętrznych można używać, pokazywane w [przewodnik F #](../index.md).

## <a name="see-also"></a>Zobacz także
 [Visual F#](index.md)  
 [Przewodnik po F#](../tour.md)  
 [Dokumentacja języka F #](../language-reference/index.md)  
 [Wnioskowanie o typie](../language-reference/type-inference.md)  
 [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)  
