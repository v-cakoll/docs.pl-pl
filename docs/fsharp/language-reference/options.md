---
title: Opcje (F#)
description: 'Dowiedz się, jak użyć opcji F #, typów, gdy bieżąca wartość nie może istnieć nazwanej wartości lub zmiennej.'
ms.date: 05/16/2016
ms.openlocfilehash: c813c377af1db758a40efa2bd73de22cbb4c66f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="options"></a>Opcje

Typ opcji w języku F # jest używany, gdy bieżąca wartość może nie istnieć do nazwanej wartości lub zmiennej. Opcja ma typu podstawowego i może zawierać wartości tego typu lub nie może mieć wartości.

## <a name="remarks"></a>Uwagi
Poniższy kod przedstawia funkcję, która generuje typ opcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Jak widać, jeśli dane wejściowe `a` jest większa niż 0, `Some(a)` jest generowany.  W przeciwnym razie `None` jest generowany.

Wartość `None` jest używany, gdy opcja nie jest wartością rzeczywistą. W przeciwnym razie wyrażenie `Some( ... )` daje wartość opcji. Wartości `Some` i `None` przydatne w przypadku dopasowania wzorca, tak jak następująca funkcja `exists`, która zwraca `true` Jeśli opcja ma wartość i `false` jeśli jej nie ma.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Przy użyciu opcji
Opcje są często używane podczas wyszukiwania nie zwraca wynik dopasowania, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

W poprzednim kodzie listy jest rekursywnie przeszukiwane. Funkcja `tryFindMatch` przyjmuje funkcja predykatu `pred` która zwraca wartość logiczną, a listy do wyszukiwania. Jeśli zostanie znaleziony element, który spełnia predykatu, kończy się rekursji i funkcja zwraca wartość jako opcja w wyrażeniu `Some(head)`. Rekursja kończy się po dopasowaniu pustej listy. W tym momencie wartość `head` nie został znaleziony, a `None` jest zwracany.

Wiele F # biblioteki funkcje, które wyszukiwania kolekcji dla wartości, który może lub nie istnieje powrotu `option` typu. Według konwencji takich funkcji rozpoczynają `try` prefiksu, na przykład [ `Seq.tryFindIndex` ](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).

Opcje może też być przydatne, gdy wartość może nie istnieć, na przykład, jeśli jest to możliwe, że zostanie wygenerowany wyjątek podczas próby utworzenia wartość. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile` Funkcja w poprzednim przykładzie ma typ `string -> File option` ponieważ zwraca ono `File` obiektu, jeśli plik zostanie pomyślnie otwarty i `None` przypadku wystąpienia wyjątku. W zależności od sytuacji nie można wybrać odpowiednie zaprojektowanie catch wyjątku, a nie zezwalając na propagację.


## <a name="option-properties-and-methods"></a>Opcja właściwości i metody
Typ opcji obsługuje poniższe właściwości i metod.



|Właściwości lub metody|Typ|Opis|
|------------------|----|-----------|
|[Brak](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Statycznej właściwości, która umożliwia tworzenie ma wartość opcji `None` wartość.|
|[Isnone —](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Zwraca `true` Jeśli opcja ma `None` wartość.|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Zwraca `true` Jeśli opcja ma wartość, która nie jest `None`.|
|[Niektóre](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Statyczny element członkowski tworzącą opcja ma wartość, która nie jest `None`.|
|[Wartość](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Zwraca wartości podstawowej lub zgłasza `System.NullReferenceException` , jeśli wartość jest `None`.|

## <a name="option-module"></a>Option — moduł
Moduł jest [opcji](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), który zawiera przydatne funkcje, które wykonują operacje na opcje. Niektóre funkcje Powtórz funkcji właściwości, ale są przydatne w kontekstach, gdy potrzebne jest funkcją. [Option.issome —](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) i [Option.isnone —](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) są obie funkcje modułu, które sprawdzić, czy opcja zawiera wartość. [Option.Get —](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) uzyskuje wartość, jeśli istnieje. Jeśli nie ma żadnej wartości, zgłasza `System.ArgumentException`.

[Option.BIND —](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) funkcja wykonuje funkcję na wartość, jeśli istnieje wartość. Funkcja musi mieć dokładnie jeden argument, a jego typ parametru musi być typ opcji. Wartość zwracana funkcji jest innego typu opcji.

Moduł opcja obejmuje również funkcje, które odpowiadają funkcje, które są dostępne dla list, tablic, sekwencji i innych typów kolekcji. Te funkcje obejmują [ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622), [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191), [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428), [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99), [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb), [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8), i [ `Option.count` ](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876). Te funkcje włączenie opcji, aby można używać jak kolekcję elementów zero lub jeden. Aby uzyskać dodatkowe informacje i przykłady, należy zapoznać się z omówieniem funkcji kolekcji [wymieniono](lists.md).


## <a name="converting-to-other-types"></a>Konwertowanie na inne typy
Opcje mogą być konwertowane do list i tablic. Gdy opcja jest konwertowany na jedną z tych struktur danych, struktura danych ma wartość zero lub jeden element. Aby przekonwertować opcji do tablicy, użyj [ `Option.toArray` ](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Aby przekonwertować opcji do listy, użyj [ `Option.toList` ](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Typy F#](fsharp-types.md)
