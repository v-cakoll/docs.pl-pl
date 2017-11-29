---
title: "Funkcje jako wartości pierwszej klasy (F#)"
description: "Dowiedz się, jak funkcje zostaną podniesione do najwyższej jakości stan w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a>Funkcje jako wartości pierwszej klasy

Definiowanie cech funkcjonalności języków programowania jest podniesienia uprawnień funkcji do pierwszej klasy stanu. Można będzie wykonać za pomocą funkcji niezależnie od można wykonać za pomocą wbudowanych typów wartości i można w tym celu o stopniu można porównywać pod względem nakładu pracy.

Następujące typowe środki najwyższej jakości stanu:

- Można powiązać funkcji do identyfikatorów? Oznacza to możesz nadać im nazw?

- Można przechowujesz funkcje w strukturach danych, takich jak na liście?

- Można przekazać funkcji jako argument w wywołaniu funkcji?

- Można zwrócić funkcji po wywołaniu funkcji?

Ostatnie dwa środki zdefiniować, co to są określane jako *operacji wyższego rzędu* lub *funkcje wyższego rzędu*. Funkcje wyższego rzędu zaakceptować funkcje jako argumenty i zwracać funkcji jako wartość wywołania funkcji. Te operacje obsługuje takie filarów programowanie funkcjonalne jako mapowanie funkcji i kompozycja funkcji.


## <a name="give-the-value-a-name"></a>Nadaj nazwę wartości

Jeśli funkcja jest wartością najwyższej jakości, musi można nazwę, tak samo, jak można określić nazwę liczb całkowitych, ciągi i inne typy wbudowane. Jest to określane w funkcjonalności materiały programowania jako powiązanie identyfikator na wartość. F # używa [ `let` powiązania](../language-reference/functions/let-bindings.md) można powiązać nazwy wartości: `let <identifier> = <value>`. Poniższy kod przedstawia dwa przykłady.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

Można określić nazwę funkcji równie łatwo. W poniższym przykładzie zdefiniowano funkcję o nazwie `squareIt` przez powiązanie identyfikatora `squareIt` do [wyrażenia lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`. Funkcja `squareIt` ma jeden parametr `n`, i zwraca kwadrat tego parametru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F # udostępnia następujące bardziej zwięzły składni uzyskanie takiego samego wyniku z mniej wpisywania.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

Przykłady, które należy wykonać przede wszystkim Użyj pierwszego stylu `let <function-name> = <lambda-expression>`, aby wyróżnić podobieństwa między deklaracji funkcji i deklaracji z innych typów wartości. Jednak wszystkie funkcje nazwany również można pisać ze zwięzłą składnią. Przykłady są napisane w obu kierunkach.


## <a name="store-the-value-in-a-data-structure"></a>Przechowywanie wartości w strukturze danych

Wartości pierwszej klasy mogą być przechowywane w strukturze danych. Poniższy kod przedstawia przykłady, których przechowywanie wartości na listach i spójnych kolekcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

Aby sprawdzić, czy nazwy funkcji przechowywane w spójnej kolekcji w rzeczywistości oceny funkcji, w poniższym przykładzie użyto `fst` i `snd` operatorom Wyodrębnij elementy pierwszej i drugiej z spójnej kolekcji `funAndArgTuple`. Pierwszy element w spójnej kolekcji jest `squareIt` i drugi element `num`. Identyfikator `num` jest powiązana w poprzednim przykładzie do liczby całkowitej 10, prawidłowym argumentem dla `squareIt` funkcji. Drugie wyrażenie dotyczy drugiego elementu w spójnej kolekcji pierwszym elementem w spójnej kolekcji: `squareIt num`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

Podobnie, po prostu jako identyfikator `num` i może być liczbą całkowitą 10 używane zamiennie, dlatego można identyfikator `squareIt` i wyrażenia lambda `fun n -> n * n`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a>Przekaż wartość jako Argument

Jeśli wartość ma stan pierwszą klasą w języku, można przekazać go jako argument do funkcji. Na przykład jest typowe do przekazania liczb całkowitych i ciągi jako argumenty. Poniższy kod przedstawia liczb całkowitych i ciągi przekazywane jako argumenty w języku F #.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

Jeśli stanem najwyższej jakości funkcji musi być przekazywane jako argumenty w taki sam sposób. Należy pamiętać, że jest to pierwszy charakterystyczne dla funkcji wyższego rzędu.

W poniższym przykładzie funkcja `applyIt` zawiera dwa parametry `op` i `arg`. Po wysłaniu w funkcję, która przyjmuje jeden parametr `op` i odpowiednie argumentu dla funkcji `arg`, funkcja zwraca wynik zastosowania `op` do `arg`. W poniższym przykładzie zarówno argument funkcji, jak i argument całkowitą są wysyłane w taki sam sposób, przy użyciu ich nazw.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

Umożliwia wysyłanie funkcji jako argument do innej funkcji źródłową obiektów wspólnych abstrakcyjnych w funkcjonalności języków programowania, takimi jak operacje mapy albo filtr. Operacja mapy, na przykład to funkcja wyższego rzędu przechwytujący obliczenia współużytkowane przez funkcje, które krokowo listy, Zrób coś do każdego elementu, a następnie wróć listę wyników. Można zwiększyć każdy element na liście liczb całkowitych, kwadratowe każdy element lub zmienić każdy element na liście ciągi na wielkie litery. Podatnych część obliczenia to proces cyklicznego tej czynności za pośrednictwem listy i tworzy listę wyników do zwrócenia. Tej części są przechwytywane w funkcji mapowania. Wszystkie trzeba napisać dla określonej aplikacji jest funkcji, które chcesz zastosować do każdego elementu listy pojedynczo (Dodawanie, squaring, zmienianie wielkości liter). Czy funkcja jest wysyłany jako argument do funkcji mapowania podobnie jak `squareIt` są wysyłane do `applyIt` w poprzednim przykładzie.

F # udostępnia metody mapy dla większości typów kolekcji, w tym [wymieniono](../language-reference/lists.md), [tablice](../language-reference/arrays.md), i [sekwencji](../language-reference/sequences.md). W poniższych przykładach użyto list. Składnia jest `List.map <the function> <the list>`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

Aby uzyskać więcej informacji, zobacz [wymieniono](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Zwracanie wartości z wywołania funkcji

Na koniec Jeśli funkcja ma stan pierwszą klasą w języku, należy może zwrócić go jako wartość wywołanie funkcji tak samo, jak zwrócić innych typów, takich jak liczby całkowite i ciągi.

Następujące wywołania funkcji przywrócić liczb całkowitych i wyświetlić je.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

Następujące wywołanie funkcja zwraca wartość typu ciąg.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

Następujące wywołanie funkcji zadeklarowana śródwierszowo, zwraca wartość logiczną. Wartość wyświetlana jest `True`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

Możliwość zwracania funkcji jako wartość wywołania funkcji jest drugi charakterystyczne dla funkcji wyższego rzędu. W poniższym przykładzie `checkFor` jest zdefiniowane jako funkcję, która przyjmuje jeden argument `item`i zwraca nową funkcję jako jego wartość. Zwrócony funkcja przyjmuje listę jako jej argument `lst`i wyszukuje `item` w `lst`. Jeśli `item` jest obecny, funkcja zwraca `true`. Jeśli `item` nie jest obecny, funkcja zwraca `false`. Jak w poprzedniej sekcji, w poniższym kodzie użyto funkcji dostarczona lista [list.EXISTS —](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), do listy wyszukiwania.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Poniższy kod używa `checkFor` Aby utworzyć nową funkcję, która przyjmuje jeden argument, listy i wyszukuje 7 na liście.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

W poniższym przykładzie użyto najwyższej jakości stanu funkcji w języku F # w celu zadeklarowania funkcji, `compose`, która zwraca złożenie dwóch argumentów funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
Nawet krótszą wersję zobacz następującą sekcję "Funkcje Curried."


Poniższy kod wysyła dwie funkcje jako argumenty do `compose`, zarówno z zająć pojedynczy argument tego samego typu. Wartość zwracana jest nową funkcję, która jest złożeniem argumenty dwóch funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
F # zawiera dwa operatory `<<` i `>>`, które tworzą funkcji. Na przykład `let squareAndDouble2 = doubleIt << squareIt` jest odpowiednikiem `let squareAndDouble = compose doubleIt squareIt` w poprzednim przykładzie.

Poniższy przykład przedstawia zwracanie funkcji jako wartość wywołania funkcji tworzy prosty odgadnięcie gier. Do tworzenia gier, wywołaj `makeGame` o wartości mają ktoś odgadnąć wysłanych `target`. Wartość zwrócona przez funkcję `makeGame` to funkcja, która przyjmuje jeden argument. (wynik) i w raportach, czy wynik jest poprawna.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

Poniższy kod wywołania `makeGame`, wysyłania wartości `7` dla `target`. Identyfikator `playGame` jest powiązany z wyrażeniem lambda zwrócony. W związku z tym `playGame` to funkcja, która przyjmuje jako jej argument jedną wartość dla `guess`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a>Funkcje rozwinięte

Większość przykładów w poprzedniej sekcji mogą być zapisywane więcej zwięzłym dzięki wykorzystaniu niejawne *currying* w deklaracji funkcji F #. Currying jest procesem, który przekształca funkcja, która ma więcej niż jeden parametr do serii osadzonych funkcji, z których każda ma jeden parametr. W języku F # funkcje, które mają więcej niż jeden parametr są z założenia typu curried. Na przykład `compose` z poprzedniej sekcji, można napisać tak, jak pokazano w następujący styl zwięzła, z trzema parametrami.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

Jednak wynik jest funkcją jeden parametr, który zwraca funkcję jeden parametr, który z kolei zwraca innej funkcji jeden parametr, jak pokazano w `compose4curried`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

Można uzyskać dostępu do tej funkcji na kilka sposobów. Każdy z poniższych przykładach zwraca i wyświetla 18. Można zastąpić `compose4` z `compose4curried` w jednym z przykładów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

Aby zweryfikować, że nadal działa tak jak poprzednio, spróbuj ponownie oryginalnej przypadków testowych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
Można ograniczyć currying umieszczając parametrów w spójnych kolekcji. Aby uzyskać więcej informacji, zobacz "Parametr wzorce" w [parametry i argumenty](../language-reference/parameters-and-arguments.md).

W poniższym przykładzie użyto niejawne currying zapisu krótszą wersję `makeGame`. Szczegóły dotyczące `makeGame` tworzy i zwraca `game` funkcji są mniej jawną w następującym formacie, ale można sprawdzić za pomocą oryginalnego przypadków testowych, czy wynik jest taka sama.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

Aby uzyskać więcej informacji na temat currying, zobacz "Częściowe aplikacji argumenty" w [funkcji](../language-reference/functions/index.md).


## <a name="identifier-and-function-definition-are-interchangeable"></a>Identyfikator i definicji funkcji są wymienne
Nazwa zmiennej `num` w poprzedniej przykłady ocenia do liczby całkowitej 10, a następnie niespodziewanego nie jest to, w którym `num` jest prawidłowy, 10 jest również prawidłowe. To samo dotyczy funkcji identyfikatorów i wartości: gdziekolwiek może służyć nazwa funkcji, można użyć wyrażenia lambda, z którą jest powiązany.

W poniższym przykładzie zdefiniowano `Boolean` wywołana funkcja `isNegative`, a następnie zamiennie używa nazwy funkcji i definicji funkcji. Przykłady trzech kolejnych wszystkie wrócić i wyświetlić `False`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

Podejmowanie go jednym kroku, należy zastąpić wartość która `applyIt` jest powiązany z dla `applyIt`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>Funkcje są wartości pierwszej klasy w języku F # #

Przykłady w poprzednich sekcjach pokazują, że funkcje w języku F # spełniają kryteria są wartości pierwszej klasy w języku F #:

- Identyfikator można powiązać z definicji funkcji.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- Funkcja można przechowywać w strukturze danych.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- Funkcja można przekazać jako argument.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- Funkcja może zwrócić jako wartość wywołania funkcji.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Aby uzyskać więcej informacji na temat języka F #, zobacz [dokumentację języka F #](../language-reference/index.md).

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy kod zawiera wszystkie przykłady w tym temacie.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a>Zobacz też

[Wyświetla listę](../language-reference/lists.md)

[Krotki](../language-reference/tuples.md)

[Funkcje](../language-reference/functions/index.md)

[`let`Powiązania](../language-reference/functions/let-bindings.md)

[Wyrażenia lambda: `fun` — słowo kluczowe](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
