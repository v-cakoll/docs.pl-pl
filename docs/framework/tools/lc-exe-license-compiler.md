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
ms.openlocfilehash: c5a8b38e819c323a06faad2edba586cb18d26edc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409081"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="29819-102">Lc.exe (Kompilator licencji)</span><span class="sxs-lookup"><span data-stu-id="29819-102">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="29819-103">Kompilator licencji czyta pliki tekstowe zawierające informacje o licencjonowaniu i tworzy plik binarny, który może zostać osadzony jako zasób w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="29819-103">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="29819-104">Plik tekstowy licx jest automatycznie generowany lub aktualizowany przez Projektanta programu Windows Forms zawsze, gdy licencjonowany formant jest dodawany do formularza.</span><span class="sxs-lookup"><span data-stu-id="29819-104">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="29819-105">W ramach kompilacji system projektu przekształci plik tekstowy licx w zasób binarny licenses, który dostarcza obsługę licencjonowania formantów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="29819-105">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="29819-106">Następnie ten zasób binarny zostanie osadzony w danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="29819-106">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="29819-107">Krzyżowa kompilacja wersji 32-bitowych i 64-bitowych jest nieobsługiwana, gdy podczas kompilowania projektu jest używany Kompilator licencji.</span><span class="sxs-lookup"><span data-stu-id="29819-107">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="29819-108">Jest to spowodowane tym, że Kompilator licencji musi ładować zestawy, a ładowanie 64-bitowych zestawów z aplikacji 32-bitowej (i odwrotnie) jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="29819-108">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="29819-109">W takim przypadku należy użyć Kompilatora licencji z wiersza polecenia, aby skompilować licencję ręcznie i określić odpowiednią architekturę.</span><span class="sxs-lookup"><span data-stu-id="29819-109">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="29819-110">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="29819-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="29819-111">Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="29819-111">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="29819-112">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="29819-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="29819-113">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="29819-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29819-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="29819-114">Syntax</span></span>  
  
```  
      lc /target:  
      targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="29819-115">Opcja</span><span class="sxs-lookup"><span data-stu-id="29819-115">Option</span></span>|<span data-ttu-id="29819-116">Opis</span><span class="sxs-lookup"><span data-stu-id="29819-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="29819-117">**/complist:** *filename*</span><span class="sxs-lookup"><span data-stu-id="29819-117">**/complist:** *filename*</span></span>|<span data-ttu-id="29819-118">Określa nazwę pliku zawierającego listę licencjonowanych składników, która ma zostać umieszczona w pliku licenses.</span><span class="sxs-lookup"><span data-stu-id="29819-118">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="29819-119">W odwołaniu do każdego składnika musi być używana jego pełna nazwa, a w wierszu może znajdować się tylko jeden składnik.</span><span class="sxs-lookup"><span data-stu-id="29819-119">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="29819-120">Użytkownicy wiersza polecenia mogą określić osobny plik dla każdego formularza w projekcie.</span><span class="sxs-lookup"><span data-stu-id="29819-120">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="29819-121">Program LC.exe akceptuje wiele plików wejściowych i tworzy jeden plik licenses.</span><span class="sxs-lookup"><span data-stu-id="29819-121">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="29819-122">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="29819-122">**/h**[**elp**]</span></span>|<span data-ttu-id="29819-123">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="29819-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="29819-124">**i:** *modułu*</span><span class="sxs-lookup"><span data-stu-id="29819-124">**/i:** *module*</span></span>|<span data-ttu-id="29819-125">Określa modułów zawierających składniki na liście **/complist** pliku.</span><span class="sxs-lookup"><span data-stu-id="29819-125">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="29819-126">Aby określić więcej niż jeden moduł, użyj wielu **/i** flagi.</span><span class="sxs-lookup"><span data-stu-id="29819-126">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="29819-127">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="29819-127">**/nologo**</span></span>|<span data-ttu-id="29819-128">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29819-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="29819-129">**firmy:** *ścieżki*</span><span class="sxs-lookup"><span data-stu-id="29819-129">**/outdir:** *path*</span></span>|<span data-ttu-id="29819-130">Określa katalog, w którym ma zostać umieszczony wyjściowy plik licenses.</span><span class="sxs-lookup"><span data-stu-id="29819-130">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="29819-131">**/ target:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="29819-131">**/target:** *targetPE*</span></span>|<span data-ttu-id="29819-132">Określa plik wykonywalny, dla którego jest generowany plik licenses.</span><span class="sxs-lookup"><span data-stu-id="29819-132">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="29819-133">**/v**</span><span class="sxs-lookup"><span data-stu-id="29819-133">**/v**</span></span>|<span data-ttu-id="29819-134">Określa tryb pełny; wyświetla informacje o postępie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="29819-134">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="29819-135">**@** *Plik*</span><span class="sxs-lookup"><span data-stu-id="29819-135">**@** *file*</span></span>|<span data-ttu-id="29819-136">Określa plik odpowiedzi (.rsp —).</span><span class="sxs-lookup"><span data-stu-id="29819-136">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="29819-137">**/?**</span><span class="sxs-lookup"><span data-stu-id="29819-137">**/?**</span></span>|<span data-ttu-id="29819-138">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="29819-138">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="29819-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="29819-139">Example</span></span>  
  
1.  <span data-ttu-id="29819-140">Jeśli używasz licencjonowanego formantu `MyCompany.Samples.LicControl1` zawartych w `Samples.DLL` w aplikacji o nazwie `HostApp.exe` *,* można utworzyć `HostAppLic.txt` zawiera następujące.</span><span class="sxs-lookup"><span data-stu-id="29819-140">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2.  <span data-ttu-id="29819-141">Utwórz .licenses — plik o nazwie `HostApp.exe.licenses` przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="29819-141">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3.  <span data-ttu-id="29819-142">Tworzenie `HostApp.exe` tym .licenses — plik jako zasób.</span><span class="sxs-lookup"><span data-stu-id="29819-142">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="29819-143">W przypadku kompilowania aplikacji w języku C# należy użyć następującego polecenia, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="29819-143">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="29819-144">Następujące polecenie kompiluje `myApp.licenses` z list licencjonowane składniki określony przez `hostapplic.txt`, `hostapplic2.txt` i `hostapplic3.txt`.</span><span class="sxs-lookup"><span data-stu-id="29819-144">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="29819-145">`modulesList` Argument określa modułów zawierających składniki licencjonowane.</span><span class="sxs-lookup"><span data-stu-id="29819-145">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="29819-146">Przykładowy plik odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="29819-146">Response File Example</span></span>  
 <span data-ttu-id="29819-147">Poniżej przedstawiono przykładowy plik odpowiedzi `response.rsp`.</span><span class="sxs-lookup"><span data-stu-id="29819-147">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="29819-148">Aby uzyskać więcej informacji na pliki odpowiedzi, zobacz [pliki odpowiedzi](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="29819-148">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="29819-149">Następujące zastosowania wiersza polecenia `response.rsp` pliku.</span><span class="sxs-lookup"><span data-stu-id="29819-149">The following command line uses the `response.rsp` file.</span></span>  
  
```  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="29819-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29819-150">See Also</span></span>  
 [<span data-ttu-id="29819-151">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="29819-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="29819-152">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="29819-152">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="29819-153">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="29819-153">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
