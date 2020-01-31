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
ms.openlocfilehash: d924dbf21a0f0b046c8d8f8f294e91bc5ff6c015
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869414"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="3c735-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c735-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="3c735-103">Pobiera token metadanych i wystąpienie interfejsu metadanych, których można użyć względem tokenu dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3c735-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c735-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c735-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c735-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c735-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3c735-106">podczas Identyfikator funkcji, dla której ma zostać pobrany token metadanych i interfejs metadanych.</span><span class="sxs-lookup"><span data-stu-id="3c735-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="3c735-107">podczas Identyfikator odwołania interfejsu metadanych, dla którego ma zostać pobrane wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="3c735-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="3c735-108">określoną Wskaźnik do adresu wystąpienia interfejsu metadanych, który może być używany w odniesieniu do tokenu dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3c735-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="3c735-109">określoną Wskaźnik do tokenu metadanych dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3c735-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c735-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c735-110">Requirements</span></span>  
 <span data-ttu-id="3c735-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c735-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c735-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3c735-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c735-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3c735-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c735-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c735-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c735-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c735-115">See also</span></span>

- [<span data-ttu-id="3c735-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c735-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
