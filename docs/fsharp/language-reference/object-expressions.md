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
# <a name="object-expressions"></a><span data-ttu-id="9bfaa-103">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="9bfaa-103">Object Expressions</span></span>

<span data-ttu-id="9bfaa-104">*Obiektu wyrażenie* to wyrażenie, które tworzy nowe wystąpienie typu utworzony dynamicznie, anonimowy obiekt, który jest oparty na istniejących typu podstawowego, interfejs lub zestawu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bfaa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bfaa-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="9bfaa-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bfaa-106">Remarks</span></span>

<span data-ttu-id="9bfaa-107">W poprzedniej składni *typename* reprezentuje istniejącego typu klasy lub typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="9bfaa-108">*Parametry typu* opisano parametry opcjonalne typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="9bfaa-109">*Argumenty* są używane tylko dla typów klasy, które wymagają parametry konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="9bfaa-110">*Definicje elementów członkowskich* zastąpienia metody klasy bazowej lub implementacji metody abstrakcyjne klasy bazowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="9bfaa-111">W poniższym przykładzie pokazano kilka różnych typów obiektów wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-111">The following example illustrates several different types of object expressions.</span></span>

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

## <a name="using-object-expressions"></a><span data-ttu-id="9bfaa-112">Przy użyciu wyrażeń obiektów</span><span class="sxs-lookup"><span data-stu-id="9bfaa-112">Using Object Expressions</span></span>

<span data-ttu-id="9bfaa-113">Należy użyć wyrażeń obiektu, jeśli chcesz uniknąć dodatkowego kodu i obciążenie, które jest wymagane do utworzenia nowego typu nazwanego.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="9bfaa-114">Jeśli używasz wyrażeń obiektów do minimalizacji liczby typów, utworzone w programie, można zmniejszyć liczbę wierszy kodu i uniknąć niepotrzebnego mnożenia typów.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="9bfaa-115">Zamiast tworzyć wiele typów tylko w celu obsługi określonych sytuacjach, można użyć wyrażenie obiektu, który dostosowuje istniejącego typu lub zawiera prawidłową implementacją interfejsu dla określonych przypadków pod ręką.</span><span class="sxs-lookup"><span data-stu-id="9bfaa-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bfaa-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bfaa-116">See also</span></span>

- [<span data-ttu-id="9bfaa-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="9bfaa-117">F# Language Reference</span></span>](index.md)
