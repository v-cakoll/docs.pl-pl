---
title: ICorDebugCode2::GetCompilerFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2dc6344616dfa5e633fca140ab2dab2b95c81a4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411285"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="088fb-102">ICorDebugCode2::GetCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="088fb-102">ICorDebugCode2::GetCompilerFlags Method</span></span>
<span data-ttu-id="088fb-103">Pobiera flagi, które określają warunki, na których ten obiekt kodu zostało albo just-in-time (JIT) kompilacji lub wygenerowanych przy użyciu generator obrazu natywnego (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="088fb-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="088fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="088fb-104">Syntax</span></span>  
  
```  
HRESULT GetCompilerFlags (  
    [out] DWORD *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="088fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="088fb-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="088fb-106">[out] Wskaźnik do wartości [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenia, która określa zachowanie kompilatora JIT lub generator obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="088fb-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="088fb-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="088fb-107">Requirements</span></span>  
 <span data-ttu-id="088fb-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="088fb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="088fb-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="088fb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="088fb-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="088fb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="088fb-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="088fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="088fb-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="088fb-112">See Also</span></span>  
 
