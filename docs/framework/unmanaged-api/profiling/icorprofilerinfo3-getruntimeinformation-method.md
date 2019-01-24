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
ms.openlocfilehash: 5262ba6ef0d2d36372326df24b519072e2aa6fc6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587518"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="ad996-102">ICorProfilerInfo3::GetRuntimeInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad996-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="ad996-103">Zawiera informacje o wersji dotyczące wspólne środowisko uruchomieniowe języka (wspólnego CLR), która jest profilowana.</span><span class="sxs-lookup"><span data-stu-id="ad996-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad996-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad996-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ad996-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad996-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="ad996-106">[out] Identyfikator przedstawiciel uruchomionego wystąpienia CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="ad996-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="ad996-107">To jest taka sama jak `ClrInstanceID` czy raportów śledzenia zdarzeń dla zdarzenia uruchamiania Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="ad996-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="ad996-108">[out] Typ środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ad996-108">[out] The runtime type.</span></span> <span data-ttu-id="ad996-109">Ten parametr zwraca `COR_PRF_DESKTOP_CLR` w przypadku klasycznej wersji środowiska CLR, lub `COR_PRF_CORE_CLR` core wersję środowiska CLR używanego w technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ad996-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="ad996-110">[out] Główny numer wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ad996-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="ad996-111">[out] Pomocniczy numer wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ad996-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="ad996-112">[out] Numer wersji kompilacji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ad996-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="ad996-113">[out] Numer wersji środowiska CLR, który jest skojarzony z aktualizacji oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="ad996-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="ad996-114">[in] Długość w znakach buforu, który `szVersionString` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="ad996-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="ad996-115">[out] Długość w znakach, z `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="ad996-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="ad996-116">[out] Ciąg wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ad996-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad996-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad996-117">Remarks</span></span>  
 <span data-ttu-id="ad996-118">Możesz przekazać wartości null dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="ad996-118">You may pass null for any parameter.</span></span> <span data-ttu-id="ad996-119">Jednak `pcchVersionString` nie może mieć wartości null Jeśli nie `szVersionString` również ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="ad996-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad996-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad996-120">Requirements</span></span>  
 <span data-ttu-id="ad996-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad996-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad996-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad996-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad996-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad996-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad996-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad996-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad996-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad996-125">See also</span></span>
- [<span data-ttu-id="ad996-126">ICorProfilerInfo3, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad996-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ad996-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ad996-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ad996-128">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="ad996-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
