---
title: ICorProfilerInfo4::GetObjectSize2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: b605419a291f7bee76ecad7e07be9a7a989f9fe9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496012"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="f934a-102">ICorProfilerInfo4::GetObjectSize2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="f934a-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="f934a-103">Zwraca rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f934a-103">Returns the size of a specified object.</span></span> <span data-ttu-id="f934a-104">Zastępuje metodę [ICorProfilerInfo:: GetObjectSize —](icorprofilerinfo-getobjectsize-method.md) przez raportowanie rozmiarów obiektów, które są większe niż to, co może być wyrażone w `ULONG` .</span><span class="sxs-lookup"><span data-stu-id="f934a-104">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f934a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f934a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f934a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f934a-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="f934a-107">podczas Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f934a-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="f934a-108">określoną Wskaźnik do rozmiaru obiektu, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f934a-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f934a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f934a-109">Remarks</span></span>  
 <span data-ttu-id="f934a-110">Różne obiekty tego samego typu często mają ten sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="f934a-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="f934a-111">Jednak niektóre typy, takie jak tablice lub ciągi, mogą mieć różne rozmiary dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f934a-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f934a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f934a-112">Requirements</span></span>  
 <span data-ttu-id="f934a-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f934a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f934a-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f934a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f934a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f934a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f934a-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f934a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f934a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f934a-117">See also</span></span>

- [<span data-ttu-id="f934a-118">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f934a-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
