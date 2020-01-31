---
title: C# informacje o interfejsie
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: b315d1f04c9e74700afba8ee7871b23ab4b2fd28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744689"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="c4015-102">:::no-loc text="interface"::: (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="c4015-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="c4015-103">Interfejs definiuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c4015-103">An interface defines a contract.</span></span> <span data-ttu-id="c4015-104">Wszelkie [`class`](class.md) lub [`struct`](struct.md) implementujące ten kontrakt muszą zawierać implementację elementów członkowskich zdefiniowanych w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c4015-104">Any [`class`](class.md) or [`struct`](struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="c4015-105">Począwszy od C# 8,0, interfejs może definiować domyślną implementację elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c4015-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="c4015-106">Może również definiować [`static`](static.md) składowe w celu zapewnienia pojedynczej implementacji dla typowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="c4015-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="c4015-107">W poniższym przykładzie Klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod`, która nie ma parametrów i zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="c4015-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="c4015-108">Aby uzyskać więcej informacji i przykładów, zobacz [interfejsy](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="c4015-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="c4015-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4015-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="c4015-110">Interfejs może być elementem członkowskim przestrzeni nazw lub klasy.</span><span class="sxs-lookup"><span data-stu-id="c4015-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="c4015-111">Deklaracja interfejsu może zawierać deklaracje (podpisy bez implementacji) następujących elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="c4015-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="c4015-112">Metody</span><span class="sxs-lookup"><span data-stu-id="c4015-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="c4015-113">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c4015-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="c4015-114">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="c4015-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="c4015-115">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c4015-115">Events</span></span>](event.md)

<span data-ttu-id="c4015-116">Te poprzedzające deklaracje składowych zwykle nie zawierają treści.</span><span class="sxs-lookup"><span data-stu-id="c4015-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="c4015-117">Począwszy od C# 8,0, element członkowski interfejsu może deklarować treść.</span><span class="sxs-lookup"><span data-stu-id="c4015-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="c4015-118">Ta nazwa jest nazywana *implementacją domyślną*.</span><span class="sxs-lookup"><span data-stu-id="c4015-118">This is called a *default implementation*.</span></span> <span data-ttu-id="c4015-119">Elementy członkowskie z organami umożliwiają interfejsowi określenie "domyślnej" implementacji klas i struktur, które nie zapewniają zastępowania implementacji.</span><span class="sxs-lookup"><span data-stu-id="c4015-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="c4015-120">Ponadto począwszy od C# 8,0, interfejs może obejmować:</span><span class="sxs-lookup"><span data-stu-id="c4015-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="c4015-121">Stałe</span><span class="sxs-lookup"><span data-stu-id="c4015-121">Constants</span></span>](const.md)
- [<span data-ttu-id="c4015-122">Operatory</span><span class="sxs-lookup"><span data-stu-id="c4015-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="c4015-123">[Konstruktor statyczny](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="c4015-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="c4015-124">Typy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="c4015-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="c4015-125">Pola statyczne, metody, właściwości, indeksatory i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c4015-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="c4015-126">Deklaracje elementów członkowskich przy użyciu jawnej składni implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c4015-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="c4015-127">Modyfikatory jawnego dostępu (domyślny dostęp jest [`public`](access-modifiers.md)).</span><span class="sxs-lookup"><span data-stu-id="c4015-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="c4015-128">Interfejsy nie mogą zawierać stanu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c4015-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="c4015-129">Gdy pola statyczne są teraz dozwolone, pola wystąpień nie są dozwolone w interfejsach.</span><span class="sxs-lookup"><span data-stu-id="c4015-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="c4015-130">[Funkcja autowłaściwości wystąpienia](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nie jest obsługiwana w interfejsach, ponieważ niejawnie deklaruje pole ukryte.</span><span class="sxs-lookup"><span data-stu-id="c4015-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="c4015-131">Ta reguła ma delikatny efekt dla deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="c4015-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="c4015-132">W deklaracji interfejsu Poniższy kod nie deklaruje właściwości, która jest implementowana w `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="c4015-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="c4015-133">Zamiast tego deklaruje właściwość, która nie ma domyślnej implementacji, ale musi być zaimplementowana w dowolnym typie, który implementuje interfejs:</span><span class="sxs-lookup"><span data-stu-id="c4015-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="c4015-134">Interfejs może dziedziczyć z jednego lub kilku interfejsów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="c4015-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="c4015-135">Gdy interfejs [zastępuje metodę](override.md) zaimplementowaną w interfejsie podstawowym, musi używać [jawnej składni implementacji interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md) .</span><span class="sxs-lookup"><span data-stu-id="c4015-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="c4015-136">Gdy lista typów podstawowych zawiera klasę bazową i interfejsy, Klasa bazowa musi znajdować się na liście.</span><span class="sxs-lookup"><span data-stu-id="c4015-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="c4015-137">Klasa implementująca interfejs może jawnie implementować elementy członkowskie tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c4015-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="c4015-138">Nie można uzyskać dostępu do jawnie zaimplementowanego elementu członkowskiego za pomocą wystąpienia klasy, ale tylko za pomocą wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c4015-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="c4015-139">Ponadto do domyślnych członków interfejsu można uzyskać dostęp tylko za pomocą wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c4015-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="c4015-140">Aby uzyskać więcej informacji na temat jawnej implementacji interfejsu, zobacz [jawną implementację interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="c4015-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="c4015-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4015-141">Example</span></span>

<span data-ttu-id="c4015-142">Poniższy przykład ilustruje implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c4015-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="c4015-143">W tym przykładzie interfejs zawiera deklarację właściwości, a Klasa zawiera implementację.</span><span class="sxs-lookup"><span data-stu-id="c4015-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="c4015-144">Każde wystąpienie klasy implementującej `IPoint` ma właściwości całkowite `x` i `y`.</span><span class="sxs-lookup"><span data-stu-id="c4015-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="c4015-145">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c4015-145">C# language specification</span></span>

<span data-ttu-id="c4015-146">Aby uzyskać więcej informacji, zobacz sekcję [interfejsy](~/_csharplang/spec/interfaces.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md) i Specyfikacja funkcji dla [domyślnych członków interfejsu C# — 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="c4015-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c4015-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4015-147">See also</span></span>

- [<span data-ttu-id="c4015-148">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c4015-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c4015-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c4015-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c4015-150">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c4015-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c4015-151">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="c4015-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="c4015-152">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c4015-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="c4015-153">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="c4015-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="c4015-154">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="c4015-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="c4015-155">class</span><span class="sxs-lookup"><span data-stu-id="c4015-155">class</span></span>](class.md)
- [<span data-ttu-id="c4015-156">struct</span><span class="sxs-lookup"><span data-stu-id="c4015-156">struct</span></span>](struct.md)
- [<span data-ttu-id="c4015-157">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c4015-157">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
