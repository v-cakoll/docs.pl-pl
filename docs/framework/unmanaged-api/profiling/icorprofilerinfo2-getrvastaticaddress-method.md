---
title: ICorProfilerInfo2::GetRVAStaticAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c2d1aee741ac54e861f7068d883731745ca7788
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584308"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="4c614-102">ICorProfilerInfo2::GetRVAStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c614-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="4c614-103">Pobiera adres określonej względnych adresów wirtualnych (RVA) pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="4c614-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c614-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c614-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c614-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c614-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4c614-106">[in] Identyfikator klasy, która zawiera żądane pole adres RVA statyczne.</span><span class="sxs-lookup"><span data-stu-id="4c614-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4c614-107">[in] Token metadanych dla żądanego pola adres RVA statyczne.</span><span class="sxs-lookup"><span data-stu-id="4c614-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4c614-108">[out] Wskaźnik na adres RVA statyczne pola.</span><span class="sxs-lookup"><span data-stu-id="4c614-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c614-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c614-109">Remarks</span></span>  
 <span data-ttu-id="4c614-110">`GetRVAStaticAddress` Metoda może zwracać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4c614-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="4c614-111">HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="4c614-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="4c614-112">Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4c614-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4c614-113">Te adresy mogą stają się nieprawidłowe po wyrzucania elementów bezużytecznych, więc po wyrzucania elementów bezużytecznych profilowania nie należy zakładać, że są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="4c614-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4c614-114">Przed ukończeniem konstruktora klasy klasy `GetRVAStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne mogą został już zainicjowany i może być zakorzenienia obiekty kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="4c614-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c614-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c614-115">Requirements</span></span>  
 <span data-ttu-id="4c614-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c614-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c614-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c614-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c614-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c614-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c614-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c614-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c614-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c614-120">See also</span></span>

- [<span data-ttu-id="4c614-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c614-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="4c614-122">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c614-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
