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
ms.openlocfilehash: 8d0e7f20be3f18e49dcc1b986460d5da0c3d7777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401943"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="3d4f9-102">ICorDebugCode::GetFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d4f9-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="3d4f9-103">Pobiera skojarzone z tym "ICorDebugCode" "ICorDebugFunction".</span><span class="sxs-lookup"><span data-stu-id="3d4f9-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d4f9-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d4f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d4f9-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="3d4f9-106">[out] Wskaźnik do adresu funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d4f9-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d4f9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d4f9-107">Remarks</span></span>  
 <span data-ttu-id="3d4f9-108">`ICorDebugCode` i `ICorDebugFunction` Obsługa relacją.</span><span class="sxs-lookup"><span data-stu-id="3d4f9-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d4f9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d4f9-109">Requirements</span></span>  
 <span data-ttu-id="3d4f9-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d4f9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d4f9-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d4f9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d4f9-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d4f9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d4f9-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d4f9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4f9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d4f9-114">See Also</span></span>  
 
