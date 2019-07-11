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
ms.openlocfilehash: 4d4efa7cb3bc98c54be2889855c3b756fdbf2847
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782247"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="999d5-102">ICorProfilerInfo2::GetStringLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="999d5-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="999d5-103">Pobiera informacje o układ obiektu ciągu.</span><span class="sxs-lookup"><span data-stu-id="999d5-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="999d5-104">Ta metoda jest przestarzała w programie .NET Framework 4 i został zastąpiony przez [icorprofilerinfo3::getstringlayout2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="999d5-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999d5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="999d5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="999d5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="999d5-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="999d5-107">[out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, który przechowuje długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="999d5-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="999d5-108">Długość jest przechowywany jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="999d5-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="999d5-109">Ten parametr zwraca długość ciągu, nie długość buforu.</span><span class="sxs-lookup"><span data-stu-id="999d5-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="999d5-110">Długość buforu nie jest już dostępna.</span><span class="sxs-lookup"><span data-stu-id="999d5-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="999d5-111">[out] Wskaźnik do przesunięcia lokalizacji względem `ObjectID` wskaźnika, która przechowuje długość ciągu, sam.</span><span class="sxs-lookup"><span data-stu-id="999d5-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="999d5-112">Długość jest przechowywany jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="999d5-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="999d5-113">[out] Wskaźnik do przesunięcia buforu względem `ObjectID` wskaźnika, który przechowuje ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="999d5-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="999d5-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="999d5-114">Remarks</span></span>  
 <span data-ttu-id="999d5-115">`GetStringLayout` Metoda pobiera przesunięcia względem `ObjectID` wskaźnika, lokalizacji, w których przechowywane są następujące:</span><span class="sxs-lookup"><span data-stu-id="999d5-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="999d5-116">Długość buforu ciągu.</span><span class="sxs-lookup"><span data-stu-id="999d5-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="999d5-117">Długość ciągu, sam.</span><span class="sxs-lookup"><span data-stu-id="999d5-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="999d5-118">Bufor, który zawiera rzeczywiste ciąg znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="999d5-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="999d5-119">Ciągi mogą być zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="999d5-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="999d5-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="999d5-120">Requirements</span></span>  
 <span data-ttu-id="999d5-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="999d5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="999d5-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="999d5-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="999d5-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="999d5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="999d5-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="999d5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999d5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="999d5-125">See also</span></span>

- [<span data-ttu-id="999d5-126">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="999d5-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="999d5-127">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="999d5-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
