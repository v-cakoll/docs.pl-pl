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
ms.openlocfilehash: f101fe2a84a26efb23f57bac3aaf4f0e64a4d36c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740033"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="b6775-102">CorDebugGCType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b6775-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="b6775-103">Wskazuje, czy moduł garbage collector jest uruchomiona na serwerze lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="b6775-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6775-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6775-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6775-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6775-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="b6775-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b6775-106">Members</span></span>  
  
|<span data-ttu-id="b6775-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="b6775-107">Member name</span></span>|<span data-ttu-id="b6775-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b6775-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="b6775-109">Moduł garbage collector jest uruchomiona na stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="b6775-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="b6775-110">Moduł garbage collector jest uruchomiona na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b6775-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6775-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6775-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6775-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6775-112">Requirements</span></span>  
 <span data-ttu-id="b6775-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6775-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6775-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6775-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6775-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6775-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6775-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6775-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6775-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6775-117">See also</span></span>

- [<span data-ttu-id="b6775-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b6775-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
