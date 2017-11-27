---
title: "ICorProfilerInfo::GetFunctionFromIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionFromIP
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3712187d74cfa180b3cd91f4cee1e9318537b6b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="8d019-102">ICorProfilerInfo::GetFunctionFromIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="8d019-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="8d019-103">Mapuje wskaźnik instrukcji kodu zarządzanego do `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="8d019-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d019-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d019-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d019-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d019-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="8d019-106">[in] Wskaźnik instrukcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="8d019-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="8d019-107">[out] Funkcja zwrócony identyfikator.</span><span class="sxs-lookup"><span data-stu-id="8d019-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d019-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d019-108">Requirements</span></span>  
 <span data-ttu-id="8d019-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d019-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d019-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d019-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d019-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d019-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d019-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d019-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d019-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d019-113">See Also</span></span>  
 [<span data-ttu-id="8d019-114">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="8d019-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
