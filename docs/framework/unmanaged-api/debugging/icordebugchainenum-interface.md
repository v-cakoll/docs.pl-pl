---
title: ICorDebugChainEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum
helpviewer_keywords:
- ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6639335c-48e1-4e74-a4f3-70a6a0f54af1
topic_type:
- apiref
ms.openlocfilehash: 63588a3d33577ff58c99e796e8e5453d2a6a9381
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123812"
---
# <a name="icordebugchainenum-interface"></a><span data-ttu-id="cd97e-102">ICorDebugChainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd97e-102">ICorDebugChainEnum Interface</span></span>

<span data-ttu-id="cd97e-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugChain.</span><span class="sxs-lookup"><span data-stu-id="cd97e-103">Implements ICorDebugEnum methods, and enumerates ICorDebugChain arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd97e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cd97e-104">Methods</span></span>  
  
|<span data-ttu-id="cd97e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cd97e-105">Method</span></span>|<span data-ttu-id="cd97e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cd97e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd97e-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="cd97e-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-next-method.md)|<span data-ttu-id="cd97e-108">Pobiera określoną liczbę wystąpień `ICorDebugChain` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="cd97e-108">Gets the specified number of `ICorDebugChain` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd97e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd97e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd97e-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="cd97e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd97e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd97e-111">Requirements</span></span>  
 <span data-ttu-id="cd97e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd97e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd97e-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cd97e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd97e-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cd97e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd97e-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd97e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd97e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd97e-116">See also</span></span>

- [<span data-ttu-id="cd97e-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cd97e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
