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
ms.openlocfilehash: ca3e9dbe5578623ccc67898c6f08213c31ad8e23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="b184a-102">CorFlags.exe (Narzędzie konwersji CorFlags)</span><span class="sxs-lookup"><span data-stu-id="b184a-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="b184a-103">Narzędzie do konwersji CorFlags pozwala na konfigurowanie sekcji CorFlags w nagłówku przenośnego obrazu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="b184a-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="b184a-104">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b184a-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="b184a-105">Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="b184a-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="b184a-106">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b184a-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="b184a-107">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b184a-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b184a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b184a-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b184a-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="b184a-109">Parameters</span></span>  
  
|<span data-ttu-id="b184a-110">Wymagany parametr</span><span class="sxs-lookup"><span data-stu-id="b184a-110">Required parameter</span></span>|<span data-ttu-id="b184a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b184a-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="b184a-112">Nazwa zestawu, dla którego chcesz skonfigurować CorFlags.</span><span class="sxs-lookup"><span data-stu-id="b184a-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="b184a-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="b184a-113">Option</span></span>|<span data-ttu-id="b184a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b184a-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b184a-115">**/ 32-BITOWE [WYMAGANE] +**</span><span class="sxs-lookup"><span data-stu-id="b184a-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="b184a-116">Ustawia flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="b184a-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="b184a-117">**/ 32-BITOWE [WYMAGANE]-**</span><span class="sxs-lookup"><span data-stu-id="b184a-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="b184a-118">Czyści flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="b184a-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="b184a-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="b184a-119">**/32BITPREF+**</span></span>|<span data-ttu-id="b184a-120">Ustawia flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="b184a-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="b184a-121">Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="b184a-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="b184a-122">Należy ustawić tą flagę tylko dla plików EXE.</span><span class="sxs-lookup"><span data-stu-id="b184a-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="b184a-123">Jeśli flaga jest ustawiona na bibliotekę DLL, biblioteki DLL nie udało się załadować w 64-bitowych procesów i <xref:System.BadImageFormatException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b184a-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="b184a-124">Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.</span><span class="sxs-lookup"><span data-stu-id="b184a-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="b184a-125">Nowość w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b184a-125">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="b184a-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="b184a-126">**/32BITPREF-**</span></span>|<span data-ttu-id="b184a-127">Czyści flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="b184a-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="b184a-128">Nowość w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b184a-128">New in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|<span data-ttu-id="b184a-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="b184a-129">**/?**</span></span>|<span data-ttu-id="b184a-130">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b184a-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="b184a-131">**/ Force**</span><span class="sxs-lookup"><span data-stu-id="b184a-131">**/Force**</span></span>|<span data-ttu-id="b184a-132">Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="b184a-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="b184a-133">**Ważne:** po zaktualizowaniu zestawu z silną nazwą, musisz zarejestrować go ponownie przed wykonaniem jego kodu.</span><span class="sxs-lookup"><span data-stu-id="b184a-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="b184a-134">**/ Help**</span><span class="sxs-lookup"><span data-stu-id="b184a-134">**/help**</span></span>|<span data-ttu-id="b184a-135">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b184a-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="b184a-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="b184a-136">**/ILONLY+**</span></span>|<span data-ttu-id="b184a-137">Ustawia flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="b184a-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="b184a-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="b184a-138">**/ILONLY-**</span></span>|<span data-ttu-id="b184a-139">Czyści flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="b184a-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="b184a-140">**/ nologo**</span><span class="sxs-lookup"><span data-stu-id="b184a-140">**/nologo**</span></span>|<span data-ttu-id="b184a-141">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b184a-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="b184a-142">**/ RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="b184a-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="b184a-143">Przywraca wersję nagłówka do CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="b184a-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="b184a-144">**/ UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="b184a-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="b184a-145">Uaktualnienia wersję nagłówka CLR do 2.5.</span><span class="sxs-lookup"><span data-stu-id="b184a-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="b184a-146">**Uwaga:** zestawy muszą mieć CLR nagłówkiem w wersji 2.5 lub nowszej do działania.</span><span class="sxs-lookup"><span data-stu-id="b184a-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b184a-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b184a-147">Remarks</span></span>  
 <span data-ttu-id="b184a-148">Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b184a-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b184a-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b184a-149">See Also</span></span>  
 [<span data-ttu-id="b184a-150">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="b184a-150">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="b184a-151">64-bit — aplikacje</span><span class="sxs-lookup"><span data-stu-id="b184a-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)  
 [<span data-ttu-id="b184a-152">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="b184a-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
