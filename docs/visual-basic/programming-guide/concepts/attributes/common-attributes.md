---
title: Atrybuty wspólne (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 5a91b0aa48a22db4ea7fb56a9c632ff0cb44dce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="0299d-102">Atrybuty wspólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0299d-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="0299d-103">W tym temacie opisano atrybuty, które są najczęściej używane w programach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0299d-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="0299d-104">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="0299d-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="0299d-105">Atrybut przestarzałe</span><span class="sxs-lookup"><span data-stu-id="0299d-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="0299d-106">Atrybut Conditional</span><span class="sxs-lookup"><span data-stu-id="0299d-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="0299d-107">Caller — atrybuty informacji</span><span class="sxs-lookup"><span data-stu-id="0299d-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="0299d-108">Atrybuty Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0299d-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <a name="Global"></a> <span data-ttu-id="0299d-109">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="0299d-109">Global Attributes</span></span>  
 <span data-ttu-id="0299d-110">Większość atrybutów są stosowane do określonego języka elementów, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — odnoszą się do całego zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="0299d-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="0299d-111">Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzanie informacji o wersji w zestawie, jak to:</span><span class="sxs-lookup"><span data-stu-id="0299d-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="0299d-112">Atrybuty globalne pojawiają się w kodzie źródłowym po jednej najwyższego poziomu `Imports` instrukcje i przed wszelkimi deklaracjami typu, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0299d-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="0299d-113">Atrybutami globalnymi może występować w wielu plikach źródłowych, ale muszą być skompilowane pliki w przebiegu kompilacji pojedynczej.</span><span class="sxs-lookup"><span data-stu-id="0299d-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="0299d-114">W projektach Visual Basic atrybutami globalnymi zazwyczaj są umieszczane w pliku AssemblyInfo.vb (plik jest tworzona automatycznie podczas tworzenia projektu w programie Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="0299d-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="0299d-115">Atrybuty zestawu wartości, które zawierają informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="0299d-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="0299d-116">Ich można podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="0299d-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="0299d-117">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="0299d-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="0299d-118">Atrybuty informacyjny</span><span class="sxs-lookup"><span data-stu-id="0299d-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="0299d-119">Atrybutów manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="0299d-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="0299d-120">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="0299d-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="0299d-121">Trzy atrybuty (przy użyciu silnej nazwy, jeśli ma to zastosowanie) określić tożsamości zestawu: nazwa, wersja i kultury.</span><span class="sxs-lookup"><span data-stu-id="0299d-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="0299d-122">Te atrybuty tworzą Pełna nazwa zestawu i są wymagane w przypadku odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0299d-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="0299d-123">Można ustawić wersja zestawu i kultury przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0299d-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="0299d-124">Jednak wartość nazwy jest ustawiony przez kompilator Visual Studio IDE w [informacji o zestawie — okno dialogowe](/visualstudio/ide/reference/assembly-information-dialog-box), lub Assembly Linker (Al.exe) podczas tworzenia zestawu oparty na pliku, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="0299d-125"><xref:System.Reflection.AssemblyFlagsAttribute> Atrybut określa, czy wiele kopii zestawu mogą współistnieć.</span><span class="sxs-lookup"><span data-stu-id="0299d-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="0299d-126">W poniższej tabeli przedstawiono atrybuty tożsamości.</span><span class="sxs-lookup"><span data-stu-id="0299d-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="0299d-127">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0299d-127">Attribute</span></span>|<span data-ttu-id="0299d-128">Cel</span><span class="sxs-lookup"><span data-stu-id="0299d-128">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="0299d-129">Opis tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-129">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="0299d-130">Określa wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-130">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="0299d-131">Określa, które kultury obsługuje zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-131">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="0299d-132">Określa, czy zestaw obsługuje wykonywanie side-by-side na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0299d-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="0299d-133">Atrybuty informacyjny</span><span class="sxs-lookup"><span data-stu-id="0299d-133">Informational Attributes</span></span>  
 <span data-ttu-id="0299d-134">Atrybuty informacyjną umożliwia zapewniają dodatkowe firmy lub informacji o produkcie dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="0299d-135">W poniższej tabeli przedstawiono atrybuty informacyjną zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0299d-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="0299d-136">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0299d-136">Attribute</span></span>|<span data-ttu-id="0299d-137">Cel</span><span class="sxs-lookup"><span data-stu-id="0299d-137">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="0299d-138">Definiuje atrybut niestandardowy, który określa nazwę produktu dla manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="0299d-139">Określa niestandardowy atrybut, który określa znak towarowy dla manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="0299d-140">Określa niestandardowy atrybut, który określa wersję informacyjny dla manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="0299d-141">Definiuje atrybut niestandardowy, który określa nazwę firmy dla manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="0299d-142">Definiuje atrybut niestandardowy, który określa copyright dla manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="0299d-143">Instruuje kompilator, aby używał odpowiedniego numeru wersji dla zasobu wersji pliku Win32.</span><span class="sxs-lookup"><span data-stu-id="0299d-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="0299d-144">Wskazuje, czy zestaw jest zgodne z typowych specyfikacji języka (CLS).</span><span class="sxs-lookup"><span data-stu-id="0299d-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="0299d-145">Atrybutów manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="0299d-145">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="0299d-146">Atrybutów manifestu zestawu można użyć, aby podać informacje w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="0299d-147">W tym tytuł, opis, domyślny alias i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0299d-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="0299d-148">W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0299d-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="0299d-149">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0299d-149">Attribute</span></span>|<span data-ttu-id="0299d-150">Cel</span><span class="sxs-lookup"><span data-stu-id="0299d-150">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="0299d-151">Określa niestandardowy atrybut, który określa tytuł zestawu dla manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="0299d-152">Definiuje atrybut niestandardowy, który określa opis zestawu dla manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="0299d-153">Określa niestandardowy atrybut, który określa konfigurację zestawu (na przykład detalicznych lub debugowanych) dla manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0299d-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="0299d-154">Definiuje alias domyślne przyjazną dla manifest zestawu</span><span class="sxs-lookup"><span data-stu-id="0299d-154">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="0299d-155">Atrybut przestarzałe</span><span class="sxs-lookup"><span data-stu-id="0299d-155">Obsolete Attribute</span></span>  
 <span data-ttu-id="0299d-156">`Obsolete` Atrybut oznacza jednostki programu, co nie jest zalecane używanie.</span><span class="sxs-lookup"><span data-stu-id="0299d-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="0299d-157">Każdym użyciu jednostki oznaczony jako przestarzały później spowoduje wygenerowanie ostrzeżenia lub błędu, w zależności od sposobu skonfigurowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0299d-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="0299d-158">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0299d-158">For example:</span></span>  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="0299d-159">W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` i do metody `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="0299d-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="0299d-160">Ponieważ drugi argument konstruktora atrybutu stosowane do `B.OldMethod` ma ustawioną wartość `true`, ta metoda spowoduje błąd kompilatora, należy za pomocą klasy `A` będą tylko produktu ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="0299d-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="0299d-161">Wywoływanie `B.NewMethod`, jednak generuje nie ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="0299d-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="0299d-162">Dostarczony jako pierwszy argument do konstruktora atrybutu ciąg będą wyświetlane jako część ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="0299d-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="0299d-163">Na przykład przypadku użycia jej wraz z definicjami poprzedniej następujący kod generuje dwa ostrzeżenia i jeden błąd:</span><span class="sxs-lookup"><span data-stu-id="0299d-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="0299d-164">Dwa ostrzeżenia dla klasy `A` są generowane: jeden dla deklaracji odwołania do klasy, a drugi dla konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="0299d-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="0299d-165">`Obsolete` Atrybut może być używany bez argumentów, ale łącznie z wyjaśnieniem przyczyny element jest przestarzały i co należy użyć zamiast tego zaleca się.</span><span class="sxs-lookup"><span data-stu-id="0299d-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="0299d-166">`Obsolete` Atrybut jest atrybutem jednorazowego użytku i mogą być stosowane do dowolnej jednostki, który umożliwia atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0299d-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="0299d-167">`Obsolete` alias jest <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0299d-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="0299d-168">Atrybut Conditional</span><span class="sxs-lookup"><span data-stu-id="0299d-168">Conditional Attribute</span></span>  
 <span data-ttu-id="0299d-169">`Conditional` Atrybut powoduje, że wykonanie metody są zależne od identyfikatora przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="0299d-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="0299d-170">`Conditional` Atrybutu jest aliasem <xref:System.Diagnostics.ConditionalAttribute>, można zastosować do metody lub atrybut klasy.</span><span class="sxs-lookup"><span data-stu-id="0299d-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="0299d-171">W tym przykładzie `Conditional` jest zastosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych programów:</span><span class="sxs-lookup"><span data-stu-id="0299d-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="0299d-172">Jeśli `TRACE_ON` nie zdefiniowano identyfikatora, będą wyświetlane nie dane śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0299d-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="0299d-173">`Conditional` Atrybutu jest często używane z `DEBUG` identyfikator do włączenia śledzenia i funkcje rejestrowania debugowania kompilacji, lecz nie w wersji kompilacji, podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="0299d-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="0299d-174">Po wywołaniu metody oznaczone jako warunkowego obecności lub braku określony symbol przetwarzania wstępnego Określa, czy wywołanie jest włączone, czy pominięcia.</span><span class="sxs-lookup"><span data-stu-id="0299d-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="0299d-175">Jeśli symbol jest zdefiniowany, wywołanie jest dołączony; w przeciwnym razie połączenie zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="0299d-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="0299d-176">Przy użyciu `Conditional` czyszczenia, jest bardziej elegancki i mniej podatne na błędy zamiast otaczającej metody wewnątrz `#if…#endif` bloków w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0299d-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="0299d-177">Metody warunkowego musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="0299d-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="0299d-178">Przy użyciu wielu identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="0299d-178">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="0299d-179">Jeśli metoda ma wiele `Conditional` atrybuty, wywołanie do metody wchodzi Jeśli zdefiniowano co najmniej jeden z symboli warunkowego (innymi słowy, symbole są logicznie połączone ze sobą za pomocą operatora OR).</span><span class="sxs-lookup"><span data-stu-id="0299d-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="0299d-180">W tym przykładzie obecności albo `A` lub `B` spowoduje wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="0299d-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="0299d-181">Aby osiągnąć efekt logicznie łączenia symbole przy użyciu operatora AND, można zdefiniować serial metoda warunkowa.</span><span class="sxs-lookup"><span data-stu-id="0299d-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="0299d-182">Na przykład, druga metoda poniżej będą wykonywane tylko wtedy, gdy oba `A` i `B` są zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="0299d-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="0299d-183">Przy użyciu warunkowego z klas atrybutów</span><span class="sxs-lookup"><span data-stu-id="0299d-183">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="0299d-184">`Conditional` Atrybut można stosować do definicji klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0299d-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="0299d-185">W tym przykładzie atrybut niestandardowy `Documentation` tylko spowoduje dodanie informacji metadanych czy DEBUG jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="0299d-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <a name="CallerInfo"></a> <span data-ttu-id="0299d-186">Caller — atrybuty informacji</span><span class="sxs-lookup"><span data-stu-id="0299d-186">Caller Info Attributes</span></span>  
 <span data-ttu-id="0299d-187">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="0299d-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="0299d-188">Możesz uzyskać ścieżka pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0299d-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="0299d-189">Aby uzyskać informacje o wywołującym — członek, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="0299d-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="0299d-190">Każdy parametr opcjonalny określenie wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="0299d-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="0299d-191">Poniższa tabela zawiera listę atrybutów wywołującego informacje, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="0299d-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="0299d-192">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0299d-192">Attribute</span></span>|<span data-ttu-id="0299d-193">Opis</span><span class="sxs-lookup"><span data-stu-id="0299d-193">Description</span></span>|<span data-ttu-id="0299d-194">Typ</span><span class="sxs-lookup"><span data-stu-id="0299d-194">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="0299d-195">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0299d-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="0299d-196">Jest to ścieżka w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0299d-196">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="0299d-197">Numer wiersza w pliku źródłowym, z którego ma zostać wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="0299d-197">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="0299d-198">Nazwa metody lub właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0299d-198">Method name or property name of the caller.</span></span> <span data-ttu-id="0299d-199">Aby uzyskać więcej informacji, zobacz [informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="0299d-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="0299d-200">Aby uzyskać więcej informacji o atrybutach wywołującego informacji, zobacz [informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="0299d-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <a name="VB"></a> <span data-ttu-id="0299d-201">Atrybuty Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0299d-201">Visual Basic Attributes</span></span>  
 <span data-ttu-id="0299d-202">W poniższej tabeli przedstawiono atrybuty, które są specyficzne dla języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0299d-202">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="0299d-203">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0299d-203">Attribute</span></span>|<span data-ttu-id="0299d-204">Cel</span><span class="sxs-lookup"><span data-stu-id="0299d-204">Purpose</span></span>|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="0299d-205">W kompilatorze wskazuje, czy obiekt modelu COM powinny zostać ujawnione klasy.</span><span class="sxs-lookup"><span data-stu-id="0299d-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="0299d-206">Zezwala członkom modułu można uzyskać dostęp przy użyciu kwalifikacji potrzebne dla modułu.</span><span class="sxs-lookup"><span data-stu-id="0299d-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="0299d-207">Określa rozmiar ciągu o stałej długości w strukturze do użycia z plikiem danych wejściowych i wyjściowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="0299d-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="0299d-208">Określa rozmiar tablicy o ustalonym w strukturze do użycia z plikiem danych wejściowych i wyjściowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="0299d-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="0299d-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="0299d-209">COMClassAttribute</span></span>  
 <span data-ttu-id="0299d-210">Użyj `COMClassAttribute` w celu uproszczenia procesu tworzenia składników COM z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0299d-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="0299d-211">Obiekty COM są znacznie różne zestawy .NET Framework i nie `COMClassAttribute`, należy wykonać kilka czynności, aby wygenerować obiektów COM z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0299d-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="0299d-212">Dla klasy oznaczonej `COMClassAttribute`, kompilator wykonuje wiele z tych kroków automatycznie.</span><span class="sxs-lookup"><span data-stu-id="0299d-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="0299d-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="0299d-213">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="0299d-214">Użyj `HideModuleNameAttribute` aby umożliwić członkom modułu można uzyskać dostęp za pomocą kwalifikacji potrzebne dla modułu.</span><span class="sxs-lookup"><span data-stu-id="0299d-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="0299d-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="0299d-215">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="0299d-216">Użyj `VBFixedStringAttribute` wymusić Visual Basic, aby utworzyć ciąg o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="0299d-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="0299d-217">Ciągi są o zmiennej długości domyślnie, a ten atrybut jest przydatne, gdy przechowywanie ciągów w plikach.</span><span class="sxs-lookup"><span data-stu-id="0299d-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="0299d-218">Poniższy kod ilustruje to:</span><span class="sxs-lookup"><span data-stu-id="0299d-218">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="0299d-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="0299d-219">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="0299d-220">Użyj `VBFixedArrayAttribute` można deklarować tablic, które stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="0299d-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="0299d-221">Podobnie jak ciągi Visual Basic tablic są o zmiennej długości domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0299d-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="0299d-222">Ten atrybut jest przydatne w przypadku serializacji lub zapisywanie danych w plikach.</span><span class="sxs-lookup"><span data-stu-id="0299d-222">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0299d-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0299d-223">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="0299d-224">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0299d-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="0299d-225">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0299d-225">Attributes</span></span>](../../../../standard/attributes/index.md)  
 [<span data-ttu-id="0299d-226">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0299d-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="0299d-227">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0299d-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
