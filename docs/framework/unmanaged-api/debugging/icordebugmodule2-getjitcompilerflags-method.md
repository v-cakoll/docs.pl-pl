---
title: "ICorDebugModule2::GetJITCompilerFlags — Metoda"
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
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 25830b2d6ae7aedba0bb0ec0447d0b10605453eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="d34a2-102">ICorDebugModule2::GetJITCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="d34a2-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="d34a2-103">Pobiera flagi sterujące kompilacji to ICorDebugModule2 just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="d34a2-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d34a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d34a2-104">Syntax</span></span>  
  
```  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d34a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d34a2-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="d34a2-106">[out] Wskaźnik do wartości [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenia, która kontroluje kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="d34a2-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d34a2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d34a2-107">Requirements</span></span>  
 <span data-ttu-id="d34a2-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d34a2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d34a2-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d34a2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d34a2-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d34a2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d34a2-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d34a2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
