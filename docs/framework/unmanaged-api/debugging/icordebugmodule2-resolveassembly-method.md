---
title: ICorDebugModule2::ResolveAssembly — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a6596807b98e6c8b8624b5df18f78dbf8d0711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417781"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="8fe18-102">ICorDebugModule2::ResolveAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="8fe18-102">ICorDebugModule2::ResolveAssembly Method</span></span>
<span data-ttu-id="8fe18-103">Usuwa zestaw odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="8fe18-103">Resolves the assembly referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fe18-104">Syntax</span></span>  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fe18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fe18-105">Parameters</span></span>  
 `tkAsemblyRef`  
 <span data-ttu-id="8fe18-106">[in] `mdToken` Wartość, która odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="8fe18-106">[in] An `mdToken` value that references the assembly.</span></span>  
  
 `ppAssembly`  
 <span data-ttu-id="8fe18-107">[out] Wskaźnik do adresu ICorDebugAssembly obiekt, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="8fe18-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fe18-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8fe18-108">Remarks</span></span>  
 <span data-ttu-id="8fe18-109">Jeśli zestaw nie jest już załadowany podczas `ResolveAssembly` jest nazywany HRESULT zostanie zwrócona wartość CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="8fe18-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe18-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fe18-110">Requirements</span></span>  
 <span data-ttu-id="8fe18-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe18-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe18-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fe18-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fe18-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fe18-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe18-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe18-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
