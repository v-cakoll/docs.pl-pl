---
title: interfejs — odwołanie do języka C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625855"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="5bd5e-102">:::no-loc text="interface":::(Odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="5bd5e-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="5bd5e-103">Interfejs definiuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-103">An interface defines a contract.</span></span> <span data-ttu-id="5bd5e-104">Wszelkie [`class`](class.md) [`struct`](../builtin-types/struct.md) lub implementuje tej umowy musi zapewnić implementację elementów członkowskich zdefiniowanych w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-104">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="5bd5e-105">Począwszy od języka C# 8.0, interfejs może zdefiniować implementację domyślną dla elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="5bd5e-106">Może również [`static`](static.md) zdefiniować elementy członkowskie w celu zapewnienia jednej implementacji dla wspólnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="5bd5e-107">W poniższym przykładzie `ImplementationClass` klasa musi `SampleMethod` implementować metodę o `void`nazwie, która nie ma parametrów i zwraca .</span><span class="sxs-lookup"><span data-stu-id="5bd5e-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="5bd5e-108">Aby uzyskać więcej informacji i przykładów, zobacz [Interfejsy](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="5bd5e-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="5bd5e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bd5e-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="5bd5e-110">Interfejs może być członkiem obszaru nazw lub klasy.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="5bd5e-111">Deklaracja interfejsu może zawierać deklaracje (podpisy bez implementacji) następujących elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="5bd5e-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="5bd5e-112">Metody</span><span class="sxs-lookup"><span data-stu-id="5bd5e-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="5bd5e-113">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5bd5e-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- <span data-ttu-id="5bd5e-114">[Indexers](../../programming-guide/indexers/using-indexers.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="5bd5e-114">[Indexers](../../programming-guide/indexers/using-indexers.md)</span></span>
- [<span data-ttu-id="5bd5e-115">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5bd5e-115">Events</span></span>](event.md)

<span data-ttu-id="5bd5e-116">Te poprzednie deklaracje elementów członkowskich zazwyczaj nie zawierają treści.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="5bd5e-117">Począwszy od języka C# 8.0, element członkowski interfejsu może zadeklarować treść.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="5bd5e-118">Jest to nazywane *domyślną implementacją*.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-118">This is called a *default implementation*.</span></span> <span data-ttu-id="5bd5e-119">Elementy członkowskie z organami pozwalają interfejsowi, aby zapewnić "domyślną" implementację dla klas i struktur, które nie zapewniają implementacji nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="5bd5e-120">Ponadto począwszy od języka C# 8.0 interfejs może zawierać:</span><span class="sxs-lookup"><span data-stu-id="5bd5e-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="5bd5e-121">Stałe</span><span class="sxs-lookup"><span data-stu-id="5bd5e-121">Constants</span></span>](const.md)
- [<span data-ttu-id="5bd5e-122">Operatory</span><span class="sxs-lookup"><span data-stu-id="5bd5e-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="5bd5e-123">[Konstruktor statyczny](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="5bd5e-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="5bd5e-124">Typy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="5bd5e-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="5bd5e-125">Pola statyczne, metody, właściwości, indeksatory i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5bd5e-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="5bd5e-126">Deklaracje członkowskie przy użyciu składni implementacji interfejsu jawnego.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="5bd5e-127">Modyfikatory dostępu jawnego [`public`](access-modifiers.md)(domyślnym dostępem jest ).</span><span class="sxs-lookup"><span data-stu-id="5bd5e-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="5bd5e-128">Interfejsy mogą nie zawierać stanu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="5bd5e-129">Podczas gdy pola statyczne są teraz dozwolone, pola wystąpień nie są dozwolone w interfejsach.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="5bd5e-130">[Wystąpienia właściwości automatyczne](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nie są obsługiwane w interfejsach, ponieważ będą one niejawnie zadeklarować ukryte pole.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="5bd5e-131">Ta reguła ma subtelny wpływ na deklaracje właściwości.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="5bd5e-132">W deklaracji interfejsu następujący kod nie deklaruje właściwości zaimplementowanej automatycznie, `class` `struct`tak jak w a lub .</span><span class="sxs-lookup"><span data-stu-id="5bd5e-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="5bd5e-133">Zamiast tego deklaruje właściwość, która nie ma implementacji domyślnej, ale musi być zaimplementowana w dowolnym typie, który implementuje interfejs:</span><span class="sxs-lookup"><span data-stu-id="5bd5e-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="5bd5e-134">Interfejs można dziedziczyć z jednego lub więcej interfejsów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="5bd5e-135">Gdy interfejs [zastępuje metodę](override.md) zaimplementowane w interfejsie podstawowym, należy użyć składni [implementacji interfejsu jawnego.](../../programming-guide/interfaces/explicit-interface-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="5bd5e-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="5bd5e-136">Gdy lista typów podstawowych zawiera klasę podstawową i interfejsy, klasa podstawowa musi być na pierwszym miejscu na liście.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="5bd5e-137">Klasa, która implementuje interfejs może jawnie implementować elementy członkowskie tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="5bd5e-138">Jawnie zaimplementowany element członkowski nie może być dostępny za pośrednictwem wystąpienia klasy, ale tylko za pośrednictwem wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="5bd5e-139">Ponadto domyślne elementy członkowskie interfejsu są dostępne tylko za pośrednictwem wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="5bd5e-140">Aby uzyskać więcej informacji na temat implementacji interfejsu jawnego, zobacz [Implementacja interfejsu jawnego](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="5bd5e-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="5bd5e-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bd5e-141">Example</span></span>

<span data-ttu-id="5bd5e-142">W poniższym przykładzie przedstawiono implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="5bd5e-143">W tym przykładzie interfejs zawiera deklarację właściwości i klasa zawiera implementację.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="5bd5e-144">Każde wystąpienie klasy, która `IPoint` implementuje ma `x` właściwości `y`całkowite i .</span><span class="sxs-lookup"><span data-stu-id="5bd5e-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="5bd5e-145">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5bd5e-145">C# language specification</span></span>

<span data-ttu-id="5bd5e-146">Aby uzyskać więcej informacji, zobacz [interfaces](~/_csharplang/spec/interfaces.md) sekcji [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i specyfikacji funkcji dla [domyślnych elementów członkowskich interfejsu — C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="5bd5e-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="5bd5e-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bd5e-147">See also</span></span>

- [<span data-ttu-id="5bd5e-148">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="5bd5e-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5bd5e-149">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="5bd5e-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5bd5e-150">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5bd5e-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5bd5e-151">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="5bd5e-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="5bd5e-152">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5bd5e-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="5bd5e-153">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="5bd5e-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="5bd5e-154">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="5bd5e-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="5bd5e-155">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5bd5e-155">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
