---
title: ICorProfilerInfo2::GetStringLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a3d26a99844d00609b28eaef08ff0874a6701fb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664967"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="92dac-102">ICorProfilerInfo2::GetStringLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="92dac-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="92dac-103">Pobiera informacje o układ obiektu ciągu.</span><span class="sxs-lookup"><span data-stu-id="92dac-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="92dac-104">Ta metoda jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]i są zastępowane [icorprofilerinfo3::getstringlayout2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="92dac-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92dac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="92dac-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92dac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="92dac-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="92dac-107">[out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, który przechowuje długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="92dac-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="92dac-108">Długość jest przechowywany jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="92dac-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92dac-109">Ten parametr zwraca długość ciągu, nie długość buforu.</span><span class="sxs-lookup"><span data-stu-id="92dac-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="92dac-110">Długość buforu nie jest już dostępna.</span><span class="sxs-lookup"><span data-stu-id="92dac-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="92dac-111">[out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, która przechowuje długość ciągu, sam.</span><span class="sxs-lookup"><span data-stu-id="92dac-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="92dac-112">Długość jest przechowywany jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="92dac-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="92dac-113">[out] Wskaźnik do przesunięcia buforu względem `ObjectID` wskaźnika, który przechowuje ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="92dac-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92dac-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92dac-114">Remarks</span></span>  
 <span data-ttu-id="92dac-115">`GetStringLayout` Metoda pobiera przesunięcia względem `ObjectID` wskaźnika, lokalizacji, w których przechowywane są następujące:</span><span class="sxs-lookup"><span data-stu-id="92dac-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="92dac-116">Długość buforu ciągu.</span><span class="sxs-lookup"><span data-stu-id="92dac-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="92dac-117">Długość ciągu, sam.</span><span class="sxs-lookup"><span data-stu-id="92dac-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="92dac-118">Bufor, który zawiera rzeczywiste ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="92dac-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="92dac-119">Ciągi mogą być zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="92dac-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92dac-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92dac-120">Requirements</span></span>  
 <span data-ttu-id="92dac-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92dac-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92dac-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92dac-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92dac-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92dac-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92dac-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92dac-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92dac-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92dac-125">See also</span></span>

- [<span data-ttu-id="92dac-126">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="92dac-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="92dac-127">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="92dac-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
