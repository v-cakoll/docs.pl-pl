---
title: ICorDebugThreadEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b7e5b0a9f4166923a559eb3886aa0f9cabbcd72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962949"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="29419-102">ICorDebugThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="29419-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="29419-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="29419-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29419-104">Metody</span><span class="sxs-lookup"><span data-stu-id="29419-104">Methods</span></span>  
  
|<span data-ttu-id="29419-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="29419-105">Method</span></span>|<span data-ttu-id="29419-106">Opis</span><span class="sxs-lookup"><span data-stu-id="29419-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29419-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="29419-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="29419-108">Pobiera określoną liczbę `ICorDebugThread` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="29419-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29419-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29419-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29419-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="29419-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29419-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29419-111">Requirements</span></span>  
 <span data-ttu-id="29419-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29419-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29419-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29419-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29419-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29419-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29419-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29419-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29419-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29419-116">See also</span></span>

- [<span data-ttu-id="29419-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="29419-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
