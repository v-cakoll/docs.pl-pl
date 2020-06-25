---
title: Peverify.exe (narzędzie PEVerify)
description: Użyj Peverify.exe (Weryfikuj przenośny plik wykonywalny), aby pomóc w ustaleniu, czy kod języka pośredniego (MSIL) firmy Microsoft & metadane spełniają standardy bezpieczeństwa typów w programie .NET.
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
ms.openlocfilehash: 478c04a45c7f9d3ad568a6bc4a12a89fe786583a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325621"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="94a53-103">Peverify.exe (Narzędzie PEVerify)</span><span class="sxs-lookup"><span data-stu-id="94a53-103">Peverify.exe (PEVerify tool)</span></span>

<span data-ttu-id="94a53-104">Narzędzie PEVerify pomaga deweloperom, którzy generują język pośredni (MSIL) firmy Microsoft (na przykład autorzy kompilatora i deweloperzy aparatów skryptów), aby określić, czy ich kod MSIL i powiązane metadane spełniają wymagania bezpieczeństwa typu.</span><span class="sxs-lookup"><span data-stu-id="94a53-104">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers and script engine developers) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="94a53-105">Niektóre kompilatory generują weryfikowalny kod bezpieczny ze względu na typy tylko wtedy, gdy unika się używania pewnych konstrukcji języka.</span><span class="sxs-lookup"><span data-stu-id="94a53-105">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="94a53-106">Jeśli używasz takiego kompilatora, możesz sprawdzić, czy nie naruszono bezpieczeństwa typu kodu.</span><span class="sxs-lookup"><span data-stu-id="94a53-106">If you're using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="94a53-107">Aby sprawdzić MSIL i metadane, można uruchomić narzędzie PEVerify na plikach.</span><span class="sxs-lookup"><span data-stu-id="94a53-107">You can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="94a53-108">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="94a53-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="94a53-109">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="94a53-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="94a53-110">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="94a53-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>
  
## <a name="syntax"></a><span data-ttu-id="94a53-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="94a53-111">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="94a53-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="94a53-112">Parameters</span></span>  
  
|<span data-ttu-id="94a53-113">Argument</span><span class="sxs-lookup"><span data-stu-id="94a53-113">Argument</span></span>|<span data-ttu-id="94a53-114">Opis</span><span class="sxs-lookup"><span data-stu-id="94a53-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="94a53-115">*Nazwa pliku*</span><span class="sxs-lookup"><span data-stu-id="94a53-115">*filename*</span></span>|<span data-ttu-id="94a53-116">Przenośny plik wykonywalny (PE), który ma zostać sprawdzony pod kątem języka MSIL i metadanych.</span><span class="sxs-lookup"><span data-stu-id="94a53-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="94a53-117">Opcja</span><span class="sxs-lookup"><span data-stu-id="94a53-117">Option</span></span>|<span data-ttu-id="94a53-118">Opis</span><span class="sxs-lookup"><span data-stu-id="94a53-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="94a53-119">**/Break =** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="94a53-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="94a53-120">Przerywa weryfikację po błędach *maxErrorCount* .</span><span class="sxs-lookup"><span data-stu-id="94a53-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="94a53-121">Ten parametr nie jest obsługiwany w .NET Framework w wersji 2.0 lub wyższej.</span><span class="sxs-lookup"><span data-stu-id="94a53-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="94a53-122">**/clock**</span><span class="sxs-lookup"><span data-stu-id="94a53-122">**/clock**</span></span>|<span data-ttu-id="94a53-123">Mierzy i raportuje następujące czasy weryfikacji w milisekundach:</span><span class="sxs-lookup"><span data-stu-id="94a53-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="94a53-124">**MD Val. cykl**</span><span class="sxs-lookup"><span data-stu-id="94a53-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="94a53-125">Cykl sprawdzania poprawności metadanych</span><span class="sxs-lookup"><span data-stu-id="94a53-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="94a53-126">**MD Val. Pure**</span><span class="sxs-lookup"><span data-stu-id="94a53-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="94a53-127">Czysty czas sprawdzania poprawności metadanych</span><span class="sxs-lookup"><span data-stu-id="94a53-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="94a53-128">**IL Ver. Cycle**</span><span class="sxs-lookup"><span data-stu-id="94a53-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="94a53-129">Cykli weryfikacji języka pośredniego firmy Microsoft (MSIL)</span><span class="sxs-lookup"><span data-stu-id="94a53-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="94a53-130">**Kod IL Ver**</span><span class="sxs-lookup"><span data-stu-id="94a53-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="94a53-131">Czysty czas weryfikacji języka MSIL</span><span class="sxs-lookup"><span data-stu-id="94a53-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="94a53-132">Czasy **MD Val. Cycle** i **Il Ver. Cycle** obejmują czas wymagany do wykonania niezbędnych procedur uruchamiania i zamykania.</span><span class="sxs-lookup"><span data-stu-id="94a53-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="94a53-133">Wartość **MD Val. Pure** i **Il Ver czyste** czasy są odzwierciedlać czas wymagany do przeprowadzenia walidacji lub weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="94a53-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="94a53-134">**/Help**</span><span class="sxs-lookup"><span data-stu-id="94a53-134">**/help**</span></span>|<span data-ttu-id="94a53-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="94a53-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="94a53-136">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="94a53-136">**/hresult**</span></span>|<span data-ttu-id="94a53-137">Wyświetla kody błędów w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="94a53-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="94a53-138">**/Ignore =** *szesnastkowy. kod* [, *szesnastkowy. Code*]</span><span class="sxs-lookup"><span data-stu-id="94a53-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="94a53-139">Ignoruje wymienione kody błędów.</span><span class="sxs-lookup"><span data-stu-id="94a53-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="94a53-140">**/Ignore = @** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="94a53-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="94a53-141">Ignoruje kody błędów wymienione w określonym pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="94a53-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="94a53-142">**/Il**</span><span class="sxs-lookup"><span data-stu-id="94a53-142">**/il**</span></span>|<span data-ttu-id="94a53-143">Wykonuje weryfikację bezpieczeństwa typu MSIL dla metod zaimplementowanych w zestawie określonym przez *filename*.</span><span class="sxs-lookup"><span data-stu-id="94a53-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="94a53-144">Narzędzie zwraca szczegółowe opisy dla każdego wykrytego problemu, chyba że zostanie określona opcja **/quiet** .</span><span class="sxs-lookup"><span data-stu-id="94a53-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="94a53-145">**/MD**</span><span class="sxs-lookup"><span data-stu-id="94a53-145">**/md**</span></span>|<span data-ttu-id="94a53-146">Wykonuje sprawdzanie poprawności metadanych na zestawie określonym przez *filename*.</span><span class="sxs-lookup"><span data-stu-id="94a53-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="94a53-147">Ta opcja przeprowadzi pełną strukturę metadanych w pliku i zgłosi wszystkie problemy z walidacją.</span><span class="sxs-lookup"><span data-stu-id="94a53-147">This option walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="94a53-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="94a53-148">**/nologo**</span></span>|<span data-ttu-id="94a53-149">Pomija wyświetlanie informacji o wersji i prawach autorskich produktu.</span><span class="sxs-lookup"><span data-stu-id="94a53-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="94a53-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="94a53-150">**/nosymbols**</span></span>|<span data-ttu-id="94a53-151">W wersji 2.0 .NET Framework wyłącza numery wierszy w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="94a53-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="94a53-152">**spowoduje**</span><span class="sxs-lookup"><span data-stu-id="94a53-152">**/quiet**</span></span>|<span data-ttu-id="94a53-153">Określa tryb cichy. Wyłącza raportowanie problemów weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="94a53-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="94a53-154">Peverify.exe w dalszym ciągu raportuje, czy plik jest bezpiecznych pod względem typów, ale nie raportuje problemów uniemożliwiających weryfikację bezpieczeństwa typów.</span><span class="sxs-lookup"><span data-stu-id="94a53-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="94a53-155">Weryfikuje tylko metody przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="94a53-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="94a53-156">**/Unique**</span><span class="sxs-lookup"><span data-stu-id="94a53-156">**/unique**</span></span>|<span data-ttu-id="94a53-157">Ignoruje powtarzające się kody błędów.</span><span class="sxs-lookup"><span data-stu-id="94a53-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="94a53-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="94a53-158">**/verbose**</span></span>|<span data-ttu-id="94a53-159">W .NET Framework w wersji 2.0 wyświetla dodatkowe informacje w komunikatach weryfikacji MSIL.</span><span class="sxs-lookup"><span data-stu-id="94a53-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="94a53-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="94a53-160">**/?**</span></span>|<span data-ttu-id="94a53-161">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="94a53-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94a53-162">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94a53-162">Remarks</span></span>  
 <span data-ttu-id="94a53-163">Środowisko uruchomieniowe języka wspólnego opiera się na wykonywaniu kodu aplikacji bezpiecznego pod kątem typów, aby ułatwić wymuszanie stosowania mechanizmów zabezpieczeń i izolacji.</span><span class="sxs-lookup"><span data-stu-id="94a53-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="94a53-164">Zwykle kod, który nie jest [typu](../../standard/security/key-security-concepts.md#type-safety-and-security) "nie sprawdza się", nie może zostać uruchomiony, chociaż można ustawić zasady zabezpieczeń, aby zezwalać na wykonywanie kodu zaufanego, ale niemożliwego do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="94a53-164">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="94a53-165">Jeśli nie określono opcji **/MD** ani **/Il** , Peverify.exe wykonuje oba typy kontroli.</span><span class="sxs-lookup"><span data-stu-id="94a53-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="94a53-166">Peverify.exe wykonuje najpierw testy **/MD** .</span><span class="sxs-lookup"><span data-stu-id="94a53-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="94a53-167">W przypadku braku błędów **/Il** są przeprowadzane sprawdzenia.</span><span class="sxs-lookup"><span data-stu-id="94a53-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="94a53-168">W przypadku określenia zarówno **/MD** , jak i **/Il**testy **/Il** są wykonywane nawet wtedy, gdy w metadanych występują błędy.</span><span class="sxs-lookup"><span data-stu-id="94a53-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="94a53-169">W takim przypadku, jeśli nie występują błędy metadanych, **PEVerify** *filename* jest równoważne **PEVerify** *filename* **/MD** **/Il**.</span><span class="sxs-lookup"><span data-stu-id="94a53-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="94a53-170">Peverify.exe wykonuje kompleksową weryfikację MSIL na podstawie analizy przepływu danych oraz listy kilkuset reguł poprawności metadanych.</span><span class="sxs-lookup"><span data-stu-id="94a53-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="94a53-171">Aby uzyskać szczegółowe informacje na temat sprawdzanych Peverify.exe, zobacz "Specyfikacja walidacji metadanych" i "Specyfikacja zestawu instrukcji MSIL" w folderze przewodnika deweloperów narzędzi w Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="94a53-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
<span data-ttu-id="94a53-172">.NET Framework w wersji 2,0 lub nowszej obsługuje sprawdzone `byref` zwroty określone przy użyciu następujących instrukcji MSIL: `dup` ,,,, `ldsflda` `ldflda` `ldelema` `call` i `unbox` .</span><span class="sxs-lookup"><span data-stu-id="94a53-172">.NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call`, and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="94a53-173">Przykłady</span><span class="sxs-lookup"><span data-stu-id="94a53-173">Examples</span></span>  
 <span data-ttu-id="94a53-174">Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="94a53-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="94a53-175">Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.</span><span class="sxs-lookup"><span data-stu-id="94a53-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="94a53-176">Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="94a53-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="94a53-177">Narzędzie wyświetla czas potrzebny do wykonywania tych sprawdzeń.</span><span class="sxs-lookup"><span data-stu-id="94a53-177">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="94a53-178">Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.</span><span class="sxs-lookup"><span data-stu-id="94a53-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="94a53-179">Następujące polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="94a53-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="94a53-180">Peverify.exe zatrzymuje się jednak, gdy liczba błędów przekroczy 100.</span><span class="sxs-lookup"><span data-stu-id="94a53-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="94a53-181">Narzędzie ignoruje także wymienione kody błędów.</span><span class="sxs-lookup"><span data-stu-id="94a53-181">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="94a53-182">Poniższe polecenie daje ten sam wynik jak powyżej poprzedniego przykładu, ale określa kody błędów do zignorowania w pliku odpowiedzi `ignoreErrors.rsp` .</span><span class="sxs-lookup"><span data-stu-id="94a53-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="94a53-183">Plik odpowiedzi może zawierać rozdzielaną przecinkami listę kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="94a53-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="94a53-184">Można też sformatować plik odpowiedzi, podając każdy kod błędu w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="94a53-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="94a53-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94a53-185">See also</span></span>

- [<span data-ttu-id="94a53-186">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="94a53-186">Tools</span></span>](index.md)
- [<span data-ttu-id="94a53-187">Pisanie kodu z bezpiecznym typem</span><span class="sxs-lookup"><span data-stu-id="94a53-187">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="94a53-188">Bezpieczeństwo i zabezpieczenia typów</span><span class="sxs-lookup"><span data-stu-id="94a53-188">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="94a53-189">Wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="94a53-189">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
