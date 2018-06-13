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
ms.openlocfilehash: c7d280cd20b8ff76efe977983e3e9f6da32990c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413962"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="273b8-102">ICorDebugEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="273b8-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="273b8-103">Przesuwa kursor do przodu w wyliczeniu określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="273b8-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="273b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="273b8-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="273b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="273b8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="273b8-106">[in] Liczba elementów, o którą należy przesunąć kursor do przodu.</span><span class="sxs-lookup"><span data-stu-id="273b8-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="273b8-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="273b8-107">Requirements</span></span>  
 <span data-ttu-id="273b8-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="273b8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="273b8-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="273b8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="273b8-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="273b8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="273b8-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="273b8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273b8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="273b8-112">See Also</span></span>  
 [<span data-ttu-id="273b8-113">ICorDebugEnum, interfejs1</span><span class="sxs-lookup"><span data-stu-id="273b8-113">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
