---
title: ASSEMBLYMETADATA — Struktura
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f0a9b9c149c86b4d9121275aa858dfdc0cdbac7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905921"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="7e860-102">ASSEMBLYMETADATA — Struktura</span><span class="sxs-lookup"><span data-stu-id="7e860-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="7e860-103">Zawiera informacje o przywoływanego zestawu, w tym jej wersji oraz jego poziom wsparcia dla ustawień regionalnych, procesory i systemy operacyjne.</span><span class="sxs-lookup"><span data-stu-id="7e860-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e860-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e860-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7e860-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7e860-105">Members</span></span>  
  
|<span data-ttu-id="7e860-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7e860-106">Member</span></span>|<span data-ttu-id="7e860-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7e860-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="7e860-108">Główny numer wersji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7e860-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="7e860-109">Ta wartość nie może mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="7e860-109">This value cannot be zero.</span></span> <span data-ttu-id="7e860-110">Jeśli wszystkie bity `usMajorVersion` są ustawione, nie określono wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="7e860-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="7e860-111">Pomocniczy numer wersji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7e860-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="7e860-112">Ta wartość nie może mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="7e860-112">This value cannot be zero.</span></span> <span data-ttu-id="7e860-113">Jeśli wszystkie bity `usMinorVersion` są ustawione, wersja pomocnicza nie jest określony.</span><span class="sxs-lookup"><span data-stu-id="7e860-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="7e860-114">Numer kompilacji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7e860-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="7e860-115">Ta wartość nie może mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="7e860-115">This value cannot be zero.</span></span> <span data-ttu-id="7e860-116">Jeśli wszystkie bity `usBuildNumber` są ustawione, nie podano numeru kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7e860-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="7e860-117">Numer poprawki przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7e860-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="7e860-118">Ta wartość nie może mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="7e860-118">This value cannot be zero.</span></span> <span data-ttu-id="7e860-119">Jeśli wszystkie bity `usRevisionNumber` są ustawione, numer wersji nie jest określony.</span><span class="sxs-lookup"><span data-stu-id="7e860-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="7e860-120">Lista nazw ustawień regionalnych, zgodne ze specyfikacją RFC1766, oddzielone średnikami, określanie ustawień regionalnych obsługiwanych przez zestaw z odwołania.</span><span class="sxs-lookup"><span data-stu-id="7e860-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="7e860-121">Wartość zerowa wskazuje niezależność od ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="7e860-121">A null value indicates locale independence.</span></span> <span data-ttu-id="7e860-122">**Uwaga:**  W .NET Framework w wersji 1.0, nie można określić kilka ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="7e860-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="7e860-123">Rozmiar w znaków `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="7e860-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="7e860-124">Tablica identyfikatorów, zgodnie z definicją w pliku Winnt.h, dla typów procesora, które są obsługiwane przez zestaw z odwołania.</span><span class="sxs-lookup"><span data-stu-id="7e860-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="7e860-125">Wartość NULL oznacza niezależność procesora.</span><span class="sxs-lookup"><span data-stu-id="7e860-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="7e860-126">Długość `rdwProcessor` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e860-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="7e860-127">Tablica [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) wystąpień, określając systemów operacyjnych, które są obsługiwane przez zestaw z odwołania.</span><span class="sxs-lookup"><span data-stu-id="7e860-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="7e860-128">Wartość NULL oznacza niezależność od systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7e860-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="7e860-129">Długość `rOS` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e860-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e860-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e860-130">Requirements</span></span>  
 <span data-ttu-id="7e860-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e860-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e860-132">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7e860-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e860-133">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e860-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e860-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e860-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e860-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e860-135">See also</span></span>

- [<span data-ttu-id="7e860-136">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="7e860-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="7e860-137">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e860-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="7e860-138">OSINFO, struktura</span><span class="sxs-lookup"><span data-stu-id="7e860-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
