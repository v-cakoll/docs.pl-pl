---
title: Kontrola dostępu
description: Dowiedz się, jak kontrolować dostęp do elementów programowania, takich jak typy, metody i funkcje, w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 8db178b26f3beb6ce95bff84ccad9ac9e8c40ce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772739"
---
# <a name="access-control"></a>Kontrola dostępu

*Kontrola dostępu* odwołuje się do deklarowania, której klienci mogą używać niektórych elementów programów, takich jak typy, metody i funkcje.

## <a name="basics-of-access-control"></a>Podstawowe informacje o kontroli dostępu

W F#, specyfikatory dostępu `public`, `internal`, i `private` można zastosować do modułów, typów, metod, definicje wartości, funkcje, właściwości i pola jawne.

- `public` Wskazuje, czy jednostki są dostępne dla wszystkich obiektów wywołujących.

- `internal` Wskazuje, że jednostki są dostępne tylko z tego samego zestawu.

- `private` Wskazuje, że jednostki są dostępne tylko z otaczającej typu lub modułu.

> [!NOTE]
> Specyfikator dostępu `protected` nie jest używany w F#, mimo że jest dopuszczalne, jeśli używasz typów, utworzone w językach, które obsługują `protected` dostępu. Dlatego Jeśli zastąpisz Metoda chroniona metoda pozostaje dostępny tylko w klasie i jego elementów potomnych.

Ogólnie rzecz biorąc, specyfikator jest umieszczany przed nazwą jednostki, chyba że `mutable` lub `inline` specyfikator jest używany, które występują po specyfikatorze kontroli dostępu.

Jeśli jest używany nie specyfikatora dostępu, wartość domyślna to `public`, z wyjątkiem `let` powiązania w typie, które są zawsze `private` do typu.

Podpisy w F# Podaj inny mechanizm do kontrolowania dostępu do F# program elementów. Podpisy nie są wymagane dla kontroli dostępu. Aby uzyskać więcej informacji, zobacz [podpisy](signatures.md).

## <a name="rules-for-access-control"></a>Zasady kontroli dostępu

Kontrola dostępu jest się następujące zasady:

- Dziedziczenie, deklaracje (oznacza to, że użycie `inherit` określić klasę bazową dla klasy), interfejs deklaracje, (które określając, że klasa implementuje interfejs) i wydobyć członków zawsze mieć identyczną dostępność co typ otaczający. W związku z tym specyfikatora dostępu nie można używać na te konstrukcje.

- Ułatwienia dostępu dla poszczególnych przypadków w złożenia dyskryminowanego jest określany przez dostępność złożenia dyskryminowanego, sam. Określonego case złożenia jest nie jest mniej dostępny niż samo połączenie.

- Ułatwienia dostępu dla poszczególnych pól typu rekordu nie zależy od dostępności samego rekordu. Etykieta określonego rekordu jest nie jest mniej dostępny niż samego rekordu.

## <a name="example"></a>Przykład

Poniższy kod ilustruje użycie specyfikatory dostępu. Istnieją dwa pliki w projekcie `Module1.fs` i `Module2.fs`. Każdy plik jest niejawnie modułu. Dlatego istnieją dwa moduły `Module1` i `Module2`. Prywatny typ i wewnętrzny typ są zdefiniowane w `Module1`. Prywatny typ nie jest dostępny z `Module2`, ale wewnętrzny typ można.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

Poniższy kod sprawdza dostępność typów, utworzone w `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Podpisy](signatures.md)