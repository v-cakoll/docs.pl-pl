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
ms.openlocfilehash: d734f35b5878ec39e4f2159c326283d168e3be2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197896"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="113c8-102">ResolveTypeLib — Metoda</span><span class="sxs-lookup"><span data-stu-id="113c8-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="113c8-103">Rozpoznaje prostą nazwę biblioteki typów, przywracając jego w pełni kwalifikowaną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="113c8-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="113c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="113c8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="113c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="113c8-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="113c8-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierający prostą nazwę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="113c8-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="113c8-107">[in] Identyfikator GUID jest przypisany do biblioteki typów w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="113c8-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="113c8-108">[in] Identyfikator lokalizacji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="113c8-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="113c8-109">[in] Główny numer wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="113c8-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="113c8-110">Na przykład w przypadku wersji *x.y*, główny numer wersji jest *x*.</span><span class="sxs-lookup"><span data-stu-id="113c8-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="113c8-111">[in] Pomocniczy numer wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="113c8-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="113c8-112">Na przykład w przypadku wersji *x.y*, pomocniczy numer wersji jest *y*.</span><span class="sxs-lookup"><span data-stu-id="113c8-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="113c8-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flagę, która identyfikuje środowisko operacyjne.</span><span class="sxs-lookup"><span data-stu-id="113c8-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="113c8-114">Typowe wartości to SYS_WIN32 i SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="113c8-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="113c8-115">[out] Wskaźnik do [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierającą pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="113c8-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="113c8-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="113c8-116">Remarks</span></span>  
 <span data-ttu-id="113c8-117">`ResolveTypeLib` Metoda jest wywoływana przez [loadtypelibwithresolver — funkcja](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) podczas [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="113c8-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="113c8-118">Niestandardowe implementacje tego interfejsu musi zwracać [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierającą pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="113c8-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="113c8-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="113c8-119">Requirements</span></span>  
 <span data-ttu-id="113c8-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="113c8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="113c8-121">**Nagłówek:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="113c8-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="113c8-122">**Biblioteka:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="113c8-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="113c8-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="113c8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113c8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="113c8-124">See also</span></span>

- [<span data-ttu-id="113c8-125">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="113c8-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="113c8-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="113c8-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
