---
title: ICorProfilerInfo2::GetArrayObjectInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: 368b8f270797beb525e0745a29990667913f4071
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497364"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="650f5-102">ICorProfilerInfo2::GetArrayObjectInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="650f5-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="650f5-103">Pobiera szczegółowe informacje o obiekcie array.</span><span class="sxs-lookup"><span data-stu-id="650f5-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="650f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="650f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="650f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="650f5-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="650f5-106">podczas Identyfikator prawidłowego obiektu tablicy.</span><span class="sxs-lookup"><span data-stu-id="650f5-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="650f5-107">podczas Ranga (liczba wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="650f5-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="650f5-108">określoną Tablica zawierająca liczby całkowite, z których każdy reprezentuje rozmiar wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="650f5-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="650f5-109">określoną Tablica zawierająca liczby całkowite, z których każda reprezentuje dolną granicę wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="650f5-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="650f5-110">określoną Wskaźnik na adres nieprzetworzonego buforu dla tablicy, który jest ustalany zgodnie z Konwencją języka C++.</span><span class="sxs-lookup"><span data-stu-id="650f5-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="650f5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="650f5-111">Remarks</span></span>  
 <span data-ttu-id="650f5-112">`pDimensionSizes`I `pDimensionLowerBounds` są to tablice równoległe, dlatego elementy znajdujące się w tym samym indeksie w każdej tablicy są cechami tej samej jednostki.</span><span class="sxs-lookup"><span data-stu-id="650f5-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="650f5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="650f5-113">Requirements</span></span>  
 <span data-ttu-id="650f5-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="650f5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="650f5-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="650f5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="650f5-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="650f5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="650f5-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="650f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650f5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="650f5-118">See also</span></span>

- [<span data-ttu-id="650f5-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="650f5-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="650f5-120">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="650f5-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
