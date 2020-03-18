---
title: 'Jak: Wyświetlanie zawartości zestawu'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187387"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="c1f3c-102">Jak: Wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="c1f3c-102">How to: View assembly contents</span></span>

<span data-ttu-id="c1f3c-103">Za pomocą [programu Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) można wyświetlić informacje o języku pośrednim firmy Microsoft (MSIL) w pliku.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="c1f3c-104">Jeśli badany plik jest zestawem, te informacje mogą zawierać atrybuty zestawu i odwołania do innych modułów i zestawów.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-104">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="c1f3c-105">Te informacje mogą być pomocne w określeniu, czy plik jest zestawem lub częścią zestawu i czy plik ma odwołania do innych modułów lub zestawów.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-105">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="c1f3c-106">Aby wyświetlić zawartość złożenia przy użyciu *programu Ildasm.exe,* wprowadź **nazwę zestawu ildasm \<>** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-106">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="c1f3c-107">Na przykład następujące polecenie demontuje zestaw *Hello.exe.*</span><span class="sxs-lookup"><span data-stu-id="c1f3c-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="c1f3c-108">Aby wyświetlić informacje manifestu zestawu, kliknij dwukrotnie ikonę **manifestu** w oknie Disaser MSIL.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="c1f3c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1f3c-109">Example</span></span>

<span data-ttu-id="c1f3c-110">Poniższy przykład rozpoczyna się od podstawowego programu "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c1f3c-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="c1f3c-111">Po skompilowaniu programu należy użyć *programu Ildasm.exe* do demontażu zestawu *Hello.exe* i wyświetl manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="c1f3c-112">Uruchamianie polecenia *ildasm.exe* w zestawie *Hello.exe* i dwukrotne kliknięcie **ikony Manifestu** w oknie Disassembler MSIL daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="c1f3c-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

<span data-ttu-id="c1f3c-113">W poniższej tabeli opisano każdą dyrektywę w manifeście zestawu *Hello.exe* użytym w przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c1f3c-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="c1f3c-114">Dyrektywy</span><span class="sxs-lookup"><span data-stu-id="c1f3c-114">Directive</span></span>|<span data-ttu-id="c1f3c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c1f3c-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c1f3c-116">**Nazwa złożenia .assembly extern \<>**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-116">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="c1f3c-117">Określa inny zestaw, który zawiera elementy, do których `mscorlib`odwołuje się bieżący moduł (w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="c1f3c-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="c1f3c-118">**token \<tokenu .publickey token>**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-118">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="c1f3c-119">Określa token rzeczywistego klucza zestawu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-119">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="c1f3c-120">**Numer \<wersji .ver>**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-120">**.ver \<version number>**</span></span>|<span data-ttu-id="c1f3c-121">Określa numer wersji zestawu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-121">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="c1f3c-122">**Nazwa \<zestawu .>**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-122">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="c1f3c-123">Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-123">Specifies the assembly name.</span></span>|
|<span data-ttu-id="c1f3c-124">**Wartość .hash algorytm \<int32>**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-124">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="c1f3c-125">Określa algorytm mieszania używane.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-125">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="c1f3c-126">**Numer \<wersji .ver>**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-126">**.ver \<version number>**</span></span>|<span data-ttu-id="c1f3c-127">Określa numer wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-127">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="c1f3c-128">**Nazwa \<pliku .module>**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-128">**.module \<file name>**</span></span>|<span data-ttu-id="c1f3c-129">Określa nazwę modułów, które tworzą złożenie.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="c1f3c-130">W tym przykładzie zestaw składa się tylko z jednego pliku.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-130">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="c1f3c-131">**Wartość .subsystem \<>**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-131">**.subsystem \<value>**</span></span>|<span data-ttu-id="c1f3c-132">Określa środowisko aplikacji wymagane dla programu.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="c1f3c-133">W tym przykładzie wartość 3 wskazuje, że ten plik wykonywalny jest uruchamiany z konsoli.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="c1f3c-134">**.corflags (corflags)**</span><span class="sxs-lookup"><span data-stu-id="c1f3c-134">**.corflags**</span></span>|<span data-ttu-id="c1f3c-135">Obecnie zarezerwowane pole w metadanych.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-135">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="c1f3c-136">Manifest zestawu może zawierać szereg różnych dyrektyw, w zależności od zawartości zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1f3c-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="c1f3c-137">Obszerna lista dyrektyw w manifeście zestawu znajduje się w dokumentacji Ecma, szczególnie "Partycja II: Definicja metadanych i semantyka" i "Partycja III: Zestaw instrukcji CIL":</span><span class="sxs-lookup"><span data-stu-id="c1f3c-137">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="c1f3c-138">Normy ECMA C# i common language infrastructure</span><span class="sxs-lookup"><span data-stu-id="c1f3c-138">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="c1f3c-139">Standard ECMA-335 - Wspólna infrastruktura językowa (CLI)</span><span class="sxs-lookup"><span data-stu-id="c1f3c-139">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="c1f3c-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1f3c-140">See also</span></span>

- [<span data-ttu-id="c1f3c-141">Domeny i zestawy aplikacji</span><span class="sxs-lookup"><span data-stu-id="c1f3c-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="c1f3c-142">Tematy inkluzywne domen aplikacji i zestawów</span><span class="sxs-lookup"><span data-stu-id="c1f3c-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="c1f3c-143">Ildasm.exe (dezasembler IL)</span><span class="sxs-lookup"><span data-stu-id="c1f3c-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
