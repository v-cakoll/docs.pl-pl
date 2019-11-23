---
title: Kompilator XSLT (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 729e6caa36ed8c2f6e77153f8d8ae356513b0603
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956993"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="458ec-102">Kompilator XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="458ec-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="458ec-103">Kompilator XSLT (xsltc. exe) kompiluje arkusze stylów XSLT i generuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="458ec-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="458ec-104">Skompilowany arkusz stylów można następnie przesłać bezpośrednio do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="458ec-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="458ec-105">Nie można generować podpisanych zestawów za pomocą xsltc. exe.</span><span class="sxs-lookup"><span data-stu-id="458ec-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="458ec-106">Narzędzie xsltc. exe jest dołączone do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="458ec-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="458ec-107">Aby uzyskać więcej informacji, zobacz [Visual Studio — pliki do pobrania](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="458ec-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="458ec-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="458ec-108">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="458ec-109">Argument</span><span class="sxs-lookup"><span data-stu-id="458ec-109">Argument</span></span>  
  
|<span data-ttu-id="458ec-110">Argument</span><span class="sxs-lookup"><span data-stu-id="458ec-110">Argument</span></span>|<span data-ttu-id="458ec-111">Opis</span><span class="sxs-lookup"><span data-stu-id="458ec-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="458ec-112">Określa nazwę arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="458ec-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="458ec-113">Arkusz stylów musi być plikiem lokalnym lub znajdować się w intranecie.</span><span class="sxs-lookup"><span data-stu-id="458ec-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="458ec-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="458ec-114">Options</span></span>  
  
|<span data-ttu-id="458ec-115">Opcja</span><span class="sxs-lookup"><span data-stu-id="458ec-115">Option</span></span>|<span data-ttu-id="458ec-116">Opis</span><span class="sxs-lookup"><span data-stu-id="458ec-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="458ec-117">`/c[lass]:``name`</span><span class="sxs-lookup"><span data-stu-id="458ec-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="458ec-118">Określa nazwę klasy dla poniższego arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="458ec-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="458ec-119">Nazwa klasy może być w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="458ec-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="458ec-120">Nazwa klasy jest domyślnie nazwą arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="458ec-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="458ec-121">Na przykład jeśli arkusz stylów są kompilowane. xsl, domyślna nazwa klasy to Customers.</span><span class="sxs-lookup"><span data-stu-id="458ec-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="458ec-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="458ec-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="458ec-123">Określa, czy informacje o debugowaniu mają być generowane.</span><span class="sxs-lookup"><span data-stu-id="458ec-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="458ec-124">Określenie `+` lub `/debug`powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w pliku bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="458ec-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="458ec-125">Nazwa wygenerowanego pliku PDB to `assemblyName`. pdb.</span><span class="sxs-lookup"><span data-stu-id="458ec-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="458ec-126">Określenie `-`, która obowiązuje, jeśli nie określono `/debug`, nie powoduje utworzenia informacji o debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="458ec-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="458ec-127">Zestaw detaliczny jest generowany.</span><span class="sxs-lookup"><span data-stu-id="458ec-127">A retail assembly is generated.</span></span> <span data-ttu-id="458ec-128">**Uwaga:**  Kompilowanie w trybie debugowania może znacząco wpłynąć na wydajność XSLT.</span><span class="sxs-lookup"><span data-stu-id="458ec-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="458ec-129">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="458ec-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="458ec-130">Pomija wyświetlanie komunikatu o prawach autorskich kompilatora.</span><span class="sxs-lookup"><span data-stu-id="458ec-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="458ec-131">`/platform:``string`</span><span class="sxs-lookup"><span data-stu-id="458ec-131">`/platform:` `string`</span></span>|<span data-ttu-id="458ec-132">Określa platformy, na których można uruchomić zestaw.</span><span class="sxs-lookup"><span data-stu-id="458ec-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="458ec-133">Poniżej opisano prawidłowe wartości platformy:</span><span class="sxs-lookup"><span data-stu-id="458ec-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="458ec-134">`x86` kompiluje zestaw do uruchomienia przez 32-bitowe, zgodne z architekturą x86 środowiska uruchomieniowego języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="458ec-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="458ec-135">`x64` kompiluje zestaw do uruchomienia przez 64-bitowe środowisko uruchomieniowe języka wspólnego na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.</span><span class="sxs-lookup"><span data-stu-id="458ec-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="458ec-136">Procesor Itanium kompiluje zestaw do uruchomienia przez 64-bitowe środowisko uruchomieniowe języka wspólnego na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="458ec-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="458ec-137">`anycpu` kompiluje zestaw do uruchamiania na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="458ec-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="458ec-138">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="458ec-138">This is the default.</span></span>|  
|<span data-ttu-id="458ec-139">`/out:``assemblyName`</span><span class="sxs-lookup"><span data-stu-id="458ec-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="458ec-140">Określa nazwę zestawu, który jest wynikiem.</span><span class="sxs-lookup"><span data-stu-id="458ec-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="458ec-141">Nazwa zestawu jest domyślnie ustawiana na nazwę głównego arkusza stylów lub pierwszego arkusza stylów, jeśli istnieje wiele arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="458ec-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="458ec-142">Jeśli arkusz stylów zawiera skrypty, skrypty są zapisywane w osobnym zestawie.</span><span class="sxs-lookup"><span data-stu-id="458ec-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="458ec-143">Nazwy zestawów skryptów są generowane na podstawie głównej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="458ec-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="458ec-144">Na przykład jeśli dla nazwy zestawu określono CustOrders. dll, pierwszy zestaw skryptu nosi nazwę CustOrders_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="458ec-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="458ec-145">`/settings:``document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="458ec-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="458ec-146">Określa, czy zezwolić na `document()` funkcje, skrypt XSLT lub definicję typu dokumentu (DTD) w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="458ec-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="458ec-147">Zachowanie domyślne powoduje wyłączenie obsługi języka DTD, funkcji `document()` i skryptów.</span><span class="sxs-lookup"><span data-stu-id="458ec-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="458ec-148">`@``file`</span><span class="sxs-lookup"><span data-stu-id="458ec-148">`@` `file`</span></span>|<span data-ttu-id="458ec-149">Pozwala określić plik, który zawiera opcje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="458ec-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="458ec-150">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="458ec-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="458ec-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="458ec-151">Remarks</span></span>  
 <span data-ttu-id="458ec-152">Rozwiązania XSLT mogą składać się z wielu modułów arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="458ec-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="458ec-153">Narzędzie xsltc. exe generuje zestawy z arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="458ec-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="458ec-154">Zestawy można następnie przesłać do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="458ec-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="458ec-155">Może to pomóc w zmniejszeniu kosztów wydajności w niektórych scenariuszach wdrażania XSLT.</span><span class="sxs-lookup"><span data-stu-id="458ec-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="458ec-156">Należy również uwzględnić skompilowany zestaw jako odwołanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="458ec-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="458ec-157">Narzędzie xsltc. exe nie weryfikuje nazw klas ( *nazw`/class:`)* ani zestawów (`/out:`*AssemblyName*).</span><span class="sxs-lookup"><span data-stu-id="458ec-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="458ec-158">Błędy są zgłaszane przez środowisko uruchomieniowe języka wspólnego, jeśli nazwy są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="458ec-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="458ec-159">Przykłady</span><span class="sxs-lookup"><span data-stu-id="458ec-159">Examples</span></span>  
 <span data-ttu-id="458ec-160">Poniższe polecenie kompiluje arkusz stylów i tworzy zestaw o nazwie booksort. dll.</span><span class="sxs-lookup"><span data-stu-id="458ec-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="458ec-161">Poniższe polecenie kompiluje arkusz stylów i tworzy plik Assembly i PDB o nazwie booksort. dll i booksort. pdb odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="458ec-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="458ec-162">Poniższe polecenie kompiluje arkusz stylów zawierający element msxsl: Script i tworzy dwa zestawy o nazwie Calc. dll i calc_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="458ec-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="458ec-163">Następujące polecenie umożliwia przetwarzanie DTD i obsługę skryptów oraz tworzy dwa zestawy o nazwie "\* test. dll i myTest_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="458ec-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="458ec-164">Poniższe polecenie kompiluje dwa moduły arkusza stylów i tworzy pojedynczy zestaw o nazwie booksort. dll.</span><span class="sxs-lookup"><span data-stu-id="458ec-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="458ec-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="458ec-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="458ec-166">Instrukcje: Wykonywanie przekształcenia XSLT przy użyciu zestawu</span><span class="sxs-lookup"><span data-stu-id="458ec-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="458ec-167">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="458ec-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
