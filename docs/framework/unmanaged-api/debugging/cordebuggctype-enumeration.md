---
title: "CorDebugGCType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugGCType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGCType
helpviewer_keywords: CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 14d6f28c2e5fa356c7f406ffb4c2787f0ace500a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="3adff-102">CorDebugGCType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3adff-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="3adff-103">Wskazuje, czy moduł zbierający elementy bezużyteczne jest uruchomiona na serwerze lub stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="3adff-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3adff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3adff-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3adff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3adff-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="3adff-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3adff-106">Members</span></span>  
  
|<span data-ttu-id="3adff-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="3adff-107">Member name</span></span>|<span data-ttu-id="3adff-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3adff-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="3adff-109">Moduł zbierający elementy bezużyteczne działa na stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="3adff-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="3adff-110">Moduł zbierający elementy bezużyteczne jest uruchomiona na serwerze.</span><span class="sxs-lookup"><span data-stu-id="3adff-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3adff-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3adff-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3adff-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3adff-112">Requirements</span></span>  
 <span data-ttu-id="3adff-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3adff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3adff-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3adff-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3adff-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3adff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3adff-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3adff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3adff-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3adff-117">See Also</span></span>  
 [<span data-ttu-id="3adff-118">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3adff-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
