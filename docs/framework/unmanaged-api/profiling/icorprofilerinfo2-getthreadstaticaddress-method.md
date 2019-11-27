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
ms.openlocfilehash: d44eae4da70418e2d4f398b2bacee1fb53d55b60
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443053"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="ab0aa-102">ICorProfilerInfo2::GetThreadStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="ab0aa-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="ab0aa-103">Pobiera adres określonego wątku-static pola, które znajduje się w zakresie określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab0aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab0aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab0aa-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="ab0aa-106">podczas Identyfikator klasy zawierającej żądane pole statyczne wątku.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="ab0aa-107">podczas Token metadanych dla żądanego pola statycznego wątku.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="ab0aa-108">podczas Identyfikator wątku, który jest zakres dla żądanego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="ab0aa-109">określoną Wskaźnik do adresu pola statycznego znajdującego się w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab0aa-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab0aa-110">Remarks</span></span>  
 <span data-ttu-id="ab0aa-111">Metoda `GetThreadStaticAddress` może zwracać jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="ab0aa-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="ab0aa-112">CORPROF_E_DATAINCOMPLETE HRESULT, jeśli podane pole statyczne nie ma przypisanego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="ab0aa-113">Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="ab0aa-114">Te adresy mogą stać się nieprawidłowe po wyrzucaniu elementów bezużytecznych, więc po przeprowadzeniu odzyskiwania pamięci nie należy zakładać, że są one poprawne.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="ab0aa-115">Przed ukończeniem konstruktora klasy klasy, `GetThreadStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, chociaż niektóre pola statyczne mogą już być zainicjowane i główne obiekty wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ab0aa-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab0aa-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab0aa-116">Requirements</span></span>  
 <span data-ttu-id="ab0aa-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab0aa-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab0aa-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ab0aa-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab0aa-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ab0aa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab0aa-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab0aa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0aa-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab0aa-121">See also</span></span>

- [<span data-ttu-id="ab0aa-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab0aa-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="ab0aa-123">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab0aa-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
