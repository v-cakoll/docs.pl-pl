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
ms.openlocfilehash: 0561f76c70da603d50b96ce5b5162efac4eff2de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492980"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="f0327-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0327-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="f0327-103">Pobiera token metadanych i wystąpienie interfejsu metadanych, który może zostać użyty dla tokenu dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0327-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0327-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0327-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0327-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0327-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f0327-106">[in] Identyfikator funkcji, dla którego należy pobrać token metadanych i metadanych interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f0327-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="f0327-107">[in] Identyfikator odwołania interfejsu metadanych można pobrać wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f0327-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="f0327-108">[out] Wskaźnik na adres metadanych wystąpienie interfejsu, który może zostać użyty dla tokenu dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0327-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="f0327-109">[out] Wskaźnik do tokenu metadanych dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0327-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0327-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0327-110">Requirements</span></span>  
 <span data-ttu-id="f0327-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0327-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0327-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0327-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0327-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0327-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0327-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0327-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0327-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0327-115">See also</span></span>
- [<span data-ttu-id="f0327-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0327-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
