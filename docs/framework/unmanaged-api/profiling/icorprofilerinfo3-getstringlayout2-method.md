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
ms.openlocfilehash: f3727343755d7014202f844be28414d31ce55bc1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862259"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="136ea-102">ICorProfilerInfo3::GetStringLayout2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="136ea-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="136ea-103">Pobiera informacje o układzie obiektu ciągu.</span><span class="sxs-lookup"><span data-stu-id="136ea-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="136ea-104">Ta metoda zastępuje metodę [ICorProfilerInfo2:: GetStringLayout —](icorprofilerinfo2-getstringlayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="136ea-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136ea-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="136ea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="136ea-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="136ea-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="136ea-107">określoną Wskaźnik do przesunięcia lokalizacji względem wskaźnika `ObjectID`, w którym jest przechowywana długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="136ea-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="136ea-108">Długość jest przechowywana jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="136ea-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="136ea-109">określoną Wskaźnik do przesunięcia buforu względem wskaźnika `ObjectID`, w którym jest przechowywany ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="136ea-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="136ea-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="136ea-110">Remarks</span></span>  
 <span data-ttu-id="136ea-111">Ciągi mogą lub nie mogą być zakończone znakiem null.</span><span class="sxs-lookup"><span data-stu-id="136ea-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="136ea-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="136ea-112">Requirements</span></span>  
 <span data-ttu-id="136ea-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="136ea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="136ea-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="136ea-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="136ea-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="136ea-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="136ea-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="136ea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136ea-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="136ea-117">See also</span></span>

- [<span data-ttu-id="136ea-118">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="136ea-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="136ea-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="136ea-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
