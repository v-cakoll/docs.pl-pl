---
title: "GetTypeLibInfo — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetTypeLibInfo
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: GetTypeLibInfo
helpviewer_keywords: GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f6b1ad18809b46b7a2b38137231028f696d51b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="10ecc-102">GetTypeLibInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="10ecc-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="10ecc-103">Zwraca informacje na temat określonej biblioteki typów, sprawdzając jego [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="10ecc-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ecc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10ecc-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10ecc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10ecc-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="10ecc-106">[in] Nazwa pliku biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="10ecc-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="10ecc-107">[out] Identyfikator GUID biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="10ecc-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="10ecc-108">[out] Identyfikator lokalizacji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="10ecc-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="10ecc-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flagę, która identyfikuje docelowego systemu operacyjnego dla biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="10ecc-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="10ecc-110">Typowe wartości to SYS_WIN32 i SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="10ecc-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="10ecc-111">[out] Numer wersji głównej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="10ecc-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="10ecc-112">Na przykład w przypadku wersji *x.y*, numer wersji głównej jest *x*.</span><span class="sxs-lookup"><span data-stu-id="10ecc-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="10ecc-113">[out] Podrzędny numer wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="10ecc-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="10ecc-114">Na przykład w przypadku wersji *x.y*, podrzędny numer wersji jest *y*.</span><span class="sxs-lookup"><span data-stu-id="10ecc-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10ecc-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10ecc-115">Remarks</span></span>  
 <span data-ttu-id="10ecc-116">`GetTypeLibInfo` Funkcja jest wywoływana przez [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="10ecc-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="10ecc-117">Narzędzie to generuje biblioteki typów, który opisuje typów w zestawie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="10ecc-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="10ecc-118">Jeśli żadnych parametrów ma wartość null, funkcja zwraca `HRESULT` z `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="10ecc-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="10ecc-119">W przeciwnym razie zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="10ecc-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10ecc-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10ecc-120">Requirements</span></span>  
 <span data-ttu-id="10ecc-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10ecc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10ecc-122">**Nagłówek:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="10ecc-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="10ecc-123">**Biblioteka:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="10ecc-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="10ecc-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10ecc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ecc-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10ecc-125">See Also</span></span>  
 [<span data-ttu-id="10ecc-126">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="10ecc-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="10ecc-127">[Funkcja LoadTypeLibEx](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="10ecc-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
