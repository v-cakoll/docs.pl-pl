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
ms.openlocfilehash: 825840536968562a53d9e05b8a4628a1df79407d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700836"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="f394d-102">ICorDebugCode::GetFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="f394d-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="f394d-103">Pobiera wartość "ICorDebugFunction" skojarzoną z tym "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="f394d-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f394d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f394d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f394d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f394d-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="f394d-106">określoną Wskaźnik do adresu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f394d-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f394d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f394d-107">Remarks</span></span>  
 <span data-ttu-id="f394d-108">`ICorDebugCode` i `ICorDebugFunction` zachowują relację jeden do jednego.</span><span class="sxs-lookup"><span data-stu-id="f394d-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f394d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f394d-109">Requirements</span></span>  
 <span data-ttu-id="f394d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f394d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f394d-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f394d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f394d-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f394d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f394d-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f394d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
