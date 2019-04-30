---
title: Opcje
description: Dowiedz się, jak używać F# opcji typów, gdy rzeczywista wartość może nie istnieć dla nazwanej wartości lub zmiennej.
ms.date: 05/16/2016
ms.openlocfilehash: 6d32693bccc74c2cab642e4f626c9463092e8a39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666485"
---
# <a name="options"></a>Opcje

Typ opcji w F# jest używany, gdy rzeczywista wartość może nie istnieć dla nazwanej wartości lub zmiennej. Opcja ma podstawowy typ i może zawierać wartość tego typu lub nie może mieć wartość.

## <a name="remarks"></a>Uwagi

Poniższy kod ilustruje funkcja, która generuje typ opcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Jak widać, jeśli dane wejściowe `a` jest większa niż 0, `Some(a)` jest generowany.  W przeciwnym razie `None` jest generowany.

Wartość `None` jest używany, gdy opcja ma wartość rzeczywistą. W przeciwnym wypadku wyrażenie `Some( ... )` udostępnia opcję wartości. Wartości `Some` i `None` jest przydatny w dopasowywania do wzorca, tak jak następującą funkcję `exists`, co powoduje zwrócenie `true` Jeśli opcja ma wartość i `false` Jeśli tak nie jest.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Za pomocą opcji

Opcje są często używane podczas wyszukiwania nie zwraca wynik dopasowania, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

W poprzednim kodzie listy jest rekursywnie przeszukiwane. Funkcja `tryFindMatch` przyjmuje funkcji predykatu `pred` zwracającego wartość typu Boolean i listę wyszukiwania. Jeśli zostanie znaleziony element, który spełnia predykat, kończy się rekursji i funkcja zwraca wartość jako opcja w wyrażeniu `Some(head)`. Rekursji kończy się po dopasowaniu pustej listy. W tym momencie wartość `head` nie została znaleziona, i `None` jest zwracana.

Wiele F# funkcje bibliotek, które wyszukiwania kolekcji dla wartość, która może lub nie istnieje zwrócenia `option` typu. Zgodnie z Konwencją, te funkcje zaczynają się od `try` prefiksu, na przykład [ `Seq.tryFindIndex` ](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).

Opcje również może być przydatne, gdy wartość może nie istnieć, na przykład, jeśli jest to możliwe, że wyjątek zostanie zgłoszony podczas próby utworzenia wartości. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile` Funkcja w poprzednim przykładzie ma typ `string -> File option` ponieważ zwraca `File` obiektu, jeśli plik zostanie pomyślnie otwarty i `None` Jeśli wystąpi wyjątek. W zależności od sytuacji może nie być odpowiednie uzasadnienie wyboru tych elementów się zostać przechwycony wyjątek, a nie zezwolenie na jego propagację.

Ponadto jest nadal możliwe przekazać `null` lub wartość, która ma wartość null, aby `Some` przypadków opcji. Zwykle jest to należy unikać i zazwyczaj znajduje się w procedurze F# programowania, ale jest możliwe ze względu na charakter typów referencyjnych na platformie .NET.

## <a name="option-properties-and-methods"></a>Opcja właściwości i metody

Typ opcji obsługuje poniższe właściwości i metody.

|Właściwości lub metody|Typ|Opis|
|------------------|----|-----------|
|[Brak](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Właściwość statyczna, która pozwala na tworzenie wartość opcji, która ma `None` wartość.|
|[Isnone —](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Zwraca `true` Jeśli opcja `None` wartość.|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Zwraca `true` Jeśli opcja ma wartość, która nie jest `None`.|
|[Niektóre](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Statyczny element członkowski, tworzącą opcja ma wartość, która nie jest `None`.|
|[Wartość](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Zwraca podstawową wartość lub zgłasza `System.NullReferenceException` Jeśli wartość jest `None`.|

## <a name="option-module"></a>Opcja modułu

Moduł jest [opcji](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), który zawiera przydatnych funkcji, które wykonują operacje na temat opcji. Niektóre funkcje Powtórz funkcji właściwości, ale są przydatne w kontekstach, gdy potrzebne są funkcją. [Option.isSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) i [Option.isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) są obie funkcje modułu, które sprawdzić, czy opcja przechowuje wartość. [Option.Get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) uzyskuje wartość, jeśli taka istnieje. Jeśli nie ma wartości, zgłasza `System.ArgumentException`.

[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) funkcja wykonuje funkcję na wartości, jeśli ma wartość. Funkcja przyjmuje dokładnie jednego argumentu i jego typowi parametru musi być typ opcji. Wartość zwracana przez funkcję jest innego typu opcji.

Moduł opcja obejmuje również funkcje, które odnoszą się do funkcji, które są dostępne dla list, tablic, sekwencji i inne typy kolekcji. Funkcje te obejmują [ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622), [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191), [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428), [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99), [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb), [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8), i [ `Option.count` ](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876). Te funkcje umożliwiają opcje do użycia takich jak kolekcja elementów zero lub jeden. Aby uzyskać więcej informacji i przykładów, zobacz Omówienie funkcji kolekcji w [Wyświetla](lists.md).

## <a name="converting-to-other-types"></a>Konwersja na inne typy

Opcje mogą być konwertowane do listy lub tablicami. Gdy opcja jest konwertowany do jednej z tych struktur danych, struktura danych ma wartość zero lub jeden element. Aby przekonwertować opcję do tablicy, użyj [ `Option.toArray` ](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Aby przekonwertować listę opcji, należy użyć [ `Option.toList` ](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
