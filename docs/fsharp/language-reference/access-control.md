---
title: Kontrola dostępu
description: Dowiedz się, jak kontrolować dostęp do elementów programistycznych, takich jak typy, metody i funkcje, F# w języku programowania.
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425110"
---
# <a name="access-control"></a>Kontrola dostępu

*Kontrola dostępu* odwołuje się do deklarowania, którzy klienci mogą używać niektórych elementów programu, takich jak typy, metody i funkcje.

## <a name="basics-of-access-control"></a>Podstawy Access Control

W F#programie specyfikatory kontroli dostępu `public`, `internal`i `private` mogą być stosowane do modułów, typów, metod, definicji wartości, funkcji, właściwości i pól jawnych.

- `public` wskazuje, że można uzyskać dostęp do jednostki przez wszystkie obiekty wywołujące.

- `internal` wskazuje, że można uzyskać dostęp do jednostki tylko z tego samego zestawu.

- `private` wskazuje, że można uzyskać dostęp do jednostki tylko z otaczającego typu lub modułu.

> [!NOTE]
> `protected` specyfikatora dostępu nie jest używany w programie F#, chociaż jest akceptowalny, jeśli używasz typów utworzonych w językach, które obsługują `protected` dostępu. W związku z tym, jeśli zastąpisz metodę chronioną, Metoda pozostanie dostępna tylko w obrębie klasy i jej elementów podrzędnych.

Ogólnie rzecz biorąc, specyfikator jest umieszczony przed nazwą jednostki, z wyjątkiem sytuacji, gdy jest używany specyfikator `mutable` lub `inline`, który pojawia się Po specyfikatorze kontroli dostępu.

Jeśli nie jest używany żaden specyfikator dostępu, wartość domyślna to `public`, z wyjątkiem powiązań `let` w typie, które są zawsze `private` do typu.

Podpisy F# w programie zapewniają inny mechanizm kontroli dostępu F# do elementów programu. Podpisy nie są wymagane do kontroli dostępu. Aby uzyskać więcej informacji, zobacz [podpisy](signature-files.md).

## <a name="rules-for-access-control"></a>Reguły dla Access Control

Kontrola dostępu podlega następującym zasadom:

- Deklaracje dziedziczenia (czyli użycie `inherit`, aby określić klasę bazową dla klasy), deklaracje interfejsu (oznacza to, że klasa implementuje interfejs), a abstrakcyjne składowe zawsze mają takie same ułatwienia dostępu jak typ otaczający. W związku z tym nie można użyć specyfikatora kontroli dostępu dla tych konstrukcji.

- Dostępność indywidualnych przypadków w Unii rozłącznych jest określana na podstawie dostępności samego związku rozłącznych. Oznacza to, że konkretny przypadek Unii nie jest mniej dostępny niż sam związek.

- Dostępność dla poszczególnych pól typu rekordu jest określana na podstawie dostępności samego rekordu. Oznacza to, że określona etykieta rekordu nie jest mniej dostępna od samego rekordu.

## <a name="example"></a>Przykład

Poniższy kod ilustruje użycie specyfikatorów kontroli dostępu. W projekcie znajdują się dwa pliki, `Module1.fs` i `Module2.fs`. Każdy plik jest niejawnie modułem. W związku z tym istnieją dwa moduły `Module1` i `Module2`. Typ prywatny i wewnętrzny są zdefiniowane w `Module1`. Nie można uzyskać dostępu do typu prywatnego z `Module2`, ale wewnętrzny typ może.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

Poniższy kod testuje dostępność typów utworzonych w `Module1.fs`.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Podpisy](signature-files.md)
