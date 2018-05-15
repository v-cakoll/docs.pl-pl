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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ebbc3422f48c0c2b8ff7b807228c63fbb35dd7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="87112-102">ICorProfilerInfo4::GetObjectSize2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="87112-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="87112-103">Zwraca rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="87112-103">Returns the size of a specified object.</span></span> <span data-ttu-id="87112-104">Zastępuje [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) metody raportowanie rozmiary obiektów, które są większe niż to, co może być wyrażona w `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="87112-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87112-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="87112-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87112-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87112-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="87112-107">[in] Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="87112-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="87112-108">[out] Wskaźnik do obiektu rozmiar w bajtach.</span><span class="sxs-lookup"><span data-stu-id="87112-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87112-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87112-109">Remarks</span></span>  
 <span data-ttu-id="87112-110">Różne obiekty o takich samych typach często mają ten sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="87112-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="87112-111">Jednak niektóre typy, takich jak macierze czy ciągi, może mieć inny rozmiar dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="87112-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87112-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87112-112">Requirements</span></span>  
 <span data-ttu-id="87112-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87112-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87112-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87112-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87112-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87112-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87112-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87112-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87112-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87112-117">See Also</span></span>  
 [<span data-ttu-id="87112-118">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="87112-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
