---
title: COR_PUB_ENUMPROCESS — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02ff60852a85d003deb68cae96a184ac8d61c65f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089415"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="2d3d4-102">COR_PUB_ENUMPROCESS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2d3d4-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="2d3d4-103">Identyfikuje typ procesu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2d3d4-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d3d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d3d4-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="2d3d4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2d3d4-105">Members</span></span>  
  
|<span data-ttu-id="2d3d4-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="2d3d4-106">Member name</span></span>|<span data-ttu-id="2d3d4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2d3d4-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="2d3d4-108">Proces zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2d3d4-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d3d4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d3d4-109">Remarks</span></span>  
 <span data-ttu-id="2d3d4-110">Bieżąca wersja interfejsu API debugowania niezarządzanego wylicza tylko zarządzanych procesów.</span><span class="sxs-lookup"><span data-stu-id="2d3d4-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d3d4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d3d4-111">Requirements</span></span>  
 <span data-ttu-id="2d3d4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d3d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d3d4-113">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2d3d4-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2d3d4-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d3d4-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2d3d4-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2d3d4-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d3d4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d3d4-116">See also</span></span>

- [<span data-ttu-id="2d3d4-117">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2d3d4-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
