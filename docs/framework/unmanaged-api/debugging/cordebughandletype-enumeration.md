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
ms.openlocfilehash: 15572037940f7c45ec5dcb7e34599756e15fd3bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793909"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="ac1e5-102">CorDebugHandleType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ac1e5-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="ac1e5-103">Wskazuje typ dojścia.</span><span class="sxs-lookup"><span data-stu-id="ac1e5-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac1e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac1e5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="ac1e5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ac1e5-105">Members</span></span>  
  
|<span data-ttu-id="ac1e5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ac1e5-106">Member</span></span>|<span data-ttu-id="ac1e5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ac1e5-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="ac1e5-108">Dojście jest silnie, co uniemożliwia odjęcie obiektu przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ac1e5-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="ac1e5-109">Dojście jest słabe, co nie zapobiega odzyskiwaniu obiektu przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ac1e5-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="ac1e5-110">Uchwyt jest nieprawidłowy, gdy zbierany jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="ac1e5-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac1e5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac1e5-111">Requirements</span></span>  
 <span data-ttu-id="ac1e5-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac1e5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac1e5-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ac1e5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac1e5-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ac1e5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac1e5-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac1e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1e5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac1e5-116">See also</span></span>

- [<span data-ttu-id="ac1e5-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ac1e5-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
