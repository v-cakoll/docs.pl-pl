---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 081a8f6edcddd5e87d3d9750b91ff42a72b92886
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656352"
---
# <a name="attributeusage-c"></a><span data-ttu-id="41568-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="41568-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="41568-103">Określa, jak używać klasy atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="41568-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="41568-104"><xref:System.AttributeUsageAttribute> jest atrybutem stosowanych do definicji atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="41568-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="41568-105">`AttributeUsage` Atrybut umożliwia kontrolowanie:</span><span class="sxs-lookup"><span data-stu-id="41568-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="41568-106">Atrybut elementy programu, którego można stosować do.</span><span class="sxs-lookup"><span data-stu-id="41568-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="41568-107">Chyba, że możesz ograniczyć jego użycia, atrybut można stosować do dowolnej z następujących elementów programu:</span><span class="sxs-lookup"><span data-stu-id="41568-107">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="41568-108">zestaw</span><span class="sxs-lookup"><span data-stu-id="41568-108">assembly</span></span>
  - <span data-ttu-id="41568-109">moduł</span><span class="sxs-lookup"><span data-stu-id="41568-109">module</span></span>
  - <span data-ttu-id="41568-110">pole</span><span class="sxs-lookup"><span data-stu-id="41568-110">field</span></span>
  - <span data-ttu-id="41568-111">zdarzenie</span><span class="sxs-lookup"><span data-stu-id="41568-111">event</span></span>
  - <span data-ttu-id="41568-112">— metoda</span><span class="sxs-lookup"><span data-stu-id="41568-112">method</span></span>
  - <span data-ttu-id="41568-113">param</span><span class="sxs-lookup"><span data-stu-id="41568-113">param</span></span>
  - <span data-ttu-id="41568-114">property</span><span class="sxs-lookup"><span data-stu-id="41568-114">property</span></span>
  - <span data-ttu-id="41568-115">return</span><span class="sxs-lookup"><span data-stu-id="41568-115">return</span></span>
  - <span data-ttu-id="41568-116">— typ</span><span class="sxs-lookup"><span data-stu-id="41568-116">type</span></span>
- <span data-ttu-id="41568-117">Czy atrybut można stosować do jednego elementu programu wiele razy.</span><span class="sxs-lookup"><span data-stu-id="41568-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="41568-118">Czy atrybuty są dziedziczone przez klasy pochodne.</span><span class="sxs-lookup"><span data-stu-id="41568-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="41568-119">Ustawienia domyślne wyglądać jak w poniższym przykładzie, po zastosowaniu jawnie:</span><span class="sxs-lookup"><span data-stu-id="41568-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="41568-120">W tym przykładzie `NewAttribute` klasy mogą być stosowane do dowolnego elementu obsługiwany program.</span><span class="sxs-lookup"><span data-stu-id="41568-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="41568-121">Ale można go zastosować tylko raz do każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="41568-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="41568-122">Ten atrybut jest dziedziczone przez klasy pochodne, gdy jest stosowany do klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="41568-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="41568-123"><xref:System.AttributeUsageAttribute.AllowMultiple> i <xref:System.AttributeUsageAttribute.Inherited> argumenty są opcjonalne, więc poniższy kod działa tak samo:</span><span class="sxs-lookup"><span data-stu-id="41568-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="41568-124">Pierwszy <xref:System.AttributeUsageAttribute> argument musi być jeden lub więcej elementów <xref:System.AttributeTargets> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="41568-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="41568-125">Wiele typów docelowych, mogą być połączone wraz z operatorem OR, podobnie jak w poniższym przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="41568-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="41568-126">Począwszy od języka C# 7.3 można można zastosować atrybutów do właściwość lub pole zapasowe dla automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="41568-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="41568-127">Ten atrybut ma zastosowanie do właściwości, chyba że określisz `field` specyfikator w atrybucie.</span><span class="sxs-lookup"><span data-stu-id="41568-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="41568-128">Oba są wyświetlane w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="41568-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="41568-129">Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple> argument jest `true`, a następnie wynikowy atrybut można stosować więcej niż jeden raz do jednej jednostki, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="41568-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="41568-130">W tym przypadku `MultiUseAttribute` mogą być stosowane wielokrotnie, ponieważ `AllowMultiple` ustawiono `true`.</span><span class="sxs-lookup"><span data-stu-id="41568-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="41568-131">Obu formatów pokazano stosowania wiele atrybutów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="41568-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="41568-132">Jeśli <xref:System.AttributeUsageAttribute.Inherited> jest `false`, a następnie ten atrybut nie jest dziedziczone przez klasy pochodne od klas opartego na atrybutach.</span><span class="sxs-lookup"><span data-stu-id="41568-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="41568-133">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="41568-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="41568-134">W tym przypadku `NonInheritedAttribute` nie jest stosowane do `DClass` za pomocą dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="41568-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="41568-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41568-135">Remarks</span></span>

<span data-ttu-id="41568-136">`AttributeUsage` Atrybut jest atrybutem jednorazowy — nie można zastosować w więcej niż jeden raz do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="41568-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="41568-137">`AttributeUsage` jest aliasem <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="41568-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="41568-138">Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="41568-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="41568-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="41568-139">Example</span></span>

<span data-ttu-id="41568-140">Poniższy przykład ilustruje efekt <xref:System.AttributeUsageAttribute.Inherited> i <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty <xref:System.AttributeUsageAttribute> atrybut i jak mogą być wyliczane atrybuty niestandardowe zastosowane do klasy.</span><span class="sxs-lookup"><span data-stu-id="41568-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="41568-141">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="41568-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="41568-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41568-142">See Also</span></span>

- <xref:System.Attribute>  
- <xref:System.Reflection>  
- [<span data-ttu-id="41568-143">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="41568-143">C# Programming Guide</span></span>](../..//index.md)  
- [<span data-ttu-id="41568-144">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="41568-144">Attributes</span></span>](../../../..//standard/attributes/index.md)  
- [<span data-ttu-id="41568-145">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="41568-145">Reflection (C#)</span></span>](../reflection.md)  
- [<span data-ttu-id="41568-146">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="41568-146">Attributes</span></span>](index.md)  
- [<span data-ttu-id="41568-147">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="41568-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="41568-148">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="41568-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
