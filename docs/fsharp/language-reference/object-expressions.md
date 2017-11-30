---
title: "Wyrażenia obiektów (F#)"
description: "Dowiedz się, jak używać wyrażeń obiektu F #, jeśli chcesz uniknąć dodatkowego kodu i dodatkowych czynności wymaganych do utworzenia nowej, o nazwie typu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c6dcf4c9-e7fd-4eee-9e4e-1176f4c27f57
ms.openlocfilehash: 28660d430473de02a8a55e37a26609827b364012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="object-expressions"></a><span data-ttu-id="6673e-104">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="6673e-104">Object Expressions</span></span>

<span data-ttu-id="6673e-105">*Obiekt wyrażenie* jest wyrażenie, które tworzy nowe wystąpienie typu obiektu utworzony dynamicznie, anonimowy, który jest oparty na istniejący typ podstawowy, interfejsu lub zestawu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="6673e-105">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>


## <a name="syntax"></a><span data-ttu-id="6673e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6673e-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="6673e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6673e-107">Remarks</span></span>
<span data-ttu-id="6673e-108">W poprzednich składni *typename* reprezentuje istniejącego typu klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6673e-108">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="6673e-109">*Parametry typu* opisano parametry opcjonalne typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6673e-109">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="6673e-110">*Argumenty* są używane tylko dla typu klasy, które wymagają parametrami konstruktora.</span><span class="sxs-lookup"><span data-stu-id="6673e-110">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="6673e-111">*Definicji elementu członkowskiego* przesłonięcia metod klasy podstawowej lub implementacje metody abstrakcyjne klasy podstawowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6673e-111">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="6673e-112">Poniższy przykład przedstawia różne rodzaje wyrażeń obiektów.</span><span class="sxs-lookup"><span data-stu-id="6673e-112">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="6673e-113">Przy użyciu wyrażeń obiektów</span><span class="sxs-lookup"><span data-stu-id="6673e-113">Using Object Expressions</span></span>
<span data-ttu-id="6673e-114">Wyrażenia obiektów jest używane, gdy chce się uniknąć dodatkowego kodu i obciążenie, które jest wymagane do utworzenia nowej, o nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="6673e-114">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="6673e-115">Użycie wyrażenia obiektu do minimalizacji liczby typów utworzony w programie, można zmniejszyć liczbę wierszy kodu i uniknąć niepotrzebnego mnożenia typów.</span><span class="sxs-lookup"><span data-stu-id="6673e-115">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="6673e-116">Zamiast tworzyć wiele typów tylko w celu obsługi określonych sytuacji, używając wyrażenie obiektu, który dostosowuje istniejącego typu lub zapewnia odpowiedniej implementacji interfejsu w przypadku określonych.</span><span class="sxs-lookup"><span data-stu-id="6673e-116">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>


## <a name="see-also"></a><span data-ttu-id="6673e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6673e-117">See Also</span></span>
[<span data-ttu-id="6673e-118">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="6673e-118">F# Language Reference</span></span>](index.md)
