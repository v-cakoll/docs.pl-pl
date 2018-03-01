---
title: "ICorProfilerInfo::GetFunctionFromIP — Metoda"
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
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 144d80bb0e4111e319427d6a265d199b04b7f863
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="065a4-102">ICorProfilerInfo::GetFunctionFromIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="065a4-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="065a4-103">Mapuje wskaźnik instrukcji kodu zarządzanego do `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="065a4-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="065a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="065a4-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="065a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="065a4-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="065a4-106">[in] Wskaźnik instrukcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="065a4-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="065a4-107">[out] Funkcja zwrócony identyfikator.</span><span class="sxs-lookup"><span data-stu-id="065a4-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="065a4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="065a4-108">Requirements</span></span>  
 <span data-ttu-id="065a4-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="065a4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="065a4-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="065a4-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="065a4-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="065a4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="065a4-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="065a4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065a4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="065a4-113">See Also</span></span>  
 [<span data-ttu-id="065a4-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="065a4-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
