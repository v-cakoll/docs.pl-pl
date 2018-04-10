---
title: Atrybuty (C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f9fc23cf7afbd28f0c9ae438cbce298cbf362fbd
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="attributes-c"></a><span data-ttu-id="5315c-102">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="5315c-102">Attributes (C#)</span></span>
<span data-ttu-id="5315c-103">Atrybuty udostępnia zaawansowane metody kojarzenia metadanych lub deklaratywne informacji z kodu (zestawy, typy metod, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="5315c-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="5315c-104">Po atrybutu jest skojarzony z jednostką program, ten atrybut można tworzyć zapytania w czasie wykonywania przy użyciu techniki o nazwie *odbicia*.</span><span class="sxs-lookup"><span data-stu-id="5315c-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="5315c-105">Aby uzyskać więcej informacji, zobacz [odbicia (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5315c-105">For more information, see [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="5315c-106">Atrybuty mieć następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="5315c-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="5315c-107">Atrybuty dodawać metadane do programu.</span><span class="sxs-lookup"><span data-stu-id="5315c-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="5315c-108">*Metadane* znajdują się informacje o typy zdefiniowane w programie.</span><span class="sxs-lookup"><span data-stu-id="5315c-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="5315c-109">Wszystkie zestawy .NET zawierają określony zestaw metadanych, które opisują typy i elementy członkowskie typu zdefiniowany w zestawie.</span><span class="sxs-lookup"><span data-stu-id="5315c-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="5315c-110">Można dodawać atrybuty niestandardowe, aby określić dodatkowe informacje, które jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="5315c-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="5315c-111">Aby uzyskać więcej informacji zobacz, [tworzenie niestandardowe atrybuty (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5315c-111">For more information, see, [Creating Custom Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="5315c-112">Co najmniej jeden atrybut można stosować do całego zestawy, moduły lub mniejsze elementy programu, takich jak klasy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5315c-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="5315c-113">Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5315c-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="5315c-114">Program można sprawdzić jego własnej ani metadanych w programach przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="5315c-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="5315c-115">Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5315c-115">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="5315c-116">Przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="5315c-116">Using Attributes</span></span>  
 <span data-ttu-id="5315c-117">Atrybuty można umieścić w praktycznie dowolnej deklaracji, chociaż określony atrybut mogą ograniczać typów deklaracje, na których jest ona prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="5315c-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="5315c-118">W C# należy określić atrybut przez umieszczenie nazwę atrybutu, ujęta w nawiasy kwadratowe ([]), powyżej deklaracji jednostki, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5315c-118">In C#, you specify an attribute by placing the name of the attribute, enclosed in square brackets ([]), above the declaration of the entity to which it applies.</span></span>  
  
 <span data-ttu-id="5315c-119">W tym przykładzie <xref:System.SerializableAttribute> atrybut służy do stosowania określonej właściwości do klasy:</span><span class="sxs-lookup"><span data-stu-id="5315c-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 <span data-ttu-id="5315c-120">Metody z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5315c-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 <span data-ttu-id="5315c-121">Więcej niż jeden atrybut można umieścić w deklaracji:</span><span class="sxs-lookup"><span data-stu-id="5315c-121">More than one attribute can be placed on a declaration:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 <span data-ttu-id="5315c-122">Niektóre atrybuty można określić więcej niż raz dla danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="5315c-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="5315c-123">Na przykład multiuse atrybutu <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="5315c-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="5315c-124">Według Konwencji wszystkich nazw atrybutów kończyć się wyrazem "Atrybutu", aby odróżnić je od innych elementów w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5315c-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="5315c-125">Nie trzeba jednak określić sufiks atrybutu przy użyciu atrybutów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5315c-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="5315c-126">Na przykład `[DllImport]` jest odpowiednikiem `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5315c-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="5315c-127">Parametry atrybutów</span><span class="sxs-lookup"><span data-stu-id="5315c-127">Attribute Parameters</span></span>  
 <span data-ttu-id="5315c-128">Wiele atrybutów ma parametry, które mogą być pozycyjnych, bez nazwy lub nazwane.</span><span class="sxs-lookup"><span data-stu-id="5315c-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="5315c-129">Parametry pozycyjne musi być podana w odpowiedniej kolejności i nie może zostać pominięta; nazwane parametry są opcjonalne i może zostać określony w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="5315c-129">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="5315c-130">Parametry pozycyjne są określony jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="5315c-130">Positional parameters are specified first.</span></span> <span data-ttu-id="5315c-131">Na przykład te trzy atrybuty są równoważne:</span><span class="sxs-lookup"><span data-stu-id="5315c-131">For example, these three attributes are equivalent:</span></span>  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 <span data-ttu-id="5315c-132">Pierwszy parametr Nazwa biblioteki DLL jest pozycyjnych i zawsze zostanie osiągnięty jako pierwszy; inne o nazwie.</span><span class="sxs-lookup"><span data-stu-id="5315c-132">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="5315c-133">W takim przypadku nazwanych parametrów domyślna wartość to false, więc można pominąć.</span><span class="sxs-lookup"><span data-stu-id="5315c-133">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="5315c-134">Zajrzyj do dokumentacji poszczególne atrybuty, aby uzyskać informacje dotyczące domyślne wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="5315c-134">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="5315c-135">Docelowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="5315c-135">Attribute Targets</span></span>  
 <span data-ttu-id="5315c-136">*Docelowej* atrybutu jest jednostki, której dotyczy ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="5315c-136">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="5315c-137">Na przykład atrybut mogą stosować do klasy, konkretnej metody lub całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5315c-137">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="5315c-138">Domyślnie atrybut dotyczy poprzedza element.</span><span class="sxs-lookup"><span data-stu-id="5315c-138">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="5315c-139">Ale można również jawnie określić, na przykład, czy atrybut jest stosowany do metody, lub jej parametr albo jego wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="5315c-139">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="5315c-140">Aby jawnie określić obiekt docelowy atrybutu, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="5315c-140">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```csharp  
[target : attribute-list]  
```  
  
 <span data-ttu-id="5315c-141">Lista możliwości `target` w poniższej tabeli przedstawiono wartości.</span><span class="sxs-lookup"><span data-stu-id="5315c-141">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="5315c-142">Wartość docelowa</span><span class="sxs-lookup"><span data-stu-id="5315c-142">Target value</span></span>|<span data-ttu-id="5315c-143">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="5315c-143">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="5315c-144">Całego zestawu</span><span class="sxs-lookup"><span data-stu-id="5315c-144">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="5315c-145">Bieżący modułu zestawu</span><span class="sxs-lookup"><span data-stu-id="5315c-145">Current assembly module</span></span>|  
|`field`|<span data-ttu-id="5315c-146">Pole w klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="5315c-146">Field in a class or a struct</span></span>|  
|`event`|<span data-ttu-id="5315c-147">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="5315c-147">Event</span></span>|  
|`method`|<span data-ttu-id="5315c-148">Metoda lub `get` i `set` metod dostępu do właściwości</span><span class="sxs-lookup"><span data-stu-id="5315c-148">Method or `get` and `set` property accessors</span></span>|  
|`param`|<span data-ttu-id="5315c-149">Parametry metody lub `set` parametry metody dostępu właściwości</span><span class="sxs-lookup"><span data-stu-id="5315c-149">Method parameters or `set` property accessor parameters</span></span>|  
|`property`|<span data-ttu-id="5315c-150">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5315c-150">Property</span></span>|  
|`return`|<span data-ttu-id="5315c-151">Zwraca wartość metody, właściwości indeksatora lub `get` metody dostępu właściwości</span><span class="sxs-lookup"><span data-stu-id="5315c-151">Return value of a method, property indexer, or `get` property accessor</span></span>|  
|`type`|<span data-ttu-id="5315c-152">Struktury, klasy, interface, enum lub delegate</span><span class="sxs-lookup"><span data-stu-id="5315c-152">Struct, class, interface, enum, or delegate</span></span>|  
  
 <span data-ttu-id="5315c-153">Poniższy przykład pokazuje, jak można zastosować atrybutów do zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="5315c-153">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="5315c-154">Aby uzyskać więcej informacji, zobacz [takie same atrybuty wspólne (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5315c-154">For more information, see [Common Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 <span data-ttu-id="5315c-155">Poniższy przykład przedstawia sposób zastosować atrybutów do metod, parametrów metod i metody zwracają wartości w języku C#.</span><span class="sxs-lookup"><span data-stu-id="5315c-155">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  <span data-ttu-id="5315c-156">Niezależnie od celów, na którym `SomeAttr` zdefiniowano był prawidłowy, `return` docelowy musi być określony, nawet jeśli `SomeAttr` zostały zdefiniowane do stosowania tylko dla wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="5315c-156">Regardless of the targets on which `SomeAttr` is defined to be valid, the `return` target has to be specified, even if `SomeAttr` were defined to apply only to return values.</span></span> <span data-ttu-id="5315c-157">Innymi słowy, kompilator nie będzie używać `AttributeUsage` informacje umożliwiające rozwiązanie docelowe atrybuty niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="5315c-157">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="5315c-158">Aby uzyskać więcej informacji, zobacz [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="5315c-158">For more information, see [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span></span>  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="5315c-159">Najczęstsze zastosowania dla atrybutów</span><span class="sxs-lookup"><span data-stu-id="5315c-159">Common Uses for Attributes</span></span>  
 <span data-ttu-id="5315c-160">Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5315c-160">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="5315c-161">Oznaczanie za pomocą metody `WebMethod` atrybutów w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5315c-161">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="5315c-162">Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5315c-162">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="5315c-163">Zawierająca opis sposobu zorganizowania parametrów metody podczas współpracy z kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="5315c-163">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="5315c-164">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5315c-164">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="5315c-165">Opisujących właściwości modelu COM dla klas, metod i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="5315c-165">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="5315c-166">Wywoływanie niezarządzanych w kodzie za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="5315c-166">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="5315c-167">Opisujące używanemu zestawowi pod względem tytułu, wersji, opis lub znakiem towarowym.</span><span class="sxs-lookup"><span data-stu-id="5315c-167">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="5315c-168">Opisujące członków klasy do serializacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="5315c-168">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="5315c-169">Opisujących sposób mapowania między elementami członkowskimi klas i węzłów XML do serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="5315c-169">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="5315c-170">Opisujących wymagania dotyczące zabezpieczeń dla metod.</span><span class="sxs-lookup"><span data-stu-id="5315c-170">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="5315c-171">Określanie właściwości używanych do wymuszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5315c-171">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="5315c-172">Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), kod jest łatwy do debugowania.</span><span class="sxs-lookup"><span data-stu-id="5315c-172">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="5315c-173">Uzyskiwanie informacji o elemencie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="5315c-173">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5315c-174">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5315c-174">Related Sections</span></span>  
 <span data-ttu-id="5315c-175">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="5315c-175">For more information, see:</span></span>  
  
-   [<span data-ttu-id="5315c-176">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="5315c-176">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="5315c-177">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="5315c-177">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="5315c-178">Porady: tworzenie złożenia C/C++ za pomocą atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="5315c-178">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="5315c-179">Atrybuty wspólne (C#)</span><span class="sxs-lookup"><span data-stu-id="5315c-179">Common Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="5315c-180">Informacje o wywołującym (C#)</span><span class="sxs-lookup"><span data-stu-id="5315c-180">Caller Information (C#)</span></span>](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="5315c-181">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5315c-181">See Also</span></span>  
 [<span data-ttu-id="5315c-182">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5315c-182">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5315c-183">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="5315c-183">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="5315c-184">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5315c-184">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)
