---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33955931"
---
# <a name="attributeusage-c"></a><span data-ttu-id="7a337-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="7a337-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="7a337-103">Określa sposób użycia klasy atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="7a337-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="7a337-104"><xref:System.AttributeUsageAttribute> jest stosowany do definicji atrybutu niestandardowego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7a337-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="7a337-105">`AttributeUsage` Atrybutu umożliwia kontrolowanie:</span><span class="sxs-lookup"><span data-stu-id="7a337-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="7a337-106">Atrybut, którego elementy program może być stosowany do.</span><span class="sxs-lookup"><span data-stu-id="7a337-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="7a337-107">Jeśli nie ograniczysz jest użycie atrybutu może być stosowany do żadnego z następujących elementów programu:</span><span class="sxs-lookup"><span data-stu-id="7a337-107">Unless you restrict is usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="7a337-108">zestaw</span><span class="sxs-lookup"><span data-stu-id="7a337-108">assembly</span></span>
  - <span data-ttu-id="7a337-109">moduł</span><span class="sxs-lookup"><span data-stu-id="7a337-109">module</span></span>
  - <span data-ttu-id="7a337-110">pole</span><span class="sxs-lookup"><span data-stu-id="7a337-110">field</span></span>
  - <span data-ttu-id="7a337-111">zdarzenie</span><span class="sxs-lookup"><span data-stu-id="7a337-111">event</span></span>
  - <span data-ttu-id="7a337-112">— metoda</span><span class="sxs-lookup"><span data-stu-id="7a337-112">method</span></span>
  - <span data-ttu-id="7a337-113">Param</span><span class="sxs-lookup"><span data-stu-id="7a337-113">param</span></span>
  - <span data-ttu-id="7a337-114">property</span><span class="sxs-lookup"><span data-stu-id="7a337-114">property</span></span>
  - <span data-ttu-id="7a337-115">return</span><span class="sxs-lookup"><span data-stu-id="7a337-115">return</span></span>
  - <span data-ttu-id="7a337-116">— typ</span><span class="sxs-lookup"><span data-stu-id="7a337-116">type</span></span>
- <span data-ttu-id="7a337-117">Określa, czy atrybut można stosować do jednego elementu programu wiele razy.</span><span class="sxs-lookup"><span data-stu-id="7a337-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="7a337-118">Określa, czy atrybuty są dziedziczone przez klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="7a337-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="7a337-119">Ustawienia domyślne wyglądać jak w następującym przykładzie jawnie stosowania:</span><span class="sxs-lookup"><span data-stu-id="7a337-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="7a337-120">W tym przykładzie `NewAttribute` klasy mogą być stosowane do dowolnego elementu obsługiwanych programu.</span><span class="sxs-lookup"><span data-stu-id="7a337-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="7a337-121">Ale można go zastosować tylko raz do każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="7a337-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="7a337-122">Ten atrybut jest dziedziczona przez klas pochodnych po zastosowaniu do klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="7a337-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="7a337-123"><xref:System.AttributeUsageAttribute.AllowMultiple> i <xref:System.AttributeUsageAttribute.Inherited> argumenty są opcjonalne, dzięki czemu następujący kod mają ten sam efekt:</span><span class="sxs-lookup"><span data-stu-id="7a337-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="7a337-124">Pierwszy <xref:System.AttributeUsageAttribute> argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7a337-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="7a337-125">Wiele typów docelowy może odnosić się wraz z operatora OR, podobnie jak w poniższym przykładzie przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="7a337-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="7a337-126">Począwszy od 7.3 C#, atrybuty można zastosować do właściwość lub pole zapasowe dla automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="7a337-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="7a337-127">Ten atrybut ma zastosowanie do właściwości, chyba że zostanie `field` Specyfikator atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7a337-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="7a337-128">W poniższym przykładzie przedstawiono zarówno:</span><span class="sxs-lookup"><span data-stu-id="7a337-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="7a337-129">Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple> argument jest `true`, a następnie wynikowy atrybut można stosować więcej niż raz do jednej jednostki, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7a337-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="7a337-130">W takim przypadku `MultiUseAttribute` może odnosić się wielokrotnie ponieważ `AllowMultiple` ma ustawioną wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="7a337-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="7a337-131">Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="7a337-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="7a337-132">Jeśli <xref:System.AttributeUsageAttribute.Inherited> jest `false`, a następnie ten atrybut nie jest dziedziczone przez klasy pochodnej z klasy oparte na atrybutach.</span><span class="sxs-lookup"><span data-stu-id="7a337-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="7a337-133">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7a337-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="7a337-134">W takim przypadku `NonInheritedAttribute` nie jest stosowana do `DClass` za pośrednictwem dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="7a337-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a337-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a337-135">Remarks</span></span>

<span data-ttu-id="7a337-136">`AttributeUsage` Jest atrybutem jednorazowy — nie można zastosować w więcej niż raz do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="7a337-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="7a337-137">`AttributeUsage` alias jest <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7a337-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="7a337-138">Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="7a337-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="7a337-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a337-139">Example</span></span>

<span data-ttu-id="7a337-140">Poniższy przykład ilustruje efekt <xref:System.AttributeUsageAttribute.Inherited> i <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty <xref:System.AttributeUsageAttribute> atrybut i jak mogą być wyliczane atrybuty niestandardowe zastosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="7a337-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="7a337-141">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7a337-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="7a337-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a337-142">See Also</span></span>
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="7a337-143">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7a337-143">C# Programming Guide</span></span>](../..//index.md)  
 [<span data-ttu-id="7a337-144">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a337-144">Attributes</span></span>](../../../..//standard/attributes/index.md)  
 [<span data-ttu-id="7a337-145">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="7a337-145">Reflection (C#)</span></span>](../reflection.md)  
 [<span data-ttu-id="7a337-146">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a337-146">Attributes</span></span>](index.md)  
 [<span data-ttu-id="7a337-147">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="7a337-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
 [<span data-ttu-id="7a337-148">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="7a337-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
