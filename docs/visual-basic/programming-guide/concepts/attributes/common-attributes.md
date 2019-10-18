---
title: Atrybuty wspólne (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 5bc568279a6952fdc5e0a000b1208cd7f9cfd6e7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524284"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="28bb6-102">Atrybuty wspólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28bb6-102">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="28bb6-103">W tym temacie opisano atrybuty, które są najczęściej używane w programach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="28bb6-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="28bb6-104">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="28bb6-104">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="28bb6-105">Przestarzały atrybut</span><span class="sxs-lookup"><span data-stu-id="28bb6-105">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="28bb6-106">Atrybut warunkowy</span><span class="sxs-lookup"><span data-stu-id="28bb6-106">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="28bb6-107">Atrybuty informacji o wywołującym</span><span class="sxs-lookup"><span data-stu-id="28bb6-107">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="28bb6-108">Atrybuty Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28bb6-108">Visual Basic Attributes</span></span>](#VB)

## <a name="Global"></a><span data-ttu-id="28bb6-109">Atrybuty globalne</span><span class="sxs-lookup"><span data-stu-id="28bb6-109">Global Attributes</span></span>

<span data-ttu-id="28bb6-110">Większość atrybutów stosuje się do określonych elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="28bb6-111">Na przykład atrybut <xref:System.Reflection.AssemblyVersionAttribute> może służyć do osadzania informacji o wersji w zestawie, takich jak:</span><span class="sxs-lookup"><span data-stu-id="28bb6-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="28bb6-112">Atrybuty globalne pojawiają się w kodzie źródłowym po każdej instrukcji `Imports` najwyższego poziomu i przed dowolnymi deklaracjami typu, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="28bb6-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="28bb6-113">Atrybuty globalne mogą pojawiać się w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28bb6-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="28bb6-114">W przypadku projektów Visual Basic atrybuty globalne są zwykle umieszczane w pliku AssemblyInfo. vb (plik jest tworzony automatycznie podczas tworzenia projektu w programie Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="28bb6-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="28bb6-115">Atrybuty zestawu są wartościami, które zawierają informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="28bb6-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="28bb6-116">Należą do następujących kategorii:</span><span class="sxs-lookup"><span data-stu-id="28bb6-116">They fall into the following categories:</span></span>

- <span data-ttu-id="28bb6-117">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="28bb6-117">Assembly identity attributes</span></span>

- <span data-ttu-id="28bb6-118">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="28bb6-118">Informational attributes</span></span>

- <span data-ttu-id="28bb6-119">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="28bb6-119">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="28bb6-120">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="28bb6-120">Assembly Identity Attributes</span></span>

<span data-ttu-id="28bb6-121">Trzy atrybuty (o silnej nazwie, jeśli ma zastosowanie) określają tożsamość zestawu: nazwę, wersję i kulturę.</span><span class="sxs-lookup"><span data-stu-id="28bb6-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="28bb6-122">Te atrybuty tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do niego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="28bb6-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="28bb6-123">Możesz ustawić wersję zestawu i kulturę przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="28bb6-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="28bb6-124">Jednak wartość nazwy jest ustawiana przez kompilator, środowisko IDE programu Visual Studio w [oknie dialogowym Informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator zestawu (Al. exe) podczas tworzenia zestawu, na podstawie pliku, który zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="28bb6-125">Atrybut <xref:System.Reflection.AssemblyFlagsAttribute> określa, czy wiele kopii zestawu może współistnieć.</span><span class="sxs-lookup"><span data-stu-id="28bb6-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="28bb6-126">W poniższej tabeli przedstawiono atrybuty tożsamości.</span><span class="sxs-lookup"><span data-stu-id="28bb6-126">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="28bb6-127">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28bb6-127">Attribute</span></span>|<span data-ttu-id="28bb6-128">Cel</span><span class="sxs-lookup"><span data-stu-id="28bb6-128">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="28bb6-129">W pełni opisuje tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-129">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="28bb6-130">Określa wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-130">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="28bb6-131">Określa kulturę obsługiwaną przez zestaw.</span><span class="sxs-lookup"><span data-stu-id="28bb6-131">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="28bb6-132">Określa, czy zestaw obsługuje wykonywanie równoczesne na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28bb6-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="28bb6-133">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="28bb6-133">Informational Attributes</span></span>

<span data-ttu-id="28bb6-134">Można użyć atrybutów informacyjnych w celu podania dodatkowych informacji o firmie lub produkcie dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="28bb6-135">W poniższej tabeli przedstawiono atrybuty informacyjne zdefiniowane w przestrzeni nazw <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="28bb6-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="28bb6-136">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28bb6-136">Attribute</span></span>|<span data-ttu-id="28bb6-137">Cel</span><span class="sxs-lookup"><span data-stu-id="28bb6-137">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="28bb6-138">Definiuje niestandardowy atrybut, który określa nazwę produktu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="28bb6-139">Definiuje niestandardowy atrybut, który określa znak towarowy dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="28bb6-140">Definiuje niestandardowy atrybut, który określa wersję informacyjną dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="28bb6-141">Definiuje niestandardowy atrybut, który określa nazwę firmy dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="28bb6-142">Definiuje niestandardowy atrybut, który określa prawo autorskie dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="28bb6-143">Instruuje kompilator, aby używał określonego numeru wersji dla zasobu wersji plików Win32.</span><span class="sxs-lookup"><span data-stu-id="28bb6-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="28bb6-144">Wskazuje, czy zestaw jest zgodny z Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="28bb6-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="28bb6-145">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="28bb6-145">Assembly Manifest Attributes</span></span>

<span data-ttu-id="28bb6-146">Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="28bb6-147">Obejmuje to tytuł, opis, alias domyślny i konfigurację.</span><span class="sxs-lookup"><span data-stu-id="28bb6-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="28bb6-148">W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w przestrzeni nazw <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="28bb6-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="28bb6-149">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28bb6-149">Attribute</span></span>|<span data-ttu-id="28bb6-150">Cel</span><span class="sxs-lookup"><span data-stu-id="28bb6-150">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="28bb6-151">Definiuje niestandardowy atrybut, który określa tytuł zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="28bb6-152">Definiuje niestandardowy atrybut, który określa opis zestawu dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="28bb6-153">Definiuje niestandardowy atrybut, który określa konfigurację zestawu (na przykład detaliczną lub Debug) dla manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="28bb6-154">Definiuje przyjazny alias domyślny dla manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="28bb6-154">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="Obsolete"></a><span data-ttu-id="28bb6-155">Przestarzały atrybut</span><span class="sxs-lookup"><span data-stu-id="28bb6-155">Obsolete Attribute</span></span>

<span data-ttu-id="28bb6-156">Atrybut `Obsolete` oznacza jednostkę programu, która nie jest już zalecana do użycia.</span><span class="sxs-lookup"><span data-stu-id="28bb6-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="28bb6-157">Każde użycie jednostki oznaczonej jako przestarzałe spowoduje wygenerowanie ostrzeżenia lub błędu w zależności od sposobu skonfigurowania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="28bb6-158">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="28bb6-158">For example:</span></span>

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

<span data-ttu-id="28bb6-159">W tym przykładzie atrybut `Obsolete` jest stosowany do klasy `A` i do metody `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="28bb6-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="28bb6-160">Ponieważ drugi argument konstruktora atrybutu zastosowany do `B.OldMethod` jest ustawiony na `true`, ta metoda spowoduje błąd kompilatora, natomiast użycie klasy `A` spowoduje po prostu wygenerowanie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="28bb6-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="28bb6-161">Wywołanie `B.NewMethod`, jednak nie powoduje ostrzeżenia ani błędu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="28bb6-162">Ciąg dostarczony jako pierwszy argument konstruktora atrybutu będzie wyświetlany jako część ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="28bb6-163">Na przykład jeśli używasz go z poprzednimi definicjami, poniższy kod generuje dwie ostrzeżenia i jeden błąd:</span><span class="sxs-lookup"><span data-stu-id="28bb6-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="28bb6-164">Wygenerowane są dwa ostrzeżenia dla `A` klasy: jeden dla deklaracji odwołania do klasy i jeden dla konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="28bb6-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="28bb6-165">Atrybut `Obsolete` może być używany bez argumentów, ale wraz z wyjaśnieniem dlaczego element jest przestarzały i czego należy używać.</span><span class="sxs-lookup"><span data-stu-id="28bb6-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="28bb6-166">Atrybut `Obsolete` jest atrybutem jednokrotnego użycia i może być stosowany do każdej jednostki, która zezwala na atrybuty.</span><span class="sxs-lookup"><span data-stu-id="28bb6-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="28bb6-167">`Obsolete` jest aliasem <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="28bb6-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="Conditional"></a><span data-ttu-id="28bb6-168">Atrybut warunkowy</span><span class="sxs-lookup"><span data-stu-id="28bb6-168">Conditional Attribute</span></span>

<span data-ttu-id="28bb6-169">Atrybut `Conditional` wykonuje metodę zależną od identyfikatora przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="28bb6-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="28bb6-170">Atrybut `Conditional` jest aliasem dla <xref:System.Diagnostics.ConditionalAttribute> i może być zastosowany do metody lub klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="28bb6-171">W tym przykładzie `Conditional` jest stosowana do metody w celu włączenia lub wyłączenia wyświetlania informacji diagnostycznych specyficznych dla programu:</span><span class="sxs-lookup"><span data-stu-id="28bb6-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

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

<span data-ttu-id="28bb6-172">Jeśli identyfikator `TRACE_ON` nie jest zdefiniowany, nie będą wyświetlane dane wyjściowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="28bb6-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="28bb6-173">Atrybut `Conditional` jest często używany z identyfikatorem `DEBUG` do włączania funkcji śledzenia i rejestrowania dla kompilacji debugowania, ale nie w kompilacjach wydań, takich jak:</span><span class="sxs-lookup"><span data-stu-id="28bb6-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="28bb6-174">Gdy wywoływana jest metoda oznaczona jako warunkowa, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie jest dołączone czy pominięte.</span><span class="sxs-lookup"><span data-stu-id="28bb6-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="28bb6-175">Jeśli symbol jest zdefiniowany, wywołanie jest dołączone; w przeciwnym razie wywołanie zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="28bb6-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="28bb6-176">Używanie `Conditional` jest oczyszczarką, bardziej eleganckim i mniej podatnym na błędy alternatywą dla otaczających metod w blokach `#if…#endif`, takich jak:</span><span class="sxs-lookup"><span data-stu-id="28bb6-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="28bb6-177">Metoda warunkowa musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="28bb6-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="28bb6-178">Używanie wielu identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="28bb6-178">Using Multiple Identifiers</span></span>

<span data-ttu-id="28bb6-179">Jeśli metoda ma wiele atrybutów `Conditional`, wywołanie metody jest uwzględnione, jeśli co najmniej jeden z symboli warunkowych jest zdefiniowany (innymi słowy, symbole są logicznie połączone ze sobą przy użyciu operatora OR).</span><span class="sxs-lookup"><span data-stu-id="28bb6-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="28bb6-180">W tym przykładzie obecność `A` lub `B` spowoduje wywołanie metody:</span><span class="sxs-lookup"><span data-stu-id="28bb6-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="28bb6-181">Aby osiągnąć efekt logicznego łączenia symboli za pomocą operatora i, można zdefiniować metody warunkowe szeregowe.</span><span class="sxs-lookup"><span data-stu-id="28bb6-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="28bb6-182">Przykładowo druga metoda zostanie wykonana tylko wtedy, gdy zdefiniowano zarówno `A`, jak i `B`:</span><span class="sxs-lookup"><span data-stu-id="28bb6-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

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

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="28bb6-183">Używanie warunkowe z klasami atrybutów</span><span class="sxs-lookup"><span data-stu-id="28bb6-183">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="28bb6-184">Atrybut `Conditional` można również zastosować do definicji klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="28bb6-185">W tym przykładzie atrybut niestandardowy `Documentation` będzie dodawać tylko informacje do metadanych w przypadku zdefiniowania debugowania.</span><span class="sxs-lookup"><span data-stu-id="28bb6-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

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

## <a name="CallerInfo"></a><span data-ttu-id="28bb6-186">Atrybuty informacji o wywołującym</span><span class="sxs-lookup"><span data-stu-id="28bb6-186">Caller Info Attributes</span></span>

<span data-ttu-id="28bb6-187">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="28bb6-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="28bb6-188">Możesz uzyskać ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="28bb6-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="28bb6-189">Aby uzyskać informacje o obiekcie wywołującym elementu członkowskiego, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="28bb6-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="28bb6-190">Każdy opcjonalny parametr określa wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="28bb6-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="28bb6-191">W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są zdefiniowane w przestrzeni nazw <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="28bb6-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="28bb6-192">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28bb6-192">Attribute</span></span>|<span data-ttu-id="28bb6-193">Opis</span><span class="sxs-lookup"><span data-stu-id="28bb6-193">Description</span></span>|<span data-ttu-id="28bb6-194">Typ</span><span class="sxs-lookup"><span data-stu-id="28bb6-194">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="28bb6-195">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="28bb6-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="28bb6-196">Jest to ścieżka w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28bb6-196">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="28bb6-197">Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="28bb6-197">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="28bb6-198">Nazwa metody lub nazwa właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="28bb6-198">Method name or property name of the caller.</span></span> <span data-ttu-id="28bb6-199">Aby uzyskać więcej informacji, zobacz [Informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="28bb6-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|

<span data-ttu-id="28bb6-200">Aby uzyskać więcej informacji o atrybutach informacji o wywołującym, zobacz [Informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="28bb6-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>

## <a name="VB"></a><span data-ttu-id="28bb6-201">Atrybuty Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28bb6-201">Visual Basic Attributes</span></span>

<span data-ttu-id="28bb6-202">W poniższej tabeli wymieniono atrybuty, które są specyficzne dla Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="28bb6-202">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="28bb6-203">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28bb6-203">Attribute</span></span>|<span data-ttu-id="28bb6-204">Cel</span><span class="sxs-lookup"><span data-stu-id="28bb6-204">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="28bb6-205">Wskazuje kompilatorowi, że klasa powinna być udostępniana jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="28bb6-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="28bb6-206">Zezwala na dostęp do elementów członkowskich modułu wyłącznie przy użyciu kwalifikacji wymaganych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="28bb6-207">Określa rozmiar ciągu o stałej długości w strukturze do użycia z funkcjami wejściowymi i wyjściowymi plików.</span><span class="sxs-lookup"><span data-stu-id="28bb6-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="28bb6-208">Określa rozmiar stałej tablicy w strukturze do użycia z funkcjami wejściowymi i wyjściowymi plików.</span><span class="sxs-lookup"><span data-stu-id="28bb6-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="28bb6-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="28bb6-209">COMClassAttribute</span></span>

<span data-ttu-id="28bb6-210">Użyj `COMClassAttribute`, aby uprościć proces tworzenia składników modelu COM z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="28bb6-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="28bb6-211">Obiekty COM różnią się znacznie od zestawów .NET Framework i nie `COMClassAttribute`, należy wykonać kilka czynności w celu wygenerowania obiektu COM z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="28bb6-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="28bb6-212">W przypadku klas oznaczonych za pomocą `COMClassAttribute` kompilator wykonuje wiele z tych kroków automatycznie.</span><span class="sxs-lookup"><span data-stu-id="28bb6-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="28bb6-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="28bb6-213">HideModuleNameAttribute</span></span>

<span data-ttu-id="28bb6-214">Użyj `HideModuleNameAttribute`, aby zezwolić na dostęp do członków modułu przy użyciu tylko kwalifikacji wymaganych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="28bb6-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="28bb6-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="28bb6-215">VBFixedStringAttribute</span></span>

<span data-ttu-id="28bb6-216">Użyj `VBFixedStringAttribute`, aby wymusić Visual Basic utworzyć ciąg o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="28bb6-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="28bb6-217">Ciągi są domyślnie o zmiennej długości, a ten atrybut jest przydatny podczas przechowywania ciągów do plików.</span><span class="sxs-lookup"><span data-stu-id="28bb6-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="28bb6-218">Poniższy kod ilustruje:</span><span class="sxs-lookup"><span data-stu-id="28bb6-218">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="28bb6-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="28bb6-219">VBFixedArrayAttribute</span></span>

<span data-ttu-id="28bb6-220">Użyj `VBFixedArrayAttribute`, aby zadeklarować tablice, których rozmiar jest ustalony.</span><span class="sxs-lookup"><span data-stu-id="28bb6-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="28bb6-221">Podobnie jak Visual Basic ciągi, domyślnie tablice są o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="28bb6-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="28bb6-222">Ten atrybut jest przydatny podczas serializacji lub zapisywania danych w plikach.</span><span class="sxs-lookup"><span data-stu-id="28bb6-222">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="28bb6-223">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28bb6-223">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="28bb6-224">Przewodnik programowania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28bb6-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="28bb6-225">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28bb6-225">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="28bb6-226">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28bb6-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="28bb6-227">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28bb6-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
