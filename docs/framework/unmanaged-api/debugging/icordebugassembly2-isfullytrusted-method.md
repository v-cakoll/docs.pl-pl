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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 895c8bc7b550fd063a9215c60f10f183e24bac83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="2ef93-102">ICorDebugAssembly2::IsFullyTrusted — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ef93-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="2ef93-103">Pobiera wartość wskazującą, czy zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="2ef93-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ef93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ef93-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ef93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ef93-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="2ef93-106">[out] `true` Jeśli zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="2ef93-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ef93-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ef93-107">Remarks</span></span>  
 <span data-ttu-id="2ef93-108">Ta metoda zwraca wartość HRESULT z CORDBG_E_NOTREADY Jeśli zasady zabezpieczeń dla zestawu nie została jeszcze rozwiązane, oznacza to, jeśli żaden kod w zestawie zostało jeszcze uruchomione.</span><span class="sxs-lookup"><span data-stu-id="2ef93-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ef93-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ef93-109">Requirements</span></span>  
 <span data-ttu-id="2ef93-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ef93-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ef93-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ef93-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ef93-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ef93-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ef93-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ef93-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
