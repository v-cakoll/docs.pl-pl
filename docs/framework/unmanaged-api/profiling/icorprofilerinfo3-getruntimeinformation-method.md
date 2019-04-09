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
ms.openlocfilehash: a13e3e525c7f019e7dc49111b88ac374345830af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164934"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="a6299-102">ICorProfilerInfo3::GetRuntimeInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6299-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="a6299-103">Zawiera informacje o wersji dotyczące wspólne środowisko uruchomieniowe języka (wspólnego CLR), która jest profilowana.</span><span class="sxs-lookup"><span data-stu-id="a6299-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6299-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6299-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a6299-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6299-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="a6299-106">[out] Identyfikator przedstawiciel uruchomionego wystąpienia CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="a6299-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="a6299-107">To jest taka sama jak `ClrInstanceID` czy raportów śledzenia zdarzeń dla zdarzenia uruchamiania Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="a6299-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="a6299-108">[out] Typ środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a6299-108">[out] The runtime type.</span></span> <span data-ttu-id="a6299-109">Ten parametr zwraca `COR_PRF_DESKTOP_CLR` w przypadku klasycznej wersji środowiska CLR, lub `COR_PRF_CORE_CLR` core wersję środowiska CLR używanego w technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a6299-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="a6299-110">[out] Główny numer wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a6299-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="a6299-111">[out] Pomocniczy numer wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a6299-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="a6299-112">[out] Numer wersji kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a6299-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="a6299-113">[out] Numer wersji środowiska CLR, który jest skojarzony z aktualizacji oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="a6299-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="a6299-114">[in] Długość w znakach buforu, który `szVersionString` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="a6299-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="a6299-115">[out] Długość w znakach, z `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="a6299-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="a6299-116">[out] Ciąg wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a6299-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6299-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6299-117">Remarks</span></span>  
 <span data-ttu-id="a6299-118">Możesz przekazać wartości null dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="a6299-118">You may pass null for any parameter.</span></span> <span data-ttu-id="a6299-119">Jednak `pcchVersionString` nie może mieć wartości null Jeśli nie `szVersionString` również ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a6299-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6299-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6299-120">Requirements</span></span>  
 <span data-ttu-id="a6299-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6299-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6299-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6299-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6299-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6299-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a6299-124">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a6299-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a6299-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6299-125">See also</span></span>

- [<span data-ttu-id="a6299-126">ICorProfilerInfo3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a6299-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a6299-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a6299-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a6299-128">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="a6299-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
