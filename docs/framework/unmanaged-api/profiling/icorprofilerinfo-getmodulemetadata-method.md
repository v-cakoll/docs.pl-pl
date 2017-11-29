---
title: "ICorProfilerInfo::GetModuleMetaData — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleMetaData
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 540ed6f1f84f096563aa94798090c3511d6db5d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="026a9-102">ICorProfilerInfo::GetModuleMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="026a9-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="026a9-103">Pobiera wystąpienie interfejsu metadanych, który jest mapowany na określony moduł.</span><span class="sxs-lookup"><span data-stu-id="026a9-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="026a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="026a9-104">Syntax</span></span>  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="026a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="026a9-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="026a9-106">[in] Identyfikator modułu, do którego zostanie zamapowane wystąpienie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="026a9-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="026a9-107">[in] Wartość [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczenia, który określa tryb w celu otwierania plików manifestu.</span><span class="sxs-lookup"><span data-stu-id="026a9-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="026a9-108">Tylko `ofRead`, `ofWrite` i `ofNoTransform` bity są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="026a9-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="026a9-109">[in] Odwołanie Identyfikatora (GUID) interfejsu metadanych, których wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="026a9-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="026a9-110">Zobacz [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) listę interfejsów.</span><span class="sxs-lookup"><span data-stu-id="026a9-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="026a9-111">[out] Wskaźnik do adresu wystąpienie interfejsu metadanych.</span><span class="sxs-lookup"><span data-stu-id="026a9-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="026a9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="026a9-112">Remarks</span></span>  
 <span data-ttu-id="026a9-113">Może poprosić o metadanych, które ma zostać otwarty w trybie odczytu i zapisu, ale spowoduje wolniejsze wykonywanie metadanych programu, ponieważ zmiany wprowadzone do metadanych nie można zoptymalizować w porównaniu z kompilatora.</span><span class="sxs-lookup"><span data-stu-id="026a9-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="026a9-114">Niektóre moduły (takie jak moduły zasobów) mają Brak metadanych.</span><span class="sxs-lookup"><span data-stu-id="026a9-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="026a9-115">W takich przypadkach `GetModuleMetaData` zwróci wartość HRESULT S_FALSE lub wartość null w *`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="026a9-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in *`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="026a9-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="026a9-116">Requirements</span></span>  
 <span data-ttu-id="026a9-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="026a9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="026a9-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="026a9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="026a9-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="026a9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="026a9-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="026a9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026a9-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="026a9-121">See Also</span></span>  
 [<span data-ttu-id="026a9-122">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="026a9-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
