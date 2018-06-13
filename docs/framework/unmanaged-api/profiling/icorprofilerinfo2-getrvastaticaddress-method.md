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
ms.openlocfilehash: 3ee12131cfa323d4426ab06ea31be4a8dd7b4583
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455468"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="e1d6a-102">ICorProfilerInfo2::GetRVAStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1d6a-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="e1d6a-103">Pobiera adres pola statycznego względną wirtualnego określony adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="e1d6a-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1d6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1d6a-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1d6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1d6a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e1d6a-106">[in] Identyfikator klasy, która zawiera żądane pole statyczne adres RVA.</span><span class="sxs-lookup"><span data-stu-id="e1d6a-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e1d6a-107">[in] Token metadanych dla żądanego pola statycznego adresu RVA.</span><span class="sxs-lookup"><span data-stu-id="e1d6a-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e1d6a-108">[out] Wskaźnik do adresu pola statycznego adresu RVA.</span><span class="sxs-lookup"><span data-stu-id="e1d6a-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1d6a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1d6a-109">Remarks</span></span>  
 <span data-ttu-id="e1d6a-110">`GetRVAStaticAddress` Metoda może zwracać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e1d6a-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="e1d6a-111">HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="e1d6a-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="e1d6a-112">Adresy obiektów, które mogą znajdować się w pamięci sterty kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e1d6a-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e1d6a-113">Te adresy mogą być nieprawidłowe po wyrzucanie elementów bezużytecznych, więc po wyrzucanie elementów bezużytecznych profilowania nie należy zakładać, że są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e1d6a-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e1d6a-114">Przed ukończeniem konstruktora klasy klasy `GetRVAStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne mogą już zainicjowany i może być umieszczanie katalogu głównym odzyskiwanie kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="e1d6a-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1d6a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1d6a-115">Requirements</span></span>  
 <span data-ttu-id="e1d6a-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1d6a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1d6a-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1d6a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1d6a-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1d6a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1d6a-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1d6a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d6a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1d6a-120">See Also</span></span>  
 [<span data-ttu-id="e1d6a-121">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1d6a-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e1d6a-122">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1d6a-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
