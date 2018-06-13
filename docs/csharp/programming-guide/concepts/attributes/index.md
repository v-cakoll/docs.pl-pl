---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: fe94f0ee778f14581fd7949f705cc22f12058b27
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956075"
---
# <a name="attributes-c"></a><span data-ttu-id="1b371-102">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="1b371-102">Attributes (C#)</span></span>

<span data-ttu-id="1b371-103">Atrybuty udostępnia zaawansowane metody kojarzenia metadanych lub deklaratywne informacji z kodu (zestawy, typy metod, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="1b371-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="1b371-104">Po atrybutu jest skojarzony z jednostką program, ten atrybut można tworzyć zapytania w czasie wykonywania przy użyciu techniki o nazwie *odbicia*.</span><span class="sxs-lookup"><span data-stu-id="1b371-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="1b371-105">Aby uzyskać więcej informacji, zobacz [odbicia (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="1b371-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="1b371-106">Atrybuty mieć następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1b371-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="1b371-107">Atrybuty dodawać metadane do programu.</span><span class="sxs-lookup"><span data-stu-id="1b371-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="1b371-108">*Metadane* znajdują się informacje o typy zdefiniowane w programie.</span><span class="sxs-lookup"><span data-stu-id="1b371-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="1b371-109">Wszystkie zestawy .NET zawierają określony zestaw metadanych, które opisują typy i elementy członkowskie typu zdefiniowany w zestawie.</span><span class="sxs-lookup"><span data-stu-id="1b371-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="1b371-110">Można dodawać atrybuty niestandardowe, aby określić dodatkowe informacje, które jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="1b371-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="1b371-111">Aby uzyskać więcej informacji zobacz, [tworzenie niestandardowe atrybuty (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1b371-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="1b371-112">Co najmniej jeden atrybut można stosować do całego zestawy, moduły lub mniejsze elementy programu, takich jak klasy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b371-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="1b371-113">Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b371-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="1b371-114">Program można sprawdzić jego własnej ani metadanych w programach przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="1b371-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="1b371-115">Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="1b371-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="1b371-116">Przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="1b371-116">Using attributes</span></span>

<span data-ttu-id="1b371-117">Atrybuty można umieścić w praktycznie dowolnej deklaracji, chociaż określony atrybut mogą ograniczać typów deklaracje, na których jest ona prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="1b371-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="1b371-118">W C# należy określić atrybut przez umieszczenie nazwy atrybutu ujęte w nawiasy kwadratowe ([]) powyżej deklaracji jednostki, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="1b371-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="1b371-119">W tym przykładzie <xref:System.SerializableAttribute> atrybut służy do stosowania określonej właściwości do klasy:</span><span class="sxs-lookup"><span data-stu-id="1b371-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="1b371-120">Metody z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> zadeklarowano jak w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1b371-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="1b371-121">Więcej niż jeden atrybut można umieścić w deklaracji, jak przedstawiono na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1b371-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="1b371-122">Niektóre atrybuty można określić więcej niż raz dla danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="1b371-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="1b371-123">Na przykład multiuse atrybutu <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="1b371-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="1b371-124">Według Konwencji wszystkich nazw atrybutów kończyć się wyrazem "Atrybutu", aby odróżnić je od innych elementów w bibliotekach .NET.</span><span class="sxs-lookup"><span data-stu-id="1b371-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="1b371-125">Nie trzeba jednak określić sufiks atrybutu przy użyciu atrybutów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b371-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="1b371-126">Na przykład `[DllImport]` jest odpowiednikiem `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b371-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="1b371-127">Parametry atrybutów</span><span class="sxs-lookup"><span data-stu-id="1b371-127">Attribute parameters</span></span>

<span data-ttu-id="1b371-128">Wiele atrybutów ma parametry, które mogą być pozycyjnych, bez nazwy lub nazwane.</span><span class="sxs-lookup"><span data-stu-id="1b371-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="1b371-129">Parametry pozycyjne musi być podana w odpowiedniej kolejności i nie można pominąć.</span><span class="sxs-lookup"><span data-stu-id="1b371-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="1b371-130">Nazwane parametry są opcjonalne i może zostać określony w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="1b371-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="1b371-131">Parametry pozycyjne są określony jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="1b371-131">Positional parameters are specified first.</span></span> <span data-ttu-id="1b371-132">Na przykład te trzy atrybuty są równoważne:</span><span class="sxs-lookup"><span data-stu-id="1b371-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="1b371-133">Pierwszy parametr Nazwa biblioteki DLL jest pozycyjnych i zawsze zostanie osiągnięty jako pierwszy; inne o nazwie.</span><span class="sxs-lookup"><span data-stu-id="1b371-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="1b371-134">W takim przypadku nazwanych parametrów domyślna wartość to false, więc można pominąć.</span><span class="sxs-lookup"><span data-stu-id="1b371-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="1b371-135">Parametry pozycyjne odpowiadają parametry konstruktora atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1b371-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="1b371-136">Parametry nazwane i opcjonalne odpowiada właściwości lub pola atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1b371-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="1b371-137">Zajrzyj do dokumentacji poszczególne atrybuty, aby uzyskać informacje dotyczące domyślne wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="1b371-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="1b371-138">Docelowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b371-138">Attribute targets</span></span>

<span data-ttu-id="1b371-139">*Docelowej* atrybutu jest jednostki, której dotyczy ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="1b371-139">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="1b371-140">Na przykład atrybut mogą stosować do klasy, konkretnej metody lub całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1b371-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="1b371-141">Domyślnie atrybut dotyczy poprzedza element.</span><span class="sxs-lookup"><span data-stu-id="1b371-141">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="1b371-142">Ale można również jawnie określić, na przykład, czy atrybut jest stosowany do metody, lub jej parametr albo jego wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="1b371-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="1b371-143">Aby jawnie określić obiekt docelowy atrybutu, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="1b371-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="1b371-144">Lista możliwości `target` w poniższej tabeli przedstawiono wartości.</span><span class="sxs-lookup"><span data-stu-id="1b371-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="1b371-145">Wartość docelowa</span><span class="sxs-lookup"><span data-stu-id="1b371-145">Target value</span></span>|<span data-ttu-id="1b371-146">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="1b371-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="1b371-147">Całego zestawu</span><span class="sxs-lookup"><span data-stu-id="1b371-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="1b371-148">Bieżący modułu zestawu</span><span class="sxs-lookup"><span data-stu-id="1b371-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="1b371-149">Pole w klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="1b371-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="1b371-150">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="1b371-150">Event</span></span>|
|`method`|<span data-ttu-id="1b371-151">Metoda lub `get` i `set` metod dostępu do właściwości</span><span class="sxs-lookup"><span data-stu-id="1b371-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="1b371-152">Parametry metody lub `set` parametry metody dostępu właściwości</span><span class="sxs-lookup"><span data-stu-id="1b371-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="1b371-153">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1b371-153">Property</span></span>|
|`return`|<span data-ttu-id="1b371-154">Zwraca wartość metody, właściwości indeksatora lub `get` metody dostępu właściwości</span><span class="sxs-lookup"><span data-stu-id="1b371-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="1b371-155">Struktury, klasy, interface, enum lub delegate</span><span class="sxs-lookup"><span data-stu-id="1b371-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="1b371-156">Należy określić `field` wartości docelowej, aby zastosować atrybut do pole zapasowe utworzone dla [automatycznie implementowana właściwość](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="1b371-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="1b371-157">Poniższy przykład pokazuje, jak można zastosować atrybutów do zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="1b371-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="1b371-158">Aby uzyskać więcej informacji, zobacz [takie same atrybuty wspólne (C#)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1b371-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="1b371-159">Poniższy przykład przedstawia sposób zastosować atrybutów do metod, parametrów metod i metody zwracają wartości w języku C#.</span><span class="sxs-lookup"><span data-stu-id="1b371-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="1b371-160">Niezależnie od celów, na którym `ValidatedContract` zdefiniowano był prawidłowy, `return` docelowy musi być określony, nawet jeśli `ValidatedContract` zostały zdefiniowane do stosowania tylko dla wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="1b371-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="1b371-161">Innymi słowy, kompilator nie będzie używać `AttributeUsage` informacje umożliwiające rozwiązanie docelowe atrybuty niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="1b371-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="1b371-162">Aby uzyskać więcej informacji, zobacz [AttributeUsage (C#)](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="1b371-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="1b371-163">Najczęstsze zastosowania dla atrybutów</span><span class="sxs-lookup"><span data-stu-id="1b371-163">Common uses for attributes</span></span>

<span data-ttu-id="1b371-164">Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:</span><span class="sxs-lookup"><span data-stu-id="1b371-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="1b371-165">Oznaczanie za pomocą metody `WebMethod` atrybutów w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="1b371-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="1b371-166">Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1b371-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="1b371-167">Zawierająca opis sposobu zorganizowania parametrów metody podczas współpracy z kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="1b371-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="1b371-168">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1b371-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="1b371-169">Opisujących właściwości modelu COM dla klas, metod i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="1b371-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="1b371-170">Wywoływanie niezarządzanych w kodzie za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="1b371-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="1b371-171">Opisujące używanemu zestawowi pod względem tytułu, wersji, opis lub znakiem towarowym.</span><span class="sxs-lookup"><span data-stu-id="1b371-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="1b371-172">Opisujące członków klasy do serializacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="1b371-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="1b371-173">Opisujących sposób mapowania między elementami członkowskimi klas i węzłów XML do serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="1b371-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="1b371-174">Opisujących wymagania dotyczące zabezpieczeń dla metod.</span><span class="sxs-lookup"><span data-stu-id="1b371-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="1b371-175">Określanie właściwości używanych do wymuszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1b371-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="1b371-176">Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), kod jest łatwy do debugowania.</span><span class="sxs-lookup"><span data-stu-id="1b371-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="1b371-177">Uzyskiwanie informacji o elemencie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="1b371-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1b371-178">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1b371-178">Related sections</span></span>

<span data-ttu-id="1b371-179">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="1b371-179">For more information, see:</span></span>

- [<span data-ttu-id="1b371-180">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="1b371-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="1b371-181">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="1b371-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="1b371-182">Porady: tworzenie złożenia C/C++ za pomocą atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="1b371-182">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="1b371-183">Atrybuty wspólne (C#)</span><span class="sxs-lookup"><span data-stu-id="1b371-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="1b371-184">Informacje o wywołującym (C#)</span><span class="sxs-lookup"><span data-stu-id="1b371-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="1b371-185">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b371-185">See also</span></span>

 [<span data-ttu-id="1b371-186">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1b371-186">C# Programming Guide</span></span>](../../index.md)  
 [<span data-ttu-id="1b371-187">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="1b371-187">Reflection (C#)</span></span>](../reflection.md)  
 [<span data-ttu-id="1b371-188">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b371-188">Attributes</span></span>](../../../../standard/attributes/index.md)  
 [<span data-ttu-id="1b371-189">Przy użyciu atrybutów w języku C#</span><span class="sxs-lookup"><span data-stu-id="1b371-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)  
