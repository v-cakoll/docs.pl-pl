---
title: 'Instrukcje: wyświetlanie zawartości zestawu'
description: Można użyć Dezasembler IL, aby wyświetlić atrybuty zestawu i odwołania do innych modułów i zestawów.
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
ms.openlocfilehash: aed490459252466c6da06e5422b83b1bc20fb885
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380066"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="cd352-103">Instrukcje: wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="cd352-103">How to: View assembly contents</span></span>

<span data-ttu-id="cd352-104">Do wyświetlania informacji o języku pośrednim (MSIL) firmy Microsoft w pliku można użyć [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md) .</span><span class="sxs-lookup"><span data-stu-id="cd352-104">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="cd352-105">Jeśli rozpatrywany plik jest zestawem, te informacje mogą zawierać atrybuty zestawu i odwołania do innych modułów i zestawów.</span><span class="sxs-lookup"><span data-stu-id="cd352-105">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="cd352-106">Te informacje mogą być pomocne w ustaleniu, czy plik jest zestawem lub częścią zestawu oraz czy plik zawiera odwołania do innych modułów lub zestawów.</span><span class="sxs-lookup"><span data-stu-id="cd352-106">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="cd352-107">Aby wyświetlić zawartość zestawu przy użyciu programu *Ildasm. exe*, wprowadź \*\* \< nazwę zestawu Ildasm>\*\* w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="cd352-107">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="cd352-108">Na przykład następujące polecenie deasembleruje zestaw *Hello. exe* .</span><span class="sxs-lookup"><span data-stu-id="cd352-108">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="cd352-109">Aby wyświetlić informacje o manifeście zestawu, kliknij dwukrotnie ikonę **manifestu** w oknie MSIL dezasembler.</span><span class="sxs-lookup"><span data-stu-id="cd352-109">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="cd352-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd352-110">Example</span></span>

<span data-ttu-id="cd352-111">Poniższy przykład rozpoczyna się od podstawowego programu "Hello world".</span><span class="sxs-lookup"><span data-stu-id="cd352-111">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="cd352-112">Po skompilowaniu programu należy użyć *Ildasm. exe* do rozbudowy zestawu *Hello. exe* i wyświetlić manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd352-112">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

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

<span data-ttu-id="cd352-113">Uruchomienie polecenia *Ildasm. exe* w zestawie *Hello. exe* i dwukrotne kliknięcie ikony **manifestu** w oknie MSIL dezasembler generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="cd352-113">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

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

<span data-ttu-id="cd352-114">W poniższej tabeli opisano każdą dyrektywę w manifeście zestawu zestawu *Hello. exe* użytego w przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cd352-114">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="cd352-115">Dyrektywę</span><span class="sxs-lookup"><span data-stu-id="cd352-115">Directive</span></span>|<span data-ttu-id="cd352-116">Opis</span><span class="sxs-lookup"><span data-stu-id="cd352-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="cd352-117">**Nazwa zewnętrznego zestawu. Assembly \<>**</span><span class="sxs-lookup"><span data-stu-id="cd352-117">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="cd352-118">Określa inny zestaw, który zawiera elementy, do których odwołuje się bieżący moduł (w tym przykładzie `mscorlib` ).</span><span class="sxs-lookup"><span data-stu-id="cd352-118">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="cd352-119">**\<>token. PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="cd352-119">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="cd352-120">Określa token rzeczywistego klucza przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd352-120">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="cd352-121">**\<numer wersji. ver>**</span><span class="sxs-lookup"><span data-stu-id="cd352-121">**.ver \<version number>**</span></span>|<span data-ttu-id="cd352-122">Określa numer wersji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd352-122">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="cd352-123">**\<Nazwa zestawu. assembly>**</span><span class="sxs-lookup"><span data-stu-id="cd352-123">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="cd352-124">Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd352-124">Specifies the assembly name.</span></span>|
|<span data-ttu-id="cd352-125">**\<wartość Int32 algorytmu hash>**</span><span class="sxs-lookup"><span data-stu-id="cd352-125">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="cd352-126">Określa używany algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="cd352-126">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="cd352-127">**\<numer wersji. ver>**</span><span class="sxs-lookup"><span data-stu-id="cd352-127">**.ver \<version number>**</span></span>|<span data-ttu-id="cd352-128">Określa numer wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd352-128">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="cd352-129">**\<Nazwa pliku modułu>**</span><span class="sxs-lookup"><span data-stu-id="cd352-129">**.module \<file name>**</span></span>|<span data-ttu-id="cd352-130">Określa nazwę modułów, które tworzą zestaw.</span><span class="sxs-lookup"><span data-stu-id="cd352-130">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="cd352-131">W tym przykładzie zestaw składa się tylko z jednego pliku.</span><span class="sxs-lookup"><span data-stu-id="cd352-131">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="cd352-132">**wartość. Subsystem \<>**</span><span class="sxs-lookup"><span data-stu-id="cd352-132">**.subsystem \<value>**</span></span>|<span data-ttu-id="cd352-133">Określa środowisko aplikacji wymagane dla programu.</span><span class="sxs-lookup"><span data-stu-id="cd352-133">Specifies the application environment required for the program.</span></span> <span data-ttu-id="cd352-134">W tym przykładzie wartość 3 wskazuje, że ten plik wykonywalny jest uruchamiany z konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="cd352-134">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="cd352-135">**. CorFlags**</span><span class="sxs-lookup"><span data-stu-id="cd352-135">**.corflags**</span></span>|<span data-ttu-id="cd352-136">Obecnie zarezerwowane pole w metadanych.</span><span class="sxs-lookup"><span data-stu-id="cd352-136">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="cd352-137">Manifest zestawu może zawierać wiele różnych dyrektyw, w zależności od zawartości zestawu.</span><span class="sxs-lookup"><span data-stu-id="cd352-137">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="cd352-138">Aby uzyskać obszerną listę dyrektyw w manifeście zestawu, zapoznaj się z dokumentacją ECMA, szczególnie "partycja II: definicja metadanych i semantyka" i "Partition III: zestaw instrukcji CIL":</span><span class="sxs-lookup"><span data-stu-id="cd352-138">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="cd352-139">Standardy ECMA C# i Common Language Infrastructure</span><span class="sxs-lookup"><span data-stu-id="cd352-139">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="cd352-140">Standard ECMA-335-Common Language Infrastructure (interfejs wiersza polecenia)</span><span class="sxs-lookup"><span data-stu-id="cd352-140">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="cd352-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd352-141">See also</span></span>

- [<span data-ttu-id="cd352-142">Domeny aplikacji i zestawy</span><span class="sxs-lookup"><span data-stu-id="cd352-142">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="cd352-143">Domeny aplikacji i zestawy Tematy porad</span><span class="sxs-lookup"><span data-stu-id="cd352-143">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="cd352-144">Ildasm. exe (IL dezasembler)</span><span class="sxs-lookup"><span data-stu-id="cd352-144">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
