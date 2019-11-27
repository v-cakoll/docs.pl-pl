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
ms.openlocfilehash: 89111bf7eb03d20c2010c7a20c4cd055c2a021e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430733"
---
# <a name="osinfo-structure"></a><span data-ttu-id="f3c60-102">OSINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="f3c60-102">OSINFO Structure</span></span>
<span data-ttu-id="f3c60-103">Zawiera szczegółowe informacje o systemie operacyjnym dla zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="f3c60-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3c60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3c60-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f3c60-105">Members</span><span class="sxs-lookup"><span data-stu-id="f3c60-105">Members</span></span>  
  
|<span data-ttu-id="f3c60-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f3c60-106">Member</span></span>|<span data-ttu-id="f3c60-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f3c60-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="f3c60-108">Jedna z wartości identyfikatora zdefiniowanych przez funkcję platformy Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="f3c60-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="f3c60-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="f3c60-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="f3c60-110">-VER_PLATFORM_WIN32s lub 0x0000, aby określić system Microsoft Windows 3,1.</span><span class="sxs-lookup"><span data-stu-id="f3c60-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="f3c60-111">-VER_PLATFORM_WIN32_WINDOWS lub 0x0001, aby określić z nich systemy Windows 95, Windows 98 lub systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f3c60-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="f3c60-112">-VER_PLATFORM_WIN32_NT lub 0x0010, aby określić system Windows NT lub systemy operacyjne, które są od niego podrzędne.</span><span class="sxs-lookup"><span data-stu-id="f3c60-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="f3c60-113">Wersja główna systemu operacyjnego lub wartość zerowa wskazująca dowolną wersję.</span><span class="sxs-lookup"><span data-stu-id="f3c60-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="f3c60-114">Wersja pomocnicza systemu operacyjnego lub wartość zerowa wskazująca dowolną wersję.</span><span class="sxs-lookup"><span data-stu-id="f3c60-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3c60-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3c60-115">Remarks</span></span>  
 <span data-ttu-id="f3c60-116">`OSINFO` jest oparty na strukturze `OSVERSIONINFOEX`, która jest używana w wywołaniach funkcji platformy Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="f3c60-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="f3c60-117">Ta struktura jest używana przez strukturę ASSEMBLYMETADATA, aby wskazać jej obsługę systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f3c60-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3c60-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3c60-118">Requirements</span></span>  
 <span data-ttu-id="f3c60-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3c60-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3c60-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3c60-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3c60-121">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3c60-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3c60-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3c60-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c60-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3c60-123">See also</span></span>

- [<span data-ttu-id="f3c60-124">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="f3c60-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="f3c60-125">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3c60-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
