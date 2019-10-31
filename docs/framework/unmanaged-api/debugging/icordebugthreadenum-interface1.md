---
title: ICorDebugThreadEnum — Interfejs
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
ms.openlocfilehash: 6969c23bcf3ea19bf6e404996d477f669f0eee5b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122405"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="c77d4-102">ICorDebugThreadEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c77d4-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="c77d4-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c77d4-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c77d4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c77d4-104">Methods</span></span>  
  
|<span data-ttu-id="c77d4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c77d4-105">Method</span></span>|<span data-ttu-id="c77d4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c77d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c77d4-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="c77d4-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="c77d4-108">Pobiera określoną liczbę wystąpień `ICorDebugThread` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="c77d4-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c77d4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c77d4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c77d4-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="c77d4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c77d4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c77d4-111">Requirements</span></span>  
 <span data-ttu-id="c77d4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c77d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c77d4-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c77d4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c77d4-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c77d4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c77d4-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c77d4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c77d4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c77d4-116">See also</span></span>

- [<span data-ttu-id="c77d4-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c77d4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
