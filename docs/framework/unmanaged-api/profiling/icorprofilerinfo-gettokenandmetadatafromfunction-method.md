---
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bcf8919037d5b79f3819fffec02708886064b40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453206"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="d4bde-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4bde-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="d4bde-103">Pobiera token metadanych i wystąpienie interfejsu metadanych, który może służyć przed token określoną funkcję.</span><span class="sxs-lookup"><span data-stu-id="d4bde-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4bde-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4bde-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4bde-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4bde-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d4bde-106">[in] Identyfikator funkcji, dla którego można pobrać token metadanych i metadanych interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d4bde-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="d4bde-107">[in] Identyfikator odwołania interfejsu metadanych można pobrać wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d4bde-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="d4bde-108">[out] Wskaźnik do adres metadanych wystąpienie interfejsu, który może służyć przed token określona funkcja.</span><span class="sxs-lookup"><span data-stu-id="d4bde-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="d4bde-109">[out] Wskaźnik do tokenu metadane dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d4bde-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4bde-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4bde-110">Requirements</span></span>  
 <span data-ttu-id="d4bde-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4bde-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4bde-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4bde-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4bde-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4bde-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4bde-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4bde-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bde-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4bde-115">See Also</span></span>  
 [<span data-ttu-id="d4bde-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4bde-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
