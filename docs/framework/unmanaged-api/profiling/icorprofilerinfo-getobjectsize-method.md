---
title: ICorProfilerInfo::GetObjectSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ed27602dfa9090b46b842e4e65af8af373cc207
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="775d8-102">ICorProfilerInfo::GetObjectSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="775d8-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="775d8-103">Pobiera rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="775d8-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="775d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="775d8-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="775d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="775d8-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="775d8-106">[in] Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="775d8-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="775d8-107">[out] Wskaźnik do obiektu rozmiar w bajtach.</span><span class="sxs-lookup"><span data-stu-id="775d8-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="775d8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="775d8-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="775d8-109">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="775d8-109">This method is obsolete.</span></span> <span data-ttu-id="775d8-110">Zwraca COR_E_OVERFLOW dla obiektów większych niż 4GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="775d8-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="775d8-111">Użyj [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="775d8-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="775d8-112">Różne obiekty o takich samych typach często mają ten sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="775d8-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="775d8-113">Jednak niektóre typy, takich jak macierze czy ciągi, może mieć inny rozmiar dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="775d8-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="775d8-114">Rozmiar zwrócony przez `GetObjectSize` — metoda nie ma żadnych dopełnienie wyrównanie, którym może występować, gdy obiekt jest w stercie kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="775d8-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="775d8-115">Jeśli używasz `GetObjectSize` wyrównanie dopełnienie ręcznie w razie potrzeby dodaj metodę z obiektu do obiektu na stercie kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="775d8-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="775d8-116">W 32-bitowej wersji systemu Windows COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 i COR_PRF_GC_GEN_2 wyrównanie 4-bajtowych Użyj i COR_PRF_GC_LARGE_OBJECT_HEAP używa wyrównanie 8-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="775d8-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="775d8-117">W 64-bitowej wersji systemu Windows wyrównania jest zawsze 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="775d8-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="775d8-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="775d8-118">Requirements</span></span>  
 <span data-ttu-id="775d8-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="775d8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="775d8-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="775d8-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="775d8-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="775d8-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="775d8-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="775d8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775d8-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="775d8-123">See Also</span></span>  
 [<span data-ttu-id="775d8-124">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="775d8-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
