---
title: CorDebugGCType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 315d6dd522f3c6be2d36b1eb411d9f471350df60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182926"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="70c7d-102">CorDebugGCType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="70c7d-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="70c7d-103">Wskazuje, czy moduł garbage collector jest uruchomiona na serwerze lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="70c7d-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c7d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70c7d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="70c7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70c7d-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="70c7d-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="70c7d-106">Members</span></span>  
  
|<span data-ttu-id="70c7d-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="70c7d-107">Member name</span></span>|<span data-ttu-id="70c7d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="70c7d-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="70c7d-109">Moduł garbage collector jest uruchomiona na stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="70c7d-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="70c7d-110">Moduł garbage collector jest uruchomiona na serwerze.</span><span class="sxs-lookup"><span data-stu-id="70c7d-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70c7d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70c7d-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70c7d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70c7d-112">Requirements</span></span>  
 <span data-ttu-id="70c7d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70c7d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70c7d-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70c7d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70c7d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70c7d-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="70c7d-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="70c7d-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70c7d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70c7d-117">See also</span></span>

- [<span data-ttu-id="70c7d-118">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="70c7d-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
