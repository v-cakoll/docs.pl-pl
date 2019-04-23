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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0106b2dd1151e302c0082b306d999ab5a1c4322
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177752"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="01e1e-102">ICorProfilerInfo2::GetStaticFieldInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="01e1e-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="01e1e-103">Pobiera wartość wskazującą rodzaj statyczną, która ma zastosowanie do określonego pola.</span><span class="sxs-lookup"><span data-stu-id="01e1e-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e1e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01e1e-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01e1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01e1e-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="01e1e-106">[in] Identyfikator klasy, w którym zdefiniowano pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="01e1e-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="01e1e-107">[in] Token metadanych dla pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="01e1e-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="01e1e-108">[out] Wskaźnik do wartości [cor_prf_static_type —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) wyliczenia oznacza to, czy określone pole jest statyczna, a jeśli tak, rodzaj statyczne która odnosi się do pola.</span><span class="sxs-lookup"><span data-stu-id="01e1e-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01e1e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01e1e-109">Remarks</span></span>  
 <span data-ttu-id="01e1e-110">Te informacje, można określić, której funkcji należy wywołać, aby uzyskać adres pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="01e1e-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="01e1e-111">Kod programu profilującego nadal należy sprawdzić metadanych dla pola statycznego upewnić się, że faktycznie ma adres.</span><span class="sxs-lookup"><span data-stu-id="01e1e-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="01e1e-112">Literały statyczne (czyli stałych) istnieje tylko w metadanych i nie ma adresu.</span><span class="sxs-lookup"><span data-stu-id="01e1e-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e1e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01e1e-113">Requirements</span></span>  
 <span data-ttu-id="01e1e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01e1e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e1e-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01e1e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01e1e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01e1e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01e1e-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e1e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e1e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01e1e-118">See also</span></span>

- [<span data-ttu-id="01e1e-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="01e1e-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="01e1e-120">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="01e1e-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
