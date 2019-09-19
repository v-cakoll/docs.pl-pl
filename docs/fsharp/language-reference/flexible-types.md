---
title: Typy elastyczne
description: Dowiedz się, F# jak używać elastycznej adnotacji typu, która wskazuje, że parametr, zmienna lub wartość ma typ zgodny z określonym typem.
ms.date: 05/16/2016
ms.openlocfilehash: bf05f78f163d1f9c73c667df60925b66a5315627
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083067"
---
# <a name="flexible-types"></a>Typy elastyczne

Typ *elastycznyj adnotacji* wskazuje, że parametr, zmienna lub wartość ma typ, który jest zgodny z określonym typem, gdzie zgodność jest określana na podstawie położenia w hierarchii obiektów klasy lub interfejsów zorientowanych na obiekt. Typy elastyczne są przydatne w przypadku, gdy konwersja automatyczna na typy wyższe w hierarchii typów nie występuje, ale mimo to chcesz włączyć funkcję do pracy z dowolnym typem w hierarchii lub dowolnym typem, który implementuje interfejs.

## <a name="syntax"></a>Składnia

```fsharp
#type
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *Typ* reprezentuje typ podstawowy lub interfejs.

Elastyczny typ jest równoważny z typem ogólnym, który ma ograniczenie, które ogranicza dozwolone typy do typów, które są zgodne z typem podstawowym lub interfejsem. Oznacza to, że dwa następujące wiersze kodu są równoważne.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Elastyczne typy są przydatne w kilku typach sytuacji. Na przykład jeśli masz funkcję wyższej kolejności (funkcja, która przyjmuje funkcję jako argument), często przydatna jest funkcja zwracająca typ elastyczny. W poniższym przykładzie użycie elastycznego typu z argumentem sekwencji w `iterate2` włącza funkcję wyższego rzędu do pracy z funkcjami, które generują sekwencje, tablice, listy i wszelkie inne wyliczalne typy.

Weź pod uwagę następujące dwie funkcje, z których jedna zwraca sekwencję, a druga zwraca typ elastyczny.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

W innym przykładzie należy rozważyć funkcję biblioteki [SEQ. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) :

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Do tej funkcji można przekazać dowolną z następujących wyliczalnych sekwencji:

- Lista list
- Lista tablic
- Tablica list
- Tablica sekwencji
- Wszystkie inne kombinacje wyliczalnych sekwencji

Poniższy kod służy `Seq.concat` do zademonstrowania scenariuszy, które można obsługiwać przy użyciu elastycznych typów.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Dane wyjściowe są następujące:

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

W F#, podobnie jak w innych językach zorientowanych obiektowo, istnieją konteksty, w których typy pochodne lub typy, które implementują interfejsy są automatycznie konwertowane na typ podstawowy lub typ interfejsu. Te konwersje automatyczne występują w argumentach bezpośrednich, ale nie w przypadku, gdy typ znajduje się w pozycji podrzędnej, jako część bardziej złożonego typu, takiego jak typ zwracany typu funkcji lub jako argument typu. W ten sposób, elastyczny zapis typu jest szczególnie przydatny, gdy typ, który jest stosowany, jest częścią bardziej złożonego typu.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy ogólne](./generics/index.md)
