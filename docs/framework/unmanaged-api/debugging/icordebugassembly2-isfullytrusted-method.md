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
ms.openlocfilehash: dd82709064fe7f7d912d93f4b3f0248769f02b9e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894888"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="87758-102">ICorDebugAssembly2::IsFullyTrusted — Metoda</span><span class="sxs-lookup"><span data-stu-id="87758-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="87758-103">Pobiera wartość wskazującą, czy zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="87758-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87758-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87758-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87758-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87758-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="87758-106">określoną `true` Jeśli zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego; w przeciwnym `false`razie.</span><span class="sxs-lookup"><span data-stu-id="87758-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87758-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87758-107">Remarks</span></span>  
 <span data-ttu-id="87758-108">Ta metoda zwraca wartość HRESULT CORDBG_E_NOTREADY, jeśli zasady zabezpieczeń dla zestawu nie zostały jeszcze rozwiązane, czyli jeśli żaden kod w zestawie nie został jeszcze uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="87758-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87758-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87758-109">Requirements</span></span>  
 <span data-ttu-id="87758-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87758-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87758-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87758-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87758-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="87758-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87758-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87758-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
