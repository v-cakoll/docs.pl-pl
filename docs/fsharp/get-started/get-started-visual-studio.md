---
title: 'Rozpoczynanie pracy z F # w programie Visual Studio'
description: 'Dowiedz się, jak używać F # za pomocą programu Visual Studio.'
ms.date: 02/13/2017
ms.openlocfilehash: 22fbe8086ec133605e1d9b4b28e524fe2ed8ac28
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728537"
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

## <a name="next-steps"></a>Następne kroki

Jeśli nie jest jeszcze, zapoznaj się [samouczek programu F #](../tour.md), która obejmuje niektóre podstawowe funkcje języka F #.  Zostanie zawiera przegląd niektórych funkcji języka F # i zapewnić wystarczającą przykłady, które można skopiować do programu Visual Studio i uruchomić.  Są także niektóre dużą zasobów zewnętrznych można używać, pokazywane w [przewodnik F #](../index.md).

## <a name="see-also"></a>Zobacz także
 [Visual F#](index.md)  
 [Przewodnik po F#](../tour.md)  
 [Dokumentacja języka F #](../language-reference/index.md)  
 [Wnioskowanie o typie](../language-reference/type-inference.md)  
 [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)  
