---
title: GetTypeLibInfo — Funkcja
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d12cbb66464baba4ee706ccb076764fbf025fc5f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786181"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="dc6aa-102">GetTypeLibInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="dc6aa-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="dc6aa-103">Zwraca informacje dotyczące określonej biblioteki typu, sprawdzając jego [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) struktury.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc6aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc6aa-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dc6aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc6aa-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="dc6aa-106">[in] Nazwa pliku biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="dc6aa-107">[out] Identyfikator GUID biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="dc6aa-108">[out] Identyfikator lokalizacji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="dc6aa-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flagę, która identyfikuje docelowego systemu operacyjnego dla biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="dc6aa-110">Typowe wartości to SYS_WIN32 i SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="dc6aa-111">[out] Główny numer wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="dc6aa-112">Na przykład w przypadku wersji *x.y*, główny numer wersji jest *x*.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="dc6aa-113">[out] Pomocniczy numer wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="dc6aa-114">Na przykład w przypadku wersji *x.y*, pomocniczy numer wersji jest *y*.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc6aa-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc6aa-115">Remarks</span></span>  
 <span data-ttu-id="dc6aa-116">`GetTypeLibInfo` Funkcja jest wywoływana przez [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="dc6aa-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="dc6aa-117">To narzędzie generuje bibliotekę typów opisującą typy w zestawie środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="dc6aa-118">Jeśli którykolwiek z parametrów ma wartość null, funkcja zwraca `HRESULT` z `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="dc6aa-119">W przeciwnym razie zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc6aa-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc6aa-120">Requirements</span></span>  
 <span data-ttu-id="dc6aa-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc6aa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc6aa-122">**Nagłówek:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="dc6aa-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="dc6aa-123">**Biblioteka:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="dc6aa-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="dc6aa-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc6aa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc6aa-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc6aa-125">See also</span></span>

- [<span data-ttu-id="dc6aa-126">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="dc6aa-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="dc6aa-127">LoadTypeLibEx — funkcja</span><span class="sxs-lookup"><span data-stu-id="dc6aa-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
