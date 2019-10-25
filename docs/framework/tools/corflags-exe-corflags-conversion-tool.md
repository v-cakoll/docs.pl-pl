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
ms.openlocfilehash: 63e70ae8cd110786ad7d2069088dbfdfde736a28
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846749"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="fb390-102">CorFlags.exe (Narzędzie konwersji CorFlags)</span><span class="sxs-lookup"><span data-stu-id="fb390-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="fb390-103">Narzędzie do konwersji CorFlags pozwala na konfigurowanie sekcji CorFlags w nagłówku przenośnego obrazu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="fb390-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="fb390-104">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb390-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="fb390-105">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="fb390-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="fb390-106">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="fb390-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="fb390-107">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="fb390-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb390-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb390-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb390-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb390-109">Parameters</span></span>  
  
|<span data-ttu-id="fb390-110">Wymagany parametr</span><span class="sxs-lookup"><span data-stu-id="fb390-110">Required parameter</span></span>|<span data-ttu-id="fb390-111">Opis</span><span class="sxs-lookup"><span data-stu-id="fb390-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="fb390-112">Nazwa zestawu, dla którego chcesz skonfigurować CorFlags.</span><span class="sxs-lookup"><span data-stu-id="fb390-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="fb390-113">Opcja</span><span class="sxs-lookup"><span data-stu-id="fb390-113">Option</span></span>|<span data-ttu-id="fb390-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fb390-114">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="fb390-115">Ustawia flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="fb390-115">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="fb390-116">Czyści flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="fb390-116">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="fb390-117">Ustawia flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="fb390-117">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="fb390-118">Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="fb390-118">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="fb390-119">Należy ustawić tą flagę tylko dla plików EXE.</span><span class="sxs-lookup"><span data-stu-id="fb390-119">Set this flag only on EXE files.</span></span> <span data-ttu-id="fb390-120">Jeśli flaga jest ustawiona dla biblioteki DLL, nie można załadować biblioteki DLL w procesach 64-bitowych i zostanie zgłoszony wyjątek <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="fb390-120">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="fb390-121">Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.</span><span class="sxs-lookup"><span data-stu-id="fb390-121">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="fb390-122">Nowość w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="fb390-122">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="fb390-123">Czyści flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="fb390-123">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="fb390-124">Nowość w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="fb390-124">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="fb390-125">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fb390-125">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="fb390-126">Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="fb390-126">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="fb390-127">**Ważne:**  W przypadku aktualizowania zestawu o silnej nazwie należy podpisać go ponownie przed wykonaniem kodu.</span><span class="sxs-lookup"><span data-stu-id="fb390-127">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="fb390-128">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fb390-128">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="fb390-129">Ustawia flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="fb390-129">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="fb390-130">Czyści flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="fb390-130">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="fb390-131">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fb390-131">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="fb390-132">Przywraca wersję nagłówka do CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="fb390-132">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="fb390-133">Uaktualnienia wersję nagłówka CLR do 2.5.</span><span class="sxs-lookup"><span data-stu-id="fb390-133">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="fb390-134">**Uwaga:**  Zestawy muszą mieć wersję nagłówka CLR równą 2,5 lub większą do uruchomienia natywnie.</span><span class="sxs-lookup"><span data-stu-id="fb390-134">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb390-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb390-135">Remarks</span></span>  
 <span data-ttu-id="fb390-136">Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="fb390-136">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb390-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb390-137">See also</span></span>

- [<span data-ttu-id="fb390-138">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="fb390-138">Tools</span></span>](index.md)
- [<span data-ttu-id="fb390-139">Aplikacje 64-bitowe</span><span class="sxs-lookup"><span data-stu-id="fb390-139">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="fb390-140">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="fb390-140">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
