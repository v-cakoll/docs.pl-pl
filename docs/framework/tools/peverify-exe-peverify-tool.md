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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0423946ab32c04274bb3d5656ed8603ec4314d88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61919714"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="ab7fe-102">Peverify.exe (narzędzie PEVerify)</span><span class="sxs-lookup"><span data-stu-id="ab7fe-102">Peverify.exe (PEVerify Tool)</span></span>
<span data-ttu-id="ab7fe-103">Narzędzie PEVerify pomaga deweloperom, którzy generują język Microsoft intermediate language (MSIL) (na przykład twórcom kompilatorów, deweloperom aparatów skryptów itd.), w ustalaniu, czy ich kod MSIL i związane z nim metadane spełniają wymogi bezpieczeństwa typu.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-103">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers, script engine developers, and so on) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="ab7fe-104">Niektóre kompilatory generują weryfikowalny kod bezpieczny ze względu na typy tylko wtedy, gdy unika się używania pewnych konstrukcji języka.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-104">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="ab7fe-105">Jeśli jako programista używasz takiego kompilatora, możesz chcieć sprawdzić, czy nie występują zagrożenia bezpieczeństwa typów kodu.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-105">If, as a developer, you are using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="ab7fe-106">W tej sytuacji możesz uruchomić narzędzie PEVerify, aby sprawdzić MSIL i metadane plików.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-106">In this situation, you can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="ab7fe-107">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="ab7fe-108">Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7).</span><span class="sxs-lookup"><span data-stu-id="ab7fe-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="ab7fe-109">Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ab7fe-109">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="ab7fe-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ab7fe-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab7fe-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab7fe-111">Syntax</span></span>  
  
```  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab7fe-112">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab7fe-112">Parameters</span></span>  
  
|<span data-ttu-id="ab7fe-113">Argument</span><span class="sxs-lookup"><span data-stu-id="ab7fe-113">Argument</span></span>|<span data-ttu-id="ab7fe-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ab7fe-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ab7fe-115">*Nazwa pliku*</span><span class="sxs-lookup"><span data-stu-id="ab7fe-115">*filename*</span></span>|<span data-ttu-id="ab7fe-116">Przenośny plik wykonywalny (PE), który ma zostać sprawdzony pod kątem języka MSIL i metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-116">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="ab7fe-117">Opcja</span><span class="sxs-lookup"><span data-stu-id="ab7fe-117">Option</span></span>|<span data-ttu-id="ab7fe-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ab7fe-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ab7fe-119">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="ab7fe-119">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="ab7fe-120">Przerywa weryfikację po *maxErrorCount* błędy.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-120">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="ab7fe-121">Ten parametr nie jest obsługiwany w .NET Framework w wersji 2.0 lub wyższej.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-121">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="ab7fe-122">**/Clock**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-122">**/clock**</span></span>|<span data-ttu-id="ab7fe-123">Mierzy i raportuje następujące czasy weryfikacji w milisekundach:</span><span class="sxs-lookup"><span data-stu-id="ab7fe-123">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="ab7fe-124">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-124">**MD Val. cycle**</span></span><br /> <span data-ttu-id="ab7fe-125">Cykl sprawdzania poprawności metadanych</span><span class="sxs-lookup"><span data-stu-id="ab7fe-125">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="ab7fe-126">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-126">**MD Val. pure**</span></span><br /> <span data-ttu-id="ab7fe-127">Czysty czas sprawdzania poprawności metadanych</span><span class="sxs-lookup"><span data-stu-id="ab7fe-127">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="ab7fe-128">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-128">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="ab7fe-129">Cykli weryfikacji języka pośredniego firmy Microsoft (MSIL)</span><span class="sxs-lookup"><span data-stu-id="ab7fe-129">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="ab7fe-130">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-130">**IL Ver pure**</span></span><br /> <span data-ttu-id="ab7fe-131">Czysty czas weryfikacji języka MSIL</span><span class="sxs-lookup"><span data-stu-id="ab7fe-131">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="ab7fe-132">**; MD Val. cycle** i **IL Ver. cycle** razy obejmują czas wymagany do wykonania niezbędnych procedur uruchamiania i zamykania.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-132">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="ab7fe-133">**MD Val. pure** i **IL Ver pure** razy odzwierciedlają czas wymagany do wykonania tylko sprawdzenia poprawności lub tylko weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-133">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="ab7fe-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-134">**/help**</span></span>|<span data-ttu-id="ab7fe-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="ab7fe-136">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-136">**/hresult**</span></span>|<span data-ttu-id="ab7fe-137">Wyświetla kody błędów w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-137">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="ab7fe-138">**/ ignore =** *gt;Hex.Code* [, *gt;Hex.Code*]</span><span class="sxs-lookup"><span data-stu-id="ab7fe-138">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="ab7fe-139">Ignoruje wymienione kody błędów.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-139">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="ab7fe-140">**/ ignore = @** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="ab7fe-140">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="ab7fe-141">Ignoruje kody błędów wymienione w określonym pliku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-141">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="ab7fe-142">**/il**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-142">**/il**</span></span>|<span data-ttu-id="ab7fe-143">Przeprowadza weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie określonym przez *filename*.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-143">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="ab7fe-144">Narzędzie zwraca szczegółowe opisy dla każdego znalezionego, chyba że określisz problemu **/quiet** opcji.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-144">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="ab7fe-145">**/md**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-145">**/md**</span></span>|<span data-ttu-id="ab7fe-146">Wykonuje sprawdzanie poprawności metadanych w zestawie określonym przez *filename*.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-146">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="ab7fe-147">Oznacza to przejrzenie pełnej struktury metadanych w pliku i raportowanie wszystkich napotkanych problemów.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-147">This walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="ab7fe-148">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-148">**/nologo**</span></span>|<span data-ttu-id="ab7fe-149">Pomija wyświetlanie informacji o wersji i prawach autorskich produktu.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-149">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="ab7fe-150">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-150">**/nosymbols**</span></span>|<span data-ttu-id="ab7fe-151">W wersji 2.0 .NET Framework wyłącza numery wierszy w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-151">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="ab7fe-152">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-152">**/quiet**</span></span>|<span data-ttu-id="ab7fe-153">Określa tryb cichy. Wyłącza raportowanie problemów weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-153">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="ab7fe-154">Peverify.exe w dalszym ciągu raportuje, czy plik jest bezpiecznych pod względem typów, ale nie raportuje problemów uniemożliwiających weryfikację bezpieczeństwa typów.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-154">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="ab7fe-155">Weryfikuje tylko metody przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-155">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="ab7fe-156">**/unique**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-156">**/unique**</span></span>|<span data-ttu-id="ab7fe-157">Ignoruje powtarzające się kody błędów.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-157">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="ab7fe-158">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-158">**/verbose**</span></span>|<span data-ttu-id="ab7fe-159">W .NET Framework w wersji 2.0 wyświetla dodatkowe informacje w komunikatach weryfikacji MSIL.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-159">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="ab7fe-160">**/?**</span><span class="sxs-lookup"><span data-stu-id="ab7fe-160">**/?**</span></span>|<span data-ttu-id="ab7fe-161">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-161">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab7fe-162">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab7fe-162">Remarks</span></span>  
 <span data-ttu-id="ab7fe-163">Środowisko uruchomieniowe języka wspólnego opiera się na wykonywaniu kodu aplikacji bezpiecznego pod kątem typów, aby ułatwić wymuszanie stosowania mechanizmów zabezpieczeń i izolacji.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-163">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="ab7fe-164">Normalnie, kodu, który nie jest [sprawdzalnie bezpieczny](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) nie można uruchomić, chociaż można ustawić zasady zabezpieczeń umożliwiające wykonanie kodu zaufanego, choć nieweryfikowalnego.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-164">Normally, code that is not [verifiably type safe](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="ab7fe-165">Jeśli żadna **/MD** ani **/il** opcje są określone, Peverify.exe wykonuje oba rodzaje sprawdzenia.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-165">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="ab7fe-166">Peverify.exe wykonuje **/MD** najpierw sprawdza.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-166">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="ab7fe-167">Jeśli nie ma żadnych błędów **/il** kontrole są wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-167">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="ab7fe-168">Jeśli określisz zarówno **/MD** i **/il**, **/il** kontrole są wprowadzane, nawet jeśli występują błędy w metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-168">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="ab7fe-169">Dlatego, jeśli nie ma żadnych błędów metadanych **peverify** *filename* jest odpowiednikiem **peverify** *filename*   **/MD** **/il**.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-169">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="ab7fe-170">Peverify.exe wykonuje kompleksową weryfikację MSIL na podstawie analizy przepływu danych oraz listy kilkuset reguł poprawności metadanych.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-170">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="ab7fe-171">Aby uzyskać szczegółowe informacje dotyczące kontroli Peverify.exe wykonuje, zobacz "Specyfikacja sprawdzania poprawności metadanych" i "Specyfikacja zestawu instrukcji MSIL" w folderze Tools Developers Guide [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab7fe-171">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="ab7fe-172">Należy pamiętać, że .NET Framework w wersji 2.0 lub nowszej obsługuje weryfikowalne `byref` zwraca określony przy użyciu następujących instrukcji MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` i `unbox`.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-172">Note that the .NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ab7fe-173">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ab7fe-173">Examples</span></span>  
 <span data-ttu-id="ab7fe-174">Poniższe polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-174">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="ab7fe-175">Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-175">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="ab7fe-176">Poniższe polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-176">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="ab7fe-177">Narzędzie wyświetla czas potrzebny do wykonywania tych sprawdzeń.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-177">The tool displays the time required to perform these checks.</span></span>  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="ab7fe-178">Po pomyślnym zrealizowaniu powyższego żądania Peverify.exe wyświetla następujący komunikat.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-178">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="ab7fe-179">Poniższe polecenie wykonuje sprawdzanie poprawności metadanych i weryfikację bezpieczeństwa typów MSIL dla metod zaimplementowanych w zestawie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-179">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="ab7fe-180">Peverify.exe zatrzymuje się jednak, gdy liczba błędów przekroczy 100.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-180">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="ab7fe-181">Narzędzie ignoruje także wymienione kody błędów.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-181">The tool also ignores the specified error codes.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="ab7fe-182">Następujące polecenie daje ten sam wynik, jak w poprzednim przykładzie powyżej, ale Określa kody błędów do zignorowania w pliku odpowiedzi `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-182">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="ab7fe-183">Plik odpowiedzi może zawierać rozdzielaną przecinkami listę kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-183">The response file can contain a comma-separated list of error codes.</span></span>  
  
```  
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="ab7fe-184">Można też sformatować plik odpowiedzi, podając każdy kod błędu w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="ab7fe-184">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab7fe-185">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab7fe-185">See also</span></span>

- [<span data-ttu-id="ab7fe-186">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="ab7fe-186">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="ab7fe-187">Sprawdzalnie bezpieczny kod</span><span class="sxs-lookup"><span data-stu-id="ab7fe-187">Writing Verifiably Type-Safe Code</span></span>](../../../docs/framework/misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="ab7fe-188">Zabezpieczenia i ochrona typu</span><span class="sxs-lookup"><span data-stu-id="ab7fe-188">Type Safety and Security</span></span>](../../../docs/standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="ab7fe-189">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="ab7fe-189">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
