---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 42a7035a9dae146ad7a303da41c83891e5e19ef8
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442025"
---
# <a name="attributes-c"></a><span data-ttu-id="0cef8-102">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="0cef8-102">Attributes (C#)</span></span>

<span data-ttu-id="0cef8-103">Atrybuty zawierają zaawansowaną metodą kojarzenia metadanych lub informacji deklaratywne, przy użyciu kodu (zestawy, typy, metody, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="0cef8-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="0cef8-104">Po atrybutu jest skojarzony z jednostką program, ten atrybut można wykonywać zapytania w czasie wykonywania za pomocą technikę o nazwie *odbicia*.</span><span class="sxs-lookup"><span data-stu-id="0cef8-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="0cef8-105">Aby uzyskać więcej informacji, zobacz [odbicia (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="0cef8-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="0cef8-106">Atrybuty mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="0cef8-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="0cef8-107">Atrybuty dodawania metadanych do programu.</span><span class="sxs-lookup"><span data-stu-id="0cef8-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="0cef8-108">*Metadane* obejmuje informacje dotyczące typów zdefiniowanych w programie.</span><span class="sxs-lookup"><span data-stu-id="0cef8-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="0cef8-109">Wszystkie zestawy .NET zawierają określony zestaw metadane opisujące typy i elementy członkowskie typu zdefiniowane w zestawie.</span><span class="sxs-lookup"><span data-stu-id="0cef8-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="0cef8-110">Możesz dodać atrybuty niestandardowe, aby określić dodatkowe informacje, która jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="0cef8-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="0cef8-111">Aby uzyskać więcej informacji znajduje się pozycja [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0cef8-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="0cef8-112">Jeden lub więcej atrybutów mogą dotyczyć całego zestawów, modułów lub mniejszych elementów programów, takich jak klasy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="0cef8-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="0cef8-113">Atrybuty można zaakceptować argumentów w taki sam sposób jak metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="0cef8-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="0cef8-114">Program można sprawdzić swój własny metadanych lub metadanych w innych programach przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="0cef8-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="0cef8-115">Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="0cef8-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="0cef8-116">Przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="0cef8-116">Using attributes</span></span>

<span data-ttu-id="0cef8-117">Atrybuty można umieścić w praktycznie dowolnej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="0cef8-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="0cef8-118">W C#, określ atrybut, umieszczając nazwę atrybutu, ujęte w nawiasy kwadratowe ([]) powyżej deklaracji jednostki, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="0cef8-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="0cef8-119">W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do stosowania szczególne właściwości do klasy:</span><span class="sxs-lookup"><span data-stu-id="0cef8-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="0cef8-120">Metody z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0cef8-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="0cef8-121">Więcej niż jeden atrybut można umieścić w deklaracji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="0cef8-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="0cef8-122">Niektóre atrybuty można określić więcej niż jeden raz dla danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="0cef8-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="0cef8-123">Na przykład multiuse — atrybut <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="0cef8-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="0cef8-124">Zgodnie z Konwencją wszystkie nazwy atrybutu kończą się wyrazem "Atrybut", aby odróżnić je od innych elementów w bibliotekach .NET.</span><span class="sxs-lookup"><span data-stu-id="0cef8-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="0cef8-125">Nie musisz jednak określić sufiks atrybutu, korzystając z atrybutów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0cef8-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="0cef8-126">Na przykład `[DllImport]` jest odpowiednikiem `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0cef8-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="0cef8-127">Parametry atrybutów</span><span class="sxs-lookup"><span data-stu-id="0cef8-127">Attribute parameters</span></span>

<span data-ttu-id="0cef8-128">Wiele atrybutów ma parametry, które mogą być pozycyjne, bez nazwy lub nazwane.</span><span class="sxs-lookup"><span data-stu-id="0cef8-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="0cef8-129">Wszystkie parametry pozycyjne musi być określona w określonej kolejności i nie może być pominięty.</span><span class="sxs-lookup"><span data-stu-id="0cef8-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="0cef8-130">Parametry nazwane są opcjonalne i może być określony w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="0cef8-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="0cef8-131">Parametry pozycyjne są określony jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="0cef8-131">Positional parameters are specified first.</span></span> <span data-ttu-id="0cef8-132">Na przykład te trzy atrybuty są równoważne:</span><span class="sxs-lookup"><span data-stu-id="0cef8-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="0cef8-133">Pierwszy parametr, nazwa biblioteki DLL jest pozycyjne i zawsze wykorzystasz; pozostałe o nazwie.</span><span class="sxs-lookup"><span data-stu-id="0cef8-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="0cef8-134">W tym przypadku nazwanych parametrów domyślna wartość to false, dzięki czemu można pominąć.</span><span class="sxs-lookup"><span data-stu-id="0cef8-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="0cef8-135">Parametry pozycyjne odpowiadają parametrom atrybut konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0cef8-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="0cef8-136">Nazwana lub opcjonalne parametry odnoszą się do właściwości lub pola atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0cef8-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="0cef8-137">Zajrzyj do dokumentacji atrybutu Aby uzyskać informacji o domyślnych wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="0cef8-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="0cef8-138">Docelowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="0cef8-138">Attribute targets</span></span>

<span data-ttu-id="0cef8-139">*Docelowej* atrybutu jest jednostki, której dotyczy ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="0cef8-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="0cef8-140">Na przykład atrybut mogą dotyczyć klasy, konkretną metodę lub całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0cef8-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="0cef8-141">Domyślnie atrybut stosuje się do elementu, który poprzedza.</span><span class="sxs-lookup"><span data-stu-id="0cef8-141">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="0cef8-142">Ale można także jawnie zidentyfikować, na przykład, czy atrybut jest stosowany do metody, lub jako parametr lub wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="0cef8-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="0cef8-143">Aby jawnie określić element docelowy atrybutu, użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="0cef8-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="0cef8-144">Lista możliwych `target` wartości zostały przedstawione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0cef8-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="0cef8-145">Wartość docelowa</span><span class="sxs-lookup"><span data-stu-id="0cef8-145">Target value</span></span>|<span data-ttu-id="0cef8-146">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="0cef8-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="0cef8-147">Cały zespół</span><span class="sxs-lookup"><span data-stu-id="0cef8-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="0cef8-148">Bieżącego zestawu modułu</span><span class="sxs-lookup"><span data-stu-id="0cef8-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="0cef8-149">Pole w klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="0cef8-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="0cef8-150">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="0cef8-150">Event</span></span>|
|`method`|<span data-ttu-id="0cef8-151">Metoda lub `get` i `set` Akcesory właściwości</span><span class="sxs-lookup"><span data-stu-id="0cef8-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="0cef8-152">Parametry metody lub `set` parametry metody dostępu właściwości</span><span class="sxs-lookup"><span data-stu-id="0cef8-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="0cef8-153">Właściwość</span><span class="sxs-lookup"><span data-stu-id="0cef8-153">Property</span></span>|
|`return`|<span data-ttu-id="0cef8-154">Zwraca wartość metody, właściwości indeksatora lub `get` metody dostępu właściwości</span><span class="sxs-lookup"><span data-stu-id="0cef8-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="0cef8-155">Struktury, klasy, interfejsu, enum lub delegata</span><span class="sxs-lookup"><span data-stu-id="0cef8-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="0cef8-156">Należy określić `field` wartość docelową, aby zastosować atrybut do pola pomocniczego utworzone dla [automatycznie implementowana właściwość](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="0cef8-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="0cef8-157">Poniższy przykład pokazuje, jak zastosować atrybutów do zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="0cef8-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="0cef8-158">Aby uzyskać więcej informacji, zobacz [atrybuty wspólne (C#)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0cef8-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="0cef8-159">Poniższy przykład pokazuje, jak zastosować atrybutów do metod i parametry metody, a metoda zwraca wartości w języku C#.</span><span class="sxs-lookup"><span data-stu-id="0cef8-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="0cef8-160">Niezależnie od tego, obiekty docelowe, na którym `ValidatedContract` zdefiniowano był prawidłowy, `return` docelowy musi być określona, nawet wtedy, gdy `ValidatedContract` zostały zdefiniowane w celu mają zastosowanie tylko do zwracania wartości.</span><span class="sxs-lookup"><span data-stu-id="0cef8-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="0cef8-161">Innymi słowy, kompilator nie będzie używać `AttributeUsage` informacje pozwalające rozwiązać niejednoznaczny atrybut elementów docelowych.</span><span class="sxs-lookup"><span data-stu-id="0cef8-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="0cef8-162">Aby uzyskać więcej informacji, zobacz [AttributeUsage (C#)](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="0cef8-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="0cef8-163">Najczęstsze zastosowania dla atrybutów</span><span class="sxs-lookup"><span data-stu-id="0cef8-163">Common uses for attributes</span></span>

<span data-ttu-id="0cef8-164">Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:</span><span class="sxs-lookup"><span data-stu-id="0cef8-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="0cef8-165">Oznaczanie metod za pomocą `WebMethod` atrybutów w usługach sieci Web, aby wskazać, że metoda powinna być wywoływane za pośrednictwem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="0cef8-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="0cef8-166">Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0cef8-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="0cef8-167">Opisujących sposób organizowania parametry metody podczas współpracy z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="0cef8-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="0cef8-168">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0cef8-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="0cef8-169">Opisujących właściwości modelu COM dla klasy, metody i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="0cef8-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="0cef8-170">Wywoływanie niezarządzanego kodu za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="0cef8-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="0cef8-171">Opisujące zestaw pod względem tytułu, wersji, opis lub znak towarowy.</span><span class="sxs-lookup"><span data-stu-id="0cef8-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="0cef8-172">Opisujących członków klasy do serializacji na potrzeby stanu trwałego.</span><span class="sxs-lookup"><span data-stu-id="0cef8-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="0cef8-173">Opisujących sposób mapowania między elementy członkowskie klasy i węzłów XML do serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="0cef8-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="0cef8-174">Opisujących wymagania dotyczące zabezpieczeń dla metod.</span><span class="sxs-lookup"><span data-stu-id="0cef8-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="0cef8-175">Określanie właściwości używane do wymuszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0cef8-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="0cef8-176">Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), dzięki czemu kod pozostaje ułatwia debugowanie.</span><span class="sxs-lookup"><span data-stu-id="0cef8-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="0cef8-177">Uzyskiwanie informacji o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="0cef8-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="0cef8-178">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0cef8-178">Related sections</span></span>

<span data-ttu-id="0cef8-179">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="0cef8-179">For more information, see:</span></span>

- [<span data-ttu-id="0cef8-180">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="0cef8-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="0cef8-181">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="0cef8-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="0cef8-182">Instrukcje: Tworzenie złożenia C/C++ za pomocą atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="0cef8-182">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="0cef8-183">Atrybuty wspólne (C#)</span><span class="sxs-lookup"><span data-stu-id="0cef8-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="0cef8-184">Informacje o wywołującym (C#)</span><span class="sxs-lookup"><span data-stu-id="0cef8-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="0cef8-185">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cef8-185">See also</span></span>

- [<span data-ttu-id="0cef8-186">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0cef8-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="0cef8-187">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="0cef8-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="0cef8-188">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0cef8-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="0cef8-189">Przy użyciu atrybutów w języku C#</span><span class="sxs-lookup"><span data-stu-id="0cef8-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
