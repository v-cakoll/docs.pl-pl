---
title: Wyrażenia obiektów (F#)
description: Dowiedz się, jak używać obiektu wyrażeń języka F# uniknąć dodatkowego kodu i czynności wymagane do utworzenia nowego typu nazwanego.
ms.date: 05/16/2016
ms.openlocfilehash: 1a971044d680d3bf5a6fff38affdaf001d5403b4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865465"
---
# <a name="object-expressions"></a><span data-ttu-id="6ef4a-103">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="6ef4a-103">Object Expressions</span></span>

<span data-ttu-id="6ef4a-104">*Obiektu wyrażenie* to wyrażenie, które tworzy nowe wystąpienie typu utworzony dynamicznie, anonimowy obiekt, który jest oparty na istniejących typu podstawowego, interfejs lub zestawu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ef4a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ef4a-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="6ef4a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ef4a-106">Remarks</span></span>

<span data-ttu-id="6ef4a-107">W poprzedniej składni *typename* reprezentuje istniejącego typu klasy lub typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="6ef4a-108">*Parametry typu* opisano parametry opcjonalne typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="6ef4a-109">*Argumenty* są używane tylko dla typów klasy, które wymagają parametry konstruktora.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="6ef4a-110">*Definicje elementów członkowskich* zastąpienia metody klasy bazowej lub implementacji metody abstrakcyjne klasy bazowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="6ef4a-111">W poniższym przykładzie pokazano kilka różnych typów obiektów wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-111">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="6ef4a-112">Przy użyciu wyrażeń obiektów</span><span class="sxs-lookup"><span data-stu-id="6ef4a-112">Using Object Expressions</span></span>

<span data-ttu-id="6ef4a-113">Należy użyć wyrażeń obiektu, jeśli chcesz uniknąć dodatkowego kodu i obciążenie, które jest wymagane do utworzenia nowego typu nazwanego.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="6ef4a-114">Jeśli używasz wyrażeń obiektów do minimalizacji liczby typów, utworzone w programie, można zmniejszyć liczbę wierszy kodu i uniknąć niepotrzebnego mnożenia typów.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="6ef4a-115">Zamiast tworzyć wiele typów tylko w celu obsługi określonych sytuacjach, można użyć wyrażenie obiektu, który dostosowuje istniejącego typu lub zawiera prawidłową implementacją interfejsu dla określonych przypadków pod ręką.</span><span class="sxs-lookup"><span data-stu-id="6ef4a-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ef4a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ef4a-116">See also</span></span>

- [<span data-ttu-id="6ef4a-117">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="6ef4a-117">F# Language Reference</span></span>](index.md)
