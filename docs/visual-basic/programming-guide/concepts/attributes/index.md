---
title: Omówienie atrybuty (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="bb3cd-102">Omówienie atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3cd-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="bb3cd-103">Atrybuty zawierają zaawansowaną metodą kojarzenia metadanych lub informacji deklaratywne, przy użyciu kodu (zestawy, typy, metody, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="bb3cd-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="bb3cd-104">Po atrybutu jest skojarzony z jednostką program, ten atrybut można wykonywać zapytania w czasie wykonywania za pomocą technikę o nazwie *odbicia*.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="bb3cd-105">Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="bb3cd-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="bb3cd-106">Atrybuty mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="bb3cd-107">Atrybuty dodawania metadanych do programu.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="bb3cd-108">*Metadane* obejmuje informacje dotyczące typów zdefiniowanych w programie.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="bb3cd-109">Wszystkie zestawy .NET zawierają określony zestaw metadane opisujące typy i elementy członkowskie typu zdefiniowane w zestawie.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="bb3cd-110">Możesz dodać atrybuty niestandardowe, aby określić dodatkowe informacje, która jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="bb3cd-111">Aby uzyskać więcej informacji znajduje się pozycja [tworzenia atrybuty niestandardowe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="bb3cd-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="bb3cd-112">Jeden lub więcej atrybutów mogą dotyczyć całego zestawów, modułów lub mniejszych elementów programów, takich jak klasy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="bb3cd-113">Atrybuty można zaakceptować argumentów w taki sam sposób jak metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="bb3cd-114">Program można sprawdzić swój własny metadanych lub metadanych w innych programach przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="bb3cd-115">Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="bb3cd-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="bb3cd-116">Przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="bb3cd-116">Using Attributes</span></span>  
 <span data-ttu-id="bb3cd-117">Atrybuty można umieścić w praktycznie dowolnej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="bb3cd-118">W języku Visual Basic atrybut jest ujęty w nawiasy ostre (\< >).</span><span class="sxs-lookup"><span data-stu-id="bb3cd-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="bb3cd-119">Musi znajdować się bezpośrednio przed elementem, do którego jest stosowana, w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="bb3cd-120">W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do stosowania szczególne właściwości do klasy:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="bb3cd-121">Metody z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana następująco:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="bb3cd-122">Więcej niż jeden atrybut można umieścić w deklaracji:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="bb3cd-123">Niektóre atrybuty można określić więcej niż jeden raz dla danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="bb3cd-124">Na przykład multiuse — atrybut <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="bb3cd-125">Zgodnie z Konwencją wszystkie nazwy atrybutu kończą się wyrazem "Atrybut", aby odróżnić je od innych elementów w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="bb3cd-126">Nie musisz jednak określić sufiks atrybutu, korzystając z atrybutów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="bb3cd-127">Na przykład `[DllImport]` jest odpowiednikiem `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="bb3cd-128">Parametry atrybutów</span><span class="sxs-lookup"><span data-stu-id="bb3cd-128">Attribute Parameters</span></span>  
 <span data-ttu-id="bb3cd-129">Wiele atrybutów ma parametry, które mogą być pozycyjne, bez nazwy lub nazwane.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="bb3cd-130">Wszystkie parametry pozycyjne musi być określona w określonej kolejności i nie może zostać pominięta; Parametry nazwane są opcjonalne i może być określony w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="bb3cd-131">Parametry pozycyjne są określony jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-131">Positional parameters are specified first.</span></span> <span data-ttu-id="bb3cd-132">Na przykład te trzy atrybuty są równoważne:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="bb3cd-133">Pierwszy parametr, nazwa biblioteki DLL jest pozycyjne i zawsze wykorzystasz; pozostałe o nazwie.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="bb3cd-134">W tym przypadku nazwanych parametrów domyślna wartość to false, dzięki czemu można pominąć.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="bb3cd-135">Zajrzyj do dokumentacji atrybutu Aby uzyskać informacji o domyślnych wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="bb3cd-136">Docelowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="bb3cd-136">Attribute Targets</span></span>  
 <span data-ttu-id="bb3cd-137">*Docelowej* atrybutu jest jednostki, której dotyczy ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="bb3cd-138">Na przykład atrybut mogą dotyczyć klasy, konkretną metodę lub całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="bb3cd-139">Domyślnie atrybut stosuje się do elementu, który poprzedza.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="bb3cd-140">Ale można także jawnie zidentyfikować, na przykład, czy atrybut jest stosowany do metody, lub jako parametr lub wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="bb3cd-141">Aby jawnie określić element docelowy atrybutu, użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="bb3cd-142">Lista możliwych `target` wartości zostały przedstawione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="bb3cd-143">Wartość docelowa</span><span class="sxs-lookup"><span data-stu-id="bb3cd-143">Target value</span></span>|<span data-ttu-id="bb3cd-144">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="bb3cd-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="bb3cd-145">Cały zespół</span><span class="sxs-lookup"><span data-stu-id="bb3cd-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="bb3cd-146">Bieżącego zestawu modułu (który jest inny niż w Module języka Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3cd-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="bb3cd-147">Poniższy przykład pokazuje, jak zastosować atrybutów do zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="bb3cd-148">Aby uzyskać więcej informacji, zobacz [wspólne atrybuty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="bb3cd-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="bb3cd-149">Najczęstsze zastosowania dla atrybutów</span><span class="sxs-lookup"><span data-stu-id="bb3cd-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="bb3cd-150">Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="bb3cd-151">Oznaczanie metod za pomocą `WebMethod` atrybutów w usługach sieci Web, aby wskazać, że metoda powinna być wywoływane za pośrednictwem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="bb3cd-152">Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="bb3cd-153">Opisujących sposób organizowania parametry metody podczas współpracy z kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="bb3cd-154">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="bb3cd-155">Opisujących właściwości modelu COM dla klasy, metody i interfejsy.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="bb3cd-156">Wywoływanie niezarządzanego kodu za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="bb3cd-157">Opisujące zestaw pod względem tytułu, wersji, opis lub znak towarowy.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="bb3cd-158">Opisujących członków klasy do serializacji na potrzeby stanu trwałego.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-158">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="bb3cd-159">Opisujących sposób mapowania między elementy członkowskie klasy i węzłów XML do serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="bb3cd-160">Opisujących wymagania dotyczące zabezpieczeń dla metod.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-160">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="bb3cd-161">Określanie właściwości używane do wymuszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-161">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="bb3cd-162">Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), dzięki czemu kod pozostaje ułatwia debugowanie.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="bb3cd-163">Uzyskiwanie informacji o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="bb3cd-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bb3cd-164">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bb3cd-164">Related Sections</span></span>  
 <span data-ttu-id="bb3cd-165">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="bb3cd-165">For more information, see:</span></span>  
  
-   [<span data-ttu-id="bb3cd-166">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3cd-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="bb3cd-167">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3cd-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="bb3cd-168">Instrukcje: Tworzenie złożenia C/C++ za pomocą atrybutów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3cd-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="bb3cd-169">Atrybuty wspólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3cd-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="bb3cd-170">Informacje o wywołującym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3cd-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb3cd-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb3cd-171">See also</span></span>
- [<span data-ttu-id="bb3cd-172">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb3cd-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="bb3cd-173">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3cd-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="bb3cd-174">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bb3cd-174">Attributes</span></span>](../../../../standard/attributes/index.md)
