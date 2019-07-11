---
title: ICorDebugCode::GetFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10ab92c660353bea85bbd0918a25f716898ef837
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747535"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="5929d-102">ICorDebugCode::GetFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="5929d-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="5929d-103">Pobiera skojarzone z tym "ICorDebugCode" "ICorDebugFunction".</span><span class="sxs-lookup"><span data-stu-id="5929d-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5929d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5929d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5929d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5929d-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="5929d-106">[out] Wskaźnik do adresu funkcji.</span><span class="sxs-lookup"><span data-stu-id="5929d-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5929d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5929d-107">Remarks</span></span>  
 <span data-ttu-id="5929d-108">`ICorDebugCode` i `ICorDebugFunction` Obsługa relacja jeden do jednego.</span><span class="sxs-lookup"><span data-stu-id="5929d-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5929d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5929d-109">Requirements</span></span>  
 <span data-ttu-id="5929d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5929d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5929d-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5929d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5929d-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5929d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5929d-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5929d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5929d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5929d-114">See also</span></span>
