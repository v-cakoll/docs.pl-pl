---
title: ICorDebugProcessEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81653c69353b60d7287240505f53b26552c21774
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960993"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="85539-102">ICorDebugProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="85539-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="85539-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="85539-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85539-104">Metody</span><span class="sxs-lookup"><span data-stu-id="85539-104">Methods</span></span>  
  
|<span data-ttu-id="85539-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="85539-105">Method</span></span>|<span data-ttu-id="85539-106">Opis</span><span class="sxs-lookup"><span data-stu-id="85539-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85539-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="85539-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-next-method.md)|<span data-ttu-id="85539-108">Pobiera określoną liczbę `ICorDebugProcess` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="85539-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85539-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85539-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85539-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="85539-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85539-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85539-111">Requirements</span></span>  
 <span data-ttu-id="85539-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85539-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85539-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85539-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85539-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85539-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85539-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85539-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85539-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85539-116">See also</span></span>

- [<span data-ttu-id="85539-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="85539-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
