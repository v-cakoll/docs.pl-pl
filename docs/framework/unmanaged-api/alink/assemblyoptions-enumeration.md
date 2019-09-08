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
ms.openlocfilehash: 49e7b73559e8def890f8df8f596fbe8ad5bb5d3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777481"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="c10e0-102">AssemblyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c10e0-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="c10e0-103">Wylicza opcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="c10e0-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c10e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c10e0-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="c10e0-105">Pola</span><span class="sxs-lookup"><span data-stu-id="c10e0-105">Fields</span></span>  
  
|<span data-ttu-id="c10e0-106">Pole</span><span class="sxs-lookup"><span data-stu-id="c10e0-106">Field</span></span>|<span data-ttu-id="c10e0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c10e0-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c10e0-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="c10e0-108">optAssemTitle</span></span>|<span data-ttu-id="c10e0-109">String — reprezentuje tytuł zestawu.</span><span class="sxs-lookup"><span data-stu-id="c10e0-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="c10e0-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="c10e0-110">optAssemDescription</span></span>|<span data-ttu-id="c10e0-111">Ciąg — zawiera opis zestawu.</span><span class="sxs-lookup"><span data-stu-id="c10e0-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="c10e0-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="c10e0-112">optAssemConfig</span></span>|<span data-ttu-id="c10e0-113">String — zawiera konfigurację zestawu.</span><span class="sxs-lookup"><span data-stu-id="c10e0-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="c10e0-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="c10e0-114">optAssemOS</span></span>|<span data-ttu-id="c10e0-115">Zakodowany ciąg jako: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="c10e0-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="c10e0-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="c10e0-116">optAssemProcessor</span></span>|<span data-ttu-id="c10e0-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="c10e0-117">ULONG</span></span>|  
|<span data-ttu-id="c10e0-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="c10e0-118">optAssemLocale</span></span>|<span data-ttu-id="c10e0-119">Ciąg — zawiera ustawienia regionalne zestawu.</span><span class="sxs-lookup"><span data-stu-id="c10e0-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="c10e0-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="c10e0-120">optAssemVersion</span></span>|<span data-ttu-id="c10e0-121">Zakodowany ciąg jako: "Główna. pomocnicza. kompilacja. poprawka".</span><span class="sxs-lookup"><span data-stu-id="c10e0-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="c10e0-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="c10e0-122">optAssemCompany</span></span>|<span data-ttu-id="c10e0-123">Ciąg — zawiera firmę.</span><span class="sxs-lookup"><span data-stu-id="c10e0-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="c10e0-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="c10e0-124">optAssemProduct</span></span>|<span data-ttu-id="c10e0-125">String — zawiera nazwę produktu.</span><span class="sxs-lookup"><span data-stu-id="c10e0-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="c10e0-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="c10e0-126">optAssemProductVersion</span></span>|<span data-ttu-id="c10e0-127">Ciąg (znany również jako InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="c10e0-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="c10e0-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="c10e0-128">optAssemCopyright</span></span>|<span data-ttu-id="c10e0-129">Ciąg — zawiera informacje o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="c10e0-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="c10e0-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="c10e0-130">optAssemTrademark</span></span>|<span data-ttu-id="c10e0-131">Ciąg — zawiera informacje o znakach towarowych.</span><span class="sxs-lookup"><span data-stu-id="c10e0-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="c10e0-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="c10e0-132">optAssemKeyFile</span></span>|<span data-ttu-id="c10e0-133">Ciąg (nazwa pliku).</span><span class="sxs-lookup"><span data-stu-id="c10e0-133">String (file name).</span></span>|  
|<span data-ttu-id="c10e0-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="c10e0-134">optAssemKeyName</span></span>|<span data-ttu-id="c10e0-135">Ciąg (nazwa klucza).</span><span class="sxs-lookup"><span data-stu-id="c10e0-135">String (The key name).</span></span>|  
|<span data-ttu-id="c10e0-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="c10e0-136">optAssemAlgID</span></span>|<span data-ttu-id="c10e0-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="c10e0-137">ULONG</span></span>|  
|<span data-ttu-id="c10e0-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="c10e0-138">optAssemFlags</span></span>|<span data-ttu-id="c10e0-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="c10e0-139">ULONG</span></span>|  
|<span data-ttu-id="c10e0-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="c10e0-140">optAssemHalfSign</span></span>|<span data-ttu-id="c10e0-141">Bool (znany również jako DelaySign).</span><span class="sxs-lookup"><span data-stu-id="c10e0-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="c10e0-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="c10e0-142">optAssemFileVersion</span></span>|<span data-ttu-id="c10e0-143">Zakodowana ciągowo jako "główna. pomocnicza. kompilacja. poprawka" — taka sama jak ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="c10e0-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="c10e0-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="c10e0-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="c10e0-145">Kodowanie ciągu jako "główna. pomocnicza. kompilacja. poprawka".</span><span class="sxs-lookup"><span data-stu-id="c10e0-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="c10e0-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="c10e0-146">optLastAssemOption</span></span>|<span data-ttu-id="c10e0-147">Licznik liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="c10e0-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c10e0-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c10e0-148">Requirements</span></span>  
 <span data-ttu-id="c10e0-149">**Nagłówek:** Alink. h</span><span class="sxs-lookup"><span data-stu-id="c10e0-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="c10e0-150">**Biblioteka**: Alink. dll</span><span class="sxs-lookup"><span data-stu-id="c10e0-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c10e0-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c10e0-151">See also</span></span>

- [<span data-ttu-id="c10e0-152">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="c10e0-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
