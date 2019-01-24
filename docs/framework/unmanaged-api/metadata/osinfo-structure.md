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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abab67f28a5fabfc6c348af6b8b502b46510d460
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548758"
---
# <a name="osinfo-structure"></a><span data-ttu-id="afb4e-102">OSINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="afb4e-102">OSINFO Structure</span></span>
<span data-ttu-id="afb4e-103">Zawiera szczegóły dotyczące systemu operacyjnego dla zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="afb4e-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afb4e-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="afb4e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="afb4e-105">Members</span></span>  
  
|<span data-ttu-id="afb4e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="afb4e-106">Member</span></span>|<span data-ttu-id="afb4e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="afb4e-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="afb4e-108">Jedna z wartości identyfikatora zdefiniowane przez funkcję platformy Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="afb4e-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="afb4e-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="afb4e-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="afb4e-110">-VER_PLATFORM_WIN32s, lub 0x0000, aby określić systemu Microsoft Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="afb4e-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="afb4e-111">-VER_PLATFORM_WIN32_WINDOWS, lub 0x0001, aby określić Windows 95, Windows 98 lub systemy operacyjne, które wywodzi się z nimi.</span><span class="sxs-lookup"><span data-stu-id="afb4e-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="afb4e-112">-VER_PLATFORM_WIN32_NT, lub 0x0010, aby określić Windows NT lub systemy operacyjne, które wywodzi się z niego.</span><span class="sxs-lookup"><span data-stu-id="afb4e-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="afb4e-113">Wersja główna systemu operacyjnego, lub wartość NULL, aby wskazać dowolną wersję.</span><span class="sxs-lookup"><span data-stu-id="afb4e-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="afb4e-114">Wersja pomocnicza systemu operacyjnego, lub wartość NULL, aby wskazać dowolną wersję.</span><span class="sxs-lookup"><span data-stu-id="afb4e-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afb4e-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afb4e-115">Remarks</span></span>  
 <span data-ttu-id="afb4e-116">`OSINFO` opiera się na `OSVERSIONINFOEX` struktury, to znaczy, używane wywołania funkcji platformy Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="afb4e-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="afb4e-117">Ta struktura jest używany przez assemblymetadata — struktura w celu wskazania, jego obsługa systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="afb4e-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb4e-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afb4e-118">Requirements</span></span>  
 <span data-ttu-id="afb4e-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb4e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb4e-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="afb4e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afb4e-121">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afb4e-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="afb4e-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb4e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb4e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afb4e-123">See also</span></span>
- [<span data-ttu-id="afb4e-124">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="afb4e-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="afb4e-125">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="afb4e-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
