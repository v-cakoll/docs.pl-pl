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
ms.openlocfilehash: 1cc05f4c10f4a5b042ff14c05f3c85a7b5935184
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497897"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="9560a-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="9560a-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="9560a-103">Pobiera token metadanych i wystąpienie interfejsu metadanych, których można użyć względem tokenu dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9560a-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9560a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9560a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9560a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9560a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9560a-106">podczas Identyfikator funkcji, dla której ma zostać pobrany token metadanych i interfejs metadanych.</span><span class="sxs-lookup"><span data-stu-id="9560a-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="9560a-107">podczas Identyfikator odwołania interfejsu metadanych, dla którego ma zostać pobrane wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="9560a-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="9560a-108">określoną Wskaźnik do adresu wystąpienia interfejsu metadanych, który może być używany w odniesieniu do tokenu dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9560a-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="9560a-109">określoną Wskaźnik do tokenu metadanych dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="9560a-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9560a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9560a-110">Requirements</span></span>  
 <span data-ttu-id="9560a-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9560a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9560a-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9560a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9560a-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9560a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9560a-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9560a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9560a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9560a-115">See also</span></span>

- [<span data-ttu-id="9560a-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9560a-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
