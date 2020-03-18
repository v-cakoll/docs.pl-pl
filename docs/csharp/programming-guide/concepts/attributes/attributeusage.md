---
title: Użycie atrybutu (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61668721"
---
# <a name="attributeusage-c"></a><span data-ttu-id="9d46d-102">Użycie atrybutu (C#)</span><span class="sxs-lookup"><span data-stu-id="9d46d-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="9d46d-103">Określa sposób użycia niestandardowej klasy atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9d46d-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="9d46d-104"><xref:System.AttributeUsageAttribute>jest atrybutem stosowanym do definicji atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9d46d-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="9d46d-105">Atrybut `AttributeUsage` umożliwia sterowanie:</span><span class="sxs-lookup"><span data-stu-id="9d46d-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="9d46d-106">Do którego atrybutu elementów programu można zastosować.</span><span class="sxs-lookup"><span data-stu-id="9d46d-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="9d46d-107">O ile nie ograniczysz jego użycia, atrybut może zostać zastosowany do jednego z następujących elementów programu:</span><span class="sxs-lookup"><span data-stu-id="9d46d-107">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="9d46d-108">zestaw</span><span class="sxs-lookup"><span data-stu-id="9d46d-108">assembly</span></span>
  - <span data-ttu-id="9d46d-109">moduł</span><span class="sxs-lookup"><span data-stu-id="9d46d-109">module</span></span>
  - <span data-ttu-id="9d46d-110">pole</span><span class="sxs-lookup"><span data-stu-id="9d46d-110">field</span></span>
  - <span data-ttu-id="9d46d-111">event</span><span class="sxs-lookup"><span data-stu-id="9d46d-111">event</span></span>
  - <span data-ttu-id="9d46d-112">method</span><span class="sxs-lookup"><span data-stu-id="9d46d-112">method</span></span>
  - <span data-ttu-id="9d46d-113">Param</span><span class="sxs-lookup"><span data-stu-id="9d46d-113">param</span></span>
  - <span data-ttu-id="9d46d-114">property</span><span class="sxs-lookup"><span data-stu-id="9d46d-114">property</span></span>
  - <span data-ttu-id="9d46d-115">return</span><span class="sxs-lookup"><span data-stu-id="9d46d-115">return</span></span>
  - <span data-ttu-id="9d46d-116">type</span><span class="sxs-lookup"><span data-stu-id="9d46d-116">type</span></span>
- <span data-ttu-id="9d46d-117">Czy atrybut może być stosowany do jednego elementu programu wiele razy.</span><span class="sxs-lookup"><span data-stu-id="9d46d-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="9d46d-118">Czy atrybuty są dziedziczone przez klasy pochodne.</span><span class="sxs-lookup"><span data-stu-id="9d46d-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="9d46d-119">Ustawienia domyślne wyglądają jak w poniższym przykładzie po zastosowaniu jawnie:</span><span class="sxs-lookup"><span data-stu-id="9d46d-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="9d46d-120">W tym przykładzie `NewAttribute` klasy można zastosować do dowolnego obsługiwanego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="9d46d-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="9d46d-121">Ale może być stosowany tylko raz do każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="9d46d-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="9d46d-122">Atrybut jest dziedziczony przez klasy pochodne po zastosowaniu do klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="9d46d-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="9d46d-123"><xref:System.AttributeUsageAttribute.AllowMultiple> Argumenty <xref:System.AttributeUsageAttribute.Inherited> i są opcjonalne, więc następujący kod ma ten sam efekt:</span><span class="sxs-lookup"><span data-stu-id="9d46d-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="9d46d-124">Pierwszy <xref:System.AttributeUsageAttribute> argument musi być jeden lub <xref:System.AttributeTargets> więcej elementów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9d46d-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="9d46d-125">Wiele typów docelowych można połączyć razem z operatorem OR, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9d46d-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="9d46d-126">Począwszy od języka C# 7.3 atrybuty mogą być stosowane do właściwości lub pola zapasowego dla właściwości auto implemented.</span><span class="sxs-lookup"><span data-stu-id="9d46d-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="9d46d-127">Atrybut ma zastosowanie do właściwości, chyba `field` że określono specyfikator w atrybucie.</span><span class="sxs-lookup"><span data-stu-id="9d46d-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="9d46d-128">Oba przedstawiono w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9d46d-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="9d46d-129">Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple> argument `true`jest , a następnie wynikowy atrybut można zastosować więcej niż jeden raz do jednej jednostki, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9d46d-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="9d46d-130">W takim `MultiUseAttribute` przypadku można stosować wielokrotnie, `AllowMultiple` ponieważ `true`jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="9d46d-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="9d46d-131">Oba formaty wyświetlane do stosowania wielu atrybutów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="9d46d-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="9d46d-132">Jeśli <xref:System.AttributeUsageAttribute.Inherited> `false`jest , a następnie atrybut nie jest dziedziczony przez klasy pochodzące z klasy przypisanej.</span><span class="sxs-lookup"><span data-stu-id="9d46d-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="9d46d-133">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9d46d-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="9d46d-134">W tym `NonInheritedAttribute` przypadku nie jest `DClass` stosowany do poprzez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="9d46d-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d46d-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d46d-135">Remarks</span></span>

<span data-ttu-id="9d46d-136">Atrybut `AttributeUsage` jest atrybutem jednorazowego użytku — nie można go zastosować więcej niż jeden raz do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="9d46d-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="9d46d-137">`AttributeUsage`jest aliasem <xref:System.AttributeUsageAttribute>dla .</span><span class="sxs-lookup"><span data-stu-id="9d46d-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="9d46d-138">Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="9d46d-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="9d46d-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d46d-139">Example</span></span>

<span data-ttu-id="9d46d-140">W poniższym przykładzie przedstawiono <xref:System.AttributeUsageAttribute.Inherited> wpływ <xref:System.AttributeUsageAttribute.AllowMultiple> i <xref:System.AttributeUsageAttribute> argumenty do atrybutu i jak można wyliczyć atrybuty niestandardowe stosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="9d46d-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="9d46d-141">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9d46d-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="9d46d-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d46d-142">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="9d46d-143">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="9d46d-143">C# Programming Guide</span></span>](../..//index.md)
- [<span data-ttu-id="9d46d-144">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d46d-144">Attributes</span></span>](../../../..//standard/attributes/index.md)
- [<span data-ttu-id="9d46d-145">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="9d46d-145">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="9d46d-146">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d46d-146">Attributes</span></span>](index.md)
- [<span data-ttu-id="9d46d-147">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="9d46d-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="9d46d-148">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="9d46d-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
