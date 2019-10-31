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
ms.openlocfilehash: 5a957a042875b546a18a17422f355b712756e91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098169"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="673b7-102">CorDebugHandleType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="673b7-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="673b7-103">Wskazuje typ dojścia.</span><span class="sxs-lookup"><span data-stu-id="673b7-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="673b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="673b7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="673b7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="673b7-105">Members</span></span>  
  
|<span data-ttu-id="673b7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="673b7-106">Member</span></span>|<span data-ttu-id="673b7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="673b7-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="673b7-108">Dojście jest silnie, co uniemożliwia odjęcie obiektu przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="673b7-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="673b7-109">Dojście jest słabe, co nie zapobiega odzyskiwaniu obiektu przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="673b7-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="673b7-110">Uchwyt jest nieprawidłowy, gdy zbierany jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="673b7-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="673b7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="673b7-111">Requirements</span></span>  
 <span data-ttu-id="673b7-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="673b7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="673b7-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="673b7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="673b7-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="673b7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="673b7-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="673b7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673b7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="673b7-116">See also</span></span>

- [<span data-ttu-id="673b7-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="673b7-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
