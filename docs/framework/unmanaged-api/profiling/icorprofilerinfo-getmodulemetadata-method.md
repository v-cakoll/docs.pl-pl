---
title: ICorProfilerInfo::GetModuleMetaData — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89a2424548bb577e3580d6eaa72f61e5cf9ccc7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111218"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="6b7a6-102">ICorProfilerInfo::GetModuleMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b7a6-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="6b7a6-103">Pobiera wystąpienie interfejsu metadanych, który jest mapowany do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b7a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b7a6-104">Syntax</span></span>  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b7a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b7a6-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="6b7a6-106">[in] Identyfikator modułu, do którego będą mapowane wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="6b7a6-107">[in] Wartość [coropenflags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczenie, które określa tryb przy otwieraniu plików manifestu.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="6b7a6-108">Tylko `ofRead`, `ofWrite` i `ofNoTransform` bity są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="6b7a6-109">[in] Odwołanie Identyfikatora (GUID), którego wystąpienie będzie można pobrać interfejsu metadanych.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="6b7a6-110">Zobacz [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) listę interfejsów.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="6b7a6-111">[out] Wskaźnik na adres metadanych wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b7a6-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b7a6-112">Remarks</span></span>  
 <span data-ttu-id="6b7a6-113">Możesz poprosić o metadanych były otwierane w trybie odczytu/zapisu, ale spowoduje wolniejsze wykonywanie metadanych programu, ponieważ zmiany wprowadzone do metadanych nie można zoptymalizować, jakie były z kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="6b7a6-114">Niektóre moduły (np. moduły zasobów) mają Brak metadanych.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="6b7a6-115">W takich przypadkach `GetModuleMetaData` zwróci wartość HRESULT S_FALSE lub wartość null w \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="6b7a6-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b7a6-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b7a6-116">Requirements</span></span>  
 <span data-ttu-id="6b7a6-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b7a6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b7a6-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b7a6-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b7a6-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b7a6-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6b7a6-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6b7a6-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b7a6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b7a6-121">See also</span></span>

- [<span data-ttu-id="6b7a6-122">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6b7a6-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
