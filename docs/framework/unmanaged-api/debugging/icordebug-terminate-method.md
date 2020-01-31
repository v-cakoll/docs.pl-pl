---
title: ICorDebug::Terminate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 2d3f8360a1fb1164fd4e26f85246251409bee376
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788959"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="16932-102">ICorDebug::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="16932-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="16932-103">Kończy działanie obiektu `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="16932-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16932-104">nie należy wywoływać `Terminate` do momentu odebrania wywołania zwrotnego [ICorDebugManagedCallback:: ExitProcess —](icordebugmanagedcallback-exitprocess-method.md) dla wszystkich debugowanych procesów.</span><span class="sxs-lookup"><span data-stu-id="16932-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16932-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="16932-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="16932-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16932-106">Remarks</span></span>  
 <span data-ttu-id="16932-107">należy wywołać `Terminate`, jeśli obiekt `ICorDebug` nie jest już wymagany.</span><span class="sxs-lookup"><span data-stu-id="16932-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16932-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16932-108">Requirements</span></span>  
 <span data-ttu-id="16932-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16932-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16932-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16932-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16932-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="16932-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16932-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16932-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16932-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16932-113">See also</span></span>

- [<span data-ttu-id="16932-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="16932-114">ICorDebug Interface</span></span>](icordebug-interface.md)
