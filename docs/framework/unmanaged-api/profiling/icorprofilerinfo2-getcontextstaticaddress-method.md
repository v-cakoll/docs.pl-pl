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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 02694933aca160e1f2c28554eb6758163ed8efc8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619941"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="32b1b-102">ICorProfilerInfo2::GetContextStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="32b1b-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="32b1b-103">Pobiera adres dla określonego pola statyczne kontekstu, który znajduje się w zakresie określonego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="32b1b-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32b1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32b1b-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32b1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32b1b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="32b1b-106">[in] Identyfikator klasy, która zawiera żądane pole statyczne kontekstu.</span><span class="sxs-lookup"><span data-stu-id="32b1b-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="32b1b-107">[in] Token metadanych dla żądanego pola statyczne kontekstu.</span><span class="sxs-lookup"><span data-stu-id="32b1b-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="32b1b-108">[in] Identyfikator kontekstu, która jest zakresem dla żądanego pola statyczne kontekstu.</span><span class="sxs-lookup"><span data-stu-id="32b1b-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="32b1b-109">[out] Wskaźnik na adres pole statyczne, który znajduje się w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="32b1b-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32b1b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32b1b-110">Remarks</span></span>  
 <span data-ttu-id="32b1b-111">`GetContextStaticAddress` Metoda może zwracać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="32b1b-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="32b1b-112">HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="32b1b-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="32b1b-113">Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="32b1b-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="32b1b-114">Te adresy mogą stają się nieprawidłowe po wyrzucania elementów bezużytecznych, więc po wyrzucania elementów bezużytecznych profilowania nie należy zakładać, że są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="32b1b-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="32b1b-115">Przed ukończeniem konstruktora klasy klasy `GetContextStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne już może być zainicjowany i zakorzenienia wyrzucania elementów kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="32b1b-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32b1b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32b1b-116">Requirements</span></span>  
 <span data-ttu-id="32b1b-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32b1b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32b1b-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32b1b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32b1b-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32b1b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32b1b-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32b1b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b1b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32b1b-121">See also</span></span>

- [<span data-ttu-id="32b1b-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="32b1b-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="32b1b-123">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="32b1b-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
