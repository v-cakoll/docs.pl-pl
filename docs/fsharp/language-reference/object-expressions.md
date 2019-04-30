---
title: Wyrażenia obiektów
description: Dowiedz się, jak używać F# wyrażenia obiektów, jeśli chcesz uniknąć dodatkowego kodu i obciążenie wymagane do utworzenia nowego typu nazwanego.
ms.date: 02/08/2019
ms.openlocfilehash: 63f2c1d7128721b7b8c744e4cf02d73c2a8b4a07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666296"
---
# <a name="object-expressions"></a>Wyrażenia obiektów

*Obiektu wyrażenie* to wyrażenie, które tworzy nowe wystąpienie typu utworzony dynamicznie, anonimowy obiekt, który jest oparty na istniejących typu podstawowego, interfejs lub zestawu interfejsów.

## <a name="syntax"></a>Składnia

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *typename* reprezentuje istniejącego typu klasy lub typ interfejsu. *Parametry typu* opisano parametry opcjonalne typu ogólnego. *Argumenty* są używane tylko dla typów klasy, które wymagają parametry konstruktora. *Definicje elementów członkowskich* zastąpienia metody klasy bazowej lub implementacji metody abstrakcyjne klasy bazowej lub interfejsu.

W poniższym przykładzie pokazano kilka różnych typów obiektów wyrażeń.

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn "%A" obj1

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a>Przy użyciu wyrażeń obiektów

Należy użyć wyrażeń obiektu, jeśli chcesz uniknąć dodatkowego kodu i obciążenie, które jest wymagane do utworzenia nowego typu nazwanego. Jeśli używasz wyrażeń obiektów do minimalizacji liczby typów, utworzone w programie, można zmniejszyć liczbę wierszy kodu i uniknąć niepotrzebnego mnożenia typów. Zamiast tworzyć wiele typów tylko w celu obsługi określonych sytuacjach, można użyć wyrażenie obiektu, który dostosowuje istniejącego typu lub zawiera prawidłową implementacją interfejsu dla określonych przypadków pod ręką.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
