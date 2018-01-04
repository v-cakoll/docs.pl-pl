---
title: Kompilator XSLT (xsltc.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1148af537ef9b502c6f3a9a3cc0588eaed39ac2f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="226f4-102">Kompilator XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="226f4-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="226f4-103">Kompilator XSLT (xsltc.exe) kompiluje arkuszy stylów XSLT i generuje zestawu.</span><span class="sxs-lookup"><span data-stu-id="226f4-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="226f4-104">Arkusz stylów skompilowanego można następnie przekazać bezpośrednio do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="226f4-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="226f4-105">Nie można wygenerować zestawy podpisane za pomocą xsltc.exe.</span><span class="sxs-lookup"><span data-stu-id="226f4-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="226f4-106">Narzędzie xsltc.exe jest dołączone do programu Visual Studio 2008.</span><span class="sxs-lookup"><span data-stu-id="226f4-106">The xsltc.exe tool is included with Visual Studio 2008.</span></span> <span data-ttu-id="226f4-107">Aby uzyskać więcej informacji, zobacz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=89463).</span><span class="sxs-lookup"><span data-stu-id="226f4-107">For more information, see the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=89463).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="226f4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="226f4-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="226f4-109">Argument</span><span class="sxs-lookup"><span data-stu-id="226f4-109">Argument</span></span>  
  
|<span data-ttu-id="226f4-110">Argument</span><span class="sxs-lookup"><span data-stu-id="226f4-110">Argument</span></span>|<span data-ttu-id="226f4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="226f4-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="226f4-112">Określa nazwę arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="226f4-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="226f4-113">Arkusz stylów musi być lokalny plik lub znajdować się w intranecie.</span><span class="sxs-lookup"><span data-stu-id="226f4-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="226f4-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="226f4-114">Options</span></span>  
  
|<span data-ttu-id="226f4-115">Opcja</span><span class="sxs-lookup"><span data-stu-id="226f4-115">Option</span></span>|<span data-ttu-id="226f4-116">Opis</span><span class="sxs-lookup"><span data-stu-id="226f4-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="226f4-117">`/c[lass]:``name`</span><span class="sxs-lookup"><span data-stu-id="226f4-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="226f4-118">Określa nazwę klasy dla następujących arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="226f4-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="226f4-119">Nazwa klasy może być w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="226f4-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="226f4-120">Nazwa klasy domyślnie nazwa arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="226f4-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="226f4-121">Na przykład jeśli customers.xsl arkusza stylów jest skompilowany, domyślną nazwę klasy jest klientów.</span><span class="sxs-lookup"><span data-stu-id="226f4-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="226f4-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="226f4-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="226f4-123">Określa, czy generować informacji o debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="226f4-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="226f4-124">Określanie `+` lub `/debug`, powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w plik programu (PDB) bazy danych.</span><span class="sxs-lookup"><span data-stu-id="226f4-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="226f4-125">Nazwa pliku PDB wygenerowanego jest `assemblyName`.pdb.</span><span class="sxs-lookup"><span data-stu-id="226f4-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="226f4-126">Określanie `-`, która jest włączona, jeśli nie określisz `/debug`, powoduje, że żadne informacje o debugowaniu ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="226f4-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="226f4-127">Generowany jest zestawem sprzedaży detalicznej.</span><span class="sxs-lookup"><span data-stu-id="226f4-127">A retail assembly is generated.</span></span> <span data-ttu-id="226f4-128">**Uwaga:** kompilowanie w trybie debugowania mogą wpływać na wydajność XSLT w znacznym stopniu.</span><span class="sxs-lookup"><span data-stu-id="226f4-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="226f4-129">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="226f4-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="226f4-130">Pomija komunikat o prawach autorskich kompilatora przy wyświetlaniu.</span><span class="sxs-lookup"><span data-stu-id="226f4-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="226f4-131">`/platform:``string`</span><span class="sxs-lookup"><span data-stu-id="226f4-131">`/platform:` `string`</span></span>|<span data-ttu-id="226f4-132">Określa platformy, które można uruchomić zestawu na.</span><span class="sxs-lookup"><span data-stu-id="226f4-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="226f4-133">Poniżej opisano platformy prawidłowe wartości:</span><span class="sxs-lookup"><span data-stu-id="226f4-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="226f4-134">`x86`kompiluje z zestawu do uruchomienia przez 32-bitowy, x86 zgodnego wykonywalnych języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="226f4-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="226f4-135">`x64`kompiluje z zestawu do uruchomienia na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T przez 64-bitowe środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="226f4-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]<span data-ttu-id="226f4-136">kompiluje z zestawu do uruchomienia w 64-bitowego środowiska CLR na komputerze, który ma [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] procesora.</span><span class="sxs-lookup"><span data-stu-id="226f4-136"> compiles your assembly to be run by the 64-bit common language runtime on a computer that has an [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] processor.</span></span><br /><br /> <span data-ttu-id="226f4-137">`anycpu`kompiluje używanemu zestawowi można uruchomić na dowolnej platformie.</span><span class="sxs-lookup"><span data-stu-id="226f4-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="226f4-138">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="226f4-138">This is the default.</span></span>|  
|<span data-ttu-id="226f4-139">`/out:``assemblyName`</span><span class="sxs-lookup"><span data-stu-id="226f4-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="226f4-140">Określa nazwę zestawu, który jest danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="226f4-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="226f4-141">Nazwy zestawu domyślnie nazwę arkusza stylów głównego lub pierwszego arkusza stylów, jeśli istnieją arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="226f4-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="226f4-142">Jeśli arkusz stylów zawiera skryptów, skrypty są zapisywane osobny zestaw.</span><span class="sxs-lookup"><span data-stu-id="226f4-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="226f4-143">Nazw zestawów skryptu są generowane na podstawie nazwy zestawu głównego.</span><span class="sxs-lookup"><span data-stu-id="226f4-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="226f4-144">Na przykład jeśli określono CustOrders.dll nazwy zestawu, pierwszy zestaw skryptu nosi nazwę CustOrders_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="226f4-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="226f4-145">`/settings:``document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="226f4-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="226f4-146">Określa, czy zezwalać `document()` funkcje, skrypt XSLT lub dokument definicji (DTD) należy wpisać w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="226f4-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="226f4-147">Domyślnie wyłącza obsługę definicji DTD, `document()` funkcji i skryptów.</span><span class="sxs-lookup"><span data-stu-id="226f4-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="226f4-148">`@``file`</span><span class="sxs-lookup"><span data-stu-id="226f4-148">`@` `file`</span></span>|<span data-ttu-id="226f4-149">Pozwala określić plik, który zawiera opcje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="226f4-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="226f4-150">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="226f4-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="226f4-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="226f4-151">Remarks</span></span>  
 <span data-ttu-id="226f4-152">Rozwiązania XSLT może obejmować wiele modułów arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="226f4-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="226f4-153">Narzędzie xsltc.exe generuje zestawy z arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="226f4-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="226f4-154">Zestawy można następnie przekazać do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="226f4-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="226f4-155">Może to ułatwić zmniejszenie kosztów wydajności w niektórych scenariuszach wdrażania XSLT.</span><span class="sxs-lookup"><span data-stu-id="226f4-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="226f4-156">Należy również uwzględnić skompilowanego zestawu jako odwołania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="226f4-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="226f4-157">Narzędzie xsltc.exe nie można zweryfikować klasy (`/class:``name`) lub zestawu (`/out:``assemblyName`) nazwy.</span><span class="sxs-lookup"><span data-stu-id="226f4-157">The xsltc.exe tool does not validate the class (`/class:``name`) or assembly (`/out:``assemblyName`) names.</span></span> <span data-ttu-id="226f4-158">Błędy zwracane przez środowisko uruchomieniowe języka wspólnego Jeśli nazwy nie są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="226f4-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="226f4-159">Przykłady</span><span class="sxs-lookup"><span data-stu-id="226f4-159">Examples</span></span>  
 <span data-ttu-id="226f4-160">Poniższe polecenie kompiluje arkusza stylów i tworzy zestaw o nazwie booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="226f4-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="226f4-161">Poniższe polecenie kompiluje arkusza stylów i powoduje utworzenie zestawu i pliku PDB, które są nazywane booksort.dll i booksort.pdb odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="226f4-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="226f4-162">Poniższe polecenie kompiluje arkusza stylów, który zawiera msxsl:script element i utworzenie dwóch zestawów o nazwie calc.dll i calc_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="226f4-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="226f4-163">Poniższe polecenie umożliwia obsługę definicji DTD przetwarzania i skryptów i tworzy dwóch zestawów o nazwie myTest.dll i myTest_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="226f4-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="226f4-164">Poniższe polecenie kompiluje dwa moduły arkusza stylów i tworzy jednym zestawie o nazwie booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="226f4-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="226f4-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="226f4-165">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="226f4-166">Instrukcje: Wykonywanie przekształcenia XSLT przy użyciu zestawu</span><span class="sxs-lookup"><span data-stu-id="226f4-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [<span data-ttu-id="226f4-167">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="226f4-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
