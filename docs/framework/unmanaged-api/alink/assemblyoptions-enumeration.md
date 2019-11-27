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
ms.openlocfilehash: ed45e06297b77ea60304cdcfe1b08e97f9e4c085
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446584"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="c9199-102">AssemblyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c9199-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="c9199-103">Wylicza opcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9199-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9199-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9199-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="c9199-105">Pola</span><span class="sxs-lookup"><span data-stu-id="c9199-105">Fields</span></span>  
  
|<span data-ttu-id="c9199-106">Pole</span><span class="sxs-lookup"><span data-stu-id="c9199-106">Field</span></span>|<span data-ttu-id="c9199-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c9199-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9199-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="c9199-108">optAssemTitle</span></span>|<span data-ttu-id="c9199-109">String — reprezentuje tytuł zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9199-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="c9199-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="c9199-110">optAssemDescription</span></span>|<span data-ttu-id="c9199-111">Ciąg — zawiera opis zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9199-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="c9199-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="c9199-112">optAssemConfig</span></span>|<span data-ttu-id="c9199-113">String — zawiera konfigurację zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9199-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="c9199-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="c9199-114">optAssemOS</span></span>|<span data-ttu-id="c9199-115">Zakodowany ciąg jako: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="c9199-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="c9199-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="c9199-116">optAssemProcessor</span></span>|<span data-ttu-id="c9199-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="c9199-117">ULONG</span></span>|  
|<span data-ttu-id="c9199-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="c9199-118">optAssemLocale</span></span>|<span data-ttu-id="c9199-119">Ciąg — zawiera ustawienia regionalne zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9199-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="c9199-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="c9199-120">optAssemVersion</span></span>|<span data-ttu-id="c9199-121">Zakodowany ciąg jako: "główna. pomocnicza. kompilacja. poprawka".</span><span class="sxs-lookup"><span data-stu-id="c9199-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="c9199-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="c9199-122">optAssemCompany</span></span>|<span data-ttu-id="c9199-123">Ciąg — zawiera firmę.</span><span class="sxs-lookup"><span data-stu-id="c9199-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="c9199-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="c9199-124">optAssemProduct</span></span>|<span data-ttu-id="c9199-125">String — zawiera nazwę produktu.</span><span class="sxs-lookup"><span data-stu-id="c9199-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="c9199-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="c9199-126">optAssemProductVersion</span></span>|<span data-ttu-id="c9199-127">Ciąg (znany również jako InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="c9199-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="c9199-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="c9199-128">optAssemCopyright</span></span>|<span data-ttu-id="c9199-129">Ciąg — zawiera informacje o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="c9199-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="c9199-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="c9199-130">optAssemTrademark</span></span>|<span data-ttu-id="c9199-131">Ciąg — zawiera informacje o znakach towarowych.</span><span class="sxs-lookup"><span data-stu-id="c9199-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="c9199-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="c9199-132">optAssemKeyFile</span></span>|<span data-ttu-id="c9199-133">Ciąg (nazwa pliku).</span><span class="sxs-lookup"><span data-stu-id="c9199-133">String (file name).</span></span>|  
|<span data-ttu-id="c9199-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="c9199-134">optAssemKeyName</span></span>|<span data-ttu-id="c9199-135">Ciąg (nazwa klucza).</span><span class="sxs-lookup"><span data-stu-id="c9199-135">String (The key name).</span></span>|  
|<span data-ttu-id="c9199-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="c9199-136">optAssemAlgID</span></span>|<span data-ttu-id="c9199-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="c9199-137">ULONG</span></span>|  
|<span data-ttu-id="c9199-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="c9199-138">optAssemFlags</span></span>|<span data-ttu-id="c9199-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="c9199-139">ULONG</span></span>|  
|<span data-ttu-id="c9199-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="c9199-140">optAssemHalfSign</span></span>|<span data-ttu-id="c9199-141">Bool (znany również jako DelaySign).</span><span class="sxs-lookup"><span data-stu-id="c9199-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="c9199-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="c9199-142">optAssemFileVersion</span></span>|<span data-ttu-id="c9199-143">Zakodowana ciągowo jako "główna. pomocnicza. kompilacja. poprawka" — taka sama jak ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="c9199-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="c9199-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="c9199-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="c9199-145">Kodowanie ciągu jako "główna. pomocnicza. kompilacja. poprawka".</span><span class="sxs-lookup"><span data-stu-id="c9199-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="c9199-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="c9199-146">optLastAssemOption</span></span>|<span data-ttu-id="c9199-147">Licznik liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="c9199-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9199-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9199-148">Requirements</span></span>  
 <span data-ttu-id="c9199-149">**Nagłówek:** Alink. h</span><span class="sxs-lookup"><span data-stu-id="c9199-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="c9199-150">**Biblioteka**: Alink. dll</span><span class="sxs-lookup"><span data-stu-id="c9199-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9199-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9199-151">See also</span></span>

- [<span data-ttu-id="c9199-152">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="c9199-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
