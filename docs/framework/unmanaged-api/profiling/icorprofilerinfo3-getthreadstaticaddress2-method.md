---
title: "ICorProfilerInfo3::GetThreadStaticAddress2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d657f0d6a28f19c45910fa354b7b40822ad12947
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="4dc37-102">ICorProfilerInfo3::GetThreadStaticAddress2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="4dc37-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="4dc37-103">Pobiera adres określonego pola statyczne dla wątku, który znajduje się w zakresie określonego wątku i domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc37-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dc37-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4dc37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dc37-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4dc37-106">[in] Identyfikator klasy, która zawiera żądane pole statyczne dla wątku.</span><span class="sxs-lookup"><span data-stu-id="4dc37-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4dc37-107">[in] Token metadanych dla żądanego pola statyczne dla wątku.</span><span class="sxs-lookup"><span data-stu-id="4dc37-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="4dc37-108">[in] Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc37-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="4dc37-109">[in] Identyfikator wątku, który jest zakresem dla żądanego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="4dc37-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4dc37-110">[out] Wskaźnik do adresu pola statycznego w określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="4dc37-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dc37-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dc37-111">Remarks</span></span>  
 <span data-ttu-id="4dc37-112">`GetThreadStaticAddress2` Metoda może zwracać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4dc37-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="4dc37-113">HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="4dc37-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="4dc37-114">Adresy obiektów, które mogą znajdować się w pamięci sterty kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4dc37-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4dc37-115">Te adresy mogą być nieprawidłowe po wyrzucanie elementów bezużytecznych, więc po wyrzucanie elementów bezużytecznych profilowania nie należy zakładać, że są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="4dc37-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4dc37-116">Przed ukończeniem konstruktora klasy klasy `GetThreadStaticAddress2` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne już może zainicjować i umieszczanie w katalogu głównym odzyskiwanie kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="4dc37-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="4dc37-117">[ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) metoda jest podobna do `GetThreadStaticAddress2` metody, ale nie akceptuje argumentu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc37-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dc37-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dc37-118">Requirements</span></span>  
 <span data-ttu-id="4dc37-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dc37-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dc37-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4dc37-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4dc37-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dc37-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dc37-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dc37-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc37-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4dc37-123">See Also</span></span>  
 [<span data-ttu-id="4dc37-124">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="4dc37-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="4dc37-125">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="4dc37-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="4dc37-126">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="4dc37-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
