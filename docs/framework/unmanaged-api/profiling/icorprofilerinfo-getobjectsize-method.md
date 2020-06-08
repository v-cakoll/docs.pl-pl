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
ms.openlocfilehash: 15c843fe138be55a3480f46e0ef8b37bcb445ad0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497975"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="a8d72-102">ICorProfilerInfo::GetObjectSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="a8d72-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="a8d72-103">Pobiera rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8d72-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8d72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8d72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8d72-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a8d72-106">podczas Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8d72-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="a8d72-107">określoną Wskaźnik do rozmiaru obiektu, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a8d72-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8d72-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a8d72-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a8d72-109">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a8d72-109">This method is obsolete.</span></span> <span data-ttu-id="a8d72-110">Zwraca COR_E_OVERFLOW dla obiektów większych niż 4 GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="a8d72-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="a8d72-111">Zamiast tego użyj metody [ICorProfilerInfo4:: GetObjectSize2 —](icorprofilerinfo4-getobjectsize2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a8d72-111">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="a8d72-112">Różne obiekty tego samego typu często mają ten sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="a8d72-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="a8d72-113">Jednak niektóre typy, takie jak tablice lub ciągi, mogą mieć różne rozmiary dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8d72-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="a8d72-114">Rozmiar zwrócony przez `GetObjectSize` metodę nie obejmuje żadnego dopełnienia wyrównania, które może być wyświetlane po obiekcie na stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a8d72-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="a8d72-115">Jeśli używasz `GetObjectSize` metody do przechodzenia z obiektu do obiektu na stercie wyrzucania elementów bezużytecznych, w razie potrzeby dodaj ręcznie wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a8d72-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="a8d72-116">W 32-bitowym systemie Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 i COR_PRF_GC_GEN_2 użyć 4-bajtowego wyrównania, a COR_PRF_GC_LARGE_OBJECT_HEAP używa wyrównania 8-bajtowego.</span><span class="sxs-lookup"><span data-stu-id="a8d72-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="a8d72-117">W 64-bitowym systemie Windows wyrównanie ma zawsze 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a8d72-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8d72-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8d72-118">Requirements</span></span>  
 <span data-ttu-id="a8d72-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8d72-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d72-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a8d72-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8d72-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a8d72-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8d72-122">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8d72-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d72-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8d72-123">See also</span></span>

- [<span data-ttu-id="a8d72-124">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8d72-124">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
