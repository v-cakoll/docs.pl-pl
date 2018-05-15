---
title: ICorProfilerInfo3::GetRuntimeInformation — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67e1d20f7faf38fa37083f1a5b1cc0c1060b7a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="dfa3e-102">ICorProfilerInfo3::GetRuntimeInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="dfa3e-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="dfa3e-103">Zawiera informacje o wersji dotyczące środowisko uruchomieniowe języka wspólnego (CLR), który jest poddawany profilowaniu.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfa3e-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="dfa3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfa3e-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="dfa3e-106">[out] Identyfikator pracownika uruchomionego wystąpienia CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="dfa3e-107">To jest taka sama jak `ClrInstanceID` czy raporty śledzenie zdarzeń dla zdarzenia uruchamiania systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="dfa3e-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="dfa3e-108">[out] Typ środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-108">[out] The runtime type.</span></span> <span data-ttu-id="dfa3e-109">Ten parametr zwraca `COR_PRF_DESKTOP_CLR` dla tej wersji środowiska CLR, lub `COR_PRF_CORE_CLR` dla wersji core CLR używane w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="dfa3e-110">[out] Główny numer wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="dfa3e-111">[out] Podrzędny numer wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="dfa3e-112">[out] Numer wersji kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="dfa3e-113">[out] Numer wersji środowiska CLR, która jest skojarzona z aktualizacji oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="dfa3e-114">[in] Długość w znakach buforu który `szVersionString` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="dfa3e-115">[out] Długość w znakach, z `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="dfa3e-116">[out] Ciąg wersji aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfa3e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfa3e-117">Remarks</span></span>  
 <span data-ttu-id="dfa3e-118">Użytkownik może przekazać wartości null dla żadnego parametru.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-118">You may pass null for any parameter.</span></span> <span data-ttu-id="dfa3e-119">Jednak `pcchVersionString` nie może mieć wartości null chyba że `szVersionString` również ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="dfa3e-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa3e-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfa3e-120">Requirements</span></span>  
 <span data-ttu-id="dfa3e-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa3e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa3e-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dfa3e-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dfa3e-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfa3e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa3e-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa3e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa3e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfa3e-125">See Also</span></span>  
 [<span data-ttu-id="dfa3e-126">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="dfa3e-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="dfa3e-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="dfa3e-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="dfa3e-128">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="dfa3e-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
