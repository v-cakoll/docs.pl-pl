---
title: "ICorDebugAssembly2::IsFullyTrusted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly2.IsFullyTrusted
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d155a12a8b281e427f00706cbc6e10a80804c7c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="9c492-102">ICorDebugAssembly2::IsFullyTrusted — Metoda</span><span class="sxs-lookup"><span data-stu-id="9c492-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="9c492-103">Pobiera wartość wskazującą, czy zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="9c492-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c492-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c492-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c492-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c492-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="9c492-106">[out] `true` Jeśli zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="9c492-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c492-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c492-107">Remarks</span></span>  
 <span data-ttu-id="9c492-108">Ta metoda zwraca wartość HRESULT z CORDBG_E_NOTREADY Jeśli zasady zabezpieczeń dla zestawu nie została jeszcze rozwiązane, oznacza to, jeśli żaden kod w zestawie zostało jeszcze uruchomione.</span><span class="sxs-lookup"><span data-stu-id="9c492-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c492-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c492-109">Requirements</span></span>  
 <span data-ttu-id="9c492-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c492-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c492-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c492-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c492-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c492-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c492-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c492-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
