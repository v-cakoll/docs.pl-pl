---
title: ICorProfilerInfo3::GetStringLayout2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57a21a3e4c1324e15a8418dacb8cfe7c5163f334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454416"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="55fbe-102">ICorProfilerInfo3::GetStringLayout2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="55fbe-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="55fbe-103">Pobiera informacje o układzie z obiektem ciągu.</span><span class="sxs-lookup"><span data-stu-id="55fbe-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="55fbe-104">Ta metoda zastępuje [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="55fbe-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55fbe-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="55fbe-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55fbe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="55fbe-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="55fbe-107">[out] Wskaźnik do przesunięcie lokalizacji względem `ObjectID` wskaźnika, przechowujący długość sam ciąg.</span><span class="sxs-lookup"><span data-stu-id="55fbe-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="55fbe-108">Długość jest przechowywana jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="55fbe-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="55fbe-109">[out] Wskaźnik do przesunięcie buforu względem `ObjectID` wskaźnika, który przechowuje ciąg znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="55fbe-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55fbe-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55fbe-110">Remarks</span></span>  
 <span data-ttu-id="55fbe-111">Ciągi może lub nie może być zerem.</span><span class="sxs-lookup"><span data-stu-id="55fbe-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55fbe-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55fbe-112">Requirements</span></span>  
 <span data-ttu-id="55fbe-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55fbe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55fbe-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55fbe-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55fbe-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55fbe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55fbe-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55fbe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fbe-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55fbe-117">See Also</span></span>  
 [<span data-ttu-id="55fbe-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="55fbe-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="55fbe-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="55fbe-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
