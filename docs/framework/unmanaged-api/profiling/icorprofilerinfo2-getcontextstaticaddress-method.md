---
title: ICorProfilerInfo2::GetContextStaticAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: d5d7da343148d5f1c2aa9b2b639b094f8269199b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433203"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="07c3e-102">ICorProfilerInfo2::GetContextStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="07c3e-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="07c3e-103">Pobiera adres dla określonego kontekstu-static pola, które znajduje się w zakresie określonego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="07c3e-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07c3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07c3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07c3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07c3e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="07c3e-106">podczas Identyfikator klasy, która zawiera wymagane pole kontekstu-static.</span><span class="sxs-lookup"><span data-stu-id="07c3e-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="07c3e-107">podczas Token metadanych dla żądanego pola kontekstu-static.</span><span class="sxs-lookup"><span data-stu-id="07c3e-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="07c3e-108">podczas Identyfikator kontekstu, który jest zakresem dla żądanego pola kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="07c3e-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="07c3e-109">określoną Wskaźnik do adresu pola statycznego znajdującego się w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="07c3e-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07c3e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07c3e-110">Remarks</span></span>  
 <span data-ttu-id="07c3e-111">Metoda `GetContextStaticAddress` może zwracać jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="07c3e-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="07c3e-112">CORPROF_E_DATAINCOMPLETE HRESULT, jeśli podane pole statyczne nie ma przypisanego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="07c3e-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="07c3e-113">Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07c3e-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="07c3e-114">Te adresy mogą stać się nieprawidłowe po wyrzucaniu elementów bezużytecznych, więc po wybraniu elementów bezużytecznych nie należy zakładać, że są one poprawne.</span><span class="sxs-lookup"><span data-stu-id="07c3e-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="07c3e-115">Przed ukończeniem konstruktora klasy klasy, `GetContextStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, chociaż niektóre pola statyczne mogą już być zainicjowane i główne obiekty wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="07c3e-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07c3e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07c3e-116">Requirements</span></span>  
 <span data-ttu-id="07c3e-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07c3e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07c3e-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="07c3e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07c3e-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="07c3e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07c3e-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07c3e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c3e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07c3e-121">See also</span></span>

- [<span data-ttu-id="07c3e-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="07c3e-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="07c3e-123">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="07c3e-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
