---
title: CorFlags.exe (Narzędzie konwersji CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b420fb451bf1bb2078a4419a648a1407c39ad178
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044738"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="95a68-102">CorFlags.exe (Narzędzie konwersji CorFlags)</span><span class="sxs-lookup"><span data-stu-id="95a68-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="95a68-103">Narzędzie do konwersji CorFlags pozwala na konfigurowanie sekcji CorFlags w nagłówku przenośnego obrazu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="95a68-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="95a68-104">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="95a68-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="95a68-105">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="95a68-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="95a68-106">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="95a68-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="95a68-107">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="95a68-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a68-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="95a68-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="95a68-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="95a68-109">Parameters</span></span>  
  
|<span data-ttu-id="95a68-110">Wymagany parametr</span><span class="sxs-lookup"><span data-stu-id="95a68-110">Required parameter</span></span>|<span data-ttu-id="95a68-111">Opis</span><span class="sxs-lookup"><span data-stu-id="95a68-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="95a68-112">Nazwa zestawu, dla którego chcesz skonfigurować CorFlags.</span><span class="sxs-lookup"><span data-stu-id="95a68-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="95a68-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="95a68-113">Option</span></span>|<span data-ttu-id="95a68-114">Opis</span><span class="sxs-lookup"><span data-stu-id="95a68-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="95a68-115">**/32BIT[REQ]+**</span><span class="sxs-lookup"><span data-stu-id="95a68-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="95a68-116">Ustawia flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="95a68-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="95a68-117">**/32BIT[REQ]-**</span><span class="sxs-lookup"><span data-stu-id="95a68-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="95a68-118">Czyści flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="95a68-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="95a68-119">**/32BITPREF +**</span><span class="sxs-lookup"><span data-stu-id="95a68-119">**/32BITPREF+**</span></span>|<span data-ttu-id="95a68-120">Ustawia flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="95a68-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="95a68-121">Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="95a68-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="95a68-122">Należy ustawić tą flagę tylko dla plików EXE.</span><span class="sxs-lookup"><span data-stu-id="95a68-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="95a68-123">Jeśli flaga jest ustawiona dla biblioteki DLL, nie można załadować biblioteki DLL w procesach 64-bitowych i <xref:System.BadImageFormatException> zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="95a68-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="95a68-124">Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.</span><span class="sxs-lookup"><span data-stu-id="95a68-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="95a68-125">Nowość w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="95a68-125">New in the .NET Framework 4.5.</span></span>|  
|<span data-ttu-id="95a68-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="95a68-126">**/32BITPREF-**</span></span>|<span data-ttu-id="95a68-127">Czyści flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="95a68-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="95a68-128">Nowość w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="95a68-128">New in the .NET Framework 4.5.</span></span>|  
|<span data-ttu-id="95a68-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="95a68-129">**/?**</span></span>|<span data-ttu-id="95a68-130">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="95a68-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="95a68-131">**/Force**</span><span class="sxs-lookup"><span data-stu-id="95a68-131">**/Force**</span></span>|<span data-ttu-id="95a68-132">Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="95a68-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="95a68-133">**Ważne:**  Jeżeli zestaw o silnej nazwie zostanie zaktualizowany, należy podpisać go ponownie przed wykonaniem jego kodu.</span><span class="sxs-lookup"><span data-stu-id="95a68-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="95a68-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="95a68-134">**/help**</span></span>|<span data-ttu-id="95a68-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="95a68-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="95a68-136">**/ILONLY +**</span><span class="sxs-lookup"><span data-stu-id="95a68-136">**/ILONLY+**</span></span>|<span data-ttu-id="95a68-137">Ustawia flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="95a68-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="95a68-138">**ILONLY**</span><span class="sxs-lookup"><span data-stu-id="95a68-138">**/ILONLY-**</span></span>|<span data-ttu-id="95a68-139">Czyści flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="95a68-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="95a68-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="95a68-140">**/nologo**</span></span>|<span data-ttu-id="95a68-141">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="95a68-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="95a68-142">**/RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="95a68-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="95a68-143">Przywraca wersję nagłówka do CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="95a68-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="95a68-144">**/UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="95a68-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="95a68-145">Uaktualnienia wersję nagłówka CLR do 2.5.</span><span class="sxs-lookup"><span data-stu-id="95a68-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="95a68-146">**Uwaga:**  Aby zestaw mógł być uruchomiony natywnie, musi mieć wersję nagłówka CLR 2.5 lub wyższą.</span><span class="sxs-lookup"><span data-stu-id="95a68-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95a68-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95a68-147">Remarks</span></span>  
 <span data-ttu-id="95a68-148">Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="95a68-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a68-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95a68-149">See also</span></span>

- [<span data-ttu-id="95a68-150">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="95a68-150">Tools</span></span>](index.md)
- [<span data-ttu-id="95a68-151">Aplikacje 64-bitowe</span><span class="sxs-lookup"><span data-stu-id="95a68-151">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="95a68-152">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="95a68-152">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
