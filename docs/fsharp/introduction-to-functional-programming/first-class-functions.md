---
title: Funkcje pierwszoklasowe
description: Zapoznaj się z funkcjami pierwszej klasy i sposobem, w jaki są one ważne F#dla programowania funkcjonalnego w programie.
ms.date: 10/29/2018
ms.openlocfilehash: 4681d32abd59cc4aade6f4cb2d062e7888bcfbbc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629717"
---
# <a name="first-class-functions"></a>Funkcje pierwszoklasowe

Definiowanie cech charakterystycznych dla funkcjonalnego języka programowania jest podniesieniem funkcji do stanu pierwszej klasy. Powinno być możliwe wykonywanie z funkcją, którą można wykonać przy użyciu wartości innych typów wbudowanych i można to zrobić przy użyciu porównywalnego stopnia nakładu pracy.

Typowe miary stanu pierwszej klasy są następujące:

- Czy można powiązać funkcje z identyfikatorami? Oznacza to, czy można nadać im nazwy?

- Czy można przechowywać funkcje w strukturach danych, na przykład na liście?

- Czy można przekazać funkcję jako argument w wywołaniu funkcji?

- Czy można zwrócić funkcję z wywołania funkcji?

Ostatnie dwie miary definiują, co są znane jako *operacje wyższego rzędu* lub *funkcje wyższego rzędu*. Funkcje wyższego rzędu akceptują funkcje jako argumenty i zwracają funkcje jako wartość wywołania funkcji. Te operacje obsługują takie sztandarowych programowanie funkcjonalne jako funkcje mapowania i skład funkcji.

## <a name="give-the-value-a-name"></a>Nadaj wartości nazwę

Jeśli funkcja jest wartością pierwszej klasy, należy być w stanie jej nazwać, tak jak nazwy całkowite, ciągi i inne typy wbudowane. Jest to określane w temacie programowanie funkcjonalnej literatury jako powiązanie identyfikatora z wartością. F#`let <identifier> = <value>` [ używa`let` powiązań](../language-reference/functions/let-bindings.md) do powiązania nazw z wartościami:. Poniższy kod przedstawia dwa przykłady.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

Funkcję można nazwać równie łatwo. W poniższym przykładzie zdefiniowano funkcję o `squareIt` nazwie przez powiązanie identyfikatora `squareIt` do [wyrażenia](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`lambda. Funkcja `squareIt` ma jeden parametr, `n`i zwraca kwadrat tego parametru.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

F#zapewnia następującą bardziej zwięzłą składnię, aby osiągnąć ten sam wynik przy mniejszej liczbie znaków.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

Poniższe przykłady używają pierwszego stylu, `let <function-name> = <lambda-expression>`aby wyróżnić podobieństwa między deklaracją funkcji a deklaracją innych typów wartości. Jednak wszystkie nazwane funkcje mogą być również zapisywane ze zwięzłą składnią. Niektóre przykłady są zapisywane w obu kierunkach.

## <a name="store-the-value-in-a-data-structure"></a>Przechowywanie wartości w strukturze danych

Wartość pierwszej klasy może być przechowywana w strukturze danych. Poniższy kod przedstawia przykłady, które przechowują wartości z list i krotek.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

Aby sprawdzić, czy nazwa funkcji przechowywana w spójnej kolekcji wykonuje funkcję, w poniższym przykładzie są używane `fst` operatory i `snd` do wyodrębnienia pierwszego i drugiego elementu z krotki `funAndArgTuple`. Pierwszy element w krotki to `squareIt` , a drugi element to. `num` Identyfikator `num` jest powiązany w poprzednim przykładzie z liczbą całkowitą 10, prawidłowym argumentem `squareIt` dla funkcji. Drugie wyrażenie stosuje pierwszy element w spójnej kolekcji do drugiego elementu w spójnej kolekcji: `squareIt num`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

Podobnie, podobnie jak identyfikatory `num` i 10 Integer mogą być używane zamiennie, więc można je identyfikatorować `squareIt` i wyrażeniu `fun n -> n * n`lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>Przekaż wartość jako argument

Jeśli wartość ma stan pierwszej klasy w języku, można przekazać ją jako argument do funkcji. Na przykład często przekazywać liczby całkowite i ciągi jako argumenty. Poniższy kod przedstawia liczby całkowite i ciągi przekazane jako argumenty w F#.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

Jeśli funkcje mają stan pierwszej klasy, musi być możliwe przekazanie ich jako argumentów w taki sam sposób. Należy pamiętać, że jest to pierwsza cecha funkcji wyższego rzędu.

W poniższym przykładzie funkcja `applyIt` ma dwa `op` parametry i `arg`. W przypadku wysyłania w funkcji, która ma jeden parametr dla `op` i odpowiedni argument dla `arg`funkcji, funkcja zwraca wynik zastosowania `op` do `arg`. W poniższym przykładzie zarówno argument funkcji, jak i argument integer są wysyłane w taki sam sposób, przy użyciu ich nazw.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

Możliwość wysyłania funkcji jako argumentu do innej funkcji jest zależna od powszechnych streszczeń w języku programowania funkcjonalnego, takich jak operacje map lub filtrów. Operacja mapy, na przykład, to funkcja wyższego rzędu, która przechwytuje obliczenia współdzielone przez funkcje, które przekładają się na listę, zrób coś do każdego elementu, a następnie Zwróć listę wyników. Możesz chcieć zwiększyć każdy element na liście liczb całkowitych lub do kwadratu każdego elementu albo zmienić każdy element na liście ciągów na wielkie litery. Część obliczeń podatna na błędy to proces cykliczny, który przechodzi przez listę i tworzy listę wyników do zwrócenia. Ta część jest przechwytywana w funkcji mapowania. Wszystko, co musisz napisać dla określonej aplikacji, to funkcja, która ma zostać zastosowana do każdego elementu listy pojedynczo (Dodawanie, podniesienie, zmiana wielkości liter). Ta funkcja jest wysyłana jako argument do funkcji mapowania, podobnie jak `squareIt` `applyIt` w poprzednim przykładzie.

F#oferuje metody mapy dla większości typów kolekcji, w tym [listy](../language-reference/lists.md), [tablice](../language-reference/arrays.md)i [sekwencje](../language-reference/sequences.md). W poniższych przykładach użyto list. Składnia to `List.map <the function> <the list>`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

Aby uzyskać więcej informacji, zobacz [listy](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Zwraca wartość z wywołania funkcji

Na koniec, jeśli funkcja ma stan pierwszej klasy w języku, musi być w stanie zwrócić ją jako wartość wywołania funkcji, tak jak w przypadku innych typów, takich jak liczby całkowite i ciągi.

Następujące wywołania funkcji zwracają liczby całkowite i wyświetlają je.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

Poniższe wywołanie funkcji zwraca ciąg.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

Następujące wywołanie funkcji, zadeklarowane wewnętrznie, zwraca wartość logiczną. Wyświetlana wartość to `True`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

Możliwość zwrócenia funkcji jako wartość wywołania funkcji jest drugą cechą funkcji wyższej kolejności. W poniższym przykładzie `checkFor` zdefiniowano jako funkcję, która przyjmuje jeden argument, `item`i zwraca nową funkcję jako wartość. Zwracana funkcja przyjmuje listę jako argument, `lst`i `item` wyszukuje w `lst`. Jeśli `item` jest obecny, funkcja zwraca `true`. Jeśli `item` nie jest obecny, funkcja zwraca `false`. Jak w poprzedniej sekcji, poniższy kod używa udostępnionej funkcji list, [list. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), aby przeszukać listę.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

Poniższy kod używa `checkFor` do tworzenia nowej funkcji, która przyjmuje jeden argument, listę i wyszukuje 7 na liście.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

Poniższy przykład używa stanu pierwszej klasy funkcji w F# , aby zadeklarować funkcję, `compose`która zwraca skład dwóch argumentów funkcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> W przypadku jeszcze krótszej wersji Zobacz sekcję "funkcje rozwinięte".

Poniższy kod wysyła dwie funkcje jako argumenty do `compose`, z których oba przyjmują jeden argument tego samego typu. Wartość zwracana jest nową funkcją, która jest składową dwóch argumentów funkcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> F#zawiera dwa operatory `<<` i `>>`, które tworzą funkcje. Na przykład `let squareAndDouble2 = doubleIt << squareIt` jest `let squareAndDouble = compose doubleIt squareIt` odpowiednikiem w poprzednim przykładzie.

Poniższy przykład zwraca funkcję, ponieważ wartość wywołania funkcji tworzy prostą grę do odgadnięcia. Aby utworzyć grę, zadzwoń `makeGame` do wartości, do której ktoś ma się odgadnąć. `target` Wartość zwracana z funkcji `makeGame` to funkcja, która przyjmuje jeden argument (wartość przypuszczenie) i określa, czy element zgadywania jest poprawny.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

Poniższy kod wywołuje `makeGame`, wysyłając wartość `7` dla `target`. Identyfikator `playGame` jest powiązany z zwróconym wyrażeniem lambda. W związku `playGame` z tym, jest funkcją, która przyjmuje jako jeden argument wartość `guess`dla.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>Funkcje rozwinięte

Wiele przykładów w poprzedniej sekcji można napisać bardziej zwięzłie poprzez skorzystanie z niejawnych *currying* w F# deklaracjach funkcji. Currying to proces, który przekształca funkcję, która ma więcej niż jeden parametr w szereg osadzonych funkcji, z których każdy ma jeden parametr. W F#programie funkcje, które mają więcej niż jeden parametr, są z natury rozwinięte. Na przykład `compose` z poprzedniej sekcji można pisać jak pokazano w następującym zwięzłym stylu z trzema parametrami.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

Jednak wynik jest funkcją jednego parametru, która zwraca funkcję jednego parametru, który z kolei zwraca kolejną funkcję jednego parametru, jak pokazano w `compose4curried`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

Możesz uzyskać dostęp do tej funkcji na kilka sposobów. Każdy z poniższych przykładów zwraca i wyświetla 18. Możesz zamienić `compose4` `compose4curried` na w dowolnym z przykładów.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

Aby sprawdzić, czy funkcja nadal działa tak jak wcześniej, wypróbuj ponownie oryginalne przypadki testowe.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> Można ograniczyć currying przez załączanie parametrów w spójnych kolekcjach. Aby uzyskać więcej informacji, zobacz "wzorce parametrów" w [parametrach i argumentach](../language-reference/parameters-and-arguments.md).

Poniższy przykład używa niejawnego currying, aby napisać krótszą `makeGame`wersję programu. Szczegóły dotyczące sposobu, `makeGame` w jaki konstrukcje i `game` zwraca funkcję są mniej jawne w tym formacie, ale można je zweryfikować przy użyciu oryginalnych przypadków testowych, które wynik jest taki sam.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

Aby uzyskać więcej informacji na temat currying, zobacz "częściowe stosowanie argumentów" [](../language-reference/functions/index.md)w funkcjach.

## <a name="identifier-and-function-definition-are-interchangeable"></a>Identyfikatory i definicje funkcji są zamienne

Nazwa `num` zmiennej w poprzednich przykładach szacuje się na liczbę całkowitą 10 i nie jest to nieuzasadnione, gdzie `num` gdzie jest prawidłowy, 10 jest również prawidłowy. To samo jest prawdziwe w przypadku identyfikatorów funkcji i ich wartości: wszędzie, gdzie można użyć nazwy funkcji, można użyć wyrażenia lambda, z którym jest powiązane.

Poniższy przykład definiuje `Boolean` funkcję o nazwie `isNegative`, a następnie używa nazwy funkcji i definicji funkcji zamiennie. Następne trzy przykłady zwracają i wyświetlają `False`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

Aby zrobić to jeszcze jeden krok, Zastąp wartość `applyIt` powiązaną z dla. `applyIt`

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>Funkcje są wartościami pierwszej klasy w języku F\#

Przykłady w poprzednich sekcjach pokazują, że funkcje w F# programie spełniają kryteria dla wartości pierwszej klasy w F#:

- Można powiązać identyfikator z definicją funkcji.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- Funkcję można przechowywać w strukturze danych.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- Funkcję można przekazać jako argument.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- Funkcję można zwrócić jako wartość wywołania funkcji.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

Aby uzyskać więcej informacji F#na temat, zobacz [ F# Dokumentacja języka](../language-reference/index.md).

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy kod zawiera wszystkie przykłady w tym temacie.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>Zobacz także

- [Listy](../language-reference/lists.md)
- [Krotki](../language-reference/tuples.md)
- [Funkcje](../language-reference/functions/index.md)
- [`let`Powiązań](../language-reference/functions/let-bindings.md)
- [Wyrażenia lambda: słowo kluczowe `fun`](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
