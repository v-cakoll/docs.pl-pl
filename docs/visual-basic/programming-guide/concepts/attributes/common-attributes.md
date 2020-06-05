---
title: Atrybuty wspólne
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 57ef8f103d64a51d896f46d2889d78ec99ff3223
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400722"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="4055d-102">Atrybuty wspólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4055d-102">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="4055d-103">W tym temacie opisano atrybuty, które są najczęściej używane w programach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4055d-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="4055d-104">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="4055d-104">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="4055d-105">Przestarzały atrybut</span><span class="sxs-lookup"><span data-stu-id="4055d-105">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="4055d-106">Atrybut warunkowy</span><span class="sxs-lookup"><span data-stu-id="4055d-106">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="4055d-107">Atrybuty informacji o wywołującym</span><span class="sxs-lookup"><span data-stu-id="4055d-107">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="4055d-108">Atrybuty Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4055d-108">Visual Basic Attributes</span></span>](#VB)

## <a name="global-attributes"></a><a name="Global"></a><span data-ttu-id="4055d-109">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="4055d-109">Global Attributes</span></span>

<span data-ttu-id="4055d-110">Większość atrybutów stosuje się do określonych elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="4055d-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="4055d-111">Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacji o wersji w zestawie, takich jak:</span><span class="sxs-lookup"><span data-stu-id="4055d-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="4055d-112">Atrybuty globalne pojawiają się w kodzie źródłowym po dowolnych instrukcjach najwyższego poziomu `Imports` i przed dowolnymi deklaracjami typu, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4055d-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="4055d-113">Atrybuty globalne mogą pojawiać się w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4055d-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="4055d-114">W przypadku projektów Visual Basic atrybuty globalne są zwykle umieszczane w pliku AssemblyInfo. vb (plik jest tworzony automatycznie podczas tworzenia projektu w programie Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="4055d-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="4055d-115">Atrybuty zestawu są wartościami, które zawierają informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="4055d-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="4055d-116">Należą do następujących kategorii:</span><span class="sxs-lookup"><span data-stu-id="4055d-116">They fall into the following categories:</span></span>

- <span data-ttu-id="4055d-117">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="4055d-117">Assembly identity attributes</span></span>

- <span data-ttu-id="4055d-118">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="4055d-118">Informational attributes</span></span>

- <span data-ttu-id="4055d-119">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="4055d-119">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="4055d-120">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="4055d-120">Assembly Identity Attributes</span></span>

<span data-ttu-id="4055d-121">Trzy atrybuty (o silnej nazwie, jeśli ma zastosowanie) określają tożsamość zestawu: nazwę, wersję i kulturę.</span><span class="sxs-lookup"><span data-stu-id="4055d-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="4055d-122">Te atrybuty tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do niego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4055d-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="4055d-123">Możesz ustawić wersję zestawu i kulturę przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4055d-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="4055d-124">Jednak wartość nazwy jest ustawiana przez kompilator, środowisko IDE programu Visual Studio w [oknie dialogowym Informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator zestawu (Al. exe) podczas tworzenia zestawu, na podstawie pliku, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="4055d-125">Ten <xref:System.Reflection.AssemblyFlagsAttribute> atrybut określa, czy wiele kopii zestawu może współistnieć.</span><span class="sxs-lookup"><span data-stu-id="4055d-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="4055d-126">W poniższej tabeli przedstawiono atrybuty tożsamości.</span><span class="sxs-lookup"><span data-stu-id="4055d-126">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="4055d-127">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4055d-127">Attribute</span></span>|<span data-ttu-id="4055d-128">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="4055d-128">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="4055d-129">W pełni opisuje tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-129">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="4055d-130">Określa wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-130">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="4055d-131">Określa kulturę obsługiwaną przez zestaw.</span><span class="sxs-lookup"><span data-stu-id="4055d-131">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="4055d-132">Określa, czy zestaw obsługuje wykonywanie równoczesne na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4055d-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="4055d-133">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="4055d-133">Informational Attributes</span></span>

<span data-ttu-id="4055d-134">Można użyć atrybutów informacyjnych w celu podania dodatkowych informacji o firmie lub produkcie dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="4055d-135">W poniższej tabeli przedstawiono atrybuty informacyjne zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4055d-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="4055d-136">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4055d-136">Attribute</span></span>|<span data-ttu-id="4055d-137">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="4055d-137">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="4055d-138">Definiuje niestandardowy atrybut, który określa nazwę produktu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="4055d-139">Definiuje niestandardowy atrybut, który określa znak towarowy dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="4055d-140">Definiuje niestandardowy atrybut, który określa wersję informacyjną dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="4055d-141">Definiuje niestandardowy atrybut, który określa nazwę firmy dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="4055d-142">Definiuje niestandardowy atrybut, który określa prawo autorskie dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="4055d-143">Instruuje kompilator, aby używał określonego numeru wersji dla zasobu wersji plików Win32.</span><span class="sxs-lookup"><span data-stu-id="4055d-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="4055d-144">Wskazuje, czy zestaw jest zgodny z Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="4055d-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="4055d-145">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="4055d-145">Assembly Manifest Attributes</span></span>

<span data-ttu-id="4055d-146">Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="4055d-147">Obejmuje to tytuł, opis, alias domyślny i konfigurację.</span><span class="sxs-lookup"><span data-stu-id="4055d-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="4055d-148">W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4055d-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="4055d-149">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4055d-149">Attribute</span></span>|<span data-ttu-id="4055d-150">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="4055d-150">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="4055d-151">Definiuje niestandardowy atrybut, który określa tytuł zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="4055d-152">Definiuje niestandardowy atrybut, który określa opis zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="4055d-153">Definiuje niestandardowy atrybut, który określa konfigurację zestawu (na przykład detaliczną lub Debug) dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="4055d-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="4055d-154">Definiuje przyjazny alias domyślny dla manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="4055d-154">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="obsolete-attribute"></a><a name="Obsolete"></a><span data-ttu-id="4055d-155">Przestarzały atrybut</span><span class="sxs-lookup"><span data-stu-id="4055d-155">Obsolete Attribute</span></span>

<span data-ttu-id="4055d-156">Ten `Obsolete` atrybut oznacza jednostkę programu, która nie jest już zalecana do użycia.</span><span class="sxs-lookup"><span data-stu-id="4055d-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="4055d-157">Każde użycie jednostki oznaczonej jako przestarzałe spowoduje wygenerowanie ostrzeżenia lub błędu w zależności od sposobu skonfigurowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4055d-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="4055d-158">Przykład:</span><span class="sxs-lookup"><span data-stu-id="4055d-158">For example:</span></span>

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

<span data-ttu-id="4055d-159">W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` i metody `B.OldMethod` .</span><span class="sxs-lookup"><span data-stu-id="4055d-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="4055d-160">Ponieważ drugi argument konstruktora atrybutu stosowany do `B.OldMethod` jest ustawiony na `true` , ta metoda spowoduje błąd kompilatora, podczas gdy użycie klasy `A` spowoduje po prostu wygenerowanie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="4055d-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="4055d-161">Jednak wywoływanie `B.NewMethod` nie powoduje żadnych ostrzeżeń ani błędów.</span><span class="sxs-lookup"><span data-stu-id="4055d-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="4055d-162">Ciąg dostarczony jako pierwszy argument konstruktora atrybutu będzie wyświetlany jako część ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="4055d-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="4055d-163">Na przykład jeśli używasz go z poprzednimi definicjami, poniższy kod generuje dwie ostrzeżenia i jeden błąd:</span><span class="sxs-lookup"><span data-stu-id="4055d-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="4055d-164">Generowane są dwa ostrzeżenia dla klasy `A` : jeden dla deklaracji klasy Reference i jeden dla konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="4055d-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="4055d-165">Ten `Obsolete` atrybut może być używany bez argumentów, ale wraz z wyjaśnieniem dlaczego element jest przestarzały i czego należy używać.</span><span class="sxs-lookup"><span data-stu-id="4055d-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="4055d-166">Ten `Obsolete` atrybut jest atrybutem jednokrotnego użycia i może być stosowany do każdej jednostki, która zezwala na atrybuty.</span><span class="sxs-lookup"><span data-stu-id="4055d-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="4055d-167">`Obsolete`jest aliasem dla <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4055d-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="conditional-attribute"></a><a name="Conditional"></a><span data-ttu-id="4055d-168">Atrybut warunkowy</span><span class="sxs-lookup"><span data-stu-id="4055d-168">Conditional Attribute</span></span>

<span data-ttu-id="4055d-169">Ten `Conditional` atrybut wykonuje metodę zależną od identyfikatora przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="4055d-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="4055d-170">`Conditional`Atrybut jest alias dla <xref:System.Diagnostics.ConditionalAttribute> i może być zastosowany do metody lub klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4055d-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="4055d-171">W tym przykładzie `Conditional` stosuje się do metody w celu włączenia lub wyłączenia wyświetlania informacji diagnostycznych specyficznych dla programu:</span><span class="sxs-lookup"><span data-stu-id="4055d-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

```vb
#Const TRACE_ON = True
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

<span data-ttu-id="4055d-172">Jeśli `TRACE_ON` Identyfikator nie jest zdefiniowany, nie będą wyświetlane dane wyjściowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4055d-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="4055d-173">Ten `Conditional` atrybut jest często używany z `DEBUG` identyfikatorem, aby włączyć funkcje śledzenia i rejestrowania dla kompilacji debugowania, ale nie w kompilacjach wydania, takich jak:</span><span class="sxs-lookup"><span data-stu-id="4055d-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="4055d-174">Gdy wywoływana jest metoda oznaczona jako warunkowa, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie jest dołączone czy pominięte.</span><span class="sxs-lookup"><span data-stu-id="4055d-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="4055d-175">Jeśli symbol jest zdefiniowany, wywołanie jest dołączone; w przeciwnym razie wywołanie zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="4055d-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="4055d-176">Korzystanie z programu `Conditional` to przejrzysty, bardziej elegancki i mniej podatny na błędy alternatywa dla otaczających metod w `#if…#endif` blokach, takich jak:</span><span class="sxs-lookup"><span data-stu-id="4055d-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="4055d-177">Metoda warunkowa musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="4055d-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="4055d-178">Używanie wielu identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="4055d-178">Using Multiple Identifiers</span></span>

<span data-ttu-id="4055d-179">Jeśli metoda ma wiele `Conditional` atrybutów, wywołanie metody jest uwzględnione, jeśli co najmniej jeden z symboli warunkowych jest zdefiniowany (innymi słowy, symbole są logicznie połączone ze sobą przy użyciu operatora OR).</span><span class="sxs-lookup"><span data-stu-id="4055d-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="4055d-180">W tym przykładzie, obecność albo `A` `B` spowoduje wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="4055d-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="4055d-181">Aby osiągnąć efekt logicznego łączenia symboli za pomocą operatora i, można zdefiniować metody warunkowe szeregowe.</span><span class="sxs-lookup"><span data-stu-id="4055d-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="4055d-182">Na przykład druga metoda zostanie wykonana tylko wtedy, gdy obie `A` i `B` są zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="4055d-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

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

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="4055d-183">Używanie warunkowe z klasami atrybutów</span><span class="sxs-lookup"><span data-stu-id="4055d-183">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="4055d-184">Ten `Conditional` atrybut może być również stosowany do definicji klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4055d-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="4055d-185">W tym przykładzie atrybut niestandardowy `Documentation` będzie dodawać tylko informacje do metadanych w przypadku zdefiniowania debugowania.</span><span class="sxs-lookup"><span data-stu-id="4055d-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

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

## <a name="caller-info-attributes"></a><a name="CallerInfo"></a><span data-ttu-id="4055d-186">Atrybuty informacji o wywołującym</span><span class="sxs-lookup"><span data-stu-id="4055d-186">Caller Info Attributes</span></span>

<span data-ttu-id="4055d-187">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="4055d-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="4055d-188">Możesz uzyskać ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4055d-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="4055d-189">Aby uzyskać informacje o obiekcie wywołującym elementu członkowskiego, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="4055d-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="4055d-190">Każdy opcjonalny parametr określa wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="4055d-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="4055d-191">W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="4055d-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="4055d-192">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4055d-192">Attribute</span></span>|<span data-ttu-id="4055d-193">Opis</span><span class="sxs-lookup"><span data-stu-id="4055d-193">Description</span></span>|<span data-ttu-id="4055d-194">Typ</span><span class="sxs-lookup"><span data-stu-id="4055d-194">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="4055d-195">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="4055d-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="4055d-196">Jest to ścieżka w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4055d-196">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="4055d-197">Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="4055d-197">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="4055d-198">Nazwa metody lub nazwa właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4055d-198">Method name or property name of the caller.</span></span> <span data-ttu-id="4055d-199">Aby uzyskać więcej informacji, zobacz [Informacje o wywołującym (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="4055d-199">For more information, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>|`String`|

<span data-ttu-id="4055d-200">Aby uzyskać więcej informacji o atrybutach informacji o wywołującym, zobacz [Informacje o wywołującym (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="4055d-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>

## <a name="visual-basic-attributes"></a><a name="VB"></a><span data-ttu-id="4055d-201">Atrybuty Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4055d-201">Visual Basic Attributes</span></span>

<span data-ttu-id="4055d-202">W poniższej tabeli wymieniono atrybuty, które są specyficzne dla Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4055d-202">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="4055d-203">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4055d-203">Attribute</span></span>|<span data-ttu-id="4055d-204">Przeznaczenie</span><span class="sxs-lookup"><span data-stu-id="4055d-204">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="4055d-205">Wskazuje kompilatorowi, że klasa powinna być udostępniana jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="4055d-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="4055d-206">Zezwala na dostęp do elementów członkowskich modułu wyłącznie przy użyciu kwalifikacji wymaganych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="4055d-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="4055d-207">Określa rozmiar ciągu o stałej długości w strukturze do użycia z funkcjami wejściowymi i wyjściowymi plików.</span><span class="sxs-lookup"><span data-stu-id="4055d-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="4055d-208">Określa rozmiar stałej tablicy w strukturze do użycia z funkcjami wejściowymi i wyjściowymi plików.</span><span class="sxs-lookup"><span data-stu-id="4055d-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="4055d-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="4055d-209">COMClassAttribute</span></span>

<span data-ttu-id="4055d-210">Użyj `COMClassAttribute` , aby uprościć proces tworzenia składników modelu COM z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4055d-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="4055d-211">Obiekty COM różnią się znacznie od zestawów .NET Framework i nie należy `COMClassAttribute` wykonać kilku kroków w celu wygenerowania obiektu com z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4055d-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="4055d-212">W przypadku klas oznaczonych za pomocą `COMClassAttribute` kompilator wykonuje wiele czynności automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4055d-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="4055d-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="4055d-213">HideModuleNameAttribute</span></span>

<span data-ttu-id="4055d-214">Służy `HideModuleNameAttribute` do zezwalania na dostęp do elementów członkowskich modułu przy użyciu tylko kwalifikacji wymaganych przez moduł.</span><span class="sxs-lookup"><span data-stu-id="4055d-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="4055d-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="4055d-215">VBFixedStringAttribute</span></span>

<span data-ttu-id="4055d-216">Użyj `VBFixedStringAttribute` , aby wymusić Visual Basic utworzyć ciąg o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="4055d-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="4055d-217">Ciągi są domyślnie o zmiennej długości, a ten atrybut jest przydatny podczas przechowywania ciągów do plików.</span><span class="sxs-lookup"><span data-stu-id="4055d-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="4055d-218">Poniższy kod ilustruje:</span><span class="sxs-lookup"><span data-stu-id="4055d-218">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="4055d-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="4055d-219">VBFixedArrayAttribute</span></span>

<span data-ttu-id="4055d-220">Służy `VBFixedArrayAttribute` do deklarowania tablic, które mają stały rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4055d-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="4055d-221">Podobnie jak Visual Basic ciągi, domyślnie tablice są o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="4055d-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="4055d-222">Ten atrybut jest przydatny podczas serializacji lub zapisywania danych w plikach.</span><span class="sxs-lookup"><span data-stu-id="4055d-222">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="4055d-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4055d-223">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="4055d-224">Przewodnik programowania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4055d-224">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="4055d-225">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4055d-225">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="4055d-226">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4055d-226">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="4055d-227">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4055d-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
