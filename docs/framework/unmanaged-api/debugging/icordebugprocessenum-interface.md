---
title: ICorDebugProcessEnum — Interfejs
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
ms.openlocfilehash: 9f5406c35915e447831d233804413034a429e8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139775"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="39c42-102">ICorDebugProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="39c42-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="39c42-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="39c42-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39c42-104">Metody</span><span class="sxs-lookup"><span data-stu-id="39c42-104">Methods</span></span>  
  
|<span data-ttu-id="39c42-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="39c42-105">Method</span></span>|<span data-ttu-id="39c42-106">Opis</span><span class="sxs-lookup"><span data-stu-id="39c42-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39c42-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="39c42-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-next-method.md)|<span data-ttu-id="39c42-108">Pobiera określoną liczbę wystąpień `ICorDebugProcess` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="39c42-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39c42-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39c42-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39c42-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="39c42-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c42-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39c42-111">Requirements</span></span>  
 <span data-ttu-id="39c42-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39c42-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39c42-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39c42-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39c42-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="39c42-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39c42-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39c42-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c42-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39c42-116">See also</span></span>

- [<span data-ttu-id="39c42-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="39c42-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
