---
title: "OSINFO — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd30fe7904fa6c0685dd9c39931cc545e4e30583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="osinfo-structure"></a><span data-ttu-id="5340b-102">OSINFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="5340b-102">OSINFO Structure</span></span>
<span data-ttu-id="5340b-103">Zawiera szczegółowe informacje dotyczące systemu operacyjnego dla zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="5340b-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5340b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5340b-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="5340b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5340b-105">Members</span></span>  
  
|<span data-ttu-id="5340b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5340b-106">Member</span></span>|<span data-ttu-id="5340b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5340b-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="5340b-108">Jedna z wartości identyfikator zdefiniowany przez funkcję platform Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="5340b-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="5340b-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="5340b-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="5340b-110">-VER_PLATFORM_WIN32s, lub 0x0000, aby określić Microsoft Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="5340b-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="5340b-111">-VER_PLATFORM_WIN32_WINDOWS, lub 0x0001, aby określić Windows 95, Windows 98 lub systemów operacyjnych podrzędne w stosunku do nich.</span><span class="sxs-lookup"><span data-stu-id="5340b-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="5340b-112">-VER_PLATFORM_WIN32_NT, lub 0x0010, do określenia systemu Windows NT lub podrzędne w stosunku do jego systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="5340b-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="5340b-113">Wersja główna systemu operacyjnego, lub wartość NULL, aby wskazać dowolnej wersji.</span><span class="sxs-lookup"><span data-stu-id="5340b-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="5340b-114">Wersja pomocnicza systemu operacyjnego, lub wartość NULL, aby wskazać dowolnej wersji.</span><span class="sxs-lookup"><span data-stu-id="5340b-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5340b-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5340b-115">Remarks</span></span>  
 <span data-ttu-id="5340b-116">`OSINFO`jest oparta na `OSVERSIONINFOEX` struktury który jest używany w wywołań funkcji platform Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="5340b-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="5340b-117">Ta struktura jest używany przez assemblymetadata — struktura w celu wskazania jego obsługę systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5340b-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5340b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5340b-118">Requirements</span></span>  
 <span data-ttu-id="5340b-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5340b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5340b-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5340b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5340b-121">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5340b-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5340b-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5340b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5340b-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5340b-123">See Also</span></span>  
 [<span data-ttu-id="5340b-124">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="5340b-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="5340b-125">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="5340b-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
