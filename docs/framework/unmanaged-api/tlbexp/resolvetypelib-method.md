---
title: ResolveTypeLib — Metoda
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b87460b9e525f2cf91b8f177c06286b5bbb3c52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486124"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="8b18d-102">ResolveTypeLib — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b18d-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="8b18d-103">Rozpoznaje prostą nazwę biblioteki typów, przywracając jego w pełni kwalifikowaną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="8b18d-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b18d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b18d-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b18d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b18d-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="8b18d-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierający prostą nazwę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8b18d-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="8b18d-107">[in] Identyfikator GUID jest przypisany do biblioteki typów w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="8b18d-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="8b18d-108">[in] Identyfikator lokalizacji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8b18d-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="8b18d-109">[in] Główny numer wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8b18d-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="8b18d-110">Na przykład w przypadku wersji *x.y*, główny numer wersji jest *x*.</span><span class="sxs-lookup"><span data-stu-id="8b18d-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="8b18d-111">[in] Pomocniczy numer wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8b18d-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="8b18d-112">Na przykład w przypadku wersji *x.y*, pomocniczy numer wersji jest *y*.</span><span class="sxs-lookup"><span data-stu-id="8b18d-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="8b18d-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flagę, która identyfikuje środowisko operacyjne.</span><span class="sxs-lookup"><span data-stu-id="8b18d-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="8b18d-114">Typowe wartości to SYS_WIN32 i SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="8b18d-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="8b18d-115">[out] Wskaźnik do [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierającą pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="8b18d-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b18d-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b18d-116">Remarks</span></span>  
 <span data-ttu-id="8b18d-117">`ResolveTypeLib` Metoda jest wywoływana przez [loadtypelibwithresolver — funkcja](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) podczas [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="8b18d-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="8b18d-118">Niestandardowe implementacje tego interfejsu musi zwracać [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierającą pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="8b18d-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b18d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b18d-119">Requirements</span></span>  
 <span data-ttu-id="8b18d-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b18d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b18d-121">**Nagłówek:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="8b18d-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="8b18d-122">**Biblioteka:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="8b18d-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="8b18d-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b18d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b18d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b18d-124">See also</span></span>
- [<span data-ttu-id="8b18d-125">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="8b18d-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="8b18d-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="8b18d-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
