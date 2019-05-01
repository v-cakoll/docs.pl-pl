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
ms.openlocfilehash: cc94c63edb602d87a7c08a9051eb2ef760834477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791680"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="180fc-102">ICorProfilerInfo2::GetStringLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="180fc-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="180fc-103">Pobiera informacje o układ obiektu ciągu.</span><span class="sxs-lookup"><span data-stu-id="180fc-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="180fc-104">Ta metoda jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]i są zastępowane [icorprofilerinfo3::getstringlayout2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="180fc-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="180fc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="180fc-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="180fc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="180fc-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="180fc-107">[out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, który przechowuje długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="180fc-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="180fc-108">Długość jest przechowywany jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="180fc-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="180fc-109">Ten parametr zwraca długość ciągu, nie długość buforu.</span><span class="sxs-lookup"><span data-stu-id="180fc-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="180fc-110">Długość buforu nie jest już dostępna.</span><span class="sxs-lookup"><span data-stu-id="180fc-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="180fc-111">[out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, która przechowuje długość ciągu, sam.</span><span class="sxs-lookup"><span data-stu-id="180fc-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="180fc-112">Długość jest przechowywany jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="180fc-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="180fc-113">[out] Wskaźnik do przesunięcia buforu względem `ObjectID` wskaźnika, który przechowuje ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="180fc-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="180fc-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="180fc-114">Remarks</span></span>  
 <span data-ttu-id="180fc-115">`GetStringLayout` Metoda pobiera przesunięcia względem `ObjectID` wskaźnika, lokalizacji, w których przechowywane są następujące:</span><span class="sxs-lookup"><span data-stu-id="180fc-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="180fc-116">Długość buforu ciągu.</span><span class="sxs-lookup"><span data-stu-id="180fc-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="180fc-117">Długość ciągu, sam.</span><span class="sxs-lookup"><span data-stu-id="180fc-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="180fc-118">Bufor, który zawiera rzeczywiste ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="180fc-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="180fc-119">Ciągi mogą być zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="180fc-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="180fc-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="180fc-120">Requirements</span></span>  
 <span data-ttu-id="180fc-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="180fc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="180fc-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="180fc-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="180fc-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="180fc-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="180fc-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="180fc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="180fc-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="180fc-125">See also</span></span>

- [<span data-ttu-id="180fc-126">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="180fc-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="180fc-127">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="180fc-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
