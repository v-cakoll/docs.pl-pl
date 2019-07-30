---
title: Wprowadzenie F# do programu Visual Studio
description: Dowiedz się, F# jak korzystać z programu Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 24c9a81cfa61dc904db9b2213224677696d7eb9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629767"
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

Zacznijmy od zapisania najpierw kodu.  Upewnij się, że `Program.fs` plik jest otwarty, a następnie zastąp jego zawartość następującym:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

W poprzednim przykładzie kodu zdefiniowano funkcję `square` , która przyjmuje `x` dane wejściowe i mnoży ją przez siebie.  Ponieważ F# używa [wnioskowania o typie](../language-reference/type-inference.md), `x` nie trzeba określać typu.  F# Kompilator rozumie typy, w których mnożenie jest prawidłowe i przypisuje typ `x` na podstawie sposobu wywoływania metody `square` .  Po umieszczeniu wskaźnika myszy `square`na stronie powinny zostać wyświetlone następujące elementy:

```fsharp
val square: x:int -> int
```

Jest to element znany jako podpis typu funkcji.  Można go odczytać w następujący sposób: "Square to funkcja, która przyjmuje liczbę całkowitą o nazwie x i tworzy liczbę całkowitą".  Należy zauważyć, że kompilator `square` nadał `int` teraz typ. jest to spowodowane tym, że mnożenie nie jest ogólne dla *wszystkich* typów, ale raczej jest ogólny w przypadku zamkniętego zestawu typów.  F# Kompilator jest wybierany `int` w tym momencie, ale dopasowuje podpis typu w przypadku wywołania `square` z `float`innym typem danych wejściowych, na przykład.

Inna funkcja `main`,,, jest zdefiniowana `EntryPoint` z atrybutem, aby poinformować F# kompilator, że wykonanie programu powinno się uruchomić w tym miejscu.  Ta sama Konwencja jest zgodna z innymi [językami programowania w stylu C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), gdzie argumenty wiersza polecenia mogą być przekazane do tej funkcji i zwracany jest kod liczby całkowitej (zazwyczaj `0`).

Jest to funkcja, która wywołuje `square` funkcję z `12`argumentem.  Następnie F# `square` kompilator przypisuje typ do `int -> int` (czyli `int`funkcję, która przyjmuje `int` i tworzy).  Wywołanie `printfn` jest sformatowaną funkcją drukowania, która używa ciągu formatu, podobnego do języków programowania w stylu C, parametrów, które odpowiadają określonym w ciągu formatu, a następnie drukuje wynik i nowy wiersz.

## <a name="running-your-code"></a>Uruchamianie kodu

Możesz uruchomić kod i zobaczyć wyniki, naciskając klawisz **Ctrl**+**F5**.  Spowoduje to uruchomienie programu bez debugowania i pozwala zobaczyć wyniki.  Alternatywnie możesz wybrać element menu **najwyższego** poziomu w programie Visual Studio i wybrać polecenie **Uruchom bez debugowania**.

W oknie konsoli programu Visual Studio należy teraz zobaczyć następujące elementy:

```
12 squared is 144!
```

Gratulacje!  Został utworzony pierwszy F# projekt w programie Visual Studio, a F# funkcja zapisała wyniki wywołania tej funkcji i uruchomi projekt, aby zobaczyć niektóre wyniki.

## <a name="next-steps"></a>Następne kroki

Jeśli jeszcze tego nie zrobiono, zapoznaj się [z F#przewodnikiem ](../tour.md), który obejmuje niektóre podstawowe funkcje F# języka.  Udostępnimy przegląd niektórych możliwości programu F#i udostępniamy dużo przykładów kodu, które można skopiować do programu Visual Studio i uruchomić.  Istnieją również pewne doskonałe zasoby zewnętrzne, których można użyć w [ F# przewodniku](../index.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik po F#](../tour.md)
- [F#Dokumentacja języka](../language-reference/index.md)
- [Wnioskowanie o typie](../language-reference/type-inference.md)
- [Odwołanie do symbolu i operatora](../language-reference/symbol-and-operator-reference/index.md)
