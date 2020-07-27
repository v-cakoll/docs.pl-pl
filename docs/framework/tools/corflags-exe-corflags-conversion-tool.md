---
title: CorFlags.exe (Narzędzie konwersji CorFlags)
description: Poznaj CorFlags.exe narzędzia konwersji CorFlags. To narzędzie umożliwia skonfigurowanie sekcji CorFlags nagłówka przenośnego obrazu wykonywalnego.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: da5efadd63cc03f6f6e4eecf3115865ca3643b39
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167223"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="bc2c6-104">CorFlags.exe (Narzędzie konwersji CorFlags)</span><span class="sxs-lookup"><span data-stu-id="bc2c6-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="bc2c6-105">Narzędzie do konwersji CorFlags pozwala na konfigurowanie sekcji CorFlags w nagłówku przenośnego obrazu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="bc2c6-106">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="bc2c6-107">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="bc2c6-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="bc2c6-108">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="bc2c6-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="bc2c6-109">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="bc2c6-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2c6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc2c6-110">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc2c6-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc2c6-111">Parameters</span></span>  
  
|<span data-ttu-id="bc2c6-112">Wymagany parametr</span><span class="sxs-lookup"><span data-stu-id="bc2c6-112">Required parameter</span></span>|<span data-ttu-id="bc2c6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bc2c6-113">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="bc2c6-114">Nazwa zestawu, dla którego chcesz skonfigurować CorFlags.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-114">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="bc2c6-115">Opcja</span><span class="sxs-lookup"><span data-stu-id="bc2c6-115">Option</span></span>|<span data-ttu-id="bc2c6-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bc2c6-116">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="bc2c6-117">Ustawia flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-117">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="bc2c6-118">Czyści flagę 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-118">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="bc2c6-119">Ustawia flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-119">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="bc2c6-120">Aplikacja działa jako proces 32-bitowy nawet na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-120">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="bc2c6-121">Należy ustawić tą flagę tylko dla plików EXE.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-121">Set this flag only on EXE files.</span></span> <span data-ttu-id="bc2c6-122">Jeśli flaga jest ustawiona dla biblioteki DLL, nie można załadować biblioteki DLL w procesach 64-bitowych i <xref:System.BadImageFormatException> zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-122">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="bc2c6-123">Plik EXE z tą flagą może być załadowany do procesu 64-bitowego.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-123">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="bc2c6-124">Nowość w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-124">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="bc2c6-125">Czyści flagę 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-125">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="bc2c6-126">Nowość w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-126">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="bc2c6-127">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-127">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="bc2c6-128">Wymusza aktualizację, nawet jeśli jest to zestaw z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-128">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="bc2c6-129">**Ważne:**  W przypadku aktualizowania zestawu o silnej nazwie należy podpisać go ponownie przed wykonaniem kodu.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-129">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="bc2c6-130">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-130">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="bc2c6-131">Ustawia flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-131">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="bc2c6-132">Czyści flagę ILONLY.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-132">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="bc2c6-133">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-133">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="bc2c6-134">Przywraca wersję nagłówka do CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-134">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="bc2c6-135">Uaktualnienia wersję nagłówka CLR do 2.5.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-135">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="bc2c6-136">**Uwaga:**  Zestawy muszą mieć wersję nagłówka CLR równą 2,5 lub większą do uruchomienia natywnie.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-136">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc2c6-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc2c6-137">Remarks</span></span>  
 <span data-ttu-id="bc2c6-138">Jeśli nie określono opcji, narzędzie konwersji CorFlags wyświetla flagi dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bc2c6-138">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2c6-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc2c6-139">See also</span></span>

- [<span data-ttu-id="bc2c6-140">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="bc2c6-140">Tools</span></span>](index.md)
- [<span data-ttu-id="bc2c6-141">Aplikacje 64-bitowe</span><span class="sxs-lookup"><span data-stu-id="bc2c6-141">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="bc2c6-142">Wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="bc2c6-142">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
