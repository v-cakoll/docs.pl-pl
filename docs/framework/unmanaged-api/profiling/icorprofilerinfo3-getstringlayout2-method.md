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
ms.openlocfilehash: 51d5b2f2ee17cc177e3b0ddc7d2e0b82fd70063d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496376"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="3851c-102">ICorProfilerInfo3::GetStringLayout2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="3851c-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="3851c-103">Pobiera informacje o układzie obiektu ciągu.</span><span class="sxs-lookup"><span data-stu-id="3851c-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="3851c-104">Ta metoda zastępuje metodę [ICorProfilerInfo2:: GetStringLayout —](icorprofilerinfo2-getstringlayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3851c-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3851c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3851c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3851c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3851c-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="3851c-107">określoną Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, w którym jest przechowywana długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="3851c-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="3851c-108">Długość jest przechowywana jako `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="3851c-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="3851c-109">określoną Wskaźnik do przesunięcia buforu, względem `ObjectID` wskaźnika, który przechowuje ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="3851c-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3851c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3851c-110">Remarks</span></span>  
 <span data-ttu-id="3851c-111">Ciągi mogą lub nie mogą być zakończone znakiem null.</span><span class="sxs-lookup"><span data-stu-id="3851c-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3851c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3851c-112">Requirements</span></span>  
 <span data-ttu-id="3851c-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3851c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3851c-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3851c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3851c-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3851c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3851c-116">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3851c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3851c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3851c-117">See also</span></span>

- [<span data-ttu-id="3851c-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="3851c-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3851c-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3851c-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
