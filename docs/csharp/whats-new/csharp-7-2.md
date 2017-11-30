---
title: "Nowości w języku C# 7.2."
description: "Przegląd nowych funkcji w języku C# 7.2."
keywords: "C# język projektu, 7.2, Visual Studio 2017 r."
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="b6bf1-104">Nowości w języku C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-104">What's new in C# 7.2</span></span>

<span data-ttu-id="b6bf1-105">7.2 C# jest innej wersji punkt dodające wiele przydatnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="b6bf1-106">Jeden motyw dla tej wersji jest wydajniejszą pracę z typami wartości, unikając niepotrzebnego kopie lub alokacji.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="b6bf1-107">Pozostałe funkcje są nieuprzywilejowany ma funkcje.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="b6bf1-108">C# 7.2 używa [wybór wersji języka](csharp-7-1.md#language-version-selection) element konfiguracji, aby wybrać wersję językową kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="b6bf1-109">Dostępne są następujące nowe funkcje językowe w tej wersji:</span><span class="sxs-lookup"><span data-stu-id="b6bf1-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="b6bf1-110">Semantykę odwołania z typami wartości</span><span class="sxs-lookup"><span data-stu-id="b6bf1-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="b6bf1-111">Kombinacja składni ulepszeń, które umożliwiają pracę z typów wartości, używając semantyki odwołania.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="b6bf1-112">Non końcowe nazwane argumenty</span><span class="sxs-lookup"><span data-stu-id="b6bf1-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="b6bf1-113">Argumenty pozycyjne może następować nazwanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="b6bf1-114">Wiodące znaki podkreślenia w literałach numerycznych</span><span class="sxs-lookup"><span data-stu-id="b6bf1-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="b6bf1-115">Literały numeryczne teraz mogą mieć wiodące znaki podkreślenia przed żadnych drukowanymi cyfr.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="b6bf1-116">`private protected`Modyfikator dostępu</span><span class="sxs-lookup"><span data-stu-id="b6bf1-116">`private protected` access modifier</span></span>](#private-protected)
  - <span data-ttu-id="b6bf1-117">`private protected` Modyfikator dostępu umożliwia dostęp do klas pochodnych w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="b6bf1-118">Semantykę odwołania z typami wartości</span><span class="sxs-lookup"><span data-stu-id="b6bf1-118">Reference semantics with value types</span></span>

<span data-ttu-id="b6bf1-119">Funkcje języka wprowadzone w 7.2 pozwalają pracować z typów wartości podczas używania semantykę odwołania.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="b6bf1-120">Są one przeznaczone do zwiększenia wydajności, minimalizując kopiowanie typów wartości bez ponoszenia alokacji pamięci skojarzone z typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="b6bf1-121">Funkcje obejmują:</span><span class="sxs-lookup"><span data-stu-id="b6bf1-121">The features include:</span></span>

 - <span data-ttu-id="b6bf1-122">`in` — Modyfikator parametrów, aby określić, że argument jest przekazywany przez odwołanie, ale nie zostały zmodyfikowane przez metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="b6bf1-123">`ref readonly` Modyfikator na zwraca metodę, aby wskazać, że metoda zwraca wartość przez odwołanie, ale nie zezwala na zapisy do tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="b6bf1-124">`readonly struct` Deklaracji, aby wskazać, że struktury jest niezmienne i powinien zostać przekazany jako `in` parametru do metody jego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="b6bf1-125">`ref struct` Deklaracji, aby wskazać, że typem struktury uzyskuje dostęp do pamięci zarządzanej bezpośrednio i muszą zawsze być stosu przydzielone.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="b6bf1-126">Możesz przeczytać więcej informacji na temat tych zmian w programie [przy użyciu typów wartości z semantykę odwołania](../reference-semantics-with-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="b6bf1-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="b6bf1-127">Non końcowe nazwane argumenty</span><span class="sxs-lookup"><span data-stu-id="b6bf1-127">Non-trailing named arguments</span></span>

<span data-ttu-id="b6bf1-128">Wywołań metody mogą teraz używać nazwane argumenty, które poprzedzać argumenty pozycyjne, gdy to nazwane argumenty są poprawne pozycji.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="b6bf1-129">Aby uzyskać więcej informacji, zobacz [nazwane i opcjonalne argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="b6bf1-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="b6bf1-130">Wiodące znaki podkreślenia w literałach numerycznych</span><span class="sxs-lookup"><span data-stu-id="b6bf1-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="b6bf1-131">Implementacja obsługę separatory cyfr w języku C# w wersji 7.0 nie zezwalają na `_` jako pierwszy znak w wartości literału.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="b6bf1-132">Hex i binarne literałach numerycznych może teraz rozpoczynać się od `_`.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="b6bf1-133">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b6bf1-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

<span data-ttu-id="b6bf1-134">Ponadto nowe modyfikator dostępu złożone: `private protected` wskazuje, że element członkowski mogą być używane przez klasy pochodne, które są zadeklarowane w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-134">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="b6bf1-135">Gdy `protected internal` zezwala na dostęp klas pochodnych lub klasy, które znajdują się w tym samym zestawie, `private protected` ogranicza dostęp do typów pochodnych zadeklarowany w tym samym zestawie.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-135">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="b6bf1-136">Aby uzyskać więcej informacji, zobacz [modyfikatorów dostępu](../language-reference/keywords/access-modifiers.md) w language reference.</span><span class="sxs-lookup"><span data-stu-id="b6bf1-136">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>
