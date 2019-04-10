---
title: Lc.exe (Kompilator licencji)
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
ms.openlocfilehash: 6c4432d94372ce10ee9ecdf6e441eda3318a20d7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298971"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="051db-102">Lc.exe (Kompilator licencji)</span><span class="sxs-lookup"><span data-stu-id="051db-102">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="051db-103">Kompilator licencji czyta pliki tekstowe zawierające informacje o licencjonowaniu i tworzy plik binarny, który może zostać osadzony jako zasób w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="051db-103">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="051db-104">Plik tekstowy licx jest automatycznie generowany lub aktualizowany przez Projektanta programu Windows Forms zawsze, gdy licencjonowany formant jest dodawany do formularza.</span><span class="sxs-lookup"><span data-stu-id="051db-104">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="051db-105">W ramach kompilacji system projektu przekształci plik tekstowy licx w zasób binarny licenses, który dostarcza obsługę licencjonowania formantów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="051db-105">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="051db-106">Następnie ten zasób binarny zostanie osadzony w danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="051db-106">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="051db-107">Krzyżowa kompilacja wersji 32-bitowych i 64-bitowych jest nieobsługiwana, gdy podczas kompilowania projektu jest używany Kompilator licencji.</span><span class="sxs-lookup"><span data-stu-id="051db-107">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="051db-108">Jest to spowodowane tym, że Kompilator licencji musi ładować zestawy, a ładowanie 64-bitowych zestawów z aplikacji 32-bitowej (i odwrotnie) jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="051db-108">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="051db-109">W takim przypadku należy użyć Kompilatora licencji z wiersza polecenia, aby skompilować licencję ręcznie i określić odpowiednią architekturę.</span><span class="sxs-lookup"><span data-stu-id="051db-109">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="051db-110">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="051db-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="051db-111">Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7).</span><span class="sxs-lookup"><span data-stu-id="051db-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="051db-112">Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="051db-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="051db-113">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="051db-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="051db-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="051db-114">Syntax</span></span>  
  
```  
      lc /target:  
      targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="051db-115">Opcja</span><span class="sxs-lookup"><span data-stu-id="051db-115">Option</span></span>|<span data-ttu-id="051db-116">Opis</span><span class="sxs-lookup"><span data-stu-id="051db-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="051db-117">**/complist:** *nazwy pliku*</span><span class="sxs-lookup"><span data-stu-id="051db-117">**/complist:** *filename*</span></span>|<span data-ttu-id="051db-118">Określa nazwę pliku zawierającego listę licencjonowanych składników, która ma zostać umieszczona w pliku licenses.</span><span class="sxs-lookup"><span data-stu-id="051db-118">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="051db-119">W odwołaniu do każdego składnika musi być używana jego pełna nazwa, a w wierszu może znajdować się tylko jeden składnik.</span><span class="sxs-lookup"><span data-stu-id="051db-119">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="051db-120">Użytkownicy wiersza polecenia mogą określić osobny plik dla każdego formularza w projekcie.</span><span class="sxs-lookup"><span data-stu-id="051db-120">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="051db-121">Program LC.exe akceptuje wiele plików wejściowych i tworzy jeden plik licenses.</span><span class="sxs-lookup"><span data-stu-id="051db-121">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="051db-122">**/ h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="051db-122">**/h**[**elp**]</span></span>|<span data-ttu-id="051db-123">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="051db-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="051db-124">**i:** *modułu*</span><span class="sxs-lookup"><span data-stu-id="051db-124">**/i:** *module*</span></span>|<span data-ttu-id="051db-125">Określa moduły, które zawierają składniki wymienione w **/complist** pliku.</span><span class="sxs-lookup"><span data-stu-id="051db-125">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="051db-126">Aby określić więcej niż jeden moduł, używanych jest wiele **/i** flag.</span><span class="sxs-lookup"><span data-stu-id="051db-126">To specify more than one module, use multiple **/i** flags.</span></span>|  
|**<span data-ttu-id="051db-127">/nologo</span><span class="sxs-lookup"><span data-stu-id="051db-127">/nologo</span></span>**|<span data-ttu-id="051db-128">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="051db-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="051db-129">**do pliku klucza:** *ścieżki*</span><span class="sxs-lookup"><span data-stu-id="051db-129">**/outdir:** *path*</span></span>|<span data-ttu-id="051db-130">Określa katalog, w którym ma zostać umieszczony wyjściowy plik licenses.</span><span class="sxs-lookup"><span data-stu-id="051db-130">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="051db-131">**/ target:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="051db-131">**/target:** *targetPE*</span></span>|<span data-ttu-id="051db-132">Określa plik wykonywalny, dla którego jest generowany plik licenses.</span><span class="sxs-lookup"><span data-stu-id="051db-132">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|**<span data-ttu-id="051db-133">/v</span><span class="sxs-lookup"><span data-stu-id="051db-133">/v</span></span>**|<span data-ttu-id="051db-134">Określa tryb pełny; wyświetla informacje o postępie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="051db-134">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="051db-135">**@** *Plik*</span><span class="sxs-lookup"><span data-stu-id="051db-135">**@** *file*</span></span>|<span data-ttu-id="051db-136">Określa plik odpowiedzi (rsp).</span><span class="sxs-lookup"><span data-stu-id="051db-136">Specifies the response (.rsp) file.</span></span>|  
|**<span data-ttu-id="051db-137">/?</span><span class="sxs-lookup"><span data-stu-id="051db-137">/?</span></span>**|<span data-ttu-id="051db-138">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="051db-138">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="051db-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="051db-139">Example</span></span>  
  
1. <span data-ttu-id="051db-140">Jeśli używasz licencjonowany formant `MyCompany.Samples.LicControl1` zawarte w `Samples.DLL` w aplikacji o nazwie `HostApp.exe` *,* można utworzyć `HostAppLic.txt` zawiera następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="051db-140">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="051db-141">Utwórz plik licenses o nazwie `HostApp.exe.licenses` przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="051db-141">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="051db-142">Tworzenie `HostApp.exe` dołączając plik licenses jako zasób.</span><span class="sxs-lookup"><span data-stu-id="051db-142">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="051db-143">W przypadku kompilowania aplikacji w języku C# należy użyć następującego polecenia, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="051db-143">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="051db-144">Następujące polecenie kompiluje `myApp.licenses` z list licencjonowanych składników `hostapplic.txt`, `hostapplic2.txt` i `hostapplic3.txt`.</span><span class="sxs-lookup"><span data-stu-id="051db-144">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="051db-145">`modulesList` Argument określa moduły zawierające licencjonowane składniki.</span><span class="sxs-lookup"><span data-stu-id="051db-145">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="051db-146">Przykład pliku odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="051db-146">Response File Example</span></span>  
 <span data-ttu-id="051db-147">Poniżej przedstawiono przykładowy plik odpowiedzi, `response.rsp`.</span><span class="sxs-lookup"><span data-stu-id="051db-147">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="051db-148">Aby uzyskać więcej informacji na temat plików odpowiedzi, zobacz [pliki odpowiedzi](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="051db-148">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="051db-149">Następujące zastosowania wiersza polecenia `response.rsp` pliku.</span><span class="sxs-lookup"><span data-stu-id="051db-149">The following command line uses the `response.rsp` file.</span></span>  
  
```  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="051db-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="051db-150">See also</span></span>

- [<span data-ttu-id="051db-151">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="051db-151">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="051db-152">Al.exe (Konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="051db-152">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="051db-153">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="051db-153">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
