---
title: Kontrola dostępu
description: Dowiedz się, jak kontrolować dostęp do elementów programistycznych, takich jak typy, metody i funkcje, F# w języku programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 38f8f3fd4114c0428fbe8baca71594cd07740b2c
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817854"
---
# <a name="access-control"></a>Kontrola dostępu

*Kontrola dostępu* odwołuje się do deklarowania, którzy klienci mogą używać niektórych elementów programu, takich jak typy, metody i funkcje.

## <a name="basics-of-access-control"></a>Podstawy Access Control

W F#programie specyfikatory `public` `internal`kontroli dostępu, i `private` mogą być stosowane do modułów, typów, metod, definicji wartości, funkcji, właściwości i pól jawnych.

- `public`wskazuje, że można uzyskać dostęp do jednostki przez wszystkie obiekty wywołujące.

- `internal`wskazuje, że można uzyskać dostęp do jednostki tylko z tego samego zestawu.

- `private`wskazuje, że można uzyskać dostęp do jednostki tylko z otaczającego typu lub modułu.

> [!NOTE]
> Specyfikator `protected` dostępu nie jest używany w programie F#, chociaż jest akceptowalny, jeśli używasz typów utworzonych w językach, które obsługują `protected` dostęp. W związku z tym, jeśli zastąpisz metodę chronioną, Metoda pozostanie dostępna tylko w obrębie klasy i jej elementów podrzędnych.

Ogólnie rzecz biorąc, specyfikator jest umieszczany przed nazwą jednostki, z wyjątkiem sytuacji, gdy `mutable` jest używany lub `inline` specyfikator kontroli dostępu.

Jeśli nie jest używany żaden specyfikator dostępu, wartość domyślna to `public`, `let` z wyjątkiem powiązań w typie, który jest zawsze `private` typem.

Podpisy F# w programie zapewniają inny mechanizm kontroli dostępu F# do elementów programu. Podpisy nie są wymagane do kontroli dostępu. Aby uzyskać więcej informacji, [](signatures.md)Zobacz podpisy.

## <a name="rules-for-access-control"></a>Reguły dla Access Control

Kontrola dostępu podlega następującym zasadom:

- Deklaracje dziedziczenia (czyli użycie `inherit` , aby określić klasę bazową dla klasy), deklaracje interfejsu (to oznacza, że klasa implementuje interfejs), a abstrakcyjne składowe zawsze mają taką samą dostępność jak typ otaczający. W związku z tym nie można użyć specyfikatora kontroli dostępu dla tych konstrukcji.

- Dostępność indywidualnych przypadków w Unii rozłącznych jest określana na podstawie dostępności samego związku rozłącznych. Oznacza to, że konkretny przypadek Unii nie jest mniej dostępny niż sam związek.

- Dostępność dla poszczególnych pól typu rekordu jest określana na podstawie dostępności samego rekordu. Oznacza to, że określona etykieta rekordu nie jest mniej dostępna od samego rekordu.

## <a name="example"></a>Przykład

Poniższy kod ilustruje użycie specyfikatorów kontroli dostępu. Istnieją dwa pliki w projekcie `Module1.fs` i. `Module2.fs` Każdy plik jest niejawnie modułem. W związku z tym istnieją dwa moduły `Module1` i `Module2`. Typ prywatny i wewnętrzny są zdefiniowane w `Module1`. Nie można uzyskać dostępu do typu prywatnego `Module2`z, ale wewnętrzny typ może.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

Poniższy kod testuje dostępność typów utworzonych w `Module1.fs`.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Podpisy](signatures.md)
