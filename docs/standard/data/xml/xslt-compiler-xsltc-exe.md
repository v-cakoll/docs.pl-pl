---
title: Kompilator XSLT (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
ms.openlocfilehash: 18f351546699487316858198b705e970de4856c1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282613"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="2b6ea-102">Kompilator XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="2b6ea-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="2b6ea-103">Kompilator XSLT (xsltc. exe) kompiluje arkusze stylów XSLT i generuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="2b6ea-104">Skompilowany arkusz stylów można następnie przesłać bezpośrednio do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2b6ea-105">Nie można generować podpisanych zestawów za pomocą xsltc. exe.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="2b6ea-106">Narzędzie xsltc. exe jest dołączone do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="2b6ea-107">Aby uzyskać więcej informacji, zobacz [Visual Studio — pliki do pobrania](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="2b6ea-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6ea-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b6ea-108">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="2b6ea-109">Argument</span><span class="sxs-lookup"><span data-stu-id="2b6ea-109">Argument</span></span>  
  
|<span data-ttu-id="2b6ea-110">Argument</span><span class="sxs-lookup"><span data-stu-id="2b6ea-110">Argument</span></span>|<span data-ttu-id="2b6ea-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2b6ea-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="2b6ea-112">Określa nazwę arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="2b6ea-113">Arkusz stylów musi być plikiem lokalnym lub znajdować się w intranecie.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="2b6ea-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="2b6ea-114">Options</span></span>  
  
|<span data-ttu-id="2b6ea-115">Opcja</span><span class="sxs-lookup"><span data-stu-id="2b6ea-115">Option</span></span>|<span data-ttu-id="2b6ea-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2b6ea-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2b6ea-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="2b6ea-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="2b6ea-118">Określa nazwę klasy dla poniższego arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="2b6ea-119">Nazwa klasy może być w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="2b6ea-120">Nazwa klasy jest domyślnie nazwą arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="2b6ea-121">Na przykład jeśli arkusz stylów są kompilowane. xsl, domyślna nazwa klasy to Customers.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="2b6ea-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="2b6ea-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="2b6ea-123">Określa, czy informacje o debugowaniu mają być generowane.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="2b6ea-124">Określenie `+` lub `/debug` , powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w pliku bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="2b6ea-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="2b6ea-125">Nazwa wygenerowanego pliku PDB to `assemblyName` . pdb.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="2b6ea-126">Określenie `-` , która obowiązuje, jeśli nie zostanie określone, powoduje, że nie `/debug` są tworzone żadne informacje debugowania.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="2b6ea-127">Zestaw detaliczny jest generowany.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-127">A retail assembly is generated.</span></span> <span data-ttu-id="2b6ea-128">**Uwaga:**  Kompilowanie w trybie debugowania może znacząco wpłynąć na wydajność XSLT.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="2b6ea-129">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="2b6ea-130">Pomija wyświetlanie komunikatu o prawach autorskich kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="2b6ea-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="2b6ea-131">`/platform:` `string`</span></span>|<span data-ttu-id="2b6ea-132">Określa platformy, na których można uruchomić zestaw.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="2b6ea-133">Poniżej opisano prawidłowe wartości platformy:</span><span class="sxs-lookup"><span data-stu-id="2b6ea-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="2b6ea-134">`x86`kompiluje zestaw do uruchomienia przez 32-bitowe, zgodne ze standardem x86 środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="2b6ea-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="2b6ea-135">`x64`kompiluje zestaw do uruchomienia przez 64-bitowe środowisko uruchomieniowe języka wspólnego na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="2b6ea-136">Procesor Itanium kompiluje zestaw do uruchomienia przez 64-bitowe środowisko uruchomieniowe języka wspólnego na komputerze z procesorem Itanium.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="2b6ea-137">`anycpu`kompiluje zestaw do uruchomienia na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="2b6ea-138">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-138">This is the default.</span></span>|  
|<span data-ttu-id="2b6ea-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="2b6ea-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="2b6ea-140">Określa nazwę zestawu, który jest wynikiem.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="2b6ea-141">Nazwa zestawu jest domyślnie ustawiana na nazwę głównego arkusza stylów lub pierwszego arkusza stylów, jeśli istnieje wiele arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="2b6ea-142">Jeśli arkusz stylów zawiera skrypty, skrypty są zapisywane w osobnym zestawie.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="2b6ea-143">Nazwy zestawów skryptów są generowane na podstawie głównej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="2b6ea-144">Na przykład jeśli dla nazwy zestawu określono CustOrders. dll, pierwszy zestaw skryptu nosi nazwę CustOrders_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="2b6ea-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="2b6ea-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="2b6ea-146">Określa, czy zezwalać na używanie `document()` funkcji, skryptu XSLT czy definicji typu dokumentu (DTD) w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="2b6ea-147">Zachowanie domyślne wyłącza obsługę DTD, `document()` funkcję i skrypty.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="2b6ea-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="2b6ea-148">`@` `file`</span></span>|<span data-ttu-id="2b6ea-149">Pozwala określić plik, który zawiera opcje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="2b6ea-150">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b6ea-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b6ea-151">Remarks</span></span>  
 <span data-ttu-id="2b6ea-152">Rozwiązania XSLT mogą składać się z wielu modułów arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="2b6ea-153">Narzędzie xsltc. exe generuje zestawy z arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="2b6ea-154">Zestawy można następnie przekazywać do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2b6ea-155">Może to pomóc w zmniejszeniu kosztów wydajności w niektórych scenariuszach wdrażania XSLT.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b6ea-156">Należy również uwzględnić skompilowany zestaw jako odwołanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="2b6ea-157">Narzędzie xsltc. exe nie weryfikuje nazw klas ( `/class:` *nazw*) ani zestawów ( `/out:` *AssemblyName*).</span><span class="sxs-lookup"><span data-stu-id="2b6ea-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="2b6ea-158">Błędy są zgłaszane przez środowisko uruchomieniowe języka wspólnego, jeśli nazwy są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2b6ea-159">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2b6ea-159">Examples</span></span>  
 <span data-ttu-id="2b6ea-160">Poniższe polecenie kompiluje arkusz stylów i tworzy zestaw o nazwie booksort. dll.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="2b6ea-161">Poniższe polecenie kompiluje arkusz stylów i tworzy plik Assembly i PDB o nazwie booksort. dll i booksort. pdb odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="2b6ea-162">Poniższe polecenie kompiluje arkusz stylów zawierający element msxsl: Script i tworzy dwa zestawy o nazwie Calc. dll i calc_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="2b6ea-163">Następujące polecenie umożliwia przetwarzanie DTD i obsługę skryptów oraz tworzy dwa zestawy o nazwie "\* test. dll i myTest_Script1. dll.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="2b6ea-164">Poniższe polecenie kompiluje dwa moduły arkusza stylów i tworzy pojedynczy zestaw o nazwie booksort. dll.</span><span class="sxs-lookup"><span data-stu-id="2b6ea-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b6ea-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b6ea-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="2b6ea-166">Instrukcje: Wykonywanie przekształcenia XSLT przy użyciu zestawu</span><span class="sxs-lookup"><span data-stu-id="2b6ea-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="2b6ea-167">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="2b6ea-167">XSLT Transformations</span></span>](xslt-transformations.md)
