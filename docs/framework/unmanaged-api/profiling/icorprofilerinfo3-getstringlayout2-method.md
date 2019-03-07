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
ms.openlocfilehash: 1542573cbba2ffe407dd78eeb34e0a6e43c4d9a7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496698"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="b297a-102">ICorProfilerInfo3::GetStringLayout2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="b297a-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="b297a-103">Pobiera informacje o układ obiektu ciągu.</span><span class="sxs-lookup"><span data-stu-id="b297a-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="b297a-104">Ta metoda zastępuje [icorprofilerinfo2::getstringlayout —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b297a-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b297a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b297a-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b297a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b297a-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="b297a-107">[out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, która przechowuje długość ciągu, sam.</span><span class="sxs-lookup"><span data-stu-id="b297a-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="b297a-108">Długość jest przechowywany jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="b297a-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="b297a-109">[out] Wskaźnik do przesunięcia buforu względem `ObjectID` wskaźnika, który przechowuje ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="b297a-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b297a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b297a-110">Remarks</span></span>  
 <span data-ttu-id="b297a-111">Ciągi mogą być lub może nie być zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="b297a-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b297a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b297a-112">Requirements</span></span>  
 <span data-ttu-id="b297a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b297a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b297a-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b297a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b297a-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b297a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b297a-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b297a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b297a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b297a-117">See also</span></span>
- [<span data-ttu-id="b297a-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="b297a-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b297a-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b297a-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
