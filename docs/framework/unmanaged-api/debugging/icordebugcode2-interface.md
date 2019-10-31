---
title: ICorDebugCode2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
ms.openlocfilehash: 7f0570b668cc33ca509c8522d1ba35ebcfca2453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125574"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="6306d-102">ICorDebugCode2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6306d-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="6306d-103">Dostarcza metody, które zwiększają możliwości programu "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="6306d-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6306d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6306d-104">Methods</span></span>  
  
|<span data-ttu-id="6306d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6306d-105">Method</span></span>|<span data-ttu-id="6306d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6306d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6306d-107">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="6306d-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="6306d-108">Pobiera fragmenty kodu, z których składa się ten obiekt kodu.</span><span class="sxs-lookup"><span data-stu-id="6306d-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="6306d-109">GetCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="6306d-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="6306d-110">Pobiera flagi określające warunki, w których ten obiekt kodu był skompilowany lub generowany przy użyciu natywnego generatora obrazu (Ngen. exe).</span><span class="sxs-lookup"><span data-stu-id="6306d-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6306d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6306d-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6306d-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6306d-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6306d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6306d-113">Requirements</span></span>  
 <span data-ttu-id="6306d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6306d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6306d-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6306d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6306d-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6306d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6306d-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6306d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6306d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6306d-118">See also</span></span>

- [<span data-ttu-id="6306d-119">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="6306d-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="6306d-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6306d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
