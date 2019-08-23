---
title: ICorDebugFrameEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9ea398c32762be31f93002533b15bcf3851b870
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910243"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="b44f7-102">ICorDebugFrameEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b44f7-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="b44f7-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="b44f7-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b44f7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b44f7-104">Methods</span></span>  
  
|<span data-ttu-id="b44f7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b44f7-105">Method</span></span>|<span data-ttu-id="b44f7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b44f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b44f7-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="b44f7-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="b44f7-108">Pobiera określoną liczbę `ICorDebugFrame` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="b44f7-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b44f7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b44f7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b44f7-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b44f7-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b44f7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b44f7-111">Requirements</span></span>  
 <span data-ttu-id="b44f7-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b44f7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b44f7-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b44f7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b44f7-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b44f7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b44f7-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b44f7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44f7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b44f7-116">See also</span></span>

- [<span data-ttu-id="b44f7-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b44f7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
