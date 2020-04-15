---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 62424163303417746a67707d9ef34185954db316
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389538"
---
# <a name="attributes-c"></a><span data-ttu-id="d1e96-102">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="d1e96-102">Attributes (C#)</span></span>

<span data-ttu-id="d1e96-103">Atrybuty zapewniają zaawansowaną metodę kojarzenia metadanych lub informacji deklaratywnych z kodem (zestawy, typy, metody, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="d1e96-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="d1e96-104">Po skojarzeniu atrybutu z encją programu, atrybut można zbadać w czasie wykonywania przy użyciu techniki zwanej *odbiciem*.</span><span class="sxs-lookup"><span data-stu-id="d1e96-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="d1e96-105">Aby uzyskać więcej informacji, zobacz [Odbicie (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="d1e96-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="d1e96-106">Atrybuty mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d1e96-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="d1e96-107">Atrybuty dodają metadane do programu.</span><span class="sxs-lookup"><span data-stu-id="d1e96-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="d1e96-108">*Metadane* to informacje o typach zdefiniowanych w programie.</span><span class="sxs-lookup"><span data-stu-id="d1e96-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="d1e96-109">Wszystkie zestawy .NET zawierają określony zestaw metadanych, który opisuje typy i elementy członkowskie typu zdefiniowane w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d1e96-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="d1e96-110">Można dodać atrybuty niestandardowe, aby określić wszelkie dodatkowe informacje, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="d1e96-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="d1e96-111">Aby uzyskać więcej informacji, zobacz Tworzenie [atrybutów niestandardowych (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d1e96-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="d1e96-112">Można zastosować jeden lub więcej atrybutów do całych zestawów, modułów lub mniejszych elementów programu, takich jak klasy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="d1e96-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="d1e96-113">Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="d1e96-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="d1e96-114">Program może sprawdzić własne metadane lub metadane w innych programach przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="d1e96-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="d1e96-115">Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="d1e96-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="d1e96-116">Korzystanie z atrybutów</span><span class="sxs-lookup"><span data-stu-id="d1e96-116">Using attributes</span></span>

<span data-ttu-id="d1e96-117">Atrybuty mogą być umieszczane w większości dowolnej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d1e96-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="d1e96-118">W języku C#można określić atrybut, umieszczając nazwę atrybutu ujętego w nawiasach kwadratowych ([]) nad deklaracją jednostki, do której ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="d1e96-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="d1e96-119">W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do stosowania określonej cechy do klasy:</span><span class="sxs-lookup"><span data-stu-id="d1e96-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="d1e96-120">Metoda z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d1e96-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="d1e96-121">Więcej niż jeden atrybut można umieścić w deklaracji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d1e96-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="d1e96-122">Niektóre atrybuty można określić więcej niż jeden raz dla danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="d1e96-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="d1e96-123">Przykładem takiego atrybutu wielofunkcyjnego <xref:System.Diagnostics.ConditionalAttribute>jest:</span><span class="sxs-lookup"><span data-stu-id="d1e96-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="d1e96-124">Zgodnie z konwencją wszystkie nazwy atrybutów kończą się słowem "Atrybut", aby odróżnić je od innych elementów w bibliotekach .NET.</span><span class="sxs-lookup"><span data-stu-id="d1e96-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="d1e96-125">Jednak nie trzeba określać sufiks atrybutu podczas korzystania z atrybutów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d1e96-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="d1e96-126">Na przykład `[DllImport]` jest `[DllImportAttribute]`odpowiednikiem `DllImportAttribute` , ale jest rzeczywistą nazwą atrybutu w bibliotece klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1e96-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="d1e96-127">Parametry atrybutu</span><span class="sxs-lookup"><span data-stu-id="d1e96-127">Attribute parameters</span></span>

<span data-ttu-id="d1e96-128">Wiele atrybutów ma parametry, które mogą być pozycyjne, nienazwane lub nazwane.</span><span class="sxs-lookup"><span data-stu-id="d1e96-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="d1e96-129">Wszelkie parametry pozycyjne muszą być określone w określonej kolejności i nie można ich pominąć.</span><span class="sxs-lookup"><span data-stu-id="d1e96-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="d1e96-130">Nazwane parametry są opcjonalne i można je określić w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d1e96-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="d1e96-131">Parametry pozycyjne są określone jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="d1e96-131">Positional parameters are specified first.</span></span> <span data-ttu-id="d1e96-132">Na przykład te trzy atrybuty są równoważne:</span><span class="sxs-lookup"><span data-stu-id="d1e96-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="d1e96-133">Pierwszy parametr, nazwa biblioteki DLL, jest pozycyjny i zawsze jest pierwszy; pozostałe są nazwane.</span><span class="sxs-lookup"><span data-stu-id="d1e96-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="d1e96-134">W takim przypadku oba nazwane parametry domyślnie false, więc mogą być pominięte.</span><span class="sxs-lookup"><span data-stu-id="d1e96-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="d1e96-135">Parametry pozycyjne odpowiadają parametrom konstruktora atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d1e96-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="d1e96-136">Parametry nazwane lub opcjonalne odpowiadają właściwościom lub polom atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d1e96-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="d1e96-137">Informacje na temat domyślnych wartości parametrów można znaleźć w dokumentacji poszczególnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d1e96-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="d1e96-138">Docelowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="d1e96-138">Attribute targets</span></span>

<span data-ttu-id="d1e96-139">Obiekt *docelowy* atrybutu jest jednostką, której dotyczy atrybut.</span><span class="sxs-lookup"><span data-stu-id="d1e96-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="d1e96-140">Na przykład atrybut może mieć zastosowanie do klasy, określonej metody lub całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d1e96-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="d1e96-141">Domyślnie atrybut ma zastosowanie do elementu, który następuje po nim.</span><span class="sxs-lookup"><span data-stu-id="d1e96-141">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="d1e96-142">Ale można również jawnie zidentyfikować, na przykład, czy atrybut jest stosowany do metody lub do jego parametru lub do jego wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="d1e96-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="d1e96-143">Aby jawnie zidentyfikować obiekt docelowy atrybutu, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="d1e96-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="d1e96-144">Lista możliwych `target` wartości jest przedstawiona w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d1e96-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="d1e96-145">Wartość docelowa</span><span class="sxs-lookup"><span data-stu-id="d1e96-145">Target value</span></span>|<span data-ttu-id="d1e96-146">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="d1e96-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="d1e96-147">Cały zespół</span><span class="sxs-lookup"><span data-stu-id="d1e96-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="d1e96-148">Obecny moduł montażowy</span><span class="sxs-lookup"><span data-stu-id="d1e96-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="d1e96-149">Pole w klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="d1e96-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="d1e96-150">Wydarzenie</span><span class="sxs-lookup"><span data-stu-id="d1e96-150">Event</span></span>|
|`method`|<span data-ttu-id="d1e96-151">Metody `get` lub `set` akcesory właściwości</span><span class="sxs-lookup"><span data-stu-id="d1e96-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="d1e96-152">Parametry metody `set` lub parametry akcesora właściwości</span><span class="sxs-lookup"><span data-stu-id="d1e96-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="d1e96-153">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d1e96-153">Property</span></span>|
|`return`|<span data-ttu-id="d1e96-154">Zwraca wartość metody, indeksatora `get` właściwości lub akcesora właściwości</span><span class="sxs-lookup"><span data-stu-id="d1e96-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="d1e96-155">Struktura, klasa, interfejs, wyliczenia lub delegata</span><span class="sxs-lookup"><span data-stu-id="d1e96-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="d1e96-156">Można określić `field` wartość docelową, aby zastosować atrybut do pola zapasowego utworzonego dla [właściwości automatycznie zaimplementowane](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="d1e96-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="d1e96-157">W poniższym przykładzie pokazano, jak zastosować atrybuty do zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="d1e96-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="d1e96-158">Aby uzyskać więcej informacji, zobacz [Wspólne atrybuty (C#)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d1e96-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="d1e96-159">Poniższy przykład pokazuje, jak zastosować atrybuty do metod, parametrów metody i wartości zwracanej metody w języku C#.</span><span class="sxs-lookup"><span data-stu-id="d1e96-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="d1e96-160">Niezależnie od docelowych, `ValidatedContract` dla których jest `return` zdefiniowany jako prawidłowy, `ValidatedContract` cel musi być określony, nawet jeśli zostały zdefiniowane do zastosowania tylko do zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="d1e96-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="d1e96-161">Innymi słowy kompilator nie `AttributeUsage` będzie używać informacji do rozpoznawania niejednoznacznych docelowych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d1e96-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="d1e96-162">Aby uzyskać więcej informacji, zobacz [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span><span class="sxs-lookup"><span data-stu-id="d1e96-162">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="d1e96-163">Typowe zastosowania atrybutów</span><span class="sxs-lookup"><span data-stu-id="d1e96-163">Common uses for attributes</span></span>

<span data-ttu-id="d1e96-164">Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:</span><span class="sxs-lookup"><span data-stu-id="d1e96-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="d1e96-165">Metody znakowania `WebMethod` przy użyciu atrybutu w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d1e96-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="d1e96-166">Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d1e96-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="d1e96-167">Opisujące sposób organizowania parametrów metody podczas współpracy z kodem macierzystym.</span><span class="sxs-lookup"><span data-stu-id="d1e96-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="d1e96-168">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d1e96-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="d1e96-169">Opisujące właściwości COM dla klas, metod i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d1e96-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="d1e96-170">Wywoływanie kodu niezarządzanego <xref:System.Runtime.InteropServices.DllImportAttribute> przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="d1e96-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="d1e96-171">Opisujące twój montaż pod względem tytułu, wersji, opisu lub znaku towarowego.</span><span class="sxs-lookup"><span data-stu-id="d1e96-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="d1e96-172">Opisujące, którzy członkowie klasy do serializacji dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="d1e96-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="d1e96-173">Opisujące sposób mapowania między członkami klasy i węzłów XML dla serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="d1e96-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="d1e96-174">Opisujące wymagania dotyczące zabezpieczeń dla metod.</span><span class="sxs-lookup"><span data-stu-id="d1e96-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="d1e96-175">Określanie właściwości używanych do wymuszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d1e96-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="d1e96-176">Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), dzięki czemu kod pozostaje łatwy do debugowania.</span><span class="sxs-lookup"><span data-stu-id="d1e96-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="d1e96-177">Uzyskiwanie informacji o wywołującym do metody.</span><span class="sxs-lookup"><span data-stu-id="d1e96-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d1e96-178">Powiązane sekcje</span><span class="sxs-lookup"><span data-stu-id="d1e96-178">Related sections</span></span>

<span data-ttu-id="d1e96-179">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="d1e96-179">For more information, see:</span></span>

- [<span data-ttu-id="d1e96-180">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="d1e96-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="d1e96-181">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="d1e96-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="d1e96-182">Jak utworzyć unię C/C++ przy użyciu atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="d1e96-182">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="d1e96-183">Typowe atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="d1e96-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="d1e96-184">Informacje o dzwoniącym (C#)</span><span class="sxs-lookup"><span data-stu-id="d1e96-184">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="d1e96-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1e96-185">See also</span></span>

- [<span data-ttu-id="d1e96-186">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="d1e96-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="d1e96-187">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="d1e96-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="d1e96-188">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d1e96-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="d1e96-189">Korzystanie z atrybutów w języku C #</span><span class="sxs-lookup"><span data-stu-id="d1e96-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
