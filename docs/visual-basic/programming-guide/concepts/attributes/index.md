---
title: Omówienie atrybutów (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: c799b9be9b936beadde28374bd9882ebc6e2d9a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966319"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="850a1-102">Omówienie atrybutów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a1-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="850a1-103">Atrybuty zapewniają zaawansowaną metodę kojarzenia metadanych lub deklaracyjne informacje z kodem (zestawy, typy, metody, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="850a1-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="850a1-104">Gdy atrybut jest skojarzony z jednostką programu, atrybut może być badany w czasie wykonywania przy użyciu techniki o nazwie odbicie.</span><span class="sxs-lookup"><span data-stu-id="850a1-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="850a1-105">Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="850a1-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="850a1-106">Atrybuty mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="850a1-106">Attributes have the following properties:</span></span>  
  
- <span data-ttu-id="850a1-107">Atrybuty dodają metadane do programu.</span><span class="sxs-lookup"><span data-stu-id="850a1-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="850a1-108">*Metadane* są informacjami o typach zdefiniowanych w programie.</span><span class="sxs-lookup"><span data-stu-id="850a1-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="850a1-109">Wszystkie zestawy .NET zawierają określony zestaw metadanych opisujący typy i elementy członkowskie typu zdefiniowane w zestawie.</span><span class="sxs-lookup"><span data-stu-id="850a1-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="850a1-110">Można dodać atrybuty niestandardowe, aby określić wszelkie dodatkowe informacje, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="850a1-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="850a1-111">Aby uzyskać więcej informacji, zobacz temat [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="850a1-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
- <span data-ttu-id="850a1-112">Można zastosować jeden lub więcej atrybutów do całych zestawów, modułów lub mniejszych elementów programu, takich jak klasy i właściwości.</span><span class="sxs-lookup"><span data-stu-id="850a1-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
- <span data-ttu-id="850a1-113">Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="850a1-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
- <span data-ttu-id="850a1-114">Program może przeanalizować własne metadane lub metadane w innych programach przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="850a1-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="850a1-115">Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="850a1-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="850a1-116">Korzystanie z atrybutów</span><span class="sxs-lookup"><span data-stu-id="850a1-116">Using Attributes</span></span>  
 <span data-ttu-id="850a1-117">Atrybuty mogą być umieszczane w większości każdej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="850a1-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="850a1-118">W Visual Basic atrybut jest ujęty w nawiasy kątowe\< (>).</span><span class="sxs-lookup"><span data-stu-id="850a1-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="850a1-119">Musi znajdować się bezpośrednio przed elementem, do którego jest stosowany, w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="850a1-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="850a1-120">W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do zastosowania konkretnej cechy klasy:</span><span class="sxs-lookup"><span data-stu-id="850a1-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="850a1-121">Metoda z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="850a1-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="850a1-122">W deklaracji można umieścić więcej niż jeden atrybut:</span><span class="sxs-lookup"><span data-stu-id="850a1-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="850a1-123">Niektóre atrybuty można określić więcej niż raz dla danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="850a1-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="850a1-124">Przykładem takiego atrybutu Multiuse jest <xref:System.Diagnostics.ConditionalAttribute>:</span><span class="sxs-lookup"><span data-stu-id="850a1-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
> <span data-ttu-id="850a1-125">Według Konwencji wszystkie nazwy atrybutów kończą się słowem "Attribute", aby odróżnić je od innych elementów w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="850a1-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="850a1-126">Nie trzeba jednak określać sufiksu atrybutu podczas używania atrybutów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="850a1-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="850a1-127">Na przykład `[DllImport]` jest równoważne z `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="850a1-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="850a1-128">Parametry atrybutu</span><span class="sxs-lookup"><span data-stu-id="850a1-128">Attribute Parameters</span></span>  
 <span data-ttu-id="850a1-129">Wiele atrybutów ma parametry, które mogą mieć położenie, nienazwane lub nazwane.</span><span class="sxs-lookup"><span data-stu-id="850a1-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="850a1-130">Wszystkie parametry pozycyjne muszą być określone w określonej kolejności i nie mogą być pomijane; parametry nazwane są opcjonalne i można je określić w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="850a1-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="850a1-131">Parametry pozycyjne są określone jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="850a1-131">Positional parameters are specified first.</span></span> <span data-ttu-id="850a1-132">Na przykład te trzy atrybuty są równoważne:</span><span class="sxs-lookup"><span data-stu-id="850a1-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="850a1-133">Pierwszy parametr, nazwa biblioteki DLL, jest położeniem i zawsze jest pierwszy. inne osoby mają nazwę.</span><span class="sxs-lookup"><span data-stu-id="850a1-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="850a1-134">W tym przypadku oba nazwane parametry domyślnie mają wartość false, więc można je pominąć.</span><span class="sxs-lookup"><span data-stu-id="850a1-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="850a1-135">Informacje dotyczące domyślnych wartości parametrów można znaleźć w dokumentacji poszczególnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="850a1-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="850a1-136">Docelowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="850a1-136">Attribute Targets</span></span>  
 <span data-ttu-id="850a1-137">*Obiektem docelowym* atrybutu jest jednostka, do której odnosi się ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="850a1-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="850a1-138">Na przykład, atrybut może dotyczyć klasy, konkretnej metody lub całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="850a1-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="850a1-139">Domyślnie atrybut ma zastosowanie do elementu, który poprzedza.</span><span class="sxs-lookup"><span data-stu-id="850a1-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="850a1-140">Ale można również jawnie określić, na przykład, czy atrybut jest stosowany do metody lub do jego parametru lub do jego wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="850a1-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="850a1-141">Aby jawnie zidentyfikować obiekt docelowy atrybutu, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="850a1-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="850a1-142">Lista możliwych `target` wartości jest pokazana w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="850a1-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="850a1-143">Wartość docelowa</span><span class="sxs-lookup"><span data-stu-id="850a1-143">Target value</span></span>|<span data-ttu-id="850a1-144">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="850a1-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="850a1-145">Cały zestaw</span><span class="sxs-lookup"><span data-stu-id="850a1-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="850a1-146">Bieżący moduł zestawu (który różni się od modułu Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a1-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="850a1-147">Poniższy przykład pokazuje, jak zastosować atrybuty do zestawów i modułów.</span><span class="sxs-lookup"><span data-stu-id="850a1-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="850a1-148">Aby uzyskać więcej informacji, zobacz [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="850a1-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="850a1-149">Typowe zastosowania atrybutów</span><span class="sxs-lookup"><span data-stu-id="850a1-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="850a1-150">Poniższa lista zawiera kilka typowych zastosowania atrybutów w kodzie:</span><span class="sxs-lookup"><span data-stu-id="850a1-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
- <span data-ttu-id="850a1-151">Oznaczanie metod przy `WebMethod` użyciu atrybutu w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="850a1-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="850a1-152">Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="850a1-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
- <span data-ttu-id="850a1-153">Opis sposobu organizowania parametrów metody podczas współdziałania z kodem natywnym.</span><span class="sxs-lookup"><span data-stu-id="850a1-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="850a1-154">Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="850a1-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
- <span data-ttu-id="850a1-155">Opisywanie właściwości modelu COM dla klas, metod i interfejsów.</span><span class="sxs-lookup"><span data-stu-id="850a1-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
- <span data-ttu-id="850a1-156">Wywoływanie kodu niezarządzanego za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="850a1-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
- <span data-ttu-id="850a1-157">Opisywanie zestawu pod względem tytułu, wersji, opisu lub znaku towarowego.</span><span class="sxs-lookup"><span data-stu-id="850a1-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
- <span data-ttu-id="850a1-158">Opisywanie elementów członkowskich klasy do serializacji dla trwałości.</span><span class="sxs-lookup"><span data-stu-id="850a1-158">Describing which members of a class to serialize for persistence.</span></span>  
  
- <span data-ttu-id="850a1-159">Opis sposobu mapowania między elementami członkowskimi klasy i węzłami XML na potrzeby serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="850a1-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
- <span data-ttu-id="850a1-160">Opisywanie wymagań dotyczących zabezpieczeń dla metod.</span><span class="sxs-lookup"><span data-stu-id="850a1-160">Describing the security requirements for methods.</span></span>  
  
- <span data-ttu-id="850a1-161">Określanie charakterystyki służącej do wymuszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="850a1-161">Specifying characteristics used to enforce security.</span></span>  
  
- <span data-ttu-id="850a1-162">Kontrolowanie optymalizacji przez kompilator just-in-Time (JIT), dzięki czemu kod pozostaje łatwy do debugowania.</span><span class="sxs-lookup"><span data-stu-id="850a1-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
- <span data-ttu-id="850a1-163">Uzyskiwanie informacji o wywołującym do metody.</span><span class="sxs-lookup"><span data-stu-id="850a1-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="850a1-164">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="850a1-164">Related Sections</span></span>  
 <span data-ttu-id="850a1-165">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="850a1-165">For more information, see:</span></span>  
  
- [<span data-ttu-id="850a1-166">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a1-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
- [<span data-ttu-id="850a1-167">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a1-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
- [<span data-ttu-id="850a1-168">Instrukcje: Utwórz element C/C++ Union przy użyciu atrybutów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a1-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
- [<span data-ttu-id="850a1-169">Atrybuty wspólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a1-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
- [<span data-ttu-id="850a1-170">Informacje o wywołującym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a1-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="850a1-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="850a1-171">See also</span></span>

- [<span data-ttu-id="850a1-172">Przewodnik programowania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="850a1-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="850a1-173">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="850a1-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="850a1-174">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="850a1-174">Attributes</span></span>](../../../../standard/attributes/index.md)
