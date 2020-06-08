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
ms.openlocfilehash: 7550caaa7cb4d7ed77dc36ecf0ce0e0cbc541db7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497065"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="d107c-102">ICorProfilerInfo2::GetContextStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="d107c-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="d107c-103">Pobiera adres dla określonego kontekstu-static pola, które znajduje się w zakresie określonego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d107c-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d107c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d107c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d107c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d107c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="d107c-106">podczas Identyfikator klasy, która zawiera wymagane pole kontekstu-static.</span><span class="sxs-lookup"><span data-stu-id="d107c-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="d107c-107">podczas Token metadanych dla żądanego pola kontekstu-static.</span><span class="sxs-lookup"><span data-stu-id="d107c-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="d107c-108">podczas Identyfikator kontekstu, który jest zakresem dla żądanego pola kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="d107c-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="d107c-109">określoną Wskaźnik do adresu pola statycznego znajdującego się w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="d107c-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d107c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d107c-110">Remarks</span></span>  
 <span data-ttu-id="d107c-111">`GetContextStaticAddress`Metoda może zwracać jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="d107c-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="d107c-112">CORPROF_E_DATAINCOMPLETE HRESULT, jeśli podane pole statyczne nie ma przypisanego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="d107c-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="d107c-113">Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d107c-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="d107c-114">Te adresy mogą stać się nieprawidłowe po wyrzucaniu elementów bezużytecznych, więc po wybraniu elementów bezużytecznych nie należy zakładać, że są one poprawne.</span><span class="sxs-lookup"><span data-stu-id="d107c-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="d107c-115">Przed ukończeniem konstruktora klasy klasy `GetContextStaticAddress` zwraca CORPROF_E_DATAINCOMPLETE dla wszystkich pól statycznych, chociaż niektóre pola statyczne mogą już być zainicjowane i główne obiekty wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d107c-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d107c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d107c-116">Requirements</span></span>  
 <span data-ttu-id="d107c-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d107c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d107c-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d107c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d107c-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d107c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d107c-120">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d107c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d107c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d107c-121">See also</span></span>

- [<span data-ttu-id="d107c-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d107c-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="d107c-123">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d107c-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
