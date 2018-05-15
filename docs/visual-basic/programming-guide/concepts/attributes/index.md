---
title: Atrybuty — Przegląd (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: e6d11daeac2f2392e1080eca8503c9b2c420ab35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="5e83b-102">Atrybuty — Przegląd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e83b-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="5e83b-103">Atrybuty udostępnia zaawansowane metody kojarzenia metadanych lub deklaratywne informacji z kodu (zestawy, typy metod, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="5e83b-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="5e83b-104">Po atrybutu jest skojarzony z jednostką program, ten atrybut można tworzyć zapytania w czasie wykonywania przy użyciu techniki o nazwie *odbicia*.</span><span class="sxs-lookup"><span data-stu-id="5e83b-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="5e83b-105">Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5e83b-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="5e83b-106">Atrybuty mieć następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="5e83b-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="5e83b-107">Atrybuty dodawać metadane do programu.</span><span class="sxs-lookup"><span data-stu-id="5e83b-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="5e83b-108">*Metadane* znajdują się informacje o typy zdefiniowane w programie.</span><span class="sxs-lookup"><span data-stu-id="5e83b-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="5e83b-109">Wszystkie zestawy .NET zawierają określony zestaw metadanych, które opisują typy i elementy członkowskie typu zdefiniowany w zestawie.</span><span class="sxs-lookup"><span data-stu-id="5e83b-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="5e83b-110">Można dodawać atrybuty niestandardowe, aby określić dodatkowe informacje, które jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="5e83b-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="5e83b-111">Aby uzyskać więcej informacji zobacz, [tworzenie niestandardowe atrybuty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5e83b-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="5e83b-112">Co najmniej jeden atrybut można stosować do całego zestawy, moduły lub mniejsze elementy programu, takich jak klasy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e83b-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="5e83b-113">Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e83b-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="5e83b-114">Program można sprawdzić jego własnej ani metadanych w programach przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="5e83b-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="5e83b-115">Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5e83b-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="5e83b-116">Przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="5e83b-116">Using Attributes</span></span>  
 <span data-ttu-id="5e83b-117">Atrybuty można umieścić w praktycznie dowolnej deklaracji, chociaż określony atrybut mogą ograniczać typów deklaracje, na których jest ona prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="5e83b-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="5e83b-118">W języku Visual Basic atrybutu jest ujęta w nawiasy (\< >).</span><span class="sxs-lookup"><span data-stu-id="5e83b-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="5e83b-119">Musi znajdować się bezpośrednio przed elementem, do którego jest stosowana, w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="5e83b-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="5e83b-120">W tym przykładzie <xref:System.SerializableAttribute> atrybut służy do stosowania określonej właściwości do klasy:</span><span class="sxs-lookup"><span data-stu-id="5e83b-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="5e83b-121">Metody z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5e83b-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="5e83b-122">Więcej niż jeden atrybut można umieścić w deklaracji:</span><span class="sxs-lookup"><span data-stu-id="5e83b-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="5e83b-123">Niektóre atrybuty można określić więcej niż raz dla danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="5e83b-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="5e83b-124">Na przykład multiuse atrybutu <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="5e83b-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="5e83b-125">Według Konwencji wszystkich nazw atrybutów kończyć się wyrazem "Atrybutu", aby odróżnić je od innych elementów w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e83b-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="5e83b-126">Nie trzeba jednak określić sufiks atrybutu przy użyciu atrybutów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5e83b-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="5e83b-127">Na przykład `[DllImport]` jest odpowiednikiem `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e83b-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="5e83b-128">Parametry atrybutów</span><span class="sxs-lookup"><span data-stu-id="5e83b-128">Attribute Parameters</span></span>  
 <span data-ttu-id="5e83b-129">Wiele atrybutów ma parametry, które mogą być pozycyjnych, bez nazwy lub nazwane.</span><span class="sxs-lookup"><span data-stu-id="5e83b-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="5e83b-130">Parametry pozycyjne musi być podana w odpowiedniej kolejności i nie może zostać pominięta; nazwane parametry są opcjonalne i może zostać określony w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="5e83b-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="5e83b-131">Parametry pozycyjne są określony jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="5e83b-131">Positional parameters are specified first.</span></span> <span data-ttu-id="5e83b-132">Na przykład te trzy atrybuty są równoważne:</span><span class="sxs-lookup"><span data-stu-id="5e83b-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="5e83b-133">Pierwszy parametr Nazwa biblioteki DLL jest pozycyjnych i zawsze zostanie osiągnięty jako pierwszy; inne o nazwie.</span><span class="sxs-lookup"><span data-stu-id="5e83b-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="5e83b-134">W takim przypadku nazwanych parametrów domyślna wartość to false, więc można pominąć.</span><span class="sxs-lookup"><span data-stu-id="5e83b-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="5e83b-135">Zajrzyj do dokumentacji poszczególne atrybuty, aby uzyskać informacje dotyczące domyślne wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="5e83b-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="5e83b-136">Docelowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="5e83b-136">Attribute Targets</span></span>  
 <span data-ttu-id="5e83b-137">*Docelowej* atrybutu jest jednostki, której dotyczy ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="5e83b-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="5e83b-138">Na przykład atrybut mogą stosować do klasy, konkretnej metody lub całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5e83b-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="5e83b-139">Domyślnie atrybut dotyczy poprzedza element.</span><span class="sxs-lookup"><span data-stu-id="5e83b-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="5e83b-140">Ale można również jawnie określić, na przykład, czy atrybut jest stosowany do metody, lub jej parametr albo jego wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="5e83b-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="5e83b-141">Aby jawnie określić obiekt docelowy atrybutu, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="5e83b-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="5e83b-142">Lista możliwości `target` w poniższej tabeli przedstawiono wartości.</span><span class="sxs-lookup"><span data-stu-id="5e83b-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="5e83b-143">Wartość docelowa</span><span class="sxs-lookup"><span data-stu-id="5e83b-143">Target value</span></span>|<span data-ttu-id="5e83b-144">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="5e83b-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="5e83b-145">Całego zestawu</span><span class="sxs-lookup"><span data-stu-id="5e83b-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="5e83b-146">Bieżący modułu zestawu (który jest inny niż moduł Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e83b-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="5e83b-147">Poniższy przykład pokazuje, jak można zastosować atrybutów do zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="5e83b-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="5e83b-148">Aby uzyskać więcej informacji, zobacz [takie same atrybuty wspólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5e83b-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="5e83b-149">Najczęstsze zastosowania dla atrybutów</span><span class="sxs-lookup"><span data-stu-id="5e83b-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="5e83b-150">Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5e83b-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="5e83b-151">Oznaczanie za pomocą metody `WebMethod` atrybutów w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5e83b-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="5e83b-152">Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5e83b-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="5e83b-153">Zawierająca opis sposobu zorganizowania parametrów metody podczas współpracy z kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="5e83b-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="5e83b-154">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5e83b-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="5e83b-155">Opisujących właściwości modelu COM dla klas, metod i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="5e83b-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="5e83b-156">Wywoływanie niezarządzanych w kodzie za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="5e83b-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="5e83b-157">Opisujące używanemu zestawowi pod względem tytułu, wersji, opis lub znakiem towarowym.</span><span class="sxs-lookup"><span data-stu-id="5e83b-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="5e83b-158">Opisujące członków klasy do serializacji trwałości.</span><span class="sxs-lookup"><span data-stu-id="5e83b-158">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="5e83b-159">Opisujących sposób mapowania między elementami członkowskimi klas i węzłów XML do serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="5e83b-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="5e83b-160">Opisujących wymagania dotyczące zabezpieczeń dla metod.</span><span class="sxs-lookup"><span data-stu-id="5e83b-160">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="5e83b-161">Określanie właściwości używanych do wymuszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5e83b-161">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="5e83b-162">Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), kod jest łatwy do debugowania.</span><span class="sxs-lookup"><span data-stu-id="5e83b-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="5e83b-163">Uzyskiwanie informacji o elemencie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="5e83b-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5e83b-164">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5e83b-164">Related Sections</span></span>  
 <span data-ttu-id="5e83b-165">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="5e83b-165">For more information, see:</span></span>  
  
-   [<span data-ttu-id="5e83b-166">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e83b-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="5e83b-167">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e83b-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="5e83b-168">Porady: tworzenie złożenia C/C++ za pomocą atrybutów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e83b-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="5e83b-169">Atrybuty wspólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e83b-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="5e83b-170">Informacje o wywołującym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e83b-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="5e83b-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e83b-171">See Also</span></span>  
 [<span data-ttu-id="5e83b-172">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e83b-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="5e83b-173">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e83b-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="5e83b-174">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5e83b-174">Attributes</span></span>](../../../../standard/attributes/index.md)
