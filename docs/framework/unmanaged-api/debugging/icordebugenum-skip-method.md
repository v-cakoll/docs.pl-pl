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
ms.openlocfilehash: 64d9db09b3e604247ab6a26cdca9eca22adbaace
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976307"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="05e47-102">ICorDebugEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="05e47-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="05e47-103">Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="05e47-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05e47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05e47-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05e47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05e47-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="05e47-106">podczas Liczba elementów, przez którą ma zostać przesunięty kursor do przodu.</span><span class="sxs-lookup"><span data-stu-id="05e47-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05e47-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05e47-107">Requirements</span></span>  
 <span data-ttu-id="05e47-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05e47-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05e47-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05e47-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05e47-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05e47-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05e47-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05e47-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e47-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05e47-112">See also</span></span>

- [<span data-ttu-id="05e47-113">ICorDebugEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="05e47-113">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
