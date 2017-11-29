---
title: "ASSEMBLYMETADATA — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLYMETADATA
api_location: mscoree.dll
api_type: COM
f1_keywords: ASSEMBLYMETADATA
helpviewer_keywords: ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5652907abc17868414c554cb5c87b0856d2c5a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="aa40d-102">ASSEMBLYMETADATA — Struktura</span><span class="sxs-lookup"><span data-stu-id="aa40d-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="aa40d-103">Zawiera informacje o przywoływanego zestawu, w tym jego wersja i poziomu wsparcia dla ustawień regionalnych, procesory i systemy operacyjne.</span><span class="sxs-lookup"><span data-stu-id="aa40d-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa40d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa40d-104">Syntax</span></span>  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="aa40d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="aa40d-105">Members</span></span>  
  
|<span data-ttu-id="aa40d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="aa40d-106">Member</span></span>|<span data-ttu-id="aa40d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="aa40d-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="aa40d-108">Numer wersji głównej przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="aa40d-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="aa40d-109">Ta wartość nie może wynosić zero.</span><span class="sxs-lookup"><span data-stu-id="aa40d-109">This value cannot be zero.</span></span> <span data-ttu-id="aa40d-110">Jeśli wszystkie bity `usMajorVersion` są ustawione, nie określono wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="aa40d-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="aa40d-111">Numer wersji pomocniczej przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="aa40d-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="aa40d-112">Ta wartość nie może wynosić zero.</span><span class="sxs-lookup"><span data-stu-id="aa40d-112">This value cannot be zero.</span></span> <span data-ttu-id="aa40d-113">Jeśli wszystkie bity `usMinorVersion` są ustawione, wersja pomocnicza nie jest określony.</span><span class="sxs-lookup"><span data-stu-id="aa40d-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="aa40d-114">Numer kompilacji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="aa40d-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="aa40d-115">Ta wartość nie może wynosić zero.</span><span class="sxs-lookup"><span data-stu-id="aa40d-115">This value cannot be zero.</span></span> <span data-ttu-id="aa40d-116">Jeśli wszystkie bity `usBuildNumber` są ustawione, nie określono numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="aa40d-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="aa40d-117">Numer poprawki przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="aa40d-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="aa40d-118">Ta wartość nie może wynosić zero.</span><span class="sxs-lookup"><span data-stu-id="aa40d-118">This value cannot be zero.</span></span> <span data-ttu-id="aa40d-119">Jeśli wszystkie bity `usRevisionNumber` są ustawione, numer wersji nie jest określony.</span><span class="sxs-lookup"><span data-stu-id="aa40d-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="aa40d-120">Lista nazw ustawień regionalnych zgodne ze specyfikacją RFC1766, oddzielone średnikami, określając ustawienia regionalne obsługiwane przez zestaw z odwołania.</span><span class="sxs-lookup"><span data-stu-id="aa40d-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="aa40d-121">Wartość null oznacza niezależność od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="aa40d-121">A null value indicates locale independence.</span></span> <span data-ttu-id="aa40d-122">**Uwaga:** w programie .NET Framework w wersji 1.0 nie można określić więcej niż jeden ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="aa40d-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="aa40d-123">Rozmiar w znaki dwubajtowe `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="aa40d-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="aa40d-124">Tablica identyfikatorów, zgodnie z definicją w pliku Winnt.h, typy procesora, które są obsługiwane przez zestaw z odwołania.</span><span class="sxs-lookup"><span data-stu-id="aa40d-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="aa40d-125">Wartości NULL wskazuje niezależność procesora.</span><span class="sxs-lookup"><span data-stu-id="aa40d-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="aa40d-126">Długość `rdwProcessor` tablicy.</span><span class="sxs-lookup"><span data-stu-id="aa40d-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="aa40d-127">Tablica [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) wystąpień określenie systemów operacyjnych, które są obsługiwane przez zestaw z odwołania.</span><span class="sxs-lookup"><span data-stu-id="aa40d-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="aa40d-128">Wartości NULL wskazuje niezależność od systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="aa40d-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="aa40d-129">Długość `rOS` tablicy.</span><span class="sxs-lookup"><span data-stu-id="aa40d-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa40d-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa40d-130">Requirements</span></span>  
 <span data-ttu-id="aa40d-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa40d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa40d-132">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa40d-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa40d-133">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa40d-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa40d-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa40d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa40d-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa40d-135">See Also</span></span>  
 [<span data-ttu-id="aa40d-136">Metadane struktury</span><span class="sxs-lookup"><span data-stu-id="aa40d-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="aa40d-137">IMetaDataAssemblyEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="aa40d-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="aa40d-138">Osinfo — struktura</span><span class="sxs-lookup"><span data-stu-id="aa40d-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
