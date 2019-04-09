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
ms.openlocfilehash: 0104a52c3aa206f86daff30d9d16298e6beae324
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099459"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="bf5fb-102">ICorDebugCode::GetFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf5fb-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="bf5fb-103">Pobiera skojarzone z tym "ICorDebugCode" "ICorDebugFunction".</span><span class="sxs-lookup"><span data-stu-id="bf5fb-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf5fb-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf5fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf5fb-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="bf5fb-106">[out] Wskaźnik do adresu funkcji.</span><span class="sxs-lookup"><span data-stu-id="bf5fb-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf5fb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf5fb-107">Remarks</span></span>  
 `ICorDebugCode` <span data-ttu-id="bf5fb-108">i `ICorDebugFunction` Obsługa relacja jeden do jednego.</span><span class="sxs-lookup"><span data-stu-id="bf5fb-108">and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5fb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf5fb-109">Requirements</span></span>  
 <span data-ttu-id="bf5fb-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf5fb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf5fb-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf5fb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf5fb-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf5fb-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bf5fb-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bf5fb-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bf5fb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf5fb-114">See also</span></span>
