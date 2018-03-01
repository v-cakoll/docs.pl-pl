---
title: "ICorDebugModule2::ResolveAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e72d2ed69c8d189adb4980c82e07ad71892dc56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="36849-102">ICorDebugModule2::ResolveAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="36849-102">ICorDebugModule2::ResolveAssembly Method</span></span>
<span data-ttu-id="36849-103">Usuwa zestaw odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="36849-103">Resolves the assembly referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36849-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36849-104">Syntax</span></span>  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36849-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36849-105">Parameters</span></span>  
 `tkAsemblyRef`  
 <span data-ttu-id="36849-106">[in] `mdToken` Wartość, która odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="36849-106">[in] An `mdToken` value that references the assembly.</span></span>  
  
 `ppAssembly`  
 <span data-ttu-id="36849-107">[out] Wskaźnik do adresu ICorDebugAssembly obiekt, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="36849-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36849-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36849-108">Remarks</span></span>  
 <span data-ttu-id="36849-109">Jeśli zestaw nie jest już załadowany podczas `ResolveAssembly` jest nazywany HRESULT zostanie zwrócona wartość CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="36849-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36849-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36849-110">Requirements</span></span>  
 <span data-ttu-id="36849-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36849-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36849-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36849-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36849-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36849-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36849-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36849-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
