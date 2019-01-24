---
title: CorDebugCreateProcessFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83cee30ed9831accb96de17768f63e7f401908f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495961"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="fc2c7-102">CorDebugCreateProcessFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fc2c7-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="fc2c7-103">Zapewnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [icordebug::CreateProcess —](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fc2c7-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc2c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc2c7-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fc2c7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fc2c7-105">Members</span></span>  
  
|<span data-ttu-id="fc2c7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fc2c7-106">Member</span></span>|<span data-ttu-id="fc2c7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fc2c7-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="fc2c7-108">Brak opcji specjalne są ustawione.</span><span class="sxs-lookup"><span data-stu-id="fc2c7-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc2c7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc2c7-109">Requirements</span></span>  
 <span data-ttu-id="fc2c7-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc2c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc2c7-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc2c7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc2c7-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc2c7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc2c7-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc2c7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2c7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc2c7-114">See also</span></span>
- [<span data-ttu-id="fc2c7-115">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fc2c7-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
