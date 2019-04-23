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
ms.openlocfilehash: ae3ba480e208762f5a80f9f1b78dd008f02b6df4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089385"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="7d860-102">CorDebugCreateProcessFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7d860-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="7d860-103">Zapewnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [icordebug::CreateProcess —](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7d860-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d860-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d860-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7d860-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7d860-105">Members</span></span>  
  
|<span data-ttu-id="7d860-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7d860-106">Member</span></span>|<span data-ttu-id="7d860-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7d860-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="7d860-108">Brak opcji specjalne są ustawione.</span><span class="sxs-lookup"><span data-stu-id="7d860-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d860-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d860-109">Requirements</span></span>  
 <span data-ttu-id="7d860-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d860-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d860-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d860-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d860-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d860-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d860-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d860-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d860-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d860-114">See also</span></span>

- [<span data-ttu-id="7d860-115">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7d860-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
