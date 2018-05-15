---
title: ICorProfilerInfo2::GetAppDomainStaticAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8e1886a3e33b533eb525f5b35480a8a7d326da0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="a3fec-102">ICorProfilerInfo2::GetAppDomainStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3fec-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="a3fec-103">Pobiera adres pola statyczne domeny określonej aplikacji, która znajduje się w zakresie domeny określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3fec-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3fec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3fec-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3fec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3fec-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="a3fec-106">[in] Identyfikator klasy klasy zawierającej pole Niestatyczne domeny żądanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3fec-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="a3fec-107">[in] Token metadanych dla pola statycznego domeny żądanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3fec-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="a3fec-108">[in] Identyfikator domeny aplikacji, która jest zakresem dla żądanego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="a3fec-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="a3fec-109">[out] Wskaźnik do adresu pola statycznego, który znajduje się w domenie określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3fec-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3fec-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3fec-110">Remarks</span></span>  
 <span data-ttu-id="a3fec-111">`GetAppDomainStaticAddress` Metoda może zwracać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a3fec-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="a3fec-112">HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="a3fec-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="a3fec-113">Adresy obiektów, które mogą znajdować się w pamięci sterty kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a3fec-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="a3fec-114">Te adresy mogą być nieprawidłowe po wyrzucanie elementów bezużytecznych, więc po wyrzucanie elementów bezużytecznych profilowania nie należy zakładać, że są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="a3fec-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="a3fec-115">Przed ukończeniem konstruktora klasy klasy `GetAppDomainStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne już może zainicjować i umieszczanie w katalogu głównym odzyskiwanie kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="a3fec-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3fec-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3fec-116">Requirements</span></span>  
 <span data-ttu-id="a3fec-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3fec-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3fec-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3fec-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3fec-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3fec-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3fec-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3fec-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3fec-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3fec-121">See Also</span></span>  
 [<span data-ttu-id="a3fec-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3fec-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="a3fec-123">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3fec-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
