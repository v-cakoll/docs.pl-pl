---
title: "ICorProfilerInfo3::GetStringLayout2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetStringLayout2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97f4ab9eefa8bf1f2b3a5057f24b6a940ba91f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="f69b5-102">ICorProfilerInfo3::GetStringLayout2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="f69b5-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="f69b5-103">Pobiera informacje o układzie z obiektem ciągu.</span><span class="sxs-lookup"><span data-stu-id="f69b5-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="f69b5-104">Ta metoda zastępuje [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f69b5-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f69b5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f69b5-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f69b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f69b5-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="f69b5-107">[out] Wskaźnik do przesunięcie lokalizacji względem `ObjectID` wskaźnika, przechowujący długość sam ciąg.</span><span class="sxs-lookup"><span data-stu-id="f69b5-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="f69b5-108">Długość jest przechowywana jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="f69b5-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="f69b5-109">[out] Wskaźnik do przesunięcie buforu względem `ObjectID` wskaźnika, który przechowuje ciąg znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="f69b5-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f69b5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f69b5-110">Remarks</span></span>  
 <span data-ttu-id="f69b5-111">Ciągi może lub nie może być zerem.</span><span class="sxs-lookup"><span data-stu-id="f69b5-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f69b5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f69b5-112">Requirements</span></span>  
 <span data-ttu-id="f69b5-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f69b5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f69b5-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f69b5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f69b5-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f69b5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f69b5-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f69b5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69b5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f69b5-117">See Also</span></span>  
 [<span data-ttu-id="f69b5-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="f69b5-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="f69b5-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f69b5-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
