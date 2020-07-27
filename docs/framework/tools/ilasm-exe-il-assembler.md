---
title: Ilasm.exe (Asembler IL)
description: Zacznij korzystać z Ilasm.exe, asemblera IL. To narzędzie generuje przenośny plik wykonywalny (PE) z języka pośredniego (IL).
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
ms.openlocfilehash: 1a85b3bf9509ffba6c2331d14196a6bef2bfa080
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166981"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="38924-104">Ilasm.exe (Asembler IL)</span><span class="sxs-lookup"><span data-stu-id="38924-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="38924-105">Program IL Assembler generuje przenośny plik wykonywalny (PE) na podstawie języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="38924-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="38924-106">(Aby uzyskać więcej informacji na temat IL, zobacz [zarządzany proces wykonywania](../../standard/managed-execution-process.md)). Można uruchomić utworzony plik wykonywalny zawierający kod IL i wymagane metadane, aby określić, czy IL działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="38924-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="38924-107">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="38924-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="38924-108">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="38924-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="38924-109">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="38924-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="38924-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="38924-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="38924-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="38924-111">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="38924-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="38924-112">Parameters</span></span>

| <span data-ttu-id="38924-113">Argument</span><span class="sxs-lookup"><span data-stu-id="38924-113">Argument</span></span> | <span data-ttu-id="38924-114">Opis</span><span class="sxs-lookup"><span data-stu-id="38924-114">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="38924-115">Nazwa pliku źródłowego il.</span><span class="sxs-lookup"><span data-stu-id="38924-115">The name of the .il source file.</span></span> <span data-ttu-id="38924-116">Ten plik zawiera dyrektywy deklaracji metadanych i symboliczne instrukcje języka IL.</span><span class="sxs-lookup"><span data-stu-id="38924-116">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="38924-117">Można dostarczyć wiele argumentów plików źródłowych, aby utworzyć jeden plik PE z *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="38924-117">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="38924-118">**Uwaga:** Upewnij się, że ostatni wiersz kodu w pliku źródłowym Il ma końcowe białe znaki lub znak końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="38924-118">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="38924-119">Opcja</span><span class="sxs-lookup"><span data-stu-id="38924-119">Option</span></span> | <span data-ttu-id="38924-120">Opis</span><span class="sxs-lookup"><span data-stu-id="38924-120">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="38924-121">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="38924-121">**/32bitpreferred**</span></span>|<span data-ttu-id="38924-122">Tworzy obraz 32-bitowy (PE32).</span><span class="sxs-lookup"><span data-stu-id="38924-122">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="38924-123">**/Alignment:**`integer`</span><span class="sxs-lookup"><span data-stu-id="38924-123">**/alignment:** `integer`</span></span>|<span data-ttu-id="38924-124">Ustawia FileAlignment na wartość określoną przez `integer` w opcjonalnym nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="38924-124">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="38924-125">Jeśli dyrektywa języka IL .alignment została określona w pliku, ta opcja zastępuje ją.</span><span class="sxs-lookup"><span data-stu-id="38924-125">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="38924-126">**/APPCONTAINER**</span><span class="sxs-lookup"><span data-stu-id="38924-126">**/appcontainer**</span></span>|<span data-ttu-id="38924-127">Tworzy plik *. dll* lub *. exe* , który jest uruchamiany w kontenerze aplikacji systemu Windows jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="38924-127">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="38924-128">**/arm**</span><span class="sxs-lookup"><span data-stu-id="38924-128">**/arm**</span></span>|<span data-ttu-id="38924-129">Określa procesor Advanced RISC Machine (ARM) jako procesor docelowy.</span><span class="sxs-lookup"><span data-stu-id="38924-129">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="38924-130">Jeśli nie określono liczby bitów obrazu, wartość domyślna to **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="38924-130">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="38924-131">**/Base:**`integer`</span><span class="sxs-lookup"><span data-stu-id="38924-131">**/base:** `integer`</span></span>|<span data-ttu-id="38924-132">Ustawia ImageBase na wartość określoną przez `integer` w opcjonalnym nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="38924-132">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="38924-133">Jeśli dyrektywa języka IL .imagebase została określona w pliku, ta opcja zastępuje ją.</span><span class="sxs-lookup"><span data-stu-id="38924-133">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="38924-134">**/clock**</span><span class="sxs-lookup"><span data-stu-id="38924-134">**/clock**</span></span>|<span data-ttu-id="38924-135">Mierzy i raportuje następujące czasy kompilacji (w milisekundach) dla określonego pliku źródłowego il:</span><span class="sxs-lookup"><span data-stu-id="38924-135">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="38924-136">**Łączny przebieg**: łączny czas poświęcony na wykonywanie wszystkich określonych operacji.</span><span class="sxs-lookup"><span data-stu-id="38924-136">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="38924-137">**Uruchamianie**: ładowanie i otwieranie pliku.</span><span class="sxs-lookup"><span data-stu-id="38924-137">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="38924-138">**Emitowanie MD**: emitowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="38924-138">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="38924-139">**Odwołanie do rozdzielczości def**: Rozpoznawanie odwołań do definicji w pliku.</span><span class="sxs-lookup"><span data-stu-id="38924-139">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="38924-140">**Generowanie pliku CEE**: generowanie obrazu pliku w pamięci.</span><span class="sxs-lookup"><span data-stu-id="38924-140">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="38924-141">**Zapisywanie pliku PE**: Zapisywanie obrazu do pliku PE.</span><span class="sxs-lookup"><span data-stu-id="38924-141">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="38924-142">**/Debug**[:**Impl**&#124;**opt**]</span><span class="sxs-lookup"><span data-stu-id="38924-142">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="38924-143">Dołącza informacje o debugowaniu (zmienne lokalne, nazwy argumentów i numery wierszy).</span><span class="sxs-lookup"><span data-stu-id="38924-143">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="38924-144">Tworzy plik PDB.</span><span class="sxs-lookup"><span data-stu-id="38924-144">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="38924-145">**/Debug** bez dodatkowych wartości wyłącza optymalizację JIT i używa punktów sekwencji z pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="38924-145">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="38924-146">**Impl** wyłącza optymalizację JIT i używa niejawnych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="38924-146">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="38924-147">Opcja **opt** włącza optymalizację JIT i używa niejawnych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="38924-147">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="38924-148">**/DLL**</span><span class="sxs-lookup"><span data-stu-id="38924-148">**/dll**</span></span>|<span data-ttu-id="38924-149">Tworzy plik *. dll* jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="38924-149">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="38924-150">**/ENC:**`file`</span><span class="sxs-lookup"><span data-stu-id="38924-150">**/enc:** `file`</span></span>|<span data-ttu-id="38924-151">Tworzy plik różnic Edytuj-i-Kontynuuj z określonego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="38924-151">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="38924-152">Ten argument jest tylko do użytku akademickiego i nie jest obsługiwany w użytku komercyjnym.</span><span class="sxs-lookup"><span data-stu-id="38924-152">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="38924-153">**/exe**</span><span class="sxs-lookup"><span data-stu-id="38924-153">**/exe**</span></span>|<span data-ttu-id="38924-154">Tworzy plik wykonywalny jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="38924-154">Produces an executable file as output.</span></span> <span data-ttu-id="38924-155">Jest to opcja domyślna.</span><span class="sxs-lookup"><span data-stu-id="38924-155">This is the default.</span></span>|
|<span data-ttu-id="38924-156">**/flags:**`integer`</span><span class="sxs-lookup"><span data-stu-id="38924-156">**/flags:** `integer`</span></span>|<span data-ttu-id="38924-157">Ustawia ImageFlags na wartość określoną przez `integer` w nagłówku środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="38924-157">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="38924-158">Jeśli dyrektywa języka IL .corflags została określona w pliku, ta opcja zastępuje ją.</span><span class="sxs-lookup"><span data-stu-id="38924-158">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="38924-159">Zobacz CorHdr. h, COMIMAGE_FLAGS, aby uzyskać listę prawidłowych wartości dla *liczby całkowitej*.</span><span class="sxs-lookup"><span data-stu-id="38924-159">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="38924-160">**/fold**</span><span class="sxs-lookup"><span data-stu-id="38924-160">**/fold**</span></span>|<span data-ttu-id="38924-161">Składa identyczne treści metod w jedną.</span><span class="sxs-lookup"><span data-stu-id="38924-161">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="38924-162">/**HIGHENTROPYVA**</span><span class="sxs-lookup"><span data-stu-id="38924-162">/**highentropyva**</span></span>|<span data-ttu-id="38924-163">Tworzy wyjściowy plik wykonywalny, który obsługuje generowanie losowe układów przestrzeni adresowej (ASLR) o wysokiej entropii.</span><span class="sxs-lookup"><span data-stu-id="38924-163">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="38924-164">(Domyślnie dla **/APPCONTAINER**).</span><span class="sxs-lookup"><span data-stu-id="38924-164">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="38924-165">**/include:**`includePath`</span><span class="sxs-lookup"><span data-stu-id="38924-165">**/include:** `includePath`</span></span>|<span data-ttu-id="38924-166">Ustawia ścieżkę do wyszukiwania plików dołączonych do programu `#include` .</span><span class="sxs-lookup"><span data-stu-id="38924-166">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="38924-167">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="38924-167">**/itanium**</span></span>|<span data-ttu-id="38924-168">Określa procesor Intel Itanium jako procesor docelowy.</span><span class="sxs-lookup"><span data-stu-id="38924-168">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="38924-169">Jeśli nie określono liczby bitów obrazu, wartość domyślna to **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="38924-169">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="38924-170">**/Key:**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="38924-170">**/key:** `keyFile`</span></span>|<span data-ttu-id="38924-171">Kompiluje `filename` ze silnym podpisem przy użyciu klucza prywatnego zawartego w `keyFile` .</span><span class="sxs-lookup"><span data-stu-id="38924-171">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="38924-172">**/Key** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="38924-172">**/key:** @`keySource`</span></span>|<span data-ttu-id="38924-173">Kompiluje `filename` ze silnym podpisem przy użyciu klucza prywatnego, który został utworzony w `keySource` .</span><span class="sxs-lookup"><span data-stu-id="38924-173">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="38924-174">**/listing**</span><span class="sxs-lookup"><span data-stu-id="38924-174">**/listing**</span></span>|<span data-ttu-id="38924-175">Tworzy plik listy w standardowym wyjściu.</span><span class="sxs-lookup"><span data-stu-id="38924-175">Produces a listing file on the standard output.</span></span> <span data-ttu-id="38924-176">Jeśli ta opcja zostanie pominięta, plik listy nie zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="38924-176">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="38924-177">Ten parametr nie jest obsługiwany w programie .NET Framework 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="38924-177">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="38924-178">**/MDV:**`versionString`</span><span class="sxs-lookup"><span data-stu-id="38924-178">**/mdv:** `versionString`</span></span>|<span data-ttu-id="38924-179">Ustawia ciąg wersji metadanych.</span><span class="sxs-lookup"><span data-stu-id="38924-179">Sets the metadata version string.</span></span>|
|<span data-ttu-id="38924-180">**/MSV:** `major` .`minor`</span><span class="sxs-lookup"><span data-stu-id="38924-180">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="38924-181">Ustawia wersję strumienia metadanych, gdzie `major` i `minor` są liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="38924-181">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="38924-182">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="38924-182">**/noautoinherit**</span></span>|<span data-ttu-id="38924-183">Wyłącza dziedziczenie domyślne z <xref:System.Object> gdy nie określono żadnej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="38924-183">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="38924-184">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="38924-184">**/nocorstub**</span></span>|<span data-ttu-id="38924-185">Powoduje pominięcie generowania procedury wejścia CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="38924-185">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="38924-186">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="38924-186">**/nologo**</span></span>|<span data-ttu-id="38924-187">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38924-187">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="38924-188">**/Output:**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="38924-188">**/output:** `file.ext`</span></span>|<span data-ttu-id="38924-189">Określa nazwę i rozszerzenie pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="38924-189">Specifies the output file name and extension.</span></span> <span data-ttu-id="38924-190">Domyślnie nazwa pliku wyjściowego jest taka sama jak nazwa pierwszego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="38924-190">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="38924-191">Domyślnym rozszerzeniem jest *. exe*.</span><span class="sxs-lookup"><span data-stu-id="38924-191">The default extension is *.exe*.</span></span> <span data-ttu-id="38924-192">W przypadku określenia opcji **/dll** domyślne rozszerzenie to *. dll*.</span><span class="sxs-lookup"><span data-stu-id="38924-192">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="38924-193">**Uwaga:** Określenie **/output**:myfile.dll nie ustawia opcji **/dll** .</span><span class="sxs-lookup"><span data-stu-id="38924-193">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="38924-194">Jeśli nie określisz **/dll**, wynik będzie plikiem wykonywalnym o nazwie *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="38924-194">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="38924-195">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="38924-195">**/optimize**</span></span>|<span data-ttu-id="38924-196">Optymalizuje długie instrukcje, co powoduje zamianę ich na krótkie.</span><span class="sxs-lookup"><span data-stu-id="38924-196">Optimizes long instructions to short.</span></span> <span data-ttu-id="38924-197">Na przykład, `br` do `br.s` .</span><span class="sxs-lookup"><span data-stu-id="38924-197">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="38924-198">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="38924-198">**/pe64**</span></span>|<span data-ttu-id="38924-199">Tworzy obraz 64-bitowy (PE32+).</span><span class="sxs-lookup"><span data-stu-id="38924-199">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="38924-200">Jeśli żaden procesor docelowy nie zostanie określony, wartość domyślna to `/itanium` .</span><span class="sxs-lookup"><span data-stu-id="38924-200">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="38924-201">**/PDB**</span><span class="sxs-lookup"><span data-stu-id="38924-201">**/pdb**</span></span>|<span data-ttu-id="38924-202">Tworzy plik PDB bez włączania śledzenia informacji o debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="38924-202">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="38924-203">**spowoduje**</span><span class="sxs-lookup"><span data-stu-id="38924-203">**/quiet**</span></span>|<span data-ttu-id="38924-204">Określa tryb cichy; nie zgłasza postępów zestawu.</span><span class="sxs-lookup"><span data-stu-id="38924-204">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="38924-205">**/Resource:**`file.res`</span><span class="sxs-lookup"><span data-stu-id="38924-205">**/resource:** `file.res`</span></span>|<span data-ttu-id="38924-206">Zawiera określony plik zasobów w \* formacie. res w pliku. *exe* lub *. dll* .</span><span class="sxs-lookup"><span data-stu-id="38924-206">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="38924-207">Tylko jeden plik. res można określić przy użyciu opcji **/Resource** .</span><span class="sxs-lookup"><span data-stu-id="38924-207">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="38924-208">**/ssver:** `int` .`int`</span><span class="sxs-lookup"><span data-stu-id="38924-208">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="38924-209">Ustawia numer wersji podsystemu w opcjonalnym nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="38924-209">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="38924-210">Dla **/APPCONTAINER** i **/ARM** minimalny numer wersji to 6,02.</span><span class="sxs-lookup"><span data-stu-id="38924-210">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="38924-211">**/Stack:**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="38924-211">**/stack:** `stackSize`</span></span>|<span data-ttu-id="38924-212">Ustawia wartość SizeOfStackReserve w opcjonalnym nagłówku NT na `stackSize` .</span><span class="sxs-lookup"><span data-stu-id="38924-212">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="38924-213">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="38924-213">**/stripreloc**</span></span>|<span data-ttu-id="38924-214">Określa, że nie są potrzebne relokacje podstawowe.</span><span class="sxs-lookup"><span data-stu-id="38924-214">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="38924-215">**/SUBSYSTEM:**`integer`</span><span class="sxs-lookup"><span data-stu-id="38924-215">**/subsystem:** `integer`</span></span>|<span data-ttu-id="38924-216">Ustawia podsystem na wartość określoną przez `integer` w opcjonalnym nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="38924-216">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="38924-217">Jeśli dyrektywa języka IL .subsystem została określona w pliku, to polecenie zastępuje ją.</span><span class="sxs-lookup"><span data-stu-id="38924-217">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="38924-218">Zobacz Winnt. h, IMAGE_SUBSYSTEM, aby uzyskać listę prawidłowych wartości dla `integer` .</span><span class="sxs-lookup"><span data-stu-id="38924-218">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="38924-219">**/x64**</span><span class="sxs-lookup"><span data-stu-id="38924-219">**/x64**</span></span>|<span data-ttu-id="38924-220">Określa 64-bitowy procesor firmy AMD jako procesor docelowy.</span><span class="sxs-lookup"><span data-stu-id="38924-220">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="38924-221">Jeśli nie określono liczby bitów obrazu, wartość domyślna to **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="38924-221">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="38924-222">**/?**</span><span class="sxs-lookup"><span data-stu-id="38924-222">**/?**</span></span>|<span data-ttu-id="38924-223">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="38924-223">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="38924-224">Wszystkie opcje dla *Ilasm.exe* nie uwzględniają wielkości liter i są rozpoznawane przez pierwsze trzy litery.</span><span class="sxs-lookup"><span data-stu-id="38924-224">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="38924-225">Na przykład **/lis** jest odpowiednikiem **/Listing** i **/res**: myresfile. res jest równoważne **/Resource**: myresfile. res. Opcje określające argumenty akceptują dwukropek (:) lub znaku równości (=) jako separatora między opcją i argumentem.</span><span class="sxs-lookup"><span data-stu-id="38924-225">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="38924-226">Na przykład **/Output**:*plik. ext* jest odpowiednikiem **/Output** = *pliku. ext*.</span><span class="sxs-lookup"><span data-stu-id="38924-226">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="38924-227">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38924-227">Remarks</span></span>

<span data-ttu-id="38924-228">Program IL Assembler umożliwia dostawcom narzędzi projektowanie i implementowanie generatorów języka IL.</span><span class="sxs-lookup"><span data-stu-id="38924-228">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="38924-229">Korzystając z *Ilasm.exe*, deweloperzy narzędzi i kompilatorów mogą skoncentrować się na GENEROWANIU kodu Il i metadanych bez konieczności wydawania plików w formacie PE.</span><span class="sxs-lookup"><span data-stu-id="38924-229">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="38924-230">Podobnie jak w przypadku innych kompilatorów przeznaczonych dla środowiska uruchomieniowego, takich jak C# i Visual Basic, *Ilasm.exe* nie tworzy pośrednich plików obiektów i nie wymaga etapów konsolidacji do utworzenia pliku PE.</span><span class="sxs-lookup"><span data-stu-id="38924-230">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="38924-231">Program IL Assembler może wyrazić wszystkie istniejące metadane i funkcje IL języków programowania, które są przeznaczone dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="38924-231">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="38924-232">Dzięki temu kod zarządzany zapisany w dowolnym z tych języków programowania może być odpowiednio wyrażony w asemblerze IL i kompilowany przy użyciu *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="38924-232">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="38924-233">Kompilacja może się nie powieść, jeśli ostatni wiersz kodu w pliku źródłowym il nie kończy się znakiem odstępu ani znakiem końca wiersza.</span><span class="sxs-lookup"><span data-stu-id="38924-233">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="38924-234">*Ilasm.exe* w połączeniu z narzędziem pomocnika, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="38924-234">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="38924-235">*Ildasm.exe* pobiera plik PE zawierający kod IL i tworzy plik tekstowy odpowiedni jako dane wejściowe do *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="38924-235">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="38924-236">Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="38924-236">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="38924-237">Po skompilowaniu kodu i uruchomieniu danych wyjściowych za pomocą *Ildasm.exe*, wynikowy plik tekstowy Il może być edytowany ręcznie w celu dodania brakujących atrybutów.</span><span class="sxs-lookup"><span data-stu-id="38924-237">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="38924-238">Następnie można uruchomić ten plik tekstowy za pomocą *Ilasm.exe* , aby utworzyć końcowy plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="38924-238">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="38924-239">Tej techniki można również użyć, aby utworzyć pojedynczy plik PE z kilku plików PE, oryginalnie utworzonych przez różne kompilatory.</span><span class="sxs-lookup"><span data-stu-id="38924-239">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="38924-240">Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).</span><span class="sxs-lookup"><span data-stu-id="38924-240">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="38924-241">Aby to połączone użycie *Ildasm.exe* i *Ilasm.exe* jak najszybciej, program asembler nie zastępuje krótkich kodowań dla długich, które mogą zostać naliczone w źródłach Il (lub mogą być emitowane przez inny kompilator).</span><span class="sxs-lookup"><span data-stu-id="38924-241">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="38924-242">Użyj opcji **/Optimize** , aby zastąpić krótkie kodowania, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="38924-242">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="38924-243">*Ildasm.exe* działa tylko na plikach na dysku.</span><span class="sxs-lookup"><span data-stu-id="38924-243">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="38924-244">Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="38924-244">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="38924-245">Aby uzyskać więcej informacji na temat gramatyki IL, zobacz plik asmparse. gramatyki w Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="38924-245">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="38924-246">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="38924-246">Version Information</span></span>

<span data-ttu-id="38924-247">Począwszy od .NET Framework 4,5, można dołączyć atrybut niestandardowy do implementacji interfejsu za pomocą kodu podobnego do poniższego:</span><span class="sxs-lookup"><span data-stu-id="38924-247">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

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

<span data-ttu-id="38924-248">Począwszy od .NET Framework 4,5, można określić dowolny obiekt typu obiekt, który ma być zorganizowany, przy użyciu jego pierwotnej reprezentacji binarnej, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="38924-248">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="38924-249">Aby uzyskać więcej informacji na temat gramatyki IL, zobacz plik asmparse. gramatyki w Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="38924-249">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="38924-250">Przykłady</span><span class="sxs-lookup"><span data-stu-id="38924-250">Examples</span></span>

<span data-ttu-id="38924-251">Następujące polecenie składa plik IL *myTestFile.Il* i tworzy *myTestFile.exe*wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="38924-251">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="38924-252">Następujące polecenie składa plik IL *myTestFile.Il* i tworzy plik *. dll* *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="38924-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="38924-253">Następujące polecenie składa plik IL *myTestFile.Il* i tworzy plik *. dll* *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="38924-253">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="38924-254">Poniższy przykład kodu pokazuje niezwykle prostą aplikację, która wyświetla "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="38924-254">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="38924-255">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="38924-255">to the console.</span></span> <span data-ttu-id="38924-256">Można skompilować ten kod, a następnie użyć narzędzia [*Ildasm.exe*](ildasm-exe-il-disassembler.md) do wygenerowania pliku Il.</span><span class="sxs-lookup"><span data-stu-id="38924-256">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

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

<span data-ttu-id="38924-257">Poniższy przykład kodu w języku IL odpowiada poprzedniemu przykładowi kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="38924-257">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="38924-258">Ten kod można skompilować do zestawu za pomocą narzędzia asemblera IL.</span><span class="sxs-lookup"><span data-stu-id="38924-258">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="38924-259">Przykłady kodu IL i C# są wyświetlane "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="38924-259">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="38924-260">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="38924-260">to the console.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="38924-261">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38924-261">See also</span></span>

- [<span data-ttu-id="38924-262">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="38924-262">Tools</span></span>](index.md)
- [<span data-ttu-id="38924-263">*Ildasm.exe* (Il dezasembler)</span><span class="sxs-lookup"><span data-stu-id="38924-263">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="38924-264">Zarządzany proces wykonywania</span><span class="sxs-lookup"><span data-stu-id="38924-264">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="38924-265">Wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="38924-265">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
