---
title: ICorDebugAssembly2::IsFullyTrusted — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: bef51fe9df0f85659603c637f11ed4e856c8e01a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133951"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="ed18d-102">ICorDebugAssembly2::IsFullyTrusted — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed18d-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="ed18d-103">Pobiera wartość wskazującą, czy zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ed18d-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed18d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed18d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed18d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed18d-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="ed18d-106">[out] `true`, jeśli zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ed18d-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed18d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed18d-107">Remarks</span></span>  
 <span data-ttu-id="ed18d-108">Ta metoda zwraca wartość HRESULT elementu CORDBG_E_NOTREADY, jeśli zasady zabezpieczeń dla zestawu nie zostały jeszcze rozwiązane, czyli jeśli żaden kod w zestawie nie został jeszcze uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="ed18d-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed18d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed18d-109">Requirements</span></span>  
 <span data-ttu-id="ed18d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed18d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed18d-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed18d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed18d-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed18d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed18d-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed18d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
