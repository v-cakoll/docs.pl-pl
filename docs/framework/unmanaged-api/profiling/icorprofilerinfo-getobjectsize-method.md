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
ms.openlocfilehash: d366a0093ca82d2e5b3c40729777a1b6c0766bda
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092204"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="1c679-102">ICorProfilerInfo::GetObjectSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c679-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="1c679-103">Pobiera rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1c679-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c679-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c679-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c679-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c679-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="1c679-106">[in] Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="1c679-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="1c679-107">[out] Wskaźnik do obiektu, rozmiar w bajtach.</span><span class="sxs-lookup"><span data-stu-id="1c679-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c679-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c679-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1c679-109">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="1c679-109">This method is obsolete.</span></span> <span data-ttu-id="1c679-110">Zwraca COR_E_OVERFLOW obiektów większą niż 4GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="1c679-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="1c679-111">Użyj [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="1c679-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="1c679-112">Te same typy dwóch różnych obiektów często mają taki sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="1c679-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="1c679-113">Jednak niektóre typy, takie jak tablice i ciągów, może mieć inny rozmiar dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1c679-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="1c679-114">Rozmiar zwrócony przez `GetObjectSize` metoda nie zawiera żadnych dopełnienie wyrównanie, które mogą być wyświetlane po obiektu na stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1c679-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="1c679-115">Jeśli używasz `GetObjectSize` metody, aby przejść do innego obiektu na stercie wyrzucania elementów bezużytecznych, Dodaj wyrównanie dopełnienie ręcznego zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="1c679-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="1c679-116">Na Windows 32-bitowych COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 i COR_PRF_GC_GEN_2 użyj 4-bajtowe wyrównanie i COR_PRF_GC_LARGE_OBJECT_HEAP korzysta z 8-bajtowe wyrównanie.</span><span class="sxs-lookup"><span data-stu-id="1c679-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="1c679-117">Na Windows 64-bitowych wyrównania jest zawsze 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="1c679-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c679-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c679-118">Requirements</span></span>  
 <span data-ttu-id="1c679-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c679-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c679-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c679-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c679-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c679-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c679-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c679-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c679-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c679-123">See also</span></span>

- [<span data-ttu-id="1c679-124">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c679-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
