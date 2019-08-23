---
title: ICorDebugModuleEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 682fe190126d4f40013678d996804e9f3481bc02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965081"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="23f02-102">ICorDebugModuleEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="23f02-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="23f02-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="23f02-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23f02-104">Metody</span><span class="sxs-lookup"><span data-stu-id="23f02-104">Methods</span></span>  
  
|<span data-ttu-id="23f02-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="23f02-105">Method</span></span>|<span data-ttu-id="23f02-106">Opis</span><span class="sxs-lookup"><span data-stu-id="23f02-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23f02-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="23f02-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="23f02-108">Pobiera określoną liczbę `ICorDebugModule` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="23f02-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23f02-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23f02-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23f02-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="23f02-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23f02-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23f02-111">Requirements</span></span>  
 <span data-ttu-id="23f02-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23f02-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f02-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23f02-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23f02-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23f02-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23f02-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f02-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f02-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23f02-116">See also</span></span>

- [<span data-ttu-id="23f02-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="23f02-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
