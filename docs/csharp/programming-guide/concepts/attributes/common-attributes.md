---
title: Typowe atrybuty (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399757"
---
# <a name="common-attributes-c"></a><span data-ttu-id="b6449-102">Typowe atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="b6449-102">Common Attributes (C#)</span></span>
<span data-ttu-id="b6449-103">W tym temacie opisano atrybuty, które są najczęściej używane w programach Języka C#.</span><span class="sxs-lookup"><span data-stu-id="b6449-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
- [<span data-ttu-id="b6449-104">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="b6449-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="b6449-105">Przestarzały atrybut</span><span class="sxs-lookup"><span data-stu-id="b6449-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="b6449-106">Atrybut warunkowy</span><span class="sxs-lookup"><span data-stu-id="b6449-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="b6449-107">Atrybuty informacji o obiekcie wywołującym</span><span class="sxs-lookup"><span data-stu-id="b6449-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
## <a name="Global"></a><span data-ttu-id="b6449-108">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="b6449-108">Global Attributes</span></span>  
 <span data-ttu-id="b6449-109">Większość atrybutów są stosowane do określonych elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="b6449-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="b6449-110">Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacji o wersji w zestawie, w tym sposób:</span><span class="sxs-lookup"><span data-stu-id="b6449-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="b6449-111">Atrybuty globalne są wyświetlane w kodzie `using` źródłowym po dowolnych dyrektywach najwyższego poziomu i przed dowolnym typem, modułem lub deklaracjami obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="b6449-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="b6449-112">Atrybuty globalne mogą być wyświetlane w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b6449-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="b6449-113">W projektach języka C# atrybuty globalne są umieszczane w pliku AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="b6449-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="b6449-114">Atrybuty zestawu są wartościami, które dostarczają informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="b6449-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="b6449-115">Należą one do następujących kategorii:</span><span class="sxs-lookup"><span data-stu-id="b6449-115">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="b6449-116">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="b6449-116">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="b6449-117">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="b6449-117">Informational attributes</span></span>  
  
- <span data-ttu-id="b6449-118">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="b6449-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="b6449-119">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="b6449-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="b6449-120">Trzy atrybuty (o silnej nazwie, jeśli dotyczy) określają tożsamość zestawu: nazwa, wersja i kultura.</span><span class="sxs-lookup"><span data-stu-id="b6449-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="b6449-121">Atrybuty te tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do niego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b6449-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="b6449-122">Można ustawić wersję zestawu i kultury przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b6449-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="b6449-123">Jednak wartość name jest ustawiana przez kompilator, IDE programu Visual Studio w [oknie dialogowym Informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator aplikacyjny zestawu (Al.exe) po utworzeniu zestawu na podstawie pliku zawierającego manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="b6449-124">Atrybut <xref:System.Reflection.AssemblyFlagsAttribute> określa, czy wiele kopii zestawu może współistnieć.</span><span class="sxs-lookup"><span data-stu-id="b6449-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="b6449-125">W poniższej tabeli przedstawiono atrybuty tożsamości.</span><span class="sxs-lookup"><span data-stu-id="b6449-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="b6449-126">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6449-126">Attribute</span></span>|<span data-ttu-id="b6449-127">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="b6449-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="b6449-128">W pełni opisuje tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="b6449-129">Określa wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="b6449-130">Określa, która kultura obsługuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="b6449-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="b6449-131">Określa, czy zestaw obsługuje wykonywanie obok siebie na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6449-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="b6449-132">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="b6449-132">Informational Attributes</span></span>  
 <span data-ttu-id="b6449-133">Atrybutów informacyjnych można użyć do podania dodatkowych informacji o firmie lub produkcie dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="b6449-134">W poniższej tabeli przedstawiono atrybuty informacyjne <xref:System.Reflection?displayProperty=nameWithType> zdefiniowane w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="b6449-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="b6449-135">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6449-135">Attribute</span></span>|<span data-ttu-id="b6449-136">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="b6449-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="b6449-137">Definiuje atrybut niestandardowy, który określa nazwę produktu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="b6449-138">Definiuje atrybut niestandardowy, który określa znak towarowy dla manifestu złożenia.</span><span class="sxs-lookup"><span data-stu-id="b6449-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="b6449-139">Definiuje atrybut niestandardowy, który określa wersję informacyjną dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="b6449-140">Definiuje atrybut niestandardowy, który określa nazwę firmy dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="b6449-141">Definiuje atrybut niestandardowy, który określa prawa autorskie do manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="b6449-142">Instruuje kompilator, aby użył określonego numeru wersji dla zasobu wersji pliku Win32.</span><span class="sxs-lookup"><span data-stu-id="b6449-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="b6449-143">Wskazuje, czy zestaw jest zgodny ze specyfikacją języka wspólnego (CLS).</span><span class="sxs-lookup"><span data-stu-id="b6449-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="b6449-144">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="b6449-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="b6449-145">Atrybuty manifestu zestawu można użyć do dostarczenia informacji w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="b6449-146">Obejmuje to tytuł, opis, alias domyślny i konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b6449-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="b6449-147">W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w obszarze <xref:System.Reflection?displayProperty=nameWithType> nazw.</span><span class="sxs-lookup"><span data-stu-id="b6449-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="b6449-148">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6449-148">Attribute</span></span>|<span data-ttu-id="b6449-149">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="b6449-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="b6449-150">Definiuje atrybut niestandardowy, który określa tytuł zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="b6449-151">Definiuje atrybut niestandardowy, który określa opis zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="b6449-152">Definiuje atrybut niestandardowy, który określa konfigurację zestawu (na przykład sprzedaży detalicznej lub debugowania) dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6449-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="b6449-153">Definiuje przyjazny alias domyślny dla manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="b6449-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a><span data-ttu-id="b6449-154">Przestarzały atrybut</span><span class="sxs-lookup"><span data-stu-id="b6449-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="b6449-155">Atrybut `Obsolete` oznacza jednostkę programu jako jednostkę, która nie jest już zalecana do użycia.</span><span class="sxs-lookup"><span data-stu-id="b6449-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="b6449-156">Każde użycie jednostki oznaczone jako przestarzałe spowoduje następnie wygenerować ostrzeżenie lub błąd, w zależności od sposobu skonfigurowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b6449-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="b6449-157">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b6449-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="b6449-158">W tym `Obsolete` przykładzie atrybut jest `A` stosowany do `B.OldMethod`klasy i metody .</span><span class="sxs-lookup"><span data-stu-id="b6449-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="b6449-159">Ponieważ drugi argument konstruktora atrybutu stosowane do `B.OldMethod` jest ustawiona na `true`, ta metoda `A` spowoduje błąd kompilatora, podczas gdy przy użyciu klasy będzie po prostu utworzyć ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="b6449-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="b6449-160">Wywołanie `B.NewMethod`, jednak nie generuje żadnego ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="b6449-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="b6449-161">Ciąg podany jako pierwszy argument konstruktora atrybutu zostanie wyświetlony jako część ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="b6449-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="b6449-162">Na przykład, gdy używasz go z poprzednimi definicjami, poniższy kod generuje dwa ostrzeżenia i jeden błąd:</span><span class="sxs-lookup"><span data-stu-id="b6449-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="b6449-163">Generowane są dwa `A` ostrzeżenia dla klasy: jeden dla deklaracji odwołania do klasy i jeden dla konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="b6449-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="b6449-164">Atrybut `Obsolete` może być używany bez argumentów, ale w tym wyjaśnienie, dlaczego element jest przestarzały i co zamiast tego jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="b6449-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="b6449-165">Atrybut `Obsolete` jest atrybutem jednorazowego użytku i może być stosowany do dowolnej encji, która zezwala na atrybuty.</span><span class="sxs-lookup"><span data-stu-id="b6449-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="b6449-166">`Obsolete`jest aliasem <xref:System.ObsoleteAttribute>dla .</span><span class="sxs-lookup"><span data-stu-id="b6449-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a><span data-ttu-id="b6449-167">Atrybut warunkowy</span><span class="sxs-lookup"><span data-stu-id="b6449-167">Conditional Attribute</span></span>  
 <span data-ttu-id="b6449-168">Atrybut `Conditional` sprawia, że wykonanie metody zależy od identyfikatora wstępnego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b6449-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="b6449-169">Atrybut `Conditional` jest aliasem <xref:System.Diagnostics.ConditionalAttribute>dla i może być stosowany do metody lub klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b6449-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="b6449-170">W tym `Conditional` przykładzie jest stosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych specyficznych dla programu:</span><span class="sxs-lookup"><span data-stu-id="b6449-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="b6449-171">Jeśli `TRACE_ON` identyfikator nie jest zdefiniowany, nie zostaną wyświetlone żadne dane wyjściowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b6449-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="b6449-172">Atrybut `Conditional` jest często używany `DEBUG` z identyfikatorem, aby włączyć śledzenie i rejestrowanie funkcji dla kompilacji debugowania, ale nie w kompilacjach wersji, w tym sposób:</span><span class="sxs-lookup"><span data-stu-id="b6449-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="b6449-173">Gdy wywoływana jest metoda oznaczona jako warunkowa, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie jest uwzględnione, czy pominięte.</span><span class="sxs-lookup"><span data-stu-id="b6449-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="b6449-174">Jeśli symbol jest zdefiniowany, połączenie jest uwzględniane; w przeciwnym razie wywołanie zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="b6449-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="b6449-175">Korzystanie `Conditional` jest czystszą, bardziej elegancką i mniej `#if…#endif` podatną na błędy alternatywą dla załączania metod wewnątrz bloków, w tym stylu:</span><span class="sxs-lookup"><span data-stu-id="b6449-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="b6449-176">Metoda warunkowa musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="b6449-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="b6449-177">Używanie wielu identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="b6449-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="b6449-178">Jeśli metoda ma `Conditional` wiele atrybutów, wywołanie metody jest uwzględniane, jeśli zdefiniowano co najmniej jeden z symboli warunkowych (innymi słowy, symbole są logicznie połączone ze sobą za pomocą operatora OR).</span><span class="sxs-lookup"><span data-stu-id="b6449-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="b6449-179">W tym przykładzie obecność `A` albo `B` spowoduje wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="b6449-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="b6449-180">Aby osiągnąć efekt logicznego łączenia symboli za pomocą operatora AND, można zdefiniować szeregowe metody warunkowe.</span><span class="sxs-lookup"><span data-stu-id="b6449-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="b6449-181">Na przykład druga metoda poniżej zostanie `A` wykonana `B` tylko wtedy, gdy oba i są zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="b6449-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="b6449-182">Używanie warunkowego z klasami atrybutów</span><span class="sxs-lookup"><span data-stu-id="b6449-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="b6449-183">Atrybut `Conditional` można również zastosować do definicji klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b6449-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="b6449-184">W tym przykładzie atrybut `Documentation` niestandardowy doda informacje do metadanych tylko wtedy, gdy zdefiniowano DEBUG.</span><span class="sxs-lookup"><span data-stu-id="b6449-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
## <a name="CallerInfo"></a><span data-ttu-id="b6449-185">Atrybuty informacji o obiekcie wywołującym</span><span class="sxs-lookup"><span data-stu-id="b6449-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="b6449-186">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="b6449-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="b6449-187">Ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b6449-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="b6449-188">Aby uzyskać informacje o obiekcie wywołującym element członkowski, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="b6449-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="b6449-189">Każdy parametr opcjonalny określa wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="b6449-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="b6449-190">W poniższej tabeli wymieniono atrybuty Informacje <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> o obiekcie wywołującym zdefiniowane w obszarze nazw:</span><span class="sxs-lookup"><span data-stu-id="b6449-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="b6449-191">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6449-191">Attribute</span></span>|<span data-ttu-id="b6449-192">Opis</span><span class="sxs-lookup"><span data-stu-id="b6449-192">Description</span></span>|<span data-ttu-id="b6449-193">Typ</span><span class="sxs-lookup"><span data-stu-id="b6449-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="b6449-194">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="b6449-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="b6449-195">Jest to ścieżka w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b6449-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="b6449-196">Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="b6449-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="b6449-197">Nazwa metody lub nazwa właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b6449-197">Method name or property name of the caller.</span></span> <span data-ttu-id="b6449-198">Aby uzyskać więcej informacji, zobacz [Informacje o obiekcie wywołującym (C#)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="b6449-198">For more information, see [Caller Information (C#)](../caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="b6449-199">Aby uzyskać więcej informacji o atrybutach informacje o obiekcie wywołującym, zobacz [Informacje o obiekcie wywołującym (C#)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="b6449-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6449-200">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6449-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="b6449-201">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b6449-201">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="b6449-202">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6449-202">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="b6449-203">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="b6449-203">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="b6449-204">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="b6449-204">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
