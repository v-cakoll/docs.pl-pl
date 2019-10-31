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
ms.openlocfilehash: d28f6eab5390194a4089cbbaf1f586c3f53a7db5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132255"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="b55eb-102">CorDebugCreateProcessFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b55eb-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="b55eb-103">Zapewnia dodatkowe opcje debugowania, których można użyć w wywołaniu metody [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b55eb-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b55eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b55eb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b55eb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b55eb-105">Members</span></span>  
  
|<span data-ttu-id="b55eb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b55eb-106">Member</span></span>|<span data-ttu-id="b55eb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b55eb-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="b55eb-108">Nie ustawiono żadnych specjalnych opcji.</span><span class="sxs-lookup"><span data-stu-id="b55eb-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b55eb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b55eb-109">Requirements</span></span>  
 <span data-ttu-id="b55eb-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b55eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b55eb-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b55eb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b55eb-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b55eb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b55eb-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b55eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b55eb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b55eb-114">See also</span></span>

- [<span data-ttu-id="b55eb-115">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b55eb-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
