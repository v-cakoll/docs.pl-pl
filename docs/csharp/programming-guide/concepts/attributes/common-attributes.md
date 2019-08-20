---
title: Atrybuty wspólne (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595459"
---
# <a name="common-attributes-c"></a><span data-ttu-id="05841-102">Atrybuty wspólne (C#)</span><span class="sxs-lookup"><span data-stu-id="05841-102">Common Attributes (C#)</span></span>
<span data-ttu-id="05841-103">W tym temacie opisano atrybuty, które są najczęściej używane w C# programach.</span><span class="sxs-lookup"><span data-stu-id="05841-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
- [<span data-ttu-id="05841-104">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="05841-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="05841-105">Przestarzały atrybut</span><span class="sxs-lookup"><span data-stu-id="05841-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="05841-106">Atrybut warunkowy</span><span class="sxs-lookup"><span data-stu-id="05841-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="05841-107">Atrybuty informacji o wywołującym</span><span class="sxs-lookup"><span data-stu-id="05841-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
## <a name="Global"></a><span data-ttu-id="05841-108">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="05841-108">Global Attributes</span></span>  
 <span data-ttu-id="05841-109">Większość atrybutów stosuje się do określonych elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="05841-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="05841-110">Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacji o wersji w zestawie, takich jak:</span><span class="sxs-lookup"><span data-stu-id="05841-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="05841-111">Atrybuty globalne pojawiają się w kodzie źródłowym po dowolnych `using` dyrektywach najwyższego poziomu i przed dowolnymi deklaracjami typu, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="05841-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="05841-112">Atrybuty globalne mogą pojawiać się w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="05841-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="05841-113">W C# projektach atrybuty globalne są umieszczane w pliku AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="05841-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="05841-114">Atrybuty zestawu są wartościami, które zawierają informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="05841-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="05841-115">Należą do następujących kategorii:</span><span class="sxs-lookup"><span data-stu-id="05841-115">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="05841-116">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="05841-116">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="05841-117">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="05841-117">Informational attributes</span></span>  
  
- <span data-ttu-id="05841-118">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="05841-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="05841-119">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="05841-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="05841-120">Trzy atrybuty (o silnej nazwie, jeśli ma zastosowanie) określają tożsamość zestawu: nazwę, wersję i kulturę.</span><span class="sxs-lookup"><span data-stu-id="05841-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="05841-121">Te atrybuty tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do niego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="05841-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="05841-122">Możesz ustawić wersję zestawu i kulturę przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="05841-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="05841-123">Jednak wartość nazwy jest ustawiana przez kompilator, środowisko IDE programu Visual Studio w [oknie dialogowym Informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator zestawu (Al. exe) podczas tworzenia zestawu, na podstawie pliku, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="05841-124">Ten <xref:System.Reflection.AssemblyFlagsAttribute> atrybut określa, czy wiele kopii zestawu może współistnieć.</span><span class="sxs-lookup"><span data-stu-id="05841-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="05841-125">W poniższej tabeli przedstawiono atrybuty tożsamości.</span><span class="sxs-lookup"><span data-stu-id="05841-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="05841-126">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05841-126">Attribute</span></span>|<span data-ttu-id="05841-127">Cel</span><span class="sxs-lookup"><span data-stu-id="05841-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="05841-128">W pełni opisuje tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="05841-129">Określa wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="05841-130">Określa kulturę obsługiwaną przez zestaw.</span><span class="sxs-lookup"><span data-stu-id="05841-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="05841-131">Określa, czy zestaw obsługuje wykonywanie równoczesne na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05841-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="05841-132">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="05841-132">Informational Attributes</span></span>  
 <span data-ttu-id="05841-133">Można użyć atrybutów informacyjnych w celu podania dodatkowych informacji o firmie lub produkcie dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="05841-134">W poniższej tabeli przedstawiono atrybuty informacyjne zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="05841-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="05841-135">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05841-135">Attribute</span></span>|<span data-ttu-id="05841-136">Cel</span><span class="sxs-lookup"><span data-stu-id="05841-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="05841-137">Definiuje niestandardowy atrybut, który określa nazwę produktu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="05841-138">Definiuje niestandardowy atrybut, który określa znak towarowy dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="05841-139">Definiuje niestandardowy atrybut, który określa wersję informacyjną dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="05841-140">Definiuje niestandardowy atrybut, który określa nazwę firmy dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="05841-141">Definiuje niestandardowy atrybut, który określa prawo autorskie dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="05841-142">Instruuje kompilator, aby używał określonego numeru wersji dla zasobu wersji plików Win32.</span><span class="sxs-lookup"><span data-stu-id="05841-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="05841-143">Wskazuje, czy zestaw jest zgodny z Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="05841-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="05841-144">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="05841-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="05841-145">Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="05841-146">Obejmuje to tytuł, opis, alias domyślny i konfigurację.</span><span class="sxs-lookup"><span data-stu-id="05841-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="05841-147">W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="05841-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="05841-148">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05841-148">Attribute</span></span>|<span data-ttu-id="05841-149">Cel</span><span class="sxs-lookup"><span data-stu-id="05841-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="05841-150">Definiuje niestandardowy atrybut, który określa tytuł zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="05841-151">Definiuje niestandardowy atrybut, który określa opis zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="05841-152">Definiuje niestandardowy atrybut, który określa konfigurację zestawu (na przykład detaliczną lub Debug) dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="05841-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="05841-153">Definiuje przyjazny alias domyślny dla manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="05841-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a><span data-ttu-id="05841-154">Przestarzały atrybut</span><span class="sxs-lookup"><span data-stu-id="05841-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="05841-155">Ten `Obsolete` atrybut oznacza jednostkę programu, która nie jest już zalecana do użycia.</span><span class="sxs-lookup"><span data-stu-id="05841-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="05841-156">Każde użycie jednostki oznaczonej jako przestarzałe spowoduje wygenerowanie ostrzeżenia lub błędu w zależności od sposobu skonfigurowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="05841-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="05841-157">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="05841-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="05841-158">W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` i metody `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="05841-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="05841-159">Ponieważ drugi argument konstruktora atrybutu stosowany do `B.OldMethod` jest ustawiony na `true`, ta metoda spowoduje błąd kompilatora, podczas gdy użycie klasy `A` spowoduje po prostu wygenerowanie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="05841-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="05841-160">Jednak `B.NewMethod`wywoływanie nie powoduje żadnych ostrzeżeń ani błędów.</span><span class="sxs-lookup"><span data-stu-id="05841-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="05841-161">Ciąg dostarczony jako pierwszy argument konstruktora atrybutu będzie wyświetlany jako część ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="05841-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="05841-162">Na przykład jeśli używasz go z poprzednimi definicjami, poniższy kod generuje dwie ostrzeżenia i jeden błąd:</span><span class="sxs-lookup"><span data-stu-id="05841-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="05841-163">Generowane są dwa ostrzeżenia `A` dla klasy: jeden dla deklaracji klasy Reference i jeden dla konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="05841-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="05841-164">Ten `Obsolete` atrybut może być używany bez argumentów, ale wraz z wyjaśnieniem dlaczego element jest przestarzały i czego należy używać.</span><span class="sxs-lookup"><span data-stu-id="05841-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="05841-165">Ten `Obsolete` atrybut jest atrybutem jednokrotnego użycia i może być stosowany do każdej jednostki, która zezwala na atrybuty.</span><span class="sxs-lookup"><span data-stu-id="05841-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="05841-166">`Obsolete`jest aliasem dla <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="05841-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a><span data-ttu-id="05841-167">Atrybut warunkowy</span><span class="sxs-lookup"><span data-stu-id="05841-167">Conditional Attribute</span></span>  
 <span data-ttu-id="05841-168">Ten `Conditional` atrybut wykonuje metodę zależną od identyfikatora przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="05841-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="05841-169">Atrybut jest alias dla <xref:System.Diagnostics.ConditionalAttribute>i może być zastosowany do metody lub klasy atrybutu. `Conditional`</span><span class="sxs-lookup"><span data-stu-id="05841-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="05841-170">W tym przykładzie `Conditional` stosuje się do metody w celu włączenia lub wyłączenia wyświetlania informacji diagnostycznych specyficznych dla programu:</span><span class="sxs-lookup"><span data-stu-id="05841-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="05841-171">`TRACE_ON` Jeśli identyfikator nie jest zdefiniowany, nie będą wyświetlane dane wyjściowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="05841-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="05841-172">Ten `Conditional` atrybut jest często używany `DEBUG` z identyfikatorem, aby włączyć funkcje śledzenia i rejestrowania dla kompilacji debugowania, ale nie w kompilacjach wydania, takich jak:</span><span class="sxs-lookup"><span data-stu-id="05841-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="05841-173">Gdy wywoływana jest metoda oznaczona jako warunkowa, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie jest dołączone czy pominięte.</span><span class="sxs-lookup"><span data-stu-id="05841-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="05841-174">Jeśli symbol jest zdefiniowany, wywołanie jest dołączone; w przeciwnym razie wywołanie zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="05841-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="05841-175">Korzystanie `Conditional` z programu to przejrzysty, bardziej elegancki i mniej podatny na błędy alternatywa dla otaczających `#if…#endif` metod w blokach, takich jak:</span><span class="sxs-lookup"><span data-stu-id="05841-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="05841-176">Metoda warunkowa musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="05841-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="05841-177">Używanie wielu identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="05841-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="05841-178">Jeśli metoda ma wiele `Conditional` atrybutów, wywołanie metody jest uwzględnione, jeśli co najmniej jeden z symboli warunkowych jest zdefiniowany (innymi słowy, symbole są logicznie połączone ze sobą przy użyciu operatora OR).</span><span class="sxs-lookup"><span data-stu-id="05841-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="05841-179">W tym przykładzie, obecność albo `A` `B` spowoduje wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="05841-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="05841-180">Aby osiągnąć efekt logicznego łączenia symboli za pomocą operatora i, można zdefiniować metody warunkowe szeregowe.</span><span class="sxs-lookup"><span data-stu-id="05841-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="05841-181">Na przykład druga metoda zostanie wykonana tylko wtedy, gdy obie `A` i `B` są zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="05841-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="05841-182">Używanie warunkowe z klasami atrybutów</span><span class="sxs-lookup"><span data-stu-id="05841-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="05841-183">Ten `Conditional` atrybut może być również stosowany do definicji klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="05841-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="05841-184">W tym przykładzie atrybut `Documentation` niestandardowy będzie dodawać tylko informacje do metadanych w przypadku zdefiniowania debugowania.</span><span class="sxs-lookup"><span data-stu-id="05841-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
## <a name="CallerInfo"></a><span data-ttu-id="05841-185">Atrybuty informacji o wywołującym</span><span class="sxs-lookup"><span data-stu-id="05841-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="05841-186">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="05841-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="05841-187">Możesz uzyskać ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="05841-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="05841-188">Aby uzyskać informacje o obiekcie wywołującym elementu członkowskiego, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="05841-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="05841-189">Każdy opcjonalny parametr określa wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="05841-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="05841-190">W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> zdefiniowane w przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="05841-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="05841-191">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05841-191">Attribute</span></span>|<span data-ttu-id="05841-192">Opis</span><span class="sxs-lookup"><span data-stu-id="05841-192">Description</span></span>|<span data-ttu-id="05841-193">Typ</span><span class="sxs-lookup"><span data-stu-id="05841-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="05841-194">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="05841-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="05841-195">Jest to ścieżka w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="05841-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="05841-196">Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="05841-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="05841-197">Nazwa metody lub nazwa właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="05841-197">Method name or property name of the caller.</span></span> <span data-ttu-id="05841-198">Aby uzyskać więcej informacji, zobacz [Informacje oC#wywołującym ()](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="05841-198">For more information, see [Caller Information (C#)](../caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="05841-199">Aby uzyskać więcej informacji o atrybutach informacji o wywołującym, zobacz [Informacje o wywołującymC#()](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="05841-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05841-200">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05841-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="05841-201">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="05841-201">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="05841-202">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05841-202">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="05841-203">OdbicieC#()</span><span class="sxs-lookup"><span data-stu-id="05841-203">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="05841-204">Uzyskiwanie dostępu do atrybutów przyC#użyciu odbicia ()</span><span class="sxs-lookup"><span data-stu-id="05841-204">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
