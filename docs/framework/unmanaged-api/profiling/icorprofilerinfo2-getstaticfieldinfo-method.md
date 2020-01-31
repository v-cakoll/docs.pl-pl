---
title: ICorProfilerInfo2::GetStaticFieldInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: d30d0bc262d76cf8980f90d8384173d89baf92d5
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862689"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="2f0e3-102">ICorProfilerInfo2::GetStaticFieldInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="2f0e3-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="2f0e3-103">Pobiera wartość wskazującą rodzaj static, który ma zastosowanie do określonego pola.</span><span class="sxs-lookup"><span data-stu-id="2f0e3-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f0e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f0e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f0e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f0e3-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2f0e3-106">podczas Identyfikator klasy, w której zdefiniowane jest pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="2f0e3-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="2f0e3-107">podczas Token metadanych dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="2f0e3-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="2f0e3-108">określoną Wskaźnik do wartości wyliczenia [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) , który wskazuje, czy określone pole jest statyczne, i jeśli tak, rodzaj static, który ma zastosowanie do pola.</span><span class="sxs-lookup"><span data-stu-id="2f0e3-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f0e3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f0e3-109">Remarks</span></span>  
 <span data-ttu-id="2f0e3-110">Te informacje mogą służyć do określenia, która funkcja ma zostać wywołana w celu pobrania adresu pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="2f0e3-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="2f0e3-111">Kod profilera powinien nadal sprawdzać metadane pola statycznego, aby upewnić się, że faktycznie ma adres.</span><span class="sxs-lookup"><span data-stu-id="2f0e3-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="2f0e3-112">Literały statyczne (czyli stałe) istnieją tylko w metadanych i nie mają adresu.</span><span class="sxs-lookup"><span data-stu-id="2f0e3-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f0e3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f0e3-113">Requirements</span></span>  
 <span data-ttu-id="2f0e3-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f0e3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f0e3-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2f0e3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f0e3-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2f0e3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f0e3-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f0e3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0e3-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f0e3-118">See also</span></span>

- [<span data-ttu-id="2f0e3-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f0e3-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2f0e3-120">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f0e3-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
