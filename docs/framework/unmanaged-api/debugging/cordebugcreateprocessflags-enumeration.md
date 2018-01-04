---
title: "CorDebugCreateProcessFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCreateProcessFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugCreateProcessFlags
helpviewer_keywords: CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e35aa2656a1e950cead94480eb06cde96e4c811
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="b76b9-102">CorDebugCreateProcessFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b76b9-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="b76b9-103">Udostępnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b76b9-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b76b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b76b9-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b76b9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b76b9-105">Members</span></span>  
  
|<span data-ttu-id="b76b9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b76b9-106">Member</span></span>|<span data-ttu-id="b76b9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b76b9-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="b76b9-108">Nie specjalne opcje można ustawić.</span><span class="sxs-lookup"><span data-stu-id="b76b9-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b76b9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b76b9-109">Requirements</span></span>  
 <span data-ttu-id="b76b9-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b76b9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b76b9-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b76b9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b76b9-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b76b9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b76b9-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b76b9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b76b9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b76b9-114">See Also</span></span>  
 [<span data-ttu-id="b76b9-115">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b76b9-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
