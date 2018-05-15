---
title: 'Porady: wyświetlanie zawartości zestawu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eadc320483d46503e7331ef57b0cc29b08f13f4c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="826e9-102">Porady: wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="826e9-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="826e9-103">Można użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić informacje o języku pośrednim (MSIL) firmy Microsoft w pliku.</span><span class="sxs-lookup"><span data-stu-id="826e9-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="826e9-104">Jeśli badane plik jest zestawem, te informacje mogą uwzględniać zestaw atrybutów, a także odwołania do innych modułów i zestawów.</span><span class="sxs-lookup"><span data-stu-id="826e9-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="826e9-105">Informacje te mogą być pomocne w określeniu, czy plik jest zestawem lub część zestawu i określa, czy plik ma odwołania do innych modułach ani zestawów.</span><span class="sxs-lookup"><span data-stu-id="826e9-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="826e9-106">Aby wyświetlić zawartość zestawu za pomocą Ildasm.exe</span><span class="sxs-lookup"><span data-stu-id="826e9-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="826e9-107">Typ **narzędzia ildasm** \< *nazwy zestawu*> w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="826e9-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="826e9-108">Na przykład następujące polecenie rozkłada `Hello.exe` zestawu.</span><span class="sxs-lookup"><span data-stu-id="826e9-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="826e9-109">Aby wyświetlić informacje manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="826e9-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="826e9-110">Kliknij dwukrotnie ikonę MANIFESTU w oknie dezasembler MSIL.</span><span class="sxs-lookup"><span data-stu-id="826e9-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="826e9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="826e9-111">Example</span></span>  
 <span data-ttu-id="826e9-112">Poniższy przykład rozpoczyna się od podstawowego program "Hello, World".</span><span class="sxs-lookup"><span data-stu-id="826e9-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="826e9-113">Po kompilacji programu, należy użyć Ildasm.exe dezasemblować zestawu Hello.exe i wyświetlania manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="826e9-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="826e9-114">Uruchamiając polecenie ildasm.exe na zestawu Hello.exe i dwukrotne kliknięcie ikony MANIFESTU w oknie IL DASM tworzy następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="826e9-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="826e9-115">W poniższej tabeli opisano każdy dyrektywy w manifeście zestawu zestawu Hello.exe używane w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="826e9-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="826e9-116">Dyrektywy</span><span class="sxs-lookup"><span data-stu-id="826e9-116">Directive</span></span>|<span data-ttu-id="826e9-117">Opis</span><span class="sxs-lookup"><span data-stu-id="826e9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="826e9-118">**Deklaracja extern \<**  *nazwy zestawu* **>**</span><span class="sxs-lookup"><span data-stu-id="826e9-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="826e9-119">Określa innego zestawu, który zawiera elementy, które odwołuje się moduł bieżący (w tym przykładzie `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="826e9-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="826e9-120">**.PublicKeyToken \<**  *tokenu* **>**</span><span class="sxs-lookup"><span data-stu-id="826e9-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="826e9-121">Określa token klucza rzeczywiste przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="826e9-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="826e9-122">**.ver \<**  *numer wersji* **>**</span><span class="sxs-lookup"><span data-stu-id="826e9-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="826e9-123">Określa numer wersji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="826e9-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="826e9-124">**Deklaracja \<**  *nazwy zestawu* **>**</span><span class="sxs-lookup"><span data-stu-id="826e9-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="826e9-125">Określa nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="826e9-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="826e9-126">**algorytm .hash \<**  *wartość int32* **>**</span><span class="sxs-lookup"><span data-stu-id="826e9-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="826e9-127">Określa algorytm wyznaczania wartości skrótu używany.</span><span class="sxs-lookup"><span data-stu-id="826e9-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="826e9-128">**.ver \<**  *numer wersji* **>**</span><span class="sxs-lookup"><span data-stu-id="826e9-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="826e9-129">Określa numer wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="826e9-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="826e9-130">**.module \<**  *nazwy pliku* **>**</span><span class="sxs-lookup"><span data-stu-id="826e9-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="826e9-131">Określa nazwę modułów, które tworzą zestaw.</span><span class="sxs-lookup"><span data-stu-id="826e9-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="826e9-132">W tym przykładzie zestaw składa się z tylko jednego pliku.</span><span class="sxs-lookup"><span data-stu-id="826e9-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="826e9-133">**.Subsystem \<**  *wartości* **>**</span><span class="sxs-lookup"><span data-stu-id="826e9-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="826e9-134">Określa środowisko aplikacji wymagane przez program.</span><span class="sxs-lookup"><span data-stu-id="826e9-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="826e9-135">W tym przykładzie wartość 3 oznacza, że ten plik wykonywalny jest uruchamiane z poziomu konsoli.</span><span class="sxs-lookup"><span data-stu-id="826e9-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="826e9-136">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="826e9-136">**.corflags**</span></span>|<span data-ttu-id="826e9-137">Obecnie zastrzeżone pole w metadanych.</span><span class="sxs-lookup"><span data-stu-id="826e9-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="826e9-138">Manifest zestawu może zawierać wiele różnych dyrektyw, w zależności od zestawu zawartości.</span><span class="sxs-lookup"><span data-stu-id="826e9-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="826e9-139">Obszernej listy dyrektywy w manifeście zestawu dokumentacji ECMA, szczególnie "Partycji II: metadane definicji i semantyki" i "III: CIL instrukcji zestawu partycji".</span><span class="sxs-lookup"><span data-stu-id="826e9-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="826e9-140">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# i wspólne normy infrastruktury języka](http://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) w witrynie sieci Web międzynarodowej Ecma.</span><span class="sxs-lookup"><span data-stu-id="826e9-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826e9-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="826e9-141">See Also</span></span>  
 [<span data-ttu-id="826e9-142">Domeny aplikacji i zestawy</span><span class="sxs-lookup"><span data-stu-id="826e9-142">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [<span data-ttu-id="826e9-143">Instrukcje dotyczące zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="826e9-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [<span data-ttu-id="826e9-144">Ildasm.exe (dezasembler IL)</span><span class="sxs-lookup"><span data-stu-id="826e9-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
