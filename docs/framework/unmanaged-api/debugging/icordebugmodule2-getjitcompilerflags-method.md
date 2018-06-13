---
title: ICorDebugModule2::GetJITCompilerFlags — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bb275f08143362d62f241ea659ea39ff8eef5d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413085"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="c3e1a-102">ICorDebugModule2::GetJITCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="c3e1a-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="c3e1a-103">Pobiera flagi sterujące kompilacji to ICorDebugModule2 just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c3e1a-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3e1a-104">Syntax</span></span>  
  
```  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3e1a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3e1a-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="c3e1a-106">[out] Wskaźnik do wartości [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenia, która kontroluje kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="c3e1a-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e1a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3e1a-107">Requirements</span></span>  
 <span data-ttu-id="c3e1a-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3e1a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3e1a-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3e1a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3e1a-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3e1a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3e1a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3e1a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
