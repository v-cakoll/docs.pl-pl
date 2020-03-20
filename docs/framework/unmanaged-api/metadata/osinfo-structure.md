---
title: OSINFO — Struktura
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175229"
---
# <a name="osinfo-structure"></a><span data-ttu-id="221be-102">OSINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="221be-102">OSINFO Structure</span></span>
<span data-ttu-id="221be-103">Zawiera szczegółowe informacje o systemie operacyjnym dla zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="221be-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="221be-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="221be-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="221be-105">Members</span></span>  
  
|<span data-ttu-id="221be-106">Członek</span><span class="sxs-lookup"><span data-stu-id="221be-106">Member</span></span>|<span data-ttu-id="221be-107">Opis</span><span class="sxs-lookup"><span data-stu-id="221be-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="221be-108">Jedna z wartości identyfikatorów zdefiniowanych przez `GetVersionEx`funkcję platformy Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="221be-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="221be-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="221be-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="221be-110">- VER_PLATFORM_WIN32s lub 0x0000, aby określić system Microsoft Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="221be-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="221be-111">- VER_PLATFORM_WIN32_WINDOWS lub 0x0001, aby określić Windows 95, Windows 98 lub systemów operacyjnych pochodzi od nich.</span><span class="sxs-lookup"><span data-stu-id="221be-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="221be-112">- VER_PLATFORM_WIN32_NT lub 0x0002, aby określić Windows NT lub systemów operacyjnych zstąpił od niego.</span><span class="sxs-lookup"><span data-stu-id="221be-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="221be-113">Wersja główna systemu operacyjnego lub wartość NULL wskazująca dowolną wersję.</span><span class="sxs-lookup"><span data-stu-id="221be-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="221be-114">Wersja pomocnicza systemu operacyjnego lub wartość NULL wskazująca dowolną wersję.</span><span class="sxs-lookup"><span data-stu-id="221be-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="221be-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="221be-115">Remarks</span></span>  
 <span data-ttu-id="221be-116">`OSINFO`opiera się `OSVERSIONINFOEX` na strukturze używanej w wywołaniach `GetVersionEx`funkcji platformy Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="221be-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="221be-117">Ta struktura jest używana przez assemblymetadata struktury, aby wskazać jego obsługi systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="221be-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="221be-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="221be-118">Requirements</span></span>  
 <span data-ttu-id="221be-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="221be-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="221be-120">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="221be-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="221be-121">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="221be-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="221be-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="221be-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221be-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="221be-123">See also</span></span>

- [<span data-ttu-id="221be-124">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="221be-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="221be-125">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="221be-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
