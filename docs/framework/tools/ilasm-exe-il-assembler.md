---
title: Ilasm.exe (Asembler IL)
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: cb995e78e534048043886070536ef0dd0a45c057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105094"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="80d53-102">Ilasm.exe (Asembler IL)</span><span class="sxs-lookup"><span data-stu-id="80d53-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="80d53-103">Program IL Assembler generuje przenośny plik wykonywalny (PE) na podstawie języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="80d53-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="80d53-104">(Aby uzyskać więcej informacji na temat il, zobacz [Managed Execution Process](../../standard/managed-execution-process.md).) Można uruchomić wynikowy plik wykonywalny, który zawiera IL i wymagane metadane, aby ustalić, czy IL działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="80d53-104">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="80d53-105">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="80d53-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="80d53-106">Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="80d53-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="80d53-107">Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="80d53-107">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="80d53-108">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="80d53-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="80d53-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="80d53-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="80d53-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="80d53-110">Parameters</span></span>

| <span data-ttu-id="80d53-111">Argument</span><span class="sxs-lookup"><span data-stu-id="80d53-111">Argument</span></span> | <span data-ttu-id="80d53-112">Opis</span><span class="sxs-lookup"><span data-stu-id="80d53-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="80d53-113">Nazwa pliku źródłowego il.</span><span class="sxs-lookup"><span data-stu-id="80d53-113">The name of the .il source file.</span></span> <span data-ttu-id="80d53-114">Ten plik zawiera dyrektywy deklaracji metadanych i symboliczne instrukcje języka IL.</span><span class="sxs-lookup"><span data-stu-id="80d53-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="80d53-115">W celu wytworzenia pojedynczego pliku PE z *plikiem Ilasm.exe*można podać wiele argumentów pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="80d53-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="80d53-116">**Uwaga:** Upewnij się, że ostatni wiersz kodu w pliku źródłowym .il ma znak końcowy lub znak końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="80d53-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="80d53-117">Opcja</span><span class="sxs-lookup"><span data-stu-id="80d53-117">Option</span></span> | <span data-ttu-id="80d53-118">Opis</span><span class="sxs-lookup"><span data-stu-id="80d53-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="80d53-119">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="80d53-119">**/32bitpreferred**</span></span>|<span data-ttu-id="80d53-120">Tworzy obraz 32-bitowy (PE32).</span><span class="sxs-lookup"><span data-stu-id="80d53-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="80d53-121">**/wyrównanie:**`integer`</span><span class="sxs-lookup"><span data-stu-id="80d53-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="80d53-122">Ustawia wyrównanie pliku na wartość `integer` określoną w nagłówku OPCJONALNY NT.</span><span class="sxs-lookup"><span data-stu-id="80d53-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="80d53-123">Jeśli dyrektywa języka IL .alignment została określona w pliku, ta opcja zastępuje ją.</span><span class="sxs-lookup"><span data-stu-id="80d53-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="80d53-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="80d53-124">**/appcontainer**</span></span>|<span data-ttu-id="80d53-125">Tworzy plik *dll* lub exe, który działa w kontenerze aplikacji systemu Windows jako dane *wyjściowe.*</span><span class="sxs-lookup"><span data-stu-id="80d53-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="80d53-126">**/ramię**</span><span class="sxs-lookup"><span data-stu-id="80d53-126">**/arm**</span></span>|<span data-ttu-id="80d53-127">Określa procesor Advanced RISC Machine (ARM) jako procesor docelowy.</span><span class="sxs-lookup"><span data-stu-id="80d53-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="80d53-128">Jeśli nie określono bitowości obrazu, wartość domyślna to **/32bitprepreferred**.</span><span class="sxs-lookup"><span data-stu-id="80d53-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="80d53-129">**/baza:**`integer`</span><span class="sxs-lookup"><span data-stu-id="80d53-129">**/base:** `integer`</span></span>|<span data-ttu-id="80d53-130">Ustawia ImageBase na wartość `integer` określoną w nagłówku OPCJONALNY NT.</span><span class="sxs-lookup"><span data-stu-id="80d53-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="80d53-131">Jeśli dyrektywa języka IL .imagebase została określona w pliku, ta opcja zastępuje ją.</span><span class="sxs-lookup"><span data-stu-id="80d53-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="80d53-132">**/zegar**</span><span class="sxs-lookup"><span data-stu-id="80d53-132">**/clock**</span></span>|<span data-ttu-id="80d53-133">Mierzy i raportuje następujące czasy kompilacji (w milisekundach) dla określonego pliku źródłowego il:</span><span class="sxs-lookup"><span data-stu-id="80d53-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="80d53-134">**Całkowita liczba uruchomionych:** całkowity czas spędzony na wykonywaniu wszystkich określonych operacji, które następują.</span><span class="sxs-lookup"><span data-stu-id="80d53-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="80d53-135">**Uruchamianie:** Ładowanie i otwieranie pliku.</span><span class="sxs-lookup"><span data-stu-id="80d53-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="80d53-136">**Emitowanie MD:** Emitowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="80d53-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="80d53-137">**Ref to Def Rozdzielczość:** Rozwiązywanie odwołań do definicji w pliku.</span><span class="sxs-lookup"><span data-stu-id="80d53-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="80d53-138">**Generowanie plików CEE**: Generowanie obrazu pliku w pamięci.</span><span class="sxs-lookup"><span data-stu-id="80d53-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="80d53-139">**Pisanie plików PE:** Zapisywanie obrazu w pliku PE.</span><span class="sxs-lookup"><span data-stu-id="80d53-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="80d53-140">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="80d53-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="80d53-141">Dołącza informacje o debugowaniu (zmienne lokalne, nazwy argumentów i numery wierszy).</span><span class="sxs-lookup"><span data-stu-id="80d53-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="80d53-142">Tworzy plik PDB.</span><span class="sxs-lookup"><span data-stu-id="80d53-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="80d53-143">**/debug** bez dodatkowej wartości wyłącza optymalizację JIT i używa punktów sekwencji z pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="80d53-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="80d53-144">**IMPL** wyłącza optymalizację JIT i używa niejawnych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="80d53-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="80d53-145">**OPT** umożliwia optymalizację JIT i używa niejawnych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="80d53-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="80d53-146">**/dll**</span><span class="sxs-lookup"><span data-stu-id="80d53-146">**/dll**</span></span>|<span data-ttu-id="80d53-147">Tworzy plik *dll* jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="80d53-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="80d53-148">**/enc:**`file`</span><span class="sxs-lookup"><span data-stu-id="80d53-148">**/enc:** `file`</span></span>|<span data-ttu-id="80d53-149">Tworzy plik różnic Edytuj-i-Kontynuuj z określonego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="80d53-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="80d53-150">Ten argument jest tylko do użytku akademickiego i nie jest obsługiwany w użytku komercyjnym.</span><span class="sxs-lookup"><span data-stu-id="80d53-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="80d53-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="80d53-151">**/exe**</span></span>|<span data-ttu-id="80d53-152">Tworzy plik wykonywalny jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="80d53-152">Produces an executable file as output.</span></span> <span data-ttu-id="80d53-153">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="80d53-153">This is the default.</span></span>|
|<span data-ttu-id="80d53-154">**/flags:**`integer`</span><span class="sxs-lookup"><span data-stu-id="80d53-154">**/flags:** `integer`</span></span>|<span data-ttu-id="80d53-155">Ustawia ImageFlags do wartości `integer` określonej w nagłówku środowiska wykonawczego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="80d53-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="80d53-156">Jeśli dyrektywa języka IL .corflags została określona w pliku, ta opcja zastępuje ją.</span><span class="sxs-lookup"><span data-stu-id="80d53-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="80d53-157">Zobacz CorHdr.h, COMIMAGE_FLAGS listę prawidłowych wartości dla *liczby całkowitej*.</span><span class="sxs-lookup"><span data-stu-id="80d53-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="80d53-158">**/złożyć**</span><span class="sxs-lookup"><span data-stu-id="80d53-158">**/fold**</span></span>|<span data-ttu-id="80d53-159">Składa identyczne treści metod w jedną.</span><span class="sxs-lookup"><span data-stu-id="80d53-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="80d53-160">/**wysoka poziomtropywy**</span><span class="sxs-lookup"><span data-stu-id="80d53-160">/**highentropyva**</span></span>|<span data-ttu-id="80d53-161">Tworzy wyjściowy plik wykonywalny, który obsługuje generowanie losowe układów przestrzeni adresowej (ASLR) o wysokiej entropii.</span><span class="sxs-lookup"><span data-stu-id="80d53-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="80d53-162">(Domyślnie dla **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="80d53-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="80d53-163">**/include:**`includePath`</span><span class="sxs-lookup"><span data-stu-id="80d53-163">**/include:** `includePath`</span></span>|<span data-ttu-id="80d53-164">Ustawia ścieżkę wyszukiwania plików dołączonych do `#include`programu .</span><span class="sxs-lookup"><span data-stu-id="80d53-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="80d53-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="80d53-165">**/itanium**</span></span>|<span data-ttu-id="80d53-166">Określa procesor Intel Itanium jako procesor docelowy.</span><span class="sxs-lookup"><span data-stu-id="80d53-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="80d53-167">Jeśli nie określono bitowości obrazu, wartością domyślną jest **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="80d53-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="80d53-168">**/key:**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="80d53-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="80d53-169">Kompiluje `filename` się z silnym podpisem `keyFile`przy użyciu klucza prywatnego zawartego w pliku .</span><span class="sxs-lookup"><span data-stu-id="80d53-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="80d53-170">**/key:** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="80d53-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="80d53-171">Kompiluje `filename` z silnym podpisem przy `keySource`użyciu klucza prywatnego produkowanego w .</span><span class="sxs-lookup"><span data-stu-id="80d53-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="80d53-172">**/aukcja**</span><span class="sxs-lookup"><span data-stu-id="80d53-172">**/listing**</span></span>|<span data-ttu-id="80d53-173">Tworzy plik listy w standardowym wyjściu.</span><span class="sxs-lookup"><span data-stu-id="80d53-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="80d53-174">Jeśli ta opcja zostanie pominięta, plik listy nie zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="80d53-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="80d53-175">Ten parametr nie jest obsługiwany w programie .NET Framework 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="80d53-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="80d53-176">**/mdv:**`versionString`</span><span class="sxs-lookup"><span data-stu-id="80d53-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="80d53-177">Ustawia ciąg wersji metadanych.</span><span class="sxs-lookup"><span data-stu-id="80d53-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="80d53-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="80d53-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="80d53-179">Ustawia wersję strumienia metadanych, gdzie `major` i `minor` są liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="80d53-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="80d53-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="80d53-180">**/noautoinherit**</span></span>|<span data-ttu-id="80d53-181">Wyłącza domyślne <xref:System.Object> dziedziczenie, gdy nie określono żadnej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="80d53-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="80d53-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="80d53-182">**/nocorstub**</span></span>|<span data-ttu-id="80d53-183">Powoduje pominięcie generowania procedury wejścia CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="80d53-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="80d53-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="80d53-184">**/nologo**</span></span>|<span data-ttu-id="80d53-185">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="80d53-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="80d53-186">**/wyjście:**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="80d53-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="80d53-187">Określa nazwę i rozszerzenie pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="80d53-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="80d53-188">Domyślnie nazwa pliku wyjściowego jest taka sama jak nazwa pierwszego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="80d53-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="80d53-189">Domyślnym rozszerzeniem jest *.exe*.</span><span class="sxs-lookup"><span data-stu-id="80d53-189">The default extension is *.exe*.</span></span> <span data-ttu-id="80d53-190">Jeśli określisz opcję **/dll,** domyślnym rozszerzeniem jest *.dll*.</span><span class="sxs-lookup"><span data-stu-id="80d53-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="80d53-191">**Uwaga:** Określenie **/output**:myfile.dll nie ustawia opcji **/dll.**</span><span class="sxs-lookup"><span data-stu-id="80d53-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="80d53-192">Jeśli nie określisz **/dll**, wynikiem będzie plik wykonywalny o nazwie *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="80d53-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="80d53-193">**/optymalizacja**</span><span class="sxs-lookup"><span data-stu-id="80d53-193">**/optimize**</span></span>|<span data-ttu-id="80d53-194">Optymalizuje długie instrukcje, co powoduje zamianę ich na krótkie.</span><span class="sxs-lookup"><span data-stu-id="80d53-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="80d53-195">Na przykład `br` `br.s`do .</span><span class="sxs-lookup"><span data-stu-id="80d53-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="80d53-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="80d53-196">**/pe64**</span></span>|<span data-ttu-id="80d53-197">Tworzy obraz 64-bitowy (PE32+).</span><span class="sxs-lookup"><span data-stu-id="80d53-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="80d53-198">Jeśli nie określono żadnego procesora docelowego, wartością domyślną jest `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="80d53-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="80d53-199">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="80d53-199">**/pdb**</span></span>|<span data-ttu-id="80d53-200">Tworzy plik PDB bez włączania śledzenia informacji o debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="80d53-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="80d53-201">**/cichy**</span><span class="sxs-lookup"><span data-stu-id="80d53-201">**/quiet**</span></span>|<span data-ttu-id="80d53-202">Określa tryb cichy; nie zgłasza postępów zestawu.</span><span class="sxs-lookup"><span data-stu-id="80d53-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="80d53-203">**/zasób:**`file.res`</span><span class="sxs-lookup"><span data-stu-id="80d53-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="80d53-204">Zawiera określony plik \*zasobu w formacie .res w wynikowym pliku *exe* lub *dll.*</span><span class="sxs-lookup"><span data-stu-id="80d53-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="80d53-205">Za pomocą opcji **/resource** można określić tylko jeden plik .res.</span><span class="sxs-lookup"><span data-stu-id="80d53-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="80d53-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="80d53-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="80d53-207">Ustawia numer wersji podsystemu w opcjonalnym nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="80d53-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="80d53-208">Dla **/appcontainer** i **/arm** minimalny numer wersji to 6.02.</span><span class="sxs-lookup"><span data-stu-id="80d53-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="80d53-209">**/stos:**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="80d53-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="80d53-210">Ustawia wartość SizeOfStackReserve w nagłówku `stackSize`NT Optional na .</span><span class="sxs-lookup"><span data-stu-id="80d53-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="80d53-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="80d53-211">**/stripreloc**</span></span>|<span data-ttu-id="80d53-212">Określa, że nie są potrzebne relokacje podstawowe.</span><span class="sxs-lookup"><span data-stu-id="80d53-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="80d53-213">**/podsystem:**`integer`</span><span class="sxs-lookup"><span data-stu-id="80d53-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="80d53-214">Ustawia podsystem na wartość `integer` określoną w nagłówku NT Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="80d53-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="80d53-215">Jeśli dyrektywa języka IL .subsystem została określona w pliku, to polecenie zastępuje ją.</span><span class="sxs-lookup"><span data-stu-id="80d53-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="80d53-216">Zobacz winnt.h, IMAGE_SUBSYSTEM listę prawidłowych wartości `integer`dla .</span><span class="sxs-lookup"><span data-stu-id="80d53-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="80d53-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="80d53-217">**/x64**</span></span>|<span data-ttu-id="80d53-218">Określa 64-bitowy procesor firmy AMD jako procesor docelowy.</span><span class="sxs-lookup"><span data-stu-id="80d53-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="80d53-219">Jeśli nie określono bitowości obrazu, wartością domyślną jest **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="80d53-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="80d53-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="80d53-220">**/?**</span></span>|<span data-ttu-id="80d53-221">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="80d53-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="80d53-222">Wszystkie opcje *ilasm.exe* są niewrażliwe na wielkość liter i rozpoznawane przez pierwsze trzy litery.</span><span class="sxs-lookup"><span data-stu-id="80d53-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="80d53-223">Na przykład **/lis** jest odpowiednikiem **/listing** i **/res**:myresfile.res jest odpowiednikiem **/resource**:myresfile.res. Opcje określające argumenty akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem.</span><span class="sxs-lookup"><span data-stu-id="80d53-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="80d53-224">Na przykład **/output**:*file.ext* jest odpowiednikiem **pliku /output**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="80d53-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="80d53-225">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80d53-225">Remarks</span></span>

<span data-ttu-id="80d53-226">Program IL Assembler umożliwia dostawcom narzędzi projektowanie i implementowanie generatorów języka IL.</span><span class="sxs-lookup"><span data-stu-id="80d53-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="80d53-227">Za pomocą *Ilasm.exe*, narzędzia i kompilator deweloperzy mogą skoncentrować się na IL i generowania metadanych bez zajmowania się emitowania IL w formacie PE.</span><span class="sxs-lookup"><span data-stu-id="80d53-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="80d53-228">Podobnie jak inne kompilatory, które są przeznaczone dla środowiska wykonawczego, takie jak C# i Visual Basic, *Ilasm.exe* nie generuje plików obiektów pośrednich i nie wymaga etapu łączenia do utworzenia pliku PE.</span><span class="sxs-lookup"><span data-stu-id="80d53-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="80d53-229">Program IL Assembler może wyrazić wszystkie istniejące metadane i funkcje IL języków programowania, które są przeznaczone dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="80d53-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="80d53-230">Dzięki temu kod zarządzany napisany w dowolnym z tych języków programowania może być odpowiednio wyrażony w IL Assembler i skompilowany z *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="80d53-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="80d53-231">Kompilacja może się nie powieść, jeśli ostatni wiersz kodu w pliku źródłowym il nie kończy się znakiem odstępu ani znakiem końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="80d53-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="80d53-232">Program *Ilasm.exe* można używać w połączeniu z narzędziem towarzyszącym [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="80d53-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="80d53-233">*Ildasm.exe* pobiera plik PE, który zawiera kod IL i tworzy plik tekstowy odpowiedni jako wejście do *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="80d53-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="80d53-234">Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="80d53-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="80d53-235">Po skompilowaniu kodu i uruchomieniu danych wyjściowych za pośrednictwem *pliku Ildasm.exe*wynikowy plik tekstowy IL może być ręcznie edytowany w celu dodania brakujących atrybutów.</span><span class="sxs-lookup"><span data-stu-id="80d53-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="80d53-236">Następnie można uruchomić ten plik tekstowy za pośrednictwem *pliku Ilasm.exe,* aby utworzyć ostateczny plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="80d53-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="80d53-237">Tej techniki można również użyć, aby utworzyć pojedynczy plik PE z kilku plików PE, oryginalnie utworzonych przez różne kompilatory.</span><span class="sxs-lookup"><span data-stu-id="80d53-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="80d53-238">Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).</span><span class="sxs-lookup"><span data-stu-id="80d53-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="80d53-239">Aby to połączone użycie *Ildasm.exe* i *Ilasm.exe* było jak najbardziej dokładne, domyślnie asembler nie zastępuje krótkich kodowania dla długich, które mogły być napisane w źródłach IL (lub które mogą być emitowane przez inny kompilator).</span><span class="sxs-lookup"><span data-stu-id="80d53-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="80d53-240">Użyj opcji **/optimize,** aby zastąpić krótkie kodowania tam, gdzie to możliwe.</span><span class="sxs-lookup"><span data-stu-id="80d53-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="80d53-241">*Ildasm.exe* działa tylko na plikach na dysku.</span><span class="sxs-lookup"><span data-stu-id="80d53-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="80d53-242">Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="80d53-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="80d53-243">Aby uzyskać więcej informacji na temat gramatyki il, zobacz asmparse.grammar pliku w windows SDK.</span><span class="sxs-lookup"><span data-stu-id="80d53-243">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="80d53-244">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="80d53-244">Version Information</span></span>

<span data-ttu-id="80d53-245">Począwszy od programu .NET Framework 4.5, można dołączyć atrybut niestandardowy do implementacji interfejsu przy użyciu kodu podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="80d53-245">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="80d53-246">Począwszy od programu .NET Framework 4.5, można określić dowolny obiekt BLOB (binarny duży obiekt) przy użyciu jego surowej reprezentacji binarnej, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="80d53-246">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="80d53-247">Aby uzyskać więcej informacji na temat gramatyki il, zobacz asmparse.grammar pliku w windows SDK.</span><span class="sxs-lookup"><span data-stu-id="80d53-247">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="80d53-248">Przykłady</span><span class="sxs-lookup"><span data-stu-id="80d53-248">Examples</span></span>

<span data-ttu-id="80d53-249">Następujące polecenie składa plik IL *myTestFile.il* i tworzy plik wykonywalny *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="80d53-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="80d53-250">Następujące polecenie składa plik IL *myTestFile.il* i tworzy plik *dll* *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="80d53-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="80d53-251">Następujące polecenie składa plik IL *myTestFile.il* i tworzy plik *.dll* *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="80d53-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="80d53-252">Poniższy przykład kodu pokazuje niezwykle prostą aplikację, która wyświetla "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="80d53-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="80d53-253">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="80d53-253">to the console.</span></span> <span data-ttu-id="80d53-254">Można skompilować ten kod, a następnie użyć narzędzia [*Ildasm.exe*](ildasm-exe-il-disassembler.md) do wygenerowania pliku IL.</span><span class="sxs-lookup"><span data-stu-id="80d53-254">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="80d53-255">Poniższy przykład kodu w języku IL odpowiada poprzedniemu przykładowi kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="80d53-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="80d53-256">Ten kod można skompilować do zestawu przy użyciu narzędzia IL Assembler.</span><span class="sxs-lookup"><span data-stu-id="80d53-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="80d53-257">Zarówno IL i C# kod przykłady wyświetlają "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="80d53-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="80d53-258">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="80d53-258">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="80d53-259">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80d53-259">See also</span></span>

- [<span data-ttu-id="80d53-260">narzędzia</span><span class="sxs-lookup"><span data-stu-id="80d53-260">Tools</span></span>](index.md)
- [<span data-ttu-id="80d53-261">*Ildasm.exe* (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="80d53-261">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="80d53-262">Proces zarządzanego wykonania</span><span class="sxs-lookup"><span data-stu-id="80d53-262">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="80d53-263">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="80d53-263">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
