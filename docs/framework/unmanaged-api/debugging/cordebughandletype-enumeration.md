---
title: CorDebugHandleType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 513fc93bdac71e2a3ba59ebb53fdde44f1659af5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220464"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="b5c31-102">CorDebugHandleType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b5c31-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="b5c31-103">Wskazuje typ uchwytu.</span><span class="sxs-lookup"><span data-stu-id="b5c31-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c31-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5c31-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="b5c31-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b5c31-105">Members</span></span>  
  
|<span data-ttu-id="b5c31-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b5c31-106">Member</span></span>|<span data-ttu-id="b5c31-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b5c31-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="b5c31-108">Dojście jest silna, który uniemożliwia są odzyskiwane przez wyrzucanie elementów bezużytecznych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="b5c31-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="b5c31-109">Dojście jest słaby, której nie uniemożliwia obiektu są odzyskiwane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b5c31-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="b5c31-110">Dojście staje się nieprawidłowy, gdy obiekt są zbierane.</span><span class="sxs-lookup"><span data-stu-id="b5c31-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5c31-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5c31-111">Requirements</span></span>  
 <span data-ttu-id="b5c31-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5c31-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5c31-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5c31-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5c31-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5c31-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b5c31-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b5c31-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5c31-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5c31-116">See also</span></span>

- [<span data-ttu-id="b5c31-117">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b5c31-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
