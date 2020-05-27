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
ms.openlocfilehash: 5c7211fc2523b70313a1e4d4d9d2da0dcecd1d32
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009434"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="4cc33-102">ASSEMBLYMETADATA — Struktura</span><span class="sxs-lookup"><span data-stu-id="4cc33-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="4cc33-103">Zawiera informacje o zestawie, do którego istnieje odwołanie, w tym jego wersji oraz o poziomie wsparcia dla ustawień regionalnych, procesorów i systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="4cc33-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cc33-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="4cc33-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4cc33-105">Members</span></span>  
  
|<span data-ttu-id="4cc33-106">Członek</span><span class="sxs-lookup"><span data-stu-id="4cc33-106">Member</span></span>|<span data-ttu-id="4cc33-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4cc33-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="4cc33-108">Numer wersji głównej przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4cc33-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="4cc33-109">Ta wartość nie może być równa zero.</span><span class="sxs-lookup"><span data-stu-id="4cc33-109">This value cannot be zero.</span></span> <span data-ttu-id="4cc33-110">Jeśli wszystkie bity `usMajorVersion` są ustawione, wersja główna nie zostanie określona.</span><span class="sxs-lookup"><span data-stu-id="4cc33-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="4cc33-111">Pomocniczy numer wersji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4cc33-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="4cc33-112">Ta wartość nie może być równa zero.</span><span class="sxs-lookup"><span data-stu-id="4cc33-112">This value cannot be zero.</span></span> <span data-ttu-id="4cc33-113">Jeśli wszystkie bity `usMinorVersion` są ustawione, nie zostanie określona wersja pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="4cc33-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="4cc33-114">Numer kompilacji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4cc33-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="4cc33-115">Ta wartość nie może być równa zero.</span><span class="sxs-lookup"><span data-stu-id="4cc33-115">This value cannot be zero.</span></span> <span data-ttu-id="4cc33-116">Jeśli wszystkie bity `usBuildNumber` są ustawione, numer kompilacji nie zostanie określony.</span><span class="sxs-lookup"><span data-stu-id="4cc33-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="4cc33-117">Numer poprawki przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4cc33-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="4cc33-118">Ta wartość nie może być równa zero.</span><span class="sxs-lookup"><span data-stu-id="4cc33-118">This value cannot be zero.</span></span> <span data-ttu-id="4cc33-119">Jeśli wszystkie bity `usRevisionNumber` są ustawione, numer poprawki nie zostanie określony.</span><span class="sxs-lookup"><span data-stu-id="4cc33-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="4cc33-120">Lista nazw ustawień regionalnych zgodna ze specyfikacją RFC1766, oddzielona średnikami, określająca wartości lokalne obsługiwane przez przywoływany zestaw.</span><span class="sxs-lookup"><span data-stu-id="4cc33-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="4cc33-121">Wartość null wskazuje niezależność ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="4cc33-121">A null value indicates locale independence.</span></span> <span data-ttu-id="4cc33-122">**Uwaga:**  W .NET Framework w wersji 1,0 nie można określić więcej niż jednego ustawienia regionalnego.</span><span class="sxs-lookup"><span data-stu-id="4cc33-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="4cc33-123">Rozmiar w postaci znaków dwubajtowych `szLocale` .</span><span class="sxs-lookup"><span data-stu-id="4cc33-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="4cc33-124">Tablica identyfikatorów, zgodnie z definicją w Winnt. h, dla typów procesorów obsługiwanych przez przywoływany zestaw.</span><span class="sxs-lookup"><span data-stu-id="4cc33-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="4cc33-125">Wartość NULL wskazuje niezależność procesora.</span><span class="sxs-lookup"><span data-stu-id="4cc33-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="4cc33-126">Długość `rdwProcessor` tablicy.</span><span class="sxs-lookup"><span data-stu-id="4cc33-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="4cc33-127">Tablica wystąpień [OSINFO](osinfo-structure.md) określających systemy operacyjne, które są obsługiwane przez przywoływany zestaw.</span><span class="sxs-lookup"><span data-stu-id="4cc33-127">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="4cc33-128">Wartość NULL wskazuje niezależność systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4cc33-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="4cc33-129">Długość `rOS` tablicy.</span><span class="sxs-lookup"><span data-stu-id="4cc33-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4cc33-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4cc33-130">Requirements</span></span>  
 <span data-ttu-id="4cc33-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cc33-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cc33-132">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4cc33-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4cc33-133">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4cc33-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4cc33-134">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cc33-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc33-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cc33-135">See also</span></span>

- [<span data-ttu-id="4cc33-136">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="4cc33-136">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="4cc33-137">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4cc33-137">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="4cc33-138">OSINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="4cc33-138">OSINFO Structure</span></span>](osinfo-structure.md)
