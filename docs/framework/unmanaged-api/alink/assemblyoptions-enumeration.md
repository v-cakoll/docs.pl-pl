---
title: "AssemblyOptions — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyOptions
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ccbbcabd3fbb372322ca6334f6ab6db4fdafc2f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="92a2c-102">AssemblyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="92a2c-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="92a2c-103">Wylicza opcje zestawu.</span><span class="sxs-lookup"><span data-stu-id="92a2c-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92a2c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92a2c-104">Syntax</span></span>  
  
```  
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
  
## <a name="fields"></a><span data-ttu-id="92a2c-105">Pola</span><span class="sxs-lookup"><span data-stu-id="92a2c-105">Fields</span></span>  
  
|<span data-ttu-id="92a2c-106">Pole</span><span class="sxs-lookup"><span data-stu-id="92a2c-106">Field</span></span>|<span data-ttu-id="92a2c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="92a2c-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92a2c-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="92a2c-108">optAssemTitle</span></span>|<span data-ttu-id="92a2c-109">String — reprezentuje tytuł zestawu.</span><span class="sxs-lookup"><span data-stu-id="92a2c-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="92a2c-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="92a2c-110">optAssemDescription</span></span>|<span data-ttu-id="92a2c-111">String — zawiera opis zestawu.</span><span class="sxs-lookup"><span data-stu-id="92a2c-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="92a2c-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="92a2c-112">optAssemConfig</span></span>|<span data-ttu-id="92a2c-113">String — zawiera konfigurację zestawu.</span><span class="sxs-lookup"><span data-stu-id="92a2c-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="92a2c-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="92a2c-114">optAssemOS</span></span>|<span data-ttu-id="92a2c-115">Parametry - zakodowane jako: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="92a2c-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="92a2c-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="92a2c-116">optAssemProcessor</span></span>|<span data-ttu-id="92a2c-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="92a2c-117">ULONG</span></span>|  
|<span data-ttu-id="92a2c-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="92a2c-118">optAssemLocale</span></span>|<span data-ttu-id="92a2c-119">String — zawiera zestaw ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="92a2c-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="92a2c-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="92a2c-120">optAssemVersion</span></span>|<span data-ttu-id="92a2c-121">Parametry - zakodowane jako: "Główna.pomocnicza.kompilacja.poprawka".</span><span class="sxs-lookup"><span data-stu-id="92a2c-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="92a2c-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="92a2c-122">optAssemCompany</span></span>|<span data-ttu-id="92a2c-123">String — zawiera firmy.</span><span class="sxs-lookup"><span data-stu-id="92a2c-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="92a2c-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="92a2c-124">optAssemProduct</span></span>|<span data-ttu-id="92a2c-125">String — zawiera nazwę produktu.</span><span class="sxs-lookup"><span data-stu-id="92a2c-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="92a2c-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="92a2c-126">optAssemProductVersion</span></span>|<span data-ttu-id="92a2c-127">Ciąg (znanej także jako InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="92a2c-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="92a2c-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="92a2c-128">optAssemCopyright</span></span>|<span data-ttu-id="92a2c-129">String — zawiera informacje o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="92a2c-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="92a2c-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="92a2c-130">optAssemTrademark</span></span>|<span data-ttu-id="92a2c-131">String — zawiera informacje o znakach towarowych.</span><span class="sxs-lookup"><span data-stu-id="92a2c-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="92a2c-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="92a2c-132">optAssemKeyFile</span></span>|<span data-ttu-id="92a2c-133">String (nazwa pliku).</span><span class="sxs-lookup"><span data-stu-id="92a2c-133">String (file name).</span></span>|  
|<span data-ttu-id="92a2c-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="92a2c-134">optAssemKeyName</span></span>|<span data-ttu-id="92a2c-135">String (nazwa klucza).</span><span class="sxs-lookup"><span data-stu-id="92a2c-135">String (The key name).</span></span>|  
|<span data-ttu-id="92a2c-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="92a2c-136">optAssemAlgID</span></span>|<span data-ttu-id="92a2c-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="92a2c-137">ULONG</span></span>|  
|<span data-ttu-id="92a2c-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="92a2c-138">optAssemFlags</span></span>|<span data-ttu-id="92a2c-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="92a2c-139">ULONG</span></span>|  
|<span data-ttu-id="92a2c-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="92a2c-140">optAssemHalfSign</span></span>|<span data-ttu-id="92a2c-141">Wartość logiczna (określane również jako DelaySign).</span><span class="sxs-lookup"><span data-stu-id="92a2c-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="92a2c-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="92a2c-142">optAssemFileVersion</span></span>|<span data-ttu-id="92a2c-143">Parametry - zakodowane jako "Główna.pomocnicza.kompilacja.poprawka"--identyczny ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="92a2c-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="92a2c-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="92a2c-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="92a2c-145">Parametry - zakodowane jako "Główna.pomocnicza.kompilacja.poprawka".</span><span class="sxs-lookup"><span data-stu-id="92a2c-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="92a2c-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="92a2c-146">optLastAssemOption</span></span>|<span data-ttu-id="92a2c-147">Licznik liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="92a2c-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92a2c-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92a2c-148">Requirements</span></span>  
 <span data-ttu-id="92a2c-149">**Nagłówek:** alink.h</span><span class="sxs-lookup"><span data-stu-id="92a2c-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="92a2c-150">**Biblioteka**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="92a2c-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a2c-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92a2c-151">See Also</span></span>  
 [<span data-ttu-id="92a2c-152">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="92a2c-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
