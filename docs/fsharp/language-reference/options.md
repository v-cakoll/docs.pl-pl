---
title: Opcje
description: Dowiedz się, F# jak używać typów opcji, gdy rzeczywista wartość może nie istnieć dla nazwanej wartości lub zmiennej.
ms.date: 05/16/2016
ms.openlocfilehash: 9326cf04f53adac7422c09a49a59c4eecd49486d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627352"
---
# <a name="options"></a>Opcje

Typ opcji w F# jest używany, gdy rzeczywista wartość może nie istnieć dla nazwanej wartości lub zmiennej. Opcja ma typ podstawowy i może zawierać wartość tego typu lub może nie mieć wartości.

## <a name="remarks"></a>Uwagi

Poniższy kod ilustruje funkcję, która generuje typ opcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Jak widać, jeśli dane wejściowe `a` są większe niż 0, `Some(a)` jest generowany.  W przeciwnym razie jest generowany. `None`

Wartość `None` jest używana, gdy opcja nie ma rzeczywistej wartości. W przeciwnym razie wyrażenie `Some( ... )` przypisuje opcję wartość. Wartości `Some` `true` i `None` są przydatne w dopasowaniu do wzorców, jak w następującej funkcji `exists`, która zwraca, jeśli opcja ma wartość i `false` Jeśli nie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Korzystanie z opcji

Opcje są często używane, gdy wyszukiwanie nie zwraca pasującego wyniku, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

W poprzednim kodzie lista jest przeszukiwana cyklicznie. Funkcja `tryFindMatch` przyjmuje funkcję `pred` predykatu zwracającą wartość logiczną i listę do wyszukania. Jeśli zostanie znaleziony element, który spełnia predykat, rekursja zostanie zakończona, a funkcja zwraca wartość jako opcję w wyrażeniu `Some(head)`. Rekursja jest zakończona, gdy pusta lista zostanie dopasowana. W tym momencie wartość `head` nie została znaleziona i `None` jest zwracana.

Wiele F# funkcji biblioteki, które przeszukują kolekcję dla wartości, która może lub nie istnieje Zwróć `option` typ. Zgodnie z Konwencją te funkcje zaczynają `try` się od prefiksu, [`Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)na przykład.

Opcje mogą być również przydatne, gdy wartość może nie istnieć, na przykład jeśli jest możliwe, że wyjątek zostanie wygenerowany podczas próby skonstruowania wartości. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

Funkcja w poprzednim przykładzie ma typ `string -> File option` , ponieważ zwraca `File` obiekt, jeśli plik zostanie otwarty pomyślnie i `None` wystąpił wyjątek. `openFile` W zależności od sytuacji może nie być odpowiedni wybór projektu, aby przechwytywać wyjątek, zamiast zezwalać na propagację.

Ponadto nadal możliwe jest przekazywanie `null` lub wartość o wartości null `Some` w przypadku opcji. Jest to ogólnie konieczne, a zwykle jest to rutynowe F# programowanie, ale jest możliwe ze względu na charakter typów referencyjnych w programie .NET.

## <a name="option-properties-and-methods"></a>Właściwości i metody opcji

Typ opcji obsługuje następujące właściwości i metody.

|Właściwość lub metoda|Typ|Opis|
|------------------|----|-----------|
|[Brak](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Właściwość statyczna, która umożliwia utworzenie wartości opcji, która ma `None` wartość.|
|[IsNone —](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Zwraca `true` czy opcja `None` ma wartość.|
|[IsSome —](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Zwraca `true` czy opcja ma wartość, która nie `None`jest wartością.|
|[Pewnego](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Statyczny element członkowski, który tworzy opcję, która ma wartość, która `None`nie jest.|
|[Wartość](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Zwraca wartość bazową lub zgłasza `System.NullReferenceException` `None`wartość.|

## <a name="option-module"></a>Moduł opcji

Istnieje [moduł, który](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c)zawiera użyteczne funkcje, które wykonują operacje na opcjach. Niektóre funkcje powtarzają funkcjonalność właściwości, ale są przydatne w kontekstach, w których jest wymagana funkcja. [Opcja.](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) ISA i [Option. isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) są funkcjami modułu, które sprawdzają, czy opcja ma wartość. [Opcja. Get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) uzyskuje wartość, jeśli istnieje. Jeśli nie ma wartości, zgłasza `System.ArgumentException`.

Funkcja [Option. bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) wykonuje funkcję na wartości, jeśli istnieje wartość. Funkcja musi mieć dokładnie jeden argument, a jej typem parametru musi być typ opcji. Wartość zwracana przez funkcję jest innym typem opcji.

Moduł opcji zawiera również funkcje, które odpowiadają funkcjom dostępnym dla list, tablic, sekwencji i innych typów kolekcji. Te funkcje obejmują [`Option.map`](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622) [`Option.iter`](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191) [,`Option.foldBack`](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb) [,,`Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876),, i. [`Option.forall`](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428) [`Option.exists`](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99) [`Option.fold`](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8) Te funkcje umożliwiają użycie opcji, takich jak kolekcja elementów zero lub jeden. Aby uzyskać więcej informacji i przykładów, zobacz Omówienie funkcji kolekcji na [listach](lists.md).

## <a name="converting-to-other-types"></a>Konwertowanie na inne typy

Opcje można przekonwertować na listy lub tablice. Gdy opcja jest konwertowana na jedną z tych struktur danych, utworzona struktura danych ma zero lub jeden element. Aby skonwertować opcję na tablicę, użyj [`Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Aby skonwertować opcję na listę, użyj [`Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
