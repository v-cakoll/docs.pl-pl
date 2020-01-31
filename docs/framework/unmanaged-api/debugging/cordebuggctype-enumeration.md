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
ms.openlocfilehash: 6f4c96517375df4cd249b72953bf37812a498c0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789364"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="462b4-102">CorDebugGCType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="462b4-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="462b4-103">Wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.</span><span class="sxs-lookup"><span data-stu-id="462b4-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="462b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="462b4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="462b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="462b4-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="462b4-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="462b4-106">Members</span></span>  
  
|<span data-ttu-id="462b4-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="462b4-107">Member name</span></span>|<span data-ttu-id="462b4-108">Opis</span><span class="sxs-lookup"><span data-stu-id="462b4-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="462b4-109">Moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="462b4-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="462b4-110">Moduł wyrzucania elementów bezużytecznych jest uruchomiony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="462b4-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="462b4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="462b4-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="462b4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="462b4-112">Requirements</span></span>  
 <span data-ttu-id="462b4-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="462b4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="462b4-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="462b4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="462b4-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="462b4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="462b4-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="462b4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462b4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="462b4-117">See also</span></span>

- [<span data-ttu-id="462b4-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="462b4-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
