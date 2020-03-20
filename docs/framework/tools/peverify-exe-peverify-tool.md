---
title: Peverify.exe (narzędzie PEVerify)
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
ms.openlocfilehash: 9d5f8c80937c36e975d42d6efb0a83295cb28be9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104980"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="34502-102">Peverify.exe (narzędzie PEVerify)</span><span class="sxs-lookup"><span data-stu-id="34502-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="34502-103">Narzędzie PEVerify pomaga deweloperom, którzy generują język Microsoft intermediate language (MSIL) (na przykład twórcom kompilatorów, deweloperom aparatów skryptów itd.), w ustalaniu, czy ich kod MSIL i związane z nim metadane spełniają wymogi bezpieczeństwa typu.</span><span class="sxs-lookup"><span data-stu-id="34502-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="34502-104">Niektóre kompilatory generują weryfikowalny kod bezpieczny ze względu na typy tylko wtedy, gdy unika się używania pewnych konstrukcji języka.</span><span class="sxs-lookup"><span data-stu-id="34502-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="34502-105">Jeśli jako programista używasz takiego kompilatora, możesz chcieć sprawdzić, czy nie występują zagrożenia bezpieczeństwa typów kodu.</span><span class="sxs-lookup"><span data-stu-id="34502-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="34502-106">W tej sytuacji możesz uruchomić narzędzie PEVerify, aby sprawdzić MSIL i metadane plików.</span><span class="sxs-lookup"><span data-stu-id="34502-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="34502-107">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34502-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="34502-108">Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="34502-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="34502-109">Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="34502-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="34502-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="34502-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34502-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="34502-111">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="34502-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="34502-112">Parameters</span></span>  
  
|<span data-ttu-id="34502-113">Argument</span><span class="sxs-lookup"><span data-stu-id="34502-113">Argument</span></span>|<span data-ttu-id="34502-114">Opis</span><span class="sxs-lookup"><span data-stu-id="34502-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="34502-115">*Pod nazwą*</span><span class="sxs-lookup"><span data-stu-id="34502-115">*filename*</span></span>|<span data-ttu-id="34502-116">Przenośny plik wykonywalny (PE), który ma zostać sprawdzony pod kątem języka MSIL i metadanych.</span><span class="sxs-lookup"><span data-stu-id="34502-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="34502-117">Opcja</span><span class="sxs-lookup"><span data-stu-id="34502-117">Option</span></span>|<span data-ttu-id="34502-118">Opis</span><span class="sxs-lookup"><span data-stu-id="34502-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="34502-119">**/break=** *maksymalna liczba*</span><span class="sxs-lookup"><span data-stu-id="34502-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="34502-120">Przerywa weryfikację po błędach *maxErrorCount.*</span><span class="sxs-lookup"><span data-stu-id="34502-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="34502-121">Ten parametr nie jest obsługiwany w .NET Framework w wersji 2.0 lub wyższej.</span><span class="sxs-lookup"><span data-stu-id="34502-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="34502-122">**/zegar**</span><span class="sxs-lookup"><span data-stu-id="34502-122">**/clock**</span></span>|<span data-ttu-id="34502-123">Mierzy i raportuje następujące czasy weryfikacji w milisekundach:</span><span class="sxs-lookup"><span data-stu-id="34502-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="34502-124">**Cykl MD Val.**</span><span class="sxs-lookup"><span data-stu-id="34502-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="34502-125">Cykl sprawdzania poprawności metadanych</span><span class="sxs-lookup"><span data-stu-id="34502-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="34502-126">**MD Val. czysty**</span><span class="sxs-lookup"><span data-stu-id="34502-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="34502-127">Czysty czas sprawdzania poprawności metadanych</span><span class="sxs-lookup"><span data-stu-id="34502-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="34502-128">**Cykl IL Ver.**</span><span class="sxs-lookup"><span data-stu-id="34502-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="34502-129">Cykli weryfikacji języka pośredniego firmy Microsoft (MSIL)</span><span class="sxs-lookup"><span data-stu-id="34502-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="34502-130">**IL Ver czysty**</span><span class="sxs-lookup"><span data-stu-id="34502-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="34502-131">Czysty czas weryfikacji języka MSIL</span><span class="sxs-lookup"><span data-stu-id="34502-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="34502-132">Cykl **MD Val.** i **czasy cyklu IL Ver.** obejmują czas wymagany do wykonania niezbędnych procedur uruchamiania i zamykania.</span><span class="sxs-lookup"><span data-stu-id="34502-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="34502-133">**Md Val. pure** i **IL Ver czyste** razy odzwierciedlają czas wymagany do przeprowadzenia walidacji lub weryfikacji tylko.</span><span class="sxs-lookup"><span data-stu-id="34502-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="34502-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="34502-134">**/help**</span></span>|<span data-ttu-id="34502-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="34502-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="34502-136">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="34502-136">**/hresult**</span></span>|<span data-ttu-id="34502-137">Wyświetla kody błędów w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="34502-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="34502-138">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="34502-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="34502-139">Ignoruje wymienione kody błędów.</span><span class="sxs-lookup"><span data-stu-id="34502-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="34502-140">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="34502-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="34502-141">Ignoruje kody błędów wymienione w określonym pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="34502-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="34502-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="34502-142">**/il**</span></span>|<span data-ttu-id="34502-143">Przeprowadza kontrole weryfikacji bezpieczeństwa typu MSIL dla metod zaimplementowanych w zestawie określonym przez *nazwę pliku*.</span><span class="sxs-lookup"><span data-stu-id="34502-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="34502-144">Narzędzie zwraca szczegółowe opisy dla każdego znalezionego problemu, chyba że zostanie określona opcja **/quiet.**</span><span class="sxs-lookup"><span data-stu-id="34502-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="34502-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="34502-145">**/md**</span></span>|<span data-ttu-id="34502-146">Wykonuje sprawdzanie poprawności metadanych w zestawie określonym przez *nazwę pliku*.</span><span class="sxs-lookup"><span data-stu-id="34502-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="34502-147">Oznacza to przejrzenie pełnej struktury metadanych w pliku i raportowanie wszystkich napotkanych problemów.</span><span class="sxs-lookup"><span data-stu-id="34502-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="34502-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="34502-148">**/nologo**</span></span>|<span data-ttu-id="34502-149">Pomija wyświetlanie informacji o wersji i prawach autorskich produktu.</span><span class="sxs-lookup"><span data-stu-id="34502-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="34502-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="34502-150">**/nosymbols**</span></span>|<span data-ttu-id="34502-151">W wersji 2.0 .NET Framework wyłącza numery wierszy w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="34502-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="34502-152">**/cichy**</span><span class="sxs-lookup"><span data-stu-id="34502-152">**/quiet**</span></span>|<span data-ttu-id="34502-153">Określa tryb cichy. Wyłącza raportowanie problemów weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="34502-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="34502-154">Peverify.exe w dalszym ciągu raportuje, czy plik jest bezpiecznych pod względem typów, ale nie raportuje problemów uniemożliwiających weryfikację bezpieczeństwa typów.</span><span class="sxs-lookup"><span data-stu-id="34502-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="34502-155">Weryfikuje tylko metody przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="34502-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="34502-156">**/unique**</span><span class="sxs-lookup"><span data-stu-id="34502-156">**/unique**</span></span>|<span data-ttu-id="34502-157">Ignoruje powtarzające się kody błędów.</span><span class="sxs-lookup"><span data-stu-id="34502-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="34502-158">**/pełne**</span><span class="sxs-lookup"><span data-stu-id="34502-158">**/verbose**</span></span>|<span data-ttu-id="34502-159">W .NET Framework w wersji 2.0 wyświetla dodatkowe informacje w komunikatach weryfikacji MSIL.</span><span class="sxs-lookup"><span data-stu-id="34502-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="34502-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="34502-160">**/?**</span></span>|<span data-ttu-id="34502-161">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="34502-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34502-162">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34502-162">Remarks</span></span>  
 <span data-ttu-id="34502-163">Środowisko uruchomieniowe języka wspólnego opiera się na wykonywaniu kodu aplikacji bezpiecznego pod kątem typów, aby ułatwić wymuszanie stosowania mechanizmów zabezpieczeń i izolacji.</span><span class="sxs-lookup"><span data-stu-id="34502-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="34502-164">Zwykle nie można uruchomić kodu, który nie jest [sprawdzalny typ safe,](../../standard/security/key-security-concepts.md#type-safety-and-security) chociaż można ustawić zasady zabezpieczeń, aby umożliwić wykonanie kodu zaufanego, ale niemożliwego do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="34502-164">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="34502-165">Jeśli nie określono opcji **/md** ani **/il,** program Peverify.exe wykonuje oba typy kontroli.</span><span class="sxs-lookup"><span data-stu-id="34502-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="34502-166">Peverify.exe najpierw wykonuje **/md** sprawdza.</span><span class="sxs-lookup"><span data-stu-id="34502-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="34502-167">Jeśli nie ma żadnych błędów, **/il** sprawdza są dokonywane.</span><span class="sxs-lookup"><span data-stu-id="34502-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="34502-168">Jeśli określisz zarówno **/md,** jak i **/il**, **/il** kontrole są dokonywane, nawet jeśli w metadanych występują błędy.</span><span class="sxs-lookup"><span data-stu-id="34502-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="34502-169">W związku z tym, jeśli nie ma żadnych błędów metadanych, nazwa *pliku* **peverify** jest odpowiednikiem nazwy *pliku* **peverify** **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="34502-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="34502-170">Peverify.exe wykonuje kompleksową weryfikację MSIL na podstawie analizy przepływu danych oraz listy kilkuset reguł poprawności metadanych.</span><span class="sxs-lookup"><span data-stu-id="34502-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="34502-171">Aby uzyskać szczegółowe informacje na temat kontroli wykonywanej przez program Peverify.exe, zobacz "Specyfikacja sprawdzania poprawności metadanych" i "Specyfikacja zestawu instrukcji MSIL" w folderze Przewodnik dla deweloperów narzędzi w zestawie Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="34502-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
 <span data-ttu-id="34502-172">Należy zauważyć, że program .NET Framework w wersji `byref` 2.0 lub nowszej obsługuje weryfikowalne zwroty określone przy `dup`użyciu następujących instrukcji MSIL: , `ldsflda`, `ldflda` `ldelema`, `call` i `unbox`.</span><span class="sxs-lookup"><span data-stu-id="34502-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="34502-173">Przykłady</span><span class="sxs-lookup"><span data-stu-id="34502-173">Examples</span></span>  
 <span data-ttu-id="34502-174">Następujące polecenie wykonuje sprawdzanie poprawności metadanych i sprawdzanie bezpieczeństwa typu `myAssembly.exe`MSIL dla metod zaimplementowanych w zestawie .</span><span class="sxs-lookup"><span data-stu-id="34502-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="34502-175">Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.</span><span class="sxs-lookup"><span data-stu-id="34502-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="34502-176">Następujące polecenie wykonuje sprawdzanie poprawności metadanych i sprawdzanie bezpieczeństwa typu `myAssembly.exe`MSIL dla metod zaimplementowanych w zestawie .</span><span class="sxs-lookup"><span data-stu-id="34502-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="34502-177">Narzędzie wyświetla czas potrzebny do wykonywania tych sprawdzeń.</span><span class="sxs-lookup"><span data-stu-id="34502-177">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="34502-178">Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.</span><span class="sxs-lookup"><span data-stu-id="34502-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="34502-179">Następujące polecenie wykonuje sprawdzanie poprawności metadanych i sprawdzanie bezpieczeństwa typu `myAssembly.exe`MSIL dla metod zaimplementowanych w zestawie .</span><span class="sxs-lookup"><span data-stu-id="34502-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="34502-180">Peverify.exe zatrzymuje się jednak, gdy liczba błędów przekroczy 100.</span><span class="sxs-lookup"><span data-stu-id="34502-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="34502-181">Narzędzie ignoruje także wymienione kody błędów.</span><span class="sxs-lookup"><span data-stu-id="34502-181">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="34502-182">Następujące polecenie daje taki sam wynik jak w powyższym poprzednim przykładzie, ale `ignoreErrors.rsp`określa kody błędów do zignorowania w pliku odpowiedzi .</span><span class="sxs-lookup"><span data-stu-id="34502-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="34502-183">Plik odpowiedzi może zawierać rozdzielaną przecinkami listę kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="34502-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="34502-184">Można też sformatować plik odpowiedzi, podając każdy kod błędu w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="34502-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="34502-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34502-185">See also</span></span>

- [<span data-ttu-id="34502-186">narzędzia</span><span class="sxs-lookup"><span data-stu-id="34502-186">Tools</span></span>](index.md)
- [<span data-ttu-id="34502-187">Pisanie sprawdzalnie kod bezpieczny dla typu</span><span class="sxs-lookup"><span data-stu-id="34502-187">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="34502-188">Bezpieczeństwo i ochrona typu</span><span class="sxs-lookup"><span data-stu-id="34502-188">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="34502-189">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="34502-189">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
