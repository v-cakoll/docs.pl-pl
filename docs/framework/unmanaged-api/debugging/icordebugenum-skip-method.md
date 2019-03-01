---
title: ICorDebugEnum::Skip — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb651aa394022182b6730d57942199f570508436
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965911"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="9c3b0-102">ICorDebugEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="9c3b0-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="9c3b0-103">Przesuwa kursor do przodu w wyliczeniu przez określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="9c3b0-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c3b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c3b0-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c3b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c3b0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9c3b0-106">[in] Liczba elementów, o którą należy przesunąć kursor do przodu.</span><span class="sxs-lookup"><span data-stu-id="9c3b0-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c3b0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c3b0-107">Requirements</span></span>  
 <span data-ttu-id="9c3b0-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c3b0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c3b0-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c3b0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c3b0-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c3b0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c3b0-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c3b0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c3b0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c3b0-112">See also</span></span>
- [<span data-ttu-id="9c3b0-113">Icordebugenum — interfejs</span><span class="sxs-lookup"><span data-stu-id="9c3b0-113">ICorDebugEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
