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
ms.openlocfilehash: d231595ab2c7b41d1a24f654e9785b90b34ac780
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744504"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="7f88d-102">ICorDebugAssembly2::IsFullyTrusted — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f88d-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="7f88d-103">Pobiera wartość wskazującą, czy zestaw ma udzielone pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7f88d-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f88d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f88d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f88d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f88d-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="7f88d-106">[out] `true` Jeśli zestaw ma udzielone pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7f88d-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f88d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f88d-107">Remarks</span></span>  
 <span data-ttu-id="7f88d-108">Ta metoda zwraca wartość HRESULT z CORDBG_E_NOTREADY Jeśli zasady zabezpieczeń dla zestawu nie została jeszcze rozwiązane, oznacza to, jeśli żaden kod w zestawie ma jeszcze uruchomione.</span><span class="sxs-lookup"><span data-stu-id="7f88d-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f88d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f88d-109">Requirements</span></span>  
 <span data-ttu-id="7f88d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f88d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f88d-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f88d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f88d-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f88d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f88d-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f88d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
