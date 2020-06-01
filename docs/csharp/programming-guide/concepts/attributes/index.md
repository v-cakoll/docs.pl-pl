---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 358285a39f72ad3ddf1b265e20b443308375d074
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241581"
---
# <a name="attributes-c"></a><span data-ttu-id="ee452-102">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="ee452-102">Attributes (C#)</span></span>

<span data-ttu-id="ee452-103">Atrybuty zapewniają zaawansowaną metodę kojarzenia metadanych lub deklaracyjne informacje z kodem (zestawy, typy, metody, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="ee452-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="ee452-104">Gdy atrybut jest skojarzony z jednostką programu, atrybut może być badany w czasie wykonywania przy użyciu techniki o nazwie *odbicie*.</span><span class="sxs-lookup"><span data-stu-id="ee452-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="ee452-105">Aby uzyskać więcej informacji, zobacz [odbicie (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="ee452-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="ee452-106">Atrybuty mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ee452-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="ee452-107">Atrybuty dodają metadane do programu.</span><span class="sxs-lookup"><span data-stu-id="ee452-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="ee452-108">*Metadane* są informacjami o typach zdefiniowanych w programie.</span><span class="sxs-lookup"><span data-stu-id="ee452-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="ee452-109">Wszystkie zestawy .NET zawierają określony zestaw metadanych opisujący typy i elementy członkowskie typu zdefiniowane w zestawie.</span><span class="sxs-lookup"><span data-stu-id="ee452-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="ee452-110">Można dodać atrybuty niestandardowe, aby określić wszelkie dodatkowe informacje, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="ee452-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="ee452-111">Aby uzyskać więcej informacji, zobacz temat [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ee452-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="ee452-112">Można zastosować jeden lub więcej atrybutów do całych zestawów, modułów lub mniejszych elementów programu, takich jak klasy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="ee452-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="ee452-113">Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="ee452-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="ee452-114">Program może przeanalizować własne metadane lub metadane w innych programach przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="ee452-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="ee452-115">Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="ee452-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="ee452-116">Używanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="ee452-116">Using attributes</span></span>

<span data-ttu-id="ee452-117">Atrybuty mogą być umieszczane w większości każdej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ee452-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="ee452-118">W języku C# należy określić atrybut poprzez umieszczenie nazwy atrybutu w nawiasach kwadratowych ([]) powyżej deklaracji jednostki, do której ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="ee452-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="ee452-119">W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do zastosowania konkretnej cechy klasy:</span><span class="sxs-lookup"><span data-stu-id="ee452-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="ee452-120">Metoda z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ee452-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="ee452-121">Więcej niż jeden atrybut może być umieszczony w deklaracji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ee452-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="ee452-122">Niektóre atrybuty można określić więcej niż raz dla danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="ee452-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="ee452-123">Przykładem takiego atrybutu Multiuse jest <xref:System.Diagnostics.ConditionalAttribute> :</span><span class="sxs-lookup"><span data-stu-id="ee452-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="ee452-124">Według Konwencji wszystkie nazwy atrybutów kończą się słowem "Attribute", aby odróżnić je od innych elementów w bibliotekach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ee452-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="ee452-125">Nie trzeba jednak określać sufiksu atrybutu podczas używania atrybutów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ee452-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="ee452-126">Na przykład `[DllImport]` jest równoważne z `[DllImportAttribute]` , ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="ee452-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="ee452-127">Parametry atrybutu</span><span class="sxs-lookup"><span data-stu-id="ee452-127">Attribute parameters</span></span>

<span data-ttu-id="ee452-128">Wiele atrybutów ma parametry, które mogą mieć położenie, nienazwane lub nazwane.</span><span class="sxs-lookup"><span data-stu-id="ee452-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="ee452-129">Wszystkie parametry pozycyjne muszą być określone w określonej kolejności i nie mogą być pominięte.</span><span class="sxs-lookup"><span data-stu-id="ee452-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="ee452-130">Parametry nazwane są opcjonalne i można je określić w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="ee452-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="ee452-131">Parametry pozycyjne są określone jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="ee452-131">Positional parameters are specified first.</span></span> <span data-ttu-id="ee452-132">Na przykład te trzy atrybuty są równoważne:</span><span class="sxs-lookup"><span data-stu-id="ee452-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="ee452-133">Pierwszy parametr, nazwa biblioteki DLL, jest położeniem i zawsze jest pierwszy. inne osoby mają nazwę.</span><span class="sxs-lookup"><span data-stu-id="ee452-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="ee452-134">W tym przypadku oba nazwane parametry domyślnie mają wartość false, więc można je pominąć.</span><span class="sxs-lookup"><span data-stu-id="ee452-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="ee452-135">Parametry pozycyjne odpowiadają parametrom konstruktora atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ee452-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="ee452-136">Parametry nazwane lub opcjonalne odpowiadają właściwościom lub polom atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ee452-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="ee452-137">Informacje dotyczące domyślnych wartości parametrów można znaleźć w dokumentacji poszczególnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="ee452-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="ee452-138">Docelowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee452-138">Attribute targets</span></span>

<span data-ttu-id="ee452-139">*Obiektem docelowym* atrybutu jest jednostka, do której odnosi się ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="ee452-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="ee452-140">Na przykład, atrybut może dotyczyć klasy, konkretnej metody lub całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee452-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="ee452-141">Domyślnie atrybut ma zastosowanie do elementu, który następuje po nim.</span><span class="sxs-lookup"><span data-stu-id="ee452-141">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="ee452-142">Ale można również jawnie określić, na przykład, czy atrybut jest stosowany do metody lub do jego parametru lub do jego wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="ee452-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="ee452-143">Aby jawnie zidentyfikować obiekt docelowy atrybutu, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="ee452-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="ee452-144">Lista możliwych `target` wartości jest pokazana w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ee452-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="ee452-145">Wartość docelowa</span><span class="sxs-lookup"><span data-stu-id="ee452-145">Target value</span></span>|<span data-ttu-id="ee452-146">Dotyczy</span><span class="sxs-lookup"><span data-stu-id="ee452-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="ee452-147">Cały zestaw</span><span class="sxs-lookup"><span data-stu-id="ee452-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="ee452-148">Bieżący moduł zestawu</span><span class="sxs-lookup"><span data-stu-id="ee452-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="ee452-149">Pole w klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="ee452-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="ee452-150">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ee452-150">Event</span></span>|
|`method`|<span data-ttu-id="ee452-151">Metody dostępu metod lub `get` `set` właściwości</span><span class="sxs-lookup"><span data-stu-id="ee452-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="ee452-152">Parametry metody lub `set` parametry metod dostępu do właściwości</span><span class="sxs-lookup"><span data-stu-id="ee452-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="ee452-153">Właściwość</span><span class="sxs-lookup"><span data-stu-id="ee452-153">Property</span></span>|
|`return`|<span data-ttu-id="ee452-154">Wartość zwracana metody, indeksatora właściwości lub metody dostępu do `get` właściwości</span><span class="sxs-lookup"><span data-stu-id="ee452-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="ee452-155">Struct, Class, Interface, enum lub Delegate</span><span class="sxs-lookup"><span data-stu-id="ee452-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="ee452-156">Należy określić `field` wartość docelową, aby zastosować atrybut do pola zapasowego utworzonego dla właściwości, która jest [implementowana](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="ee452-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="ee452-157">Poniższy przykład pokazuje, jak zastosować atrybuty do zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="ee452-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="ee452-158">Aby uzyskać więcej informacji, zobacz [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="ee452-158">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="ee452-159">Poniższy przykład pokazuje, jak zastosować atrybuty do metod, parametrów metody i wartości zwracanych metody w języku C#.</span><span class="sxs-lookup"><span data-stu-id="ee452-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="ee452-160">Bez względu na to, w którym `ValidatedContract` miejscu docelowym jest zdefiniowane prawidłowe, należy `return` określić element docelowy, nawet jeśli `ValidatedContract` zostały zdefiniowane do zastosowania tylko do wartości zwracanych.</span><span class="sxs-lookup"><span data-stu-id="ee452-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="ee452-161">Innymi słowy kompilator nie będzie używać `AttributeUsage` informacji do rozwiązywania niejednoznacznych obiektów docelowych atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ee452-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="ee452-162">Aby uzyskać więcej informacji, zobacz [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span><span class="sxs-lookup"><span data-stu-id="ee452-162">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="ee452-163">Typowe zastosowania atrybutów</span><span class="sxs-lookup"><span data-stu-id="ee452-163">Common uses for attributes</span></span>

<span data-ttu-id="ee452-164">Poniższa lista zawiera kilka typowych zastosowania atrybutów w kodzie:</span><span class="sxs-lookup"><span data-stu-id="ee452-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="ee452-165">Oznaczanie metod przy użyciu `WebMethod` atrybutu w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ee452-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="ee452-166">Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ee452-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="ee452-167">Opis sposobu organizowania parametrów metody podczas współdziałania z kodem natywnym.</span><span class="sxs-lookup"><span data-stu-id="ee452-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="ee452-168">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ee452-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="ee452-169">Opisywanie właściwości modelu COM dla klas, metod i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="ee452-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="ee452-170">Wywoływanie kodu niezarządzanego za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="ee452-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="ee452-171">Opisywanie zestawu pod względem tytułu, wersji, opisu lub znaku towarowego.</span><span class="sxs-lookup"><span data-stu-id="ee452-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="ee452-172">Opisywanie elementów członkowskich klasy do serializacji dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="ee452-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="ee452-173">Opis sposobu mapowania między elementami członkowskimi klasy i węzłami XML na potrzeby serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="ee452-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="ee452-174">Opisywanie wymagań dotyczących zabezpieczeń dla metod.</span><span class="sxs-lookup"><span data-stu-id="ee452-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="ee452-175">Określanie charakterystyki służącej do wymuszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ee452-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="ee452-176">Kontrolowanie optymalizacji przez kompilator just-in-Time (JIT), dzięki czemu kod pozostaje łatwy do debugowania.</span><span class="sxs-lookup"><span data-stu-id="ee452-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="ee452-177">Uzyskiwanie informacji o wywołującym do metody.</span><span class="sxs-lookup"><span data-stu-id="ee452-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ee452-178">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ee452-178">Related sections</span></span>

<span data-ttu-id="ee452-179">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="ee452-179">For more information, see:</span></span>

- [<span data-ttu-id="ee452-180">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="ee452-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="ee452-181">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="ee452-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="ee452-182">Jak utworzyć Unię C/C++ za pomocą atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="ee452-182">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="ee452-183">Atrybuty wspólne (C#)</span><span class="sxs-lookup"><span data-stu-id="ee452-183">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="ee452-184">Informacje o wywołującym (C#)</span><span class="sxs-lookup"><span data-stu-id="ee452-184">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="ee452-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee452-185">See also</span></span>

- [<span data-ttu-id="ee452-186">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ee452-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="ee452-187">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="ee452-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="ee452-188">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee452-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="ee452-189">Używanie atrybutów w C #</span><span class="sxs-lookup"><span data-stu-id="ee452-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
