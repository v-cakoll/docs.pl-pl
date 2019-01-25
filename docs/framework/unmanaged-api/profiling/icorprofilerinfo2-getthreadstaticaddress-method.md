---
title: ICorProfilerInfo2::GetThreadStaticAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3574d7e889481931f40dbfb3158ad523c7e5637e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534998"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="21ac1-102">ICorProfilerInfo2::GetThreadStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="21ac1-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="21ac1-103">Pobiera adres określone pole statyczne wątku, który znajduje się w zakresie określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="21ac1-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21ac1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21ac1-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21ac1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21ac1-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="21ac1-106">[in] Identyfikator klasy, która zawiera żądane pole statyczne wątku.</span><span class="sxs-lookup"><span data-stu-id="21ac1-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="21ac1-107">[in] Token metadanych dla żądanego pola statyczne wątku.</span><span class="sxs-lookup"><span data-stu-id="21ac1-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="21ac1-108">[in] Identyfikator wątku, która jest zakresem dla żądanego pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="21ac1-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="21ac1-109">[out] Wskaźnik na adres pole statyczne, który znajduje się w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="21ac1-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21ac1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21ac1-110">Remarks</span></span>  
 <span data-ttu-id="21ac1-111">`GetThreadStaticAddress` Metoda może zwracać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="21ac1-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="21ac1-112">HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="21ac1-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="21ac1-113">Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="21ac1-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="21ac1-114">Te adresy mogą stać się nieprawidłowe po wyrzucania elementów bezużytecznych, dlatego po wyrzucania elementów kolekcji profilowania nie należy zakładać, że są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="21ac1-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="21ac1-115">Przed ukończeniem konstruktora klasy klasy `GetThreadStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne już może być zainicjowany i zakorzenienia wyrzucania elementów kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="21ac1-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21ac1-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21ac1-116">Requirements</span></span>  
 <span data-ttu-id="21ac1-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21ac1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21ac1-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21ac1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21ac1-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21ac1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21ac1-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21ac1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ac1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21ac1-121">See also</span></span>
- [<span data-ttu-id="21ac1-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="21ac1-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="21ac1-123">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="21ac1-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
