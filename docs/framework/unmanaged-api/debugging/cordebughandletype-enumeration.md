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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651733"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="ee047-102">CorDebugHandleType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ee047-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="ee047-103">Wskazuje typ uchwytu.</span><span class="sxs-lookup"><span data-stu-id="ee047-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee047-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee047-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="ee047-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ee047-105">Members</span></span>  
  
|<span data-ttu-id="ee047-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ee047-106">Member</span></span>|<span data-ttu-id="ee047-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ee047-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="ee047-108">Dojście jest silna, który uniemożliwia są odzyskiwane przez wyrzucanie elementów bezużytecznych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="ee047-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="ee047-109">Dojście jest słaby, której nie uniemożliwia obiektu są odzyskiwane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ee047-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="ee047-110">Dojście staje się nieprawidłowy, gdy obiekt są zbierane.</span><span class="sxs-lookup"><span data-stu-id="ee047-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee047-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee047-111">Requirements</span></span>  
 <span data-ttu-id="ee047-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee047-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee047-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee047-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee047-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee047-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee047-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee047-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee047-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee047-116">See also</span></span>

- [<span data-ttu-id="ee047-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ee047-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
