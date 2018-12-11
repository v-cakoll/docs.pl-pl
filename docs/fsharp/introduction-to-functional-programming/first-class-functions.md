---
title: Funkcje pierwszej klasy
description: Dowiedz się więcej o najwyższej klasy funkcji i jak są one ważne w przypadku programowania funkcyjnego w F#.
ms.date: 10/29/2018
ms.openlocfilehash: 505ad686614b53d779cb617fc04ac74c2a88b31b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148641"
---
# <a name="first-class-functions"></a>Funkcje pierwszej klasy

Definiowanie cech funkcjonalności językach programowania jest podniesienie uprawnień funkcji do pierwszej klasy stanu. Można zrobić za pomocą funkcji, niezależnie od rodzaju można zrobić za pomocą wbudowanych typów wartości i można zrobić o stopniu porównywalne nakładu pracy.

Typowe środki najwyższej jakości stanu są następujące:

- Można powiązać funkcji do identyfikatorów? Oznacza to można nadać im nazwy?

- Może przechowujesz funkcje w strukturach danych, takich jak na liście?

- Można przekazać funkcję jako argument w wywołaniu funkcji?

- Może zwrócić funkcję po wywołaniu funkcji?

Ostatnie dwie miary zdefiniować, co to są znane jako *operacje wyższego rzędu* lub *funkcji wyższego rzędu*. Funkcji wyższego rzędu Zaakceptuj funkcji jako argumentów i zwracanie funkcji jako wartość wywołania funkcji. Te operacje obsługi tych filarów programowania funkcjonalnego jako mapowanie funkcji i kompozycja funkcji.

## <a name="give-the-value-a-name"></a>Nadaj nazwę wartości

Jeśli funkcja jest wartością pierwszej klasy, należy możliwość nadaj mu tak samo, jak możesz nazwać liczb całkowitych, ciągów i innych wbudowanych typów. Jest to określane w funkcjonalności programowania literaturze dostępne jako powiązanie identyfikatora do wartości. F#używa [ `let` powiązania](../language-reference/functions/let-bindings.md) można powiązać nazwy wartości: `let <identifier> = <value>`. Poniższy kod pokazuje dwa przykłady.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

Funkcja równie łatwo można nazwać. W poniższym przykładzie zdefiniowano funkcję o nazwie `squareIt` przez powiązanie identyfikatora `squareIt` do [wyrażenia lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`. Funkcja `squareIt` ma jeden parametr `n`, i zwraca kwadrat tego parametru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F#udostępnia następujące bardziej zwięzły widok składnię, aby osiągnąć ten sam wynik w trakcie pisania mniej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

Przykłady, które należy wykonać przede wszystkim Użyj pierwszego stylu `let <function-name> = <lambda-expression>`, aby podkreślić podobieństwa deklaracji funkcji, jak i deklarację inne typy wartości. Jednak o nazwie funkcji można również będą zapisywane przy użyciu zwięzłej składni. Przykłady są napisane w obu kierunkach.

## <a name="store-the-value-in-a-data-structure"></a>Wartość w strukturze danych Store

Wartości pierwszej klasy mogą być przechowywane w strukturze danych. Poniższy kod przedstawia przykłady, które przechowują wartości na listach i w spójnych kolekcjach.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

Aby sprawdzić, czy nazwy funkcji, przechowywane w krotce w rzeczywistości oceny do funkcji, w poniższym przykładzie użyto `fst` i `snd` operatory, aby wyodrębnić elementy pierwszego i drugiego z krotki `funAndArgTuple`. Pierwszy element w spójnej kolekcji jest `squareIt` i drugi element stanowi `num`. Identyfikator `num` jest powiązana w poprzednim przykładzie na liczbę całkowitą 10 prawidłowym argumentem dla `squareIt` funkcji. Drugie wyrażenie dotyczy pierwszego elementu w krotce drugi element krotki: `squareIt num`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

Podobnie, po prostu jako identyfikator `num` i liczba całkowita 10 może być używane zamiennie, więc można identyfikator `squareIt` i wyrażenia lambda `fun n -> n * n`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>Przekaż wartość jako Argument

Jeśli wartość ma stan najwyższej jakości w języku, możesz przekazać go jako argument do funkcji. Na przykład jest wspólne dla przekazywania ciągów i liczby całkowite jako argumenty. Poniższy kod przedstawia liczb całkowitych i ciągi przekazywane jako argumenty w F#.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

Jeśli stanem najwyższej klasy funkcji musi być przekazywane jako argumenty w taki sam sposób. Należy pamiętać, że jest to pierwszy charakterystyka funkcji wyższego rzędu.

W poniższym przykładzie funkcja `applyIt` zawiera dwa parametry `op` i `arg`. Jeśli wyślesz w funkcji, która ma jeden parametr dla `op` i odpowiedniego argumentu dla funkcji `arg`, funkcja zwraca wynik zastosowania `op` do `arg`. W poniższym przykładzie zarówno argumentu funkcji, jak i całkowitego argumentu są wysyłane w taki sam sposób, przy użyciu ich nazw.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

Możliwość wysyłania funkcji jako argument do innej funkcji źródłową wspólne elementy abstrakcji w funkcjonalności języków programowania, takich jak mapy lub filtr operacji. Operacja mapy, na przykład jest funkcja wyższego rzędu, która przechwytuje obliczanie udostępnionych przez funkcje, które przejrzeć listę, zrobić coś do każdego elementu, a następnie wróć do listy wyników. Można zwiększyć każdy element na liście liczb całkowitych, kwadratowe każdy element lub zmienić każdy element na liście ciągi na wielkie litery. Podatne część obliczeń jest proces cyklicznego tej czynności za pomocą listy i tworzy listę wyników do zwrócenia. Ta część jest przechwytywane w funkcji mapowania. Wszystko, trzeba napisać dla konkretnej aplikacji, to funkcja, którą chcesz zastosować do każdego elementu listy indywidualnie (Dodawanie, squaring, zmienianie wielkości liter). Że funkcja jest wysyłany jako argument do funkcji mapowania, podobnie jak `squareIt` są wysyłane do `applyIt` w poprzednim przykładzie.

F#udostępnia metody mapy dla większości typów kolekcji, w tym [Wyświetla](../language-reference/lists.md), [tablic](../language-reference/arrays.md), i [sekwencje](../language-reference/sequences.md). W poniższych przykładach używane listy. Składnia jest `List.map <the function> <the list>`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

Aby uzyskać więcej informacji, zobacz [Wyświetla](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Wartość zwracana z wywołania funkcji

Na koniec wtedy funkcja stan najwyższej jakości w języku, należy może zwrócić go jako wartość wywołania funkcji, tak samo, jak zwrócić innych typów, takich jak liczby całkowite i ciągów.

Następujące wywołania funkcji zwracają liczby całkowite i ich wyświetlenie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

Poniższe wywołanie funkcji zwraca ciąg.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

Poniższe wywołanie funkcji zadeklarowana śródwierszowo, zwraca wartość typu Boolean. Jest wyświetlana wartość `True`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

Aby zwrócić funkcję jako wartość wywołania funkcji jest druga cechę funkcji wyższego rzędu. W poniższym przykładzie `checkFor` jest definiowany jako funkcja, która przyjmuje jeden argument `item`i zwraca nową funkcję jako jego wartość. Zwrócone funkcja przyjmuje listę jako jej argument `lst`i wyszukuje `item` w `lst`. Jeśli `item` jest obecny, funkcja zwraca `true`. Jeśli `item` nie jest obecny, funkcja zwraca `false`. Tak jak w poprzedniej sekcji, w poniższym kodzie użyto funkcji dostarczonej listy [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), aby wyszukać na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Poniższy kod używa `checkFor` Aby utworzyć nową funkcję, która przyjmuje jeden argument, listy i wyszukuje 7 na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

W poniższym przykładzie użyto najwyższej jakości stanu funkcji w F# do deklarowania funkcji, `compose`, która zwraca złożeniem dwóch argumentów funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> Nawet krótszych wersji zapoznać się z sekcją "Curried funkcji."

Poniższy kod wysyła dwie funkcje jako argumenty `compose`, z którym podjąć jeden argument tego samego typu. Wartość zwracana jest nową funkcję, która jest kompozycją argumentów dwóch funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> F#udostępnia dwa operatory `<<` i `>>`, które tworzą funkcje. Na przykład `let squareAndDouble2 = doubleIt << squareIt` jest odpowiednikiem `let squareAndDouble = compose doubleIt squareIt` w poprzednim przykładzie.

Poniższy przykład zwraca funkcję jako wartość wywołania funkcji tworzy prostą zgadywania gier. Aby utworzyć grę, wywołaj `makeGame` wartością ma inną osobę do odgadnięcia wysyłany `target`. Wartość zwrócona przez funkcję `makeGame` jest funkcją, która przyjmuje jeden argument (wynik) i raporty, czy wynik jest poprawny.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

Poniższy kod wywoła `makeGame`, wysyłania wartości `7` dla `target`. Identyfikator `playGame` jest powiązany z wyrażenia lambda zwrócone. W związku z tym `playGame` jest funkcją, która przyjmuje jako argumentem jedną wartość dla `guess`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>Funkcje rozwinięte

Większość przykładów w poprzedniej sekcji można napisać bardziej zwięzłym, wykorzystując niejawny *currying* w F# deklaracje funkcji. Currying jest procesem, który przekształca funkcja, która ma więcej niż jeden parametr do serii osadzonych funkcji, z których każdy ma jeden parametr. W F#, funkcje, które mają więcej niż jeden parametr natury są przenoszeni. Na przykład `compose` z poprzedniej sekcji, można napisać tak, jak pokazano na poniższej zwarty styl z trzema parametrami.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

Jednakże, wynik zależy od jeden parametr, który zwraca funkcja jeden parametr, który z kolei zwraca inną funkcję jeden parametr, jak pokazano na `compose4curried`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

Możesz uzyskać dostęp do tej funkcji na kilka sposobów. Każdy z poniższych przykładów zwraca i wyświetla 18. Możesz zastąpić `compose4` z `compose4curried` w jednym z przykładów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

Aby sprawdzić, czy funkcja nadal działa tak jak poprzednio, spróbuj ponownie, oryginalnym przypadków testowych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> Możesz ograniczyć currying, umieszczając parametrów w spójnych kolekcjach. Aby uzyskać więcej informacji, zobacz "Parametr wzorców" w [parametrami i argumentami](../language-reference/parameters-and-arguments.md).

W poniższym przykładzie użyto niejawne currying do zapisania krótszą wersję `makeGame`. Szczegóły dotyczące `makeGame` tworzy i zwraca `game` funkcji są mniej jawne, w tym formacie, ale można sprawdzić za pomocą oryginalnego przypadków testowych, czy wynik jest taki sam.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

Aby uzyskać więcej informacji na temat currying, zobacz "Częściowe stosowanie argumentów" w [funkcji](../language-reference/functions/index.md).

## <a name="identifier-and-function-definition-are-interchangeable"></a>Identyfikator i definicji funkcji są wymienne

Nazwa zmiennej `num` w ciągu poprzednich przykładach, daje w wyniku całkowitą 10 i nie ma Nic dziwnego to, w którym `num` jest prawidłowy, 10 ma również zastosowanie. To samo dotyczy identyfikatorów funkcji i ich wartości: gdziekolwiek nazwę funkcji mogą być używane, można użyć wyrażenia lambda, z którą jest powiązany.

W poniższym przykładzie zdefiniowano `Boolean` funkcję o nazwie `isNegative`, a następnie używa nazwy funkcji i definicji funkcji zamiennie. Następne trzy przykłady wszystkie przywrócić i wyświetlić `False`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

Aby móc go jeden krok dalej, zastąp wartość która `applyIt` jest powiązany dla `applyIt`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>Funkcje są wartości pierwszej klasy w F\#

Na potrzeby przykładów w poprzednich sekcjach pokazują, że funkcje w F# spełniają kryteria są wartości pierwszej klasy w F#:

- Można powiązać identyfikatora definicji funkcji.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- Funkcję można przechowywać w strukturze danych.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- Funkcję można przekazać jako argument.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- Funkcja może zwrócić jako wartość wywołania funkcji.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Aby uzyskać więcej informacji na temat F#, zobacz [ F# Language Reference](../language-reference/index.md).

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy kod zawiera wszystkie przykłady w tym temacie.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>Zobacz także

- [Listy](../language-reference/lists.md)
- [Krotki](../language-reference/tuples.md)
- [Funkcje](../language-reference/functions/index.md)
- [`let` Powiązania](../language-reference/functions/let-bindings.md)
- [Wyrażenia lambda: `fun` — Słowo kluczowe](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
