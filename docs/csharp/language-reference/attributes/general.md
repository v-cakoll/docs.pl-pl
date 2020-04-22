---
title: 'Atrybuty zastrzeżone języka C#: Warunkowe, Przestarzałe, AtrybutUsage'
ms.date: 04/09/2020
description: Te atrybuty są interpretowane przez kompilator w celu wpłyć na kod wygenerowany przez kompilator
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021760"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a><span data-ttu-id="77413-103">Atrybuty zastrzeżone: Atrybut warunkowyattribute, Przestarzały atrybut, AtrybutUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="77413-103">Reserved attributes: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute</span></span>

<span data-ttu-id="77413-104">Te atrybuty mogą być stosowane do elementów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="77413-104">These attributes can be applied to elements in your code.</span></span> <span data-ttu-id="77413-105">Dodają one znaczenie semantyczne do tych elementów.</span><span class="sxs-lookup"><span data-stu-id="77413-105">They add semantic meaning to those elements.</span></span> <span data-ttu-id="77413-106">Kompilator używa tych znaczeń semantycznych, aby zmienić jego dane wyjściowe i zgłosić możliwe błędy przez deweloperów przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="77413-106">The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.</span></span>

## <a name="conditional-attribute"></a><span data-ttu-id="77413-107">Atrybut `Conditional`</span><span class="sxs-lookup"><span data-stu-id="77413-107">`Conditional` attribute</span></span>

<span data-ttu-id="77413-108">Atrybut `Conditional` sprawia, że wykonanie metody zależy od identyfikatora przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="77413-108">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="77413-109">Atrybut `Conditional` jest aliasem <xref:System.Diagnostics.ConditionalAttribute>dla , i może być stosowany do metody lub klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77413-109">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="77413-110">W poniższym `Conditional` przykładzie jest stosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych specyficznych dla programu:</span><span class="sxs-lookup"><span data-stu-id="77413-110">In the following example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

<span data-ttu-id="77413-111">Jeśli `TRACE_ON` identyfikator nie jest zdefiniowany, dane wyjściowe śledzenia nie są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="77413-111">If the `TRACE_ON` identifier isn't defined, the trace output isn't displayed.</span></span> <span data-ttu-id="77413-112">Poznaj się w interaktywnym oknie.</span><span class="sxs-lookup"><span data-stu-id="77413-112">Explore for yourself in the interactive window.</span></span>

<span data-ttu-id="77413-113">Atrybut `Conditional` jest często używany `DEBUG` z identyfikatorem, aby włączyć śledzenie i rejestrowanie funkcji dla kompilacji debugowania, ale nie w kompilacjach wersji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="77413-113">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

<span data-ttu-id="77413-114">Gdy wywoływana jest metoda oznaczona warunkowo, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie zostało uwzględnione, czy pominięte.</span><span class="sxs-lookup"><span data-stu-id="77413-114">When a method marked conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="77413-115">Jeśli symbol jest zdefiniowany, wywołanie jest włączone; w przeciwnym razie wywołanie zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="77413-115">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="77413-116">Metoda warunkowa musi być metodą w deklaracji klasy lub `void` struktury i musi mieć typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="77413-116">A conditional method must be a method in a class or struct declaration and must have a `void` return type.</span></span> <span data-ttu-id="77413-117">Używanie `Conditional` jest czystsze, bardziej eleganckie i mniej `#if…#endif` podatne na błędy niż załączanie metod wewnątrz bloków.</span><span class="sxs-lookup"><span data-stu-id="77413-117">Using `Conditional` is cleaner, more elegant, and less error-prone than enclosing methods inside `#if…#endif` blocks.</span></span>

<span data-ttu-id="77413-118">Jeśli metoda ma `Conditional` wiele atrybutów, wywołanie metody jest uwzględniane, jeśli w jednym lub więcej symboli warunkowych jest zdefiniowany (symbole są logicznie połączone ze sobą za pomocą operatora OR).</span><span class="sxs-lookup"><span data-stu-id="77413-118">If a method has multiple `Conditional` attributes, a call to the method is included if at one or more conditional symbols is defined (the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="77413-119">W poniższym przykładzie obecność `A` albo `B` powoduje wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="77413-119">In the following example, the presence of either `A` or `B` results in a method call:</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="77413-120">Używanie `Conditional` z klasami atrybutów</span><span class="sxs-lookup"><span data-stu-id="77413-120">Using `Conditional` with attribute classes</span></span>

<span data-ttu-id="77413-121">Atrybut `Conditional` można również zastosować do definicji klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77413-121">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="77413-122">W poniższym przykładzie atrybut `Documentation` niestandardowy doda informacje do `DEBUG` metadanych tylko wtedy, gdy jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="77413-122">In the following example, the custom attribute `Documentation` will only add information to the metadata if `DEBUG` is defined.</span></span>

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a><span data-ttu-id="77413-123">Atrybut `Obsolete`</span><span class="sxs-lookup"><span data-stu-id="77413-123">`Obsolete` attribute</span></span>

<span data-ttu-id="77413-124">Atrybut `Obsolete` oznacza element kodu jako nie jest już zalecane do użycia.</span><span class="sxs-lookup"><span data-stu-id="77413-124">The `Obsolete` attribute marks a code element as no longer recommended for use.</span></span> <span data-ttu-id="77413-125">Użycie jednostki oznaczonej jako przestarzałe generuje ostrzeżenie lub błąd.</span><span class="sxs-lookup"><span data-stu-id="77413-125">Use of an entity marked obsolete generates a warning or an error.</span></span> <span data-ttu-id="77413-126">Atrybut `Obsolete` jest atrybutem jednorazowego użytku i może być stosowany do dowolnej jednostki, która zezwala na atrybuty.</span><span class="sxs-lookup"><span data-stu-id="77413-126">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="77413-127">`Obsolete`jest aliasem <xref:System.ObsoleteAttribute>dla .</span><span class="sxs-lookup"><span data-stu-id="77413-127">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

<span data-ttu-id="77413-128">W poniższym `Obsolete` przykładzie atrybut jest `A` stosowany do `B.OldMethod`klasy i metody .</span><span class="sxs-lookup"><span data-stu-id="77413-128">In the following example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="77413-129">Ponieważ drugi argument konstruktora atrybutów `B.OldMethod` stosowane `true`do jest ustawiona na , ta metoda `A` spowoduje błąd kompilatora, natomiast przy użyciu klasy po prostu wywoła ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="77413-129">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="77413-130">Wywołanie `B.NewMethod`, jednak nie generuje żadnego ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="77413-130">Calling `B.NewMethod`, however, produces no warning or error.</span></span> <span data-ttu-id="77413-131">Na przykład podczas korzystania z poprzednich definicji, następujący kod generuje dwa ostrzeżenia i jeden błąd:</span><span class="sxs-lookup"><span data-stu-id="77413-131">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

<span data-ttu-id="77413-132">Ciąg podany jako pierwszy argument do konstruktora atrybutów będą wyświetlane jako część ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="77413-132">The string provided as the first argument to the attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="77413-133">Generowane są `A` dwa ostrzeżenia dla klasy: jeden dla deklaracji odwołania do klasy i jeden dla konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="77413-133">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span> <span data-ttu-id="77413-134">Atrybut `Obsolete` może służyć bez argumentów, ale oprócz wyjaśnienia, co należy użyć zamiast tego jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="77413-134">The `Obsolete` attribute can be used without arguments, but including an explanation what to use instead is recommended.</span></span>

## <a name="attributeusage-attribute"></a><span data-ttu-id="77413-135">Atrybut `AttributeUsage`</span><span class="sxs-lookup"><span data-stu-id="77413-135">`AttributeUsage` attribute</span></span>

<span data-ttu-id="77413-136">Atrybut `AttributeUsage` określa, jak można użyć niestandardowej klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77413-136">The `AttributeUsage` attribute determines how a custom attribute class can be used.</span></span> <span data-ttu-id="77413-137"><xref:System.AttributeUsageAttribute>jest atrybutem stosowanym do definicji atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="77413-137"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="77413-138">Atrybut `AttributeUsage` umożliwia sterowanie:</span><span class="sxs-lookup"><span data-stu-id="77413-138">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="77413-139">Do którego atrybutu elementów programu można zastosować.</span><span class="sxs-lookup"><span data-stu-id="77413-139">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="77413-140">Jeśli nie ograniczysz jego użycia, atrybut może zostać zastosowany do dowolnego z następujących elementów programu:</span><span class="sxs-lookup"><span data-stu-id="77413-140">Unless you restrict its usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="77413-141">zestaw</span><span class="sxs-lookup"><span data-stu-id="77413-141">assembly</span></span>
  - <span data-ttu-id="77413-142">moduł</span><span class="sxs-lookup"><span data-stu-id="77413-142">module</span></span>
  - <span data-ttu-id="77413-143">pole</span><span class="sxs-lookup"><span data-stu-id="77413-143">field</span></span>
  - <span data-ttu-id="77413-144">event</span><span class="sxs-lookup"><span data-stu-id="77413-144">event</span></span>
  - <span data-ttu-id="77413-145">method</span><span class="sxs-lookup"><span data-stu-id="77413-145">method</span></span>
  - <span data-ttu-id="77413-146">Param</span><span class="sxs-lookup"><span data-stu-id="77413-146">param</span></span>
  - <span data-ttu-id="77413-147">property</span><span class="sxs-lookup"><span data-stu-id="77413-147">property</span></span>
  - <span data-ttu-id="77413-148">return</span><span class="sxs-lookup"><span data-stu-id="77413-148">return</span></span>
  - <span data-ttu-id="77413-149">type</span><span class="sxs-lookup"><span data-stu-id="77413-149">type</span></span>
- <span data-ttu-id="77413-150">Czy atrybut może być stosowany do pojedynczego elementu programu wiele razy.</span><span class="sxs-lookup"><span data-stu-id="77413-150">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="77413-151">Czy atrybuty są dziedziczone przez klasy pochodne.</span><span class="sxs-lookup"><span data-stu-id="77413-151">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="77413-152">Ustawienia domyślne wyglądają jak w poniższym przykładzie, gdy są wyraźnie stosowane:</span><span class="sxs-lookup"><span data-stu-id="77413-152">The default settings look like the following example when applied explicitly:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

<span data-ttu-id="77413-153">W tym przykładzie `NewAttribute` klasy można zastosować do dowolnego obsługiwanego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="77413-153">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="77413-154">Ale może być stosowany tylko raz do każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="77413-154">But it can be applied only once to each entity.</span></span> <span data-ttu-id="77413-155">Atrybut jest dziedziczony przez klasy pochodne po zastosowaniu do klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="77413-155">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="77413-156">Argumenty <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> i są opcjonalne, więc następujący kod ma ten sam efekt:</span><span class="sxs-lookup"><span data-stu-id="77413-156">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

<span data-ttu-id="77413-157">Pierwszy <xref:System.AttributeUsageAttribute> argument musi być co najmniej <xref:System.AttributeTargets> jeden element wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="77413-157">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="77413-158">Wiele typów docelowych można połączyć z operatorem OR, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="77413-158">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

<span data-ttu-id="77413-159">Począwszy od języka C# 7.3, atrybuty mogą być stosowane do właściwości lub pola zapasowego dla właściwości automatycznie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="77413-159">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="77413-160">Atrybut ma zastosowanie do właściwości, chyba `field` że określisz specyfikator atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77413-160">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="77413-161">Oba są pokazane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="77413-161">Both are shown in the following example:</span></span>

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

<span data-ttu-id="77413-162">Jeśli <xref:System.AttributeUsageAttribute.AllowMultiple> argument `true`jest , wynikowy atrybut może być stosowany więcej niż jeden raz do pojedynczej jednostki, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="77413-162">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

<span data-ttu-id="77413-163">W takim `MultiUseAttribute` przypadku można zastosować wielokrotnie, `AllowMultiple` ponieważ `true`jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="77413-163">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="77413-164">Oba formaty wyświetlane do stosowania wielu atrybutów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="77413-164">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="77413-165">Jeśli <xref:System.AttributeUsageAttribute.Inherited> `false`tak , atrybut nie jest dziedziczony przez klasy pochodzące z przypisanej klasy.</span><span class="sxs-lookup"><span data-stu-id="77413-165">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="77413-166">Przykład:</span><span class="sxs-lookup"><span data-stu-id="77413-166">For example:</span></span>

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

<span data-ttu-id="77413-167">W tym `NonInheritedAttribute` przypadku nie jest `DClass` stosowany do za pośrednictwem dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="77413-167">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="see-also"></a><span data-ttu-id="77413-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77413-168">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="77413-169">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="77413-169">Attributes</span></span>](../../../standard/attributes/index.md)
- [<span data-ttu-id="77413-170">Odbicie</span><span class="sxs-lookup"><span data-stu-id="77413-170">Reflection</span></span>](../../programming-guide/concepts/reflection.md)
