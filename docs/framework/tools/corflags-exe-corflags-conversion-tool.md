---
title: "CorFlags.exe (Narzędzie konwersji CorFlags)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 111c697d4d62cd52cd7913039e3c17e8a25ab50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="4df0b-102">CorFlags.exe (Narzędzie konwersji CorFlags)</span><span class="sxs-lookup"><span data-stu-id="4df0b-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="4df0b-103">Narzędzie do konwersji CorFlags pozwala na konfigurowanie sekcji CorFlags w nagłówku przenośnego obrazu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="4df0b-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="4df0b-104">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4df0b-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4df0b-105">Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="4df0b-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4df0b-106">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4df0b-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="4df0b-107">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4df0b-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df0b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4df0b-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4df0b-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="4df0b-109">Parameters</span></span>  
  
|<span data-ttu-id="4df0b-110">Wymagany parametr</span><span class="sxs-lookup"><span data-stu-id="4df0b-110">Required parameter</span></span>|<span data-ttu-id="4df0b-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4df0b-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="4df0b-112">Nazwa zestawu, dla którego chcesz skonfigurować CorFlags.</span><span class="sxs-lookup"><span data-stu-id="4df0b-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="4df0b-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="4df0b-113">Option</span></span>|<span data-ttu-id="4df0b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4df0b-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4df0b-115">**/ 32-BITOWE [WYMAGANE] +**</span><span class="sxs-lookup"><span data-stu-id="4df0b-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="4df0b-116">Ustawia flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="4df0b-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="4df0b-117">**/ 32-BITOWE [WYMAGANE]-**</span><span class="sxs-lookup"><span data-stu-id="4df0b-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="4df0b-118">Czyści flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="4df0b-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="4df0b-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="4df0b-119">**/32BITPREF+**</span></span>|<span data-ttu-id="4df0b-120">Ustawia flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="4df0b-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="4df0b-121">Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="4df0b-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="4df0b-122">Należy ustawić tą flagę tylko dla plików EXE.</span><span class="sxs-lookup"><span data-stu-id="4df0b-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="4df0b-123">Jeśli flaga jest ustawiona na bibliotekę DLL, biblioteki DLL nie udało się załadować w 64-bitowych procesów i <xref:System.BadImageFormatException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4df0b-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="4df0b-124">Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.</span><span class="sxs-lookup"><span data-stu-id="4df0b-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="4df0b-125">Nowość w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4df0b-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="4df0b-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="4df0b-126">**/32BITPREF-**</span></span>|<span data-ttu-id="4df0b-127">Czyści flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="4df0b-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="4df0b-128">Nowość w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4df0b-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="4df0b-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="4df0b-129">**/?**</span></span>|<span data-ttu-id="4df0b-130">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4df0b-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="4df0b-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="4df0b-131">**/Force**</span></span>|<span data-ttu-id="4df0b-132">Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="4df0b-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="4df0b-133">**Ważne:** po zaktualizowaniu zestawu z silną nazwą, musisz zarejestrować go ponownie przed wykonaniem jego kodu.</span><span class="sxs-lookup"><span data-stu-id="4df0b-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="4df0b-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="4df0b-134">**/help**</span></span>|<span data-ttu-id="4df0b-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="4df0b-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="4df0b-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="4df0b-136">**/ILONLY+**</span></span>|<span data-ttu-id="4df0b-137">Ustawia flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="4df0b-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="4df0b-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="4df0b-138">**/ILONLY-**</span></span>|<span data-ttu-id="4df0b-139">Czyści flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="4df0b-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="4df0b-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="4df0b-140">**/nologo**</span></span>|<span data-ttu-id="4df0b-141">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4df0b-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="4df0b-142">**/ RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="4df0b-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="4df0b-143">Przywraca wersję nagłówka do CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="4df0b-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="4df0b-144">**/ UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="4df0b-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="4df0b-145">Uaktualnienia wersję nagłówka CLR do 2.5.</span><span class="sxs-lookup"><span data-stu-id="4df0b-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="4df0b-146">**Uwaga:** zestawy muszą mieć CLR nagłówkiem w wersji 2.5 lub nowszej do działania.</span><span class="sxs-lookup"><span data-stu-id="4df0b-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4df0b-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4df0b-147">Remarks</span></span>  
 <span data-ttu-id="4df0b-148">Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4df0b-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df0b-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4df0b-149">See Also</span></span>  
 [<span data-ttu-id="4df0b-150">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="4df0b-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="4df0b-151">Aplikacje 64-bitowe</span><span class="sxs-lookup"><span data-stu-id="4df0b-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="4df0b-152">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="4df0b-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
