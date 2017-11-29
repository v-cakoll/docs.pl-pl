---
title: "ICorProfilerInfo3::GetRuntimeInformation — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetRuntimeInformation Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a18f0604b1585ffb1dd8230c289bcd95bfa3dfae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="783c9-102">ICorProfilerInfo3::GetRuntimeInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="783c9-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="783c9-103">Zawiera informacje o wersji dotyczące środowisko uruchomieniowe języka wspólnego (CLR), który jest poddawany profilowaniu.</span><span class="sxs-lookup"><span data-stu-id="783c9-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="783c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="783c9-104">Syntax</span></span>  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="783c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="783c9-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="783c9-106">[out] Identyfikator pracownika uruchomionego wystąpienia CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="783c9-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="783c9-107">To jest taka sama jak `ClrInstanceID` czy raporty śledzenie zdarzeń dla zdarzenia uruchamiania systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="783c9-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="783c9-108">[out] Typ środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="783c9-108">[out] The runtime type.</span></span> <span data-ttu-id="783c9-109">Ten parametr zwraca `COR_PRF_DESKTOP_CLR` dla tej wersji środowiska CLR, lub `COR_PRF_CORE_CLR` dla wersji core CLR używane w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="783c9-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="783c9-110">[out] Główny numer wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="783c9-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="783c9-111">[out] Podrzędny numer wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="783c9-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="783c9-112">[out] Numer wersji kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="783c9-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="783c9-113">[out] Numer wersji środowiska CLR, która jest skojarzona z aktualizacji oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="783c9-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="783c9-114">[in] Długość w znakach buforu który `szVersionString` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="783c9-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="783c9-115">[out] Długość w znakach, z `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="783c9-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="783c9-116">[out] Ciąg wersji aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="783c9-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="783c9-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="783c9-117">Remarks</span></span>  
 <span data-ttu-id="783c9-118">Użytkownik może przekazać wartości null dla żadnego parametru.</span><span class="sxs-lookup"><span data-stu-id="783c9-118">You may pass null for any parameter.</span></span> <span data-ttu-id="783c9-119">Jednak `pcchVersionString` nie może mieć wartości null chyba że `szVersionString` również ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="783c9-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="783c9-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="783c9-120">Requirements</span></span>  
 <span data-ttu-id="783c9-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="783c9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="783c9-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="783c9-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="783c9-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="783c9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="783c9-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="783c9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="783c9-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="783c9-125">See Also</span></span>  
 [<span data-ttu-id="783c9-126">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="783c9-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="783c9-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="783c9-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="783c9-128">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="783c9-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
