---
title: ICorProfilerInfo::GetClassFromObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
ms.openlocfilehash: 613267549329d2f48dcd18ae341e47538e414ac0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498534"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="66a7a-102">ICorProfilerInfo::GetClassFromObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="66a7a-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="66a7a-103">Pobiera `ClassID` obiekt z danego obiektu `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="66a7a-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66a7a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66a7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66a7a-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="66a7a-106">podczas Identyfikator obiektu, dla którego ma zostać pobrany `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="66a7a-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="66a7a-107">określoną Wskaźnik do zwracanego elementu `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="66a7a-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66a7a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66a7a-108">Remarks</span></span>  
 <span data-ttu-id="66a7a-109">Wartość null `pClassId` wskazuje `objectId` Typ, który jest wyładowania.</span><span class="sxs-lookup"><span data-stu-id="66a7a-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a7a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66a7a-110">Requirements</span></span>  
 <span data-ttu-id="66a7a-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a7a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a7a-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="66a7a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66a7a-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66a7a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66a7a-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a7a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a7a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66a7a-115">See also</span></span>

- [<span data-ttu-id="66a7a-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="66a7a-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
