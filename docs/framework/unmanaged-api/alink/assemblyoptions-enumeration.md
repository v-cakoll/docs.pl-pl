---
title: AssemblyOptions — Wyliczenie
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 324e30f6cbcaa1d1d81c7c03967dbb629d2cd6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742267"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="6e8c3-102">AssemblyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6e8c3-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="6e8c3-103">Wylicza opcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e8c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e8c3-104">Syntax</span></span>  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="6e8c3-105">Pola</span><span class="sxs-lookup"><span data-stu-id="6e8c3-105">Fields</span></span>  
  
|<span data-ttu-id="6e8c3-106">Pole</span><span class="sxs-lookup"><span data-stu-id="6e8c3-106">Field</span></span>|<span data-ttu-id="6e8c3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6e8c3-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6e8c3-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="6e8c3-108">optAssemTitle</span></span>|<span data-ttu-id="6e8c3-109">String — reprezentuje tytuł zestawu.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="6e8c3-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="6e8c3-110">optAssemDescription</span></span>|<span data-ttu-id="6e8c3-111">String — zawiera opis zestawu.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="6e8c3-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="6e8c3-112">optAssemConfig</span></span>|<span data-ttu-id="6e8c3-113">String — zawiera konfigurację zestawu.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="6e8c3-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="6e8c3-114">optAssemOS</span></span>|<span data-ttu-id="6e8c3-115">Parametry - zakodowanymi w formacie: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="6e8c3-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="6e8c3-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="6e8c3-116">optAssemProcessor</span></span>|<span data-ttu-id="6e8c3-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="6e8c3-117">ULONG</span></span>|  
|<span data-ttu-id="6e8c3-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="6e8c3-118">optAssemLocale</span></span>|<span data-ttu-id="6e8c3-119">String — zawiera zestaw ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="6e8c3-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="6e8c3-120">optAssemVersion</span></span>|<span data-ttu-id="6e8c3-121">Parametry - zakodowanymi w formacie: "Główna.pomocnicza.kompilacja.poprawka".</span><span class="sxs-lookup"><span data-stu-id="6e8c3-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="6e8c3-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="6e8c3-122">optAssemCompany</span></span>|<span data-ttu-id="6e8c3-123">String — zawiera firmy.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="6e8c3-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="6e8c3-124">optAssemProduct</span></span>|<span data-ttu-id="6e8c3-125">String — zawiera nazwę produktu.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="6e8c3-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="6e8c3-126">optAssemProductVersion</span></span>|<span data-ttu-id="6e8c3-127">Ciąg (znany także jako InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="6e8c3-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="6e8c3-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="6e8c3-128">optAssemCopyright</span></span>|<span data-ttu-id="6e8c3-129">String — zawiera informacje o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="6e8c3-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="6e8c3-130">optAssemTrademark</span></span>|<span data-ttu-id="6e8c3-131">String — zawiera informacje o znakach towarowych.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="6e8c3-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="6e8c3-132">optAssemKeyFile</span></span>|<span data-ttu-id="6e8c3-133">String (nazwa pliku).</span><span class="sxs-lookup"><span data-stu-id="6e8c3-133">String (file name).</span></span>|  
|<span data-ttu-id="6e8c3-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="6e8c3-134">optAssemKeyName</span></span>|<span data-ttu-id="6e8c3-135">Ciąg (nazwa klucza).</span><span class="sxs-lookup"><span data-stu-id="6e8c3-135">String (The key name).</span></span>|  
|<span data-ttu-id="6e8c3-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="6e8c3-136">optAssemAlgID</span></span>|<span data-ttu-id="6e8c3-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="6e8c3-137">ULONG</span></span>|  
|<span data-ttu-id="6e8c3-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="6e8c3-138">optAssemFlags</span></span>|<span data-ttu-id="6e8c3-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="6e8c3-139">ULONG</span></span>|  
|<span data-ttu-id="6e8c3-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="6e8c3-140">optAssemHalfSign</span></span>|<span data-ttu-id="6e8c3-141">Wartość logiczna (określana także jako DelaySign).</span><span class="sxs-lookup"><span data-stu-id="6e8c3-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="6e8c3-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="6e8c3-142">optAssemFileVersion</span></span>|<span data-ttu-id="6e8c3-143">Parametry - zakodowanymi w formacie "Główna.pomocnicza.kompilacja.poprawka"--takie same jak ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="6e8c3-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="6e8c3-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="6e8c3-145">Parametry - zakodowanymi w formacie "Główna.pomocnicza.kompilacja.poprawka".</span><span class="sxs-lookup"><span data-stu-id="6e8c3-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="6e8c3-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="6e8c3-146">optLastAssemOption</span></span>|<span data-ttu-id="6e8c3-147">Licznik liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="6e8c3-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e8c3-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e8c3-148">Requirements</span></span>  
 <span data-ttu-id="6e8c3-149">**Nagłówek:** alink.h</span><span class="sxs-lookup"><span data-stu-id="6e8c3-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="6e8c3-150">**Biblioteka**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="6e8c3-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e8c3-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e8c3-151">See also</span></span>

- [<span data-ttu-id="6e8c3-152">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="6e8c3-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
