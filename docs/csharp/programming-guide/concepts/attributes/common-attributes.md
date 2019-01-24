---
title: Atrybuty wspólne (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 4a1dd6200f7eb9e69caefe62d9e9defd90856ce1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558595"
---
# <a name="common-attributes-c"></a><span data-ttu-id="0ef73-102">Atrybuty wspólne (C#)</span><span class="sxs-lookup"><span data-stu-id="0ef73-102">Common Attributes (C#)</span></span>
<span data-ttu-id="0ef73-103">W tym temacie opisano atrybuty, które są najczęściej używane w programach języka C#.</span><span class="sxs-lookup"><span data-stu-id="0ef73-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
-   [<span data-ttu-id="0ef73-104">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="0ef73-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="0ef73-105">Atrybut przestarzałe</span><span class="sxs-lookup"><span data-stu-id="0ef73-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="0ef73-106">Atrybut Conditional</span><span class="sxs-lookup"><span data-stu-id="0ef73-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="0ef73-107">Caller — atrybuty informacji</span><span class="sxs-lookup"><span data-stu-id="0ef73-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
##  <a name="Global"></a> <span data-ttu-id="0ef73-108">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="0ef73-108">Global Attributes</span></span>  
 <span data-ttu-id="0ef73-109">Większość atrybuty są stosowane do elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — odnoszą się do całego zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="0ef73-110">Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacje o wersji w zespół, takich jak to:</span><span class="sxs-lookup"><span data-stu-id="0ef73-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="0ef73-111">Atrybuty globalne są wyświetlane w kodzie źródłowym po każdym najwyższego poziomu `using` dyrektyw i przed deklaracjami dowolnego typu, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0ef73-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="0ef73-112">Atrybuty globalne mogą być wyświetlane w wielu plikach źródłowych, ale pliki muszą być skompilowane w pojedynczej kompilacji przebiegu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="0ef73-113">W projektach C# atrybuty globalne są umieszczane w pliku AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="0ef73-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="0ef73-114">Atrybuty zestawu są wartości, które dostarczają informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="0ef73-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="0ef73-115">Można je podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="0ef73-115">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="0ef73-116">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="0ef73-116">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="0ef73-117">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="0ef73-117">Informational attributes</span></span>  
  
-   <span data-ttu-id="0ef73-118">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="0ef73-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="0ef73-119">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="0ef73-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="0ef73-120">Trzy atrybuty (silną nazwą, jeśli ma to zastosowanie) określają tożsamość zestawu: nazwę, wersję i kulturę.</span><span class="sxs-lookup"><span data-stu-id="0ef73-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="0ef73-121">Te atrybuty tworzą pełną nazwę zestawu i są wymagane, gdy można się odwoływać w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0ef73-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="0ef73-122">Można ustawić wersję i kulturę przy użyciu atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="0ef73-123">Jednak nazwa ma wartość przez kompilator programu Visual Studio IDE w [informacje o zestawie — okno dialogowe](/visualstudio/ide/reference/assembly-information-dialog-box), lub Assembly Linker (Al.exe), po utworzeniu zestawu w oparciu o plik, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="0ef73-124"><xref:System.Reflection.AssemblyFlagsAttribute> Atrybut określa, czy wiele kopii zestawu mogą współistnieć.</span><span class="sxs-lookup"><span data-stu-id="0ef73-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="0ef73-125">W poniższej tabeli przedstawiono atrybuty tożsamości.</span><span class="sxs-lookup"><span data-stu-id="0ef73-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="0ef73-126">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0ef73-126">Attribute</span></span>|<span data-ttu-id="0ef73-127">Cel</span><span class="sxs-lookup"><span data-stu-id="0ef73-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="0ef73-128">W pełni opisuje tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="0ef73-129">Określa wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="0ef73-130">Określa, które kultury obsługuje zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="0ef73-131">Określa, czy zestaw obsługuje wykonywanie side-by-side na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ef73-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="0ef73-132">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="0ef73-132">Informational Attributes</span></span>  
 <span data-ttu-id="0ef73-133">Aby zapewnić dodatkowe firmy lub informacje o produkcie dla zestawu, można użyć atrybuty informacyjne.</span><span class="sxs-lookup"><span data-stu-id="0ef73-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="0ef73-134">W poniższej tabeli przedstawiono atrybuty informacyjne, zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0ef73-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="0ef73-135">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0ef73-135">Attribute</span></span>|<span data-ttu-id="0ef73-136">Cel</span><span class="sxs-lookup"><span data-stu-id="0ef73-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="0ef73-137">Określa niestandardowy atrybut, który określa nazwę produktu w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="0ef73-138">Definiuje atrybutu niestandardowego, który określa znak towarowy manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="0ef73-139">Określa niestandardowy atrybut, który określa informacjami o wersji dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="0ef73-140">Określa atrybut niestandardowy, który określa nazwę firmy na potrzeby manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="0ef73-141">Określa niestandardowy atrybut, który określa prawa autorskiego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="0ef73-142">Instruuje kompilator, aby użyć numeru wersji określonej dla zasobu wersji pliku systemu Win32.</span><span class="sxs-lookup"><span data-stu-id="0ef73-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="0ef73-143">Wskazuje, czy zestaw jest zgodny z Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="0ef73-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="0ef73-144">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="0ef73-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="0ef73-145">Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="0ef73-146">W tym tytuł, opis, domyślny alias i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0ef73-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="0ef73-147">W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowanych w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0ef73-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="0ef73-148">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0ef73-148">Attribute</span></span>|<span data-ttu-id="0ef73-149">Cel</span><span class="sxs-lookup"><span data-stu-id="0ef73-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="0ef73-150">Określa niestandardowy atrybut, który określa tytuł zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="0ef73-151">Określa niestandardowy atrybut, który określa opis zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="0ef73-152">Definiuje niestandardowy atrybut, który określa konfigurację zestawu (na przykład sprzedaży detalicznej lub debugowanie) w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="0ef73-153">Określa przyjazną domyślny alias manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="0ef73-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="0ef73-154">Atrybut przestarzałe</span><span class="sxs-lookup"><span data-stu-id="0ef73-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="0ef73-155">`Obsolete` Atrybut oznacza jednostka program jako taki, który nie jest już zalecany do użycia.</span><span class="sxs-lookup"><span data-stu-id="0ef73-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="0ef73-156">Każde użycie jednostki oznaczony jako przestarzały później, spowoduje wygenerowanie ostrzeżenia lub błędu, w zależności od sposobu skonfigurowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="0ef73-157">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0ef73-157">For example:</span></span>  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 <span data-ttu-id="0ef73-158">W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` oraz metody `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="0ef73-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="0ef73-159">Ponieważ drugi argument konstruktora atrybutu jest stosowane do `B.OldMethod` ustawiono `true`, ta metoda spowoduje błąd kompilatora, natomiast przy użyciu klasy `A` będzie po prostu wygenerować ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="0ef73-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="0ef73-160">Wywoływanie `B.NewMethod`, jednak generuje nie ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="0ef73-161">Ciąg, podana jako pierwszy argument konstruktora atrybutu będą wyświetlane jako część ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="0ef73-162">Na przykład podczas korzystania z poprzednim definicje, poniższy kod generuje dwa ostrzeżenia i jeden błąd:</span><span class="sxs-lookup"><span data-stu-id="0ef73-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="0ef73-163">Dwa ostrzeżenia dla klasy `A` są generowane: jeden dla deklaracji odwołań do klas i jeden dla konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="0ef73-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="0ef73-164">`Obsolete` Atrybut może być używana bez argumentów, ale tym wyjaśnienie, dlaczego elementu jest przestarzały i nie zamiast tego użyć zalecanych.</span><span class="sxs-lookup"><span data-stu-id="0ef73-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="0ef73-165">`Obsolete` Atrybut jest atrybutem jednorazowego użytku i mogą być stosowane do każda jednostka, która umożliwia atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0ef73-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="0ef73-166">`Obsolete` jest aliasem <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0ef73-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="0ef73-167">Atrybut Conditional</span><span class="sxs-lookup"><span data-stu-id="0ef73-167">Conditional Attribute</span></span>  
 <span data-ttu-id="0ef73-168">`Conditional` Atrybutu sprawia, że wykonanie metody są zależne od identyfikatora przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="0ef73-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="0ef73-169">`Conditional` Atrybut jest aliasem <xref:System.Diagnostics.ConditionalAttribute>i mogą być stosowane do metodę lub klasę atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0ef73-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="0ef73-170">W tym przykładzie `Conditional` zostanie zastosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych programów:</span><span class="sxs-lookup"><span data-stu-id="0ef73-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 <span data-ttu-id="0ef73-171">Jeśli `TRACE_ON` identyfikator nie jest zdefiniowany, będą wyświetlane żadne dane wyjściowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0ef73-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="0ef73-172">`Conditional` Atrybutu jest często używana z `DEBUG` identyfikator, aby włączyć śledzenie i rejestrowanie funkcji, wydajność debugowania kompilacji, ale nie w wersji kompilacji, podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="0ef73-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="0ef73-173">Gdy wywoływana jest metoda oznaczona jako warunkowe, obecności lub braku określonego symbolu przetwarzania wstępnego Określa, czy wywołanie jest włączone, czy pominięty.</span><span class="sxs-lookup"><span data-stu-id="0ef73-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="0ef73-174">Jeśli zdefiniowano symbol wywołanie jest uwzględniany; w przeciwnym razie wywołanie zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="0ef73-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="0ef73-175">Za pomocą `Conditional` jest bardziej przejrzystą i bardziej eleganckim i mniej podatne na błędy zamiast otaczającej metody wewnątrz `#if…#endif` bloki następująco:</span><span class="sxs-lookup"><span data-stu-id="0ef73-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="0ef73-176">Metoda warunkowego musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="0ef73-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="0ef73-177">Przy użyciu wielu identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="0ef73-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="0ef73-178">Jeśli metoda ma wiele `Conditional` atrybutów, wywołanie do metody jest dołączona, jeśli zdefiniowano co najmniej jeden z warunkowego symbole (innymi słowy, symbole są logicznie połączone ze sobą za pomocą operatora OR).</span><span class="sxs-lookup"><span data-stu-id="0ef73-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="0ef73-179">W tym przykładzie obecności albo `A` lub `B` spowoduje wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="0ef73-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="0ef73-180">Aby osiągnąć ten efekt logicznie łączenia symbole za pomocą operatora AND, można zdefiniować serial metoda warunkowa.</span><span class="sxs-lookup"><span data-stu-id="0ef73-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="0ef73-181">Na przykład, druga metoda poniżej będą wykonywane tylko wtedy, gdy oba `A` i `B` są zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="0ef73-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="0ef73-182">Używanie warunkowego z klas atrybutów</span><span class="sxs-lookup"><span data-stu-id="0ef73-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="0ef73-183">`Conditional` Atrybut można stosować do definicji klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ef73-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="0ef73-184">W tym przykładzie atrybut niestandardowy `Documentation` tylko doda informacje metadanych Jeśli DEBUG jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="0ef73-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
##  <a name="CallerInfo"></a> <span data-ttu-id="0ef73-185">Caller — atrybuty informacji</span><span class="sxs-lookup"><span data-stu-id="0ef73-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="0ef73-186">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="0ef73-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="0ef73-187">Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0ef73-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="0ef73-188">Aby uzyskać informacje o wywołującym elementu członkowskiego, należy użyć atrybutów stosowanych do opcjonalnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="0ef73-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="0ef73-189">Każdy parametr opcjonalny określenie wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="0ef73-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="0ef73-190">W poniższej tabeli przedstawiono atrybuty informacji o obiekcie wywołującym, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="0ef73-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="0ef73-191">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0ef73-191">Attribute</span></span>|<span data-ttu-id="0ef73-192">Opis</span><span class="sxs-lookup"><span data-stu-id="0ef73-192">Description</span></span>|<span data-ttu-id="0ef73-193">Typ</span><span class="sxs-lookup"><span data-stu-id="0ef73-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="0ef73-194">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0ef73-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="0ef73-195">Jest to ścieżka w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0ef73-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="0ef73-196">Numer wiersza w pliku źródłowym, w którym metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="0ef73-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="0ef73-197">Nazwa metody lub właściwości name obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0ef73-197">Method name or property name of the caller.</span></span> <span data-ttu-id="0ef73-198">Aby uzyskać więcej informacji, zobacz [informacje o wywołującym (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="0ef73-198">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="0ef73-199">Aby uzyskać więcej informacji na temat atrybutów informacji o obiekcie wywołującym zobacz [informacje o wywołującym (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="0ef73-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef73-200">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ef73-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="0ef73-201">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0ef73-201">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0ef73-202">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0ef73-202">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="0ef73-203">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="0ef73-203">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="0ef73-204">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="0ef73-204">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
