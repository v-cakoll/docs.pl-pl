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
ms.openlocfilehash: b954aa0e4db10fd4b3bde951c7f27d18b8634f5a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132183"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="33f97-102">CorDebugGCType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="33f97-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="33f97-103">Wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.</span><span class="sxs-lookup"><span data-stu-id="33f97-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33f97-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="33f97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33f97-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="33f97-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="33f97-106">Members</span></span>  
  
|<span data-ttu-id="33f97-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="33f97-107">Member name</span></span>|<span data-ttu-id="33f97-108">Opis</span><span class="sxs-lookup"><span data-stu-id="33f97-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="33f97-109">Moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="33f97-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="33f97-110">Moduł wyrzucania elementów bezużytecznych jest uruchomiony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="33f97-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33f97-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33f97-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f97-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33f97-112">Requirements</span></span>  
 <span data-ttu-id="33f97-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33f97-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33f97-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33f97-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33f97-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33f97-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33f97-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33f97-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f97-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33f97-117">See also</span></span>

- [<span data-ttu-id="33f97-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="33f97-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
