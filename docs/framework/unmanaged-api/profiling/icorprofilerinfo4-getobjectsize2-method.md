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
ms.openlocfilehash: 15829e08a755b91ff91ca939b92a5a87bd377e8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176296"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="b7dd7-102">ICorProfilerInfo4::GetObjectSize2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7dd7-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="b7dd7-103">Zwraca rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b7dd7-103">Returns the size of a specified object.</span></span> <span data-ttu-id="b7dd7-104">Zastępuje [icorprofilerinfo::getobjectsize —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) metoda raportowanie rozmiarów obiektów, które są większe niż mogą być wyrażone w `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="b7dd7-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7dd7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7dd7-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7dd7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7dd7-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b7dd7-107">[in] Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="b7dd7-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="b7dd7-108">[out] Wskaźnik do obiektu, rozmiar w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b7dd7-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7dd7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7dd7-109">Remarks</span></span>  
 <span data-ttu-id="b7dd7-110">Te same typy dwóch różnych obiektów często mają taki sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="b7dd7-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="b7dd7-111">Jednak niektóre typy, takie jak tablice i ciągów, może mieć inny rozmiar dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b7dd7-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7dd7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7dd7-112">Requirements</span></span>  
 <span data-ttu-id="b7dd7-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7dd7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7dd7-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7dd7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7dd7-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7dd7-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b7dd7-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b7dd7-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b7dd7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7dd7-117">See also</span></span>

- [<span data-ttu-id="b7dd7-118">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b7dd7-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
