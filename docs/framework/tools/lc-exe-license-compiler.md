---
title: Lc.exe (Kompilator licencji)
description: Użyj Lc.exe, kompilatora licencji. To narzędzie odczytuje pliki tekstowe z informacjami o licencjonowaniu i tworzy plik binarny do osadzenia w pliku wykonywalnym CLR jako zasób.
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 45a80ba7c3e24c0f419758315b2d2daafd3890f4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164250"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="09013-104">Lc.exe (Kompilator licencji)</span><span class="sxs-lookup"><span data-stu-id="09013-104">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="09013-105">Kompilator licencji czyta pliki tekstowe zawierające informacje o licencjonowaniu i tworzy plik binarny, który może zostać osadzony jako zasób w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="09013-105">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="09013-106">Plik tekstowy licx jest automatycznie generowany lub aktualizowany przez Projektanta programu Windows Forms zawsze, gdy licencjonowany formant jest dodawany do formularza.</span><span class="sxs-lookup"><span data-stu-id="09013-106">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="09013-107">W ramach kompilacji system projektu przekształci plik tekstowy licx w zasób binarny licenses, który dostarcza obsługę licencjonowania formantów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="09013-107">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="09013-108">Następnie ten zasób binarny zostanie osadzony w danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="09013-108">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="09013-109">Krzyżowa kompilacja wersji 32-bitowych i 64-bitowych jest nieobsługiwana, gdy podczas kompilowania projektu jest używany Kompilator licencji.</span><span class="sxs-lookup"><span data-stu-id="09013-109">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="09013-110">Jest to spowodowane tym, że Kompilator licencji musi ładować zestawy, a ładowanie 64-bitowych zestawów z aplikacji 32-bitowej (i odwrotnie) jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="09013-110">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="09013-111">W takim przypadku należy użyć Kompilatora licencji z wiersza polecenia, aby skompilować licencję ręcznie i określić odpowiednią architekturę.</span><span class="sxs-lookup"><span data-stu-id="09013-111">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="09013-112">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09013-112">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="09013-113">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="09013-113">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="09013-114">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="09013-114">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="09013-115">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="09013-115">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09013-116">Składnia</span><span class="sxs-lookup"><span data-stu-id="09013-116">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="09013-117">Opcja</span><span class="sxs-lookup"><span data-stu-id="09013-117">Option</span></span>|<span data-ttu-id="09013-118">Opis</span><span class="sxs-lookup"><span data-stu-id="09013-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="09013-119">**/complist:** *filename*</span><span class="sxs-lookup"><span data-stu-id="09013-119">**/complist:** *filename*</span></span>|<span data-ttu-id="09013-120">Określa nazwę pliku zawierającego listę licencjonowanych składników, która ma zostać umieszczona w pliku licenses.</span><span class="sxs-lookup"><span data-stu-id="09013-120">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="09013-121">W odwołaniu do każdego składnika musi być używana jego pełna nazwa, a w wierszu może znajdować się tylko jeden składnik.</span><span class="sxs-lookup"><span data-stu-id="09013-121">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="09013-122">Użytkownicy wiersza polecenia mogą określić osobny plik dla każdego formularza w projekcie.</span><span class="sxs-lookup"><span data-stu-id="09013-122">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="09013-123">Program LC.exe akceptuje wiele plików wejściowych i tworzy jeden plik licenses.</span><span class="sxs-lookup"><span data-stu-id="09013-123">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="09013-124">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="09013-124">**/h**[**elp**]</span></span>|<span data-ttu-id="09013-125">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09013-125">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="09013-126">**/i:** *moduł*</span><span class="sxs-lookup"><span data-stu-id="09013-126">**/i:** *module*</span></span>|<span data-ttu-id="09013-127">Określa moduły zawierające składniki wymienione w pliku **/complist** .</span><span class="sxs-lookup"><span data-stu-id="09013-127">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="09013-128">Aby określić więcej niż jeden moduł, Użyj wielu flag **/i** .</span><span class="sxs-lookup"><span data-stu-id="09013-128">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="09013-129">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="09013-129">**/nologo**</span></span>|<span data-ttu-id="09013-130">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="09013-130">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="09013-131">**/OutDir:** *ścieżka*</span><span class="sxs-lookup"><span data-stu-id="09013-131">**/outdir:** *path*</span></span>|<span data-ttu-id="09013-132">Określa katalog, w którym ma zostać umieszczony wyjściowy plik licenses.</span><span class="sxs-lookup"><span data-stu-id="09013-132">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="09013-133">**/target:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="09013-133">**/target:** *targetPE*</span></span>|<span data-ttu-id="09013-134">Określa plik wykonywalny, dla którego jest generowany plik licenses.</span><span class="sxs-lookup"><span data-stu-id="09013-134">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="09013-135">**przełącznika**</span><span class="sxs-lookup"><span data-stu-id="09013-135">**/v**</span></span>|<span data-ttu-id="09013-136">Określa tryb pełny; wyświetla informacje o postępie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="09013-136">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="09013-137">\**@\*\*\*plik*</span><span class="sxs-lookup"><span data-stu-id="09013-137">**@** *file*</span></span>|<span data-ttu-id="09013-138">Określa plik odpowiedzi (. RSP).</span><span class="sxs-lookup"><span data-stu-id="09013-138">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="09013-139">**/?**</span><span class="sxs-lookup"><span data-stu-id="09013-139">**/?**</span></span>|<span data-ttu-id="09013-140">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="09013-140">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09013-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="09013-141">Example</span></span>  
  
1. <span data-ttu-id="09013-142">Jeśli używasz licencjonowanej kontroli `MyCompany.Samples.LicControl1` zawartej w `Samples.DLL` w aplikacji o nazwie `HostApp.exe` *,* możesz utworzyć `HostAppLic.txt` , która zawiera poniższe elementy.</span><span class="sxs-lookup"><span data-stu-id="09013-142">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="09013-143">Utwórz plik. licenses o nazwie `HostApp.exe.licenses` przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="09013-143">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="09013-144">Kompilacja `HostApp.exe` obejmująca plik. licenses jako zasób.</span><span class="sxs-lookup"><span data-stu-id="09013-144">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="09013-145">W przypadku kompilowania aplikacji w języku C# należy użyć następującego polecenia, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="09013-145">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="09013-146">Następujące polecenie kompiluje `myApp.licenses` z list licencjonowanych składników określonych przez `hostapplic.txt` , `hostapplic2.txt` i `hostapplic3.txt` .</span><span class="sxs-lookup"><span data-stu-id="09013-146">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="09013-147">`modulesList`Argument określa moduły zawierające licencjonowane składniki.</span><span class="sxs-lookup"><span data-stu-id="09013-147">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="09013-148">Przykład pliku odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="09013-148">Response File Example</span></span>  
 <span data-ttu-id="09013-149">Na poniższej liście przedstawiono przykład pliku odpowiedzi, `response.rsp` .</span><span class="sxs-lookup"><span data-stu-id="09013-149">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="09013-150">Aby uzyskać więcej informacji na temat plików odpowiedzi, zobacz [pliki odpowiedzi](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="09013-150">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="09013-151">Poniższy wiersz polecenia używa `response.rsp` pliku.</span><span class="sxs-lookup"><span data-stu-id="09013-151">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="09013-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09013-152">See also</span></span>

- [<span data-ttu-id="09013-153">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="09013-153">Tools</span></span>](index.md)
- [<span data-ttu-id="09013-154">Al.exe (Konsolidator zestawu)</span><span class="sxs-lookup"><span data-stu-id="09013-154">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="09013-155">Wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="09013-155">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
