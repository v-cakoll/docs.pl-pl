---
title: ICorProfilerInfo::GetFunctionFromIP — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: cd1f3982fe1439135bf96579370a5a798c61dd2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863806"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="d1d08-102">ICorProfilerInfo::GetFunctionFromIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1d08-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="d1d08-103">Mapuje wskaźnik zarządzanej instrukcji kodu na `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="d1d08-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1d08-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1d08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1d08-105">Parameters</span></span>

- `ip`

  <span data-ttu-id="d1d08-106">\[w] wskaźnik instrukcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d1d08-106">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="d1d08-107">\[out] zwrócony identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1d08-107">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1d08-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1d08-108">Requirements</span></span>  
 <span data-ttu-id="d1d08-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1d08-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d08-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d1d08-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1d08-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d1d08-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1d08-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d08-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d08-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1d08-113">See also</span></span>

- [<span data-ttu-id="d1d08-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1d08-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
