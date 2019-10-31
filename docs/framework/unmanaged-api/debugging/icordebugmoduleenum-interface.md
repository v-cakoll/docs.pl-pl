---
title: ICorDebugModuleEnum — Interfejs
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
ms.openlocfilehash: eaf00369cf77aaa1ba16879bae1b74aba2eb9eab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123539"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="e7408-102">ICorDebugModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e7408-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="e7408-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="e7408-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7408-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e7408-104">Methods</span></span>  
  
|<span data-ttu-id="e7408-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e7408-105">Method</span></span>|<span data-ttu-id="e7408-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e7408-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7408-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="e7408-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="e7408-108">Pobiera określoną liczbę wystąpień `ICorDebugModule` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="e7408-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7408-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7408-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7408-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e7408-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7408-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7408-111">Requirements</span></span>  
 <span data-ttu-id="e7408-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7408-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7408-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e7408-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7408-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e7408-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7408-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7408-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7408-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7408-116">See also</span></span>

- [<span data-ttu-id="e7408-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e7408-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
