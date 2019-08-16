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
ms.openlocfilehash: 0f274befe78e45be3e53335572fd9c1e0b401fd3
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040171"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="c5bf9-102">ResolveTypeLib — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5bf9-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="c5bf9-103">Rozpoznaje prostą nazwę biblioteki typów przez zwrócenie jej w pełni kwalifikowanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5bf9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5bf9-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5bf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5bf9-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="c5bf9-106">podczas [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , który zawiera prostą nazwę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="c5bf9-107">podczas Identyfikator GUID przypisany do biblioteki typów w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="c5bf9-108">podczas Identyfikator lokalizacji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="c5bf9-109">podczas Numer wersji głównej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="c5bf9-110">Na przykład w przypadku wersji *x. y*główny numer wersji to *x*.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="c5bf9-111">podczas Numer wersji pomocniczej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="c5bf9-112">Na przykład w przypadku wersji *x. y*pomocniczy numer wersji to *y*.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="c5bf9-113">podczas Flaga [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) , która identyfikuje środowisko operacyjne.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-113">[in] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="c5bf9-114">Wspólne wartości to SYS_WIN32 i SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="c5bf9-115">określoną Wskaźnik do typu [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , który zawiera pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametrze.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5bf9-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5bf9-116">Remarks</span></span>  
 <span data-ttu-id="c5bf9-117">Metoda jest wywoływana przez [funkcję LoadTypeLibWithResolver —](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) podczas przetwarzania [Tlbexp. exe (Eksporter biblioteki typów).](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) `ResolveTypeLib`</span><span class="sxs-lookup"><span data-stu-id="c5bf9-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="c5bf9-118">Niestandardowe implementacje tego interfejsu muszą zwracać element [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , który zawiera pełną ścieżkę biblioteki typów o nazwie w `bstrSimpleName` parametrze.</span><span class="sxs-lookup"><span data-stu-id="c5bf9-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5bf9-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5bf9-119">Requirements</span></span>  
 <span data-ttu-id="c5bf9-120">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5bf9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5bf9-121">**Nagłówki** TlbRef. idl, TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="c5bf9-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="c5bf9-122">**Biblioteki** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="c5bf9-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="c5bf9-123">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5bf9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bf9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5bf9-124">See also</span></span>

- [<span data-ttu-id="c5bf9-125">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="c5bf9-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="c5bf9-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="c5bf9-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
