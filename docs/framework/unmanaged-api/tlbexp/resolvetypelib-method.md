---
title: "ResolveTypeLib — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72d1cedbfc1a1ec6c3588a7b0be9cf657d7369fd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="ff630-102">ResolveTypeLib — Metoda</span><span class="sxs-lookup"><span data-stu-id="ff630-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="ff630-103">Rozpoznaje prostą nazwę biblioteki typów, przywracając jego w pełni kwalifikowaną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ff630-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff630-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff630-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ff630-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff630-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="ff630-106">[in] A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) zawierającą prostą nazwę biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="ff630-106">[in] A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="ff630-107">[in] Identyfikator GUID przypisane do biblioteki typów w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="ff630-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="ff630-108">[in] Identyfikator lokalizacji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="ff630-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="ff630-109">[in] Numer wersji głównej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="ff630-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="ff630-110">Na przykład w przypadku wersji *x.y*, numer wersji głównej jest *x*.</span><span class="sxs-lookup"><span data-stu-id="ff630-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="ff630-111">[in] Podrzędny numer wersji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="ff630-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="ff630-112">Na przykład w przypadku wersji *x.y*, podrzędny numer wersji jest *y*.</span><span class="sxs-lookup"><span data-stu-id="ff630-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="ff630-113">[in] A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) Flaga, która identyfikuje środowisku operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="ff630-113">[in] A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) flag that identifies the operating environment.</span></span> <span data-ttu-id="ff630-114">Typowe wartości to SYS_WIN32 i SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="ff630-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="ff630-115">[out] Wskaźnik do [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) zawiera pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="ff630-115">[out] A pointer to a [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff630-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff630-116">Remarks</span></span>  
 <span data-ttu-id="ff630-117">`ResolveTypeLib` Metoda jest wywoływana przez [loadtypelibwithresolver — funkcja](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) podczas [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ff630-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="ff630-118">Niestandardowe implementacje tego interfejsu musi zwracać [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) zawiera pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.</span><span class="sxs-lookup"><span data-stu-id="ff630-118">Custom implementations of this interface must return a [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff630-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff630-119">Requirements</span></span>  
 <span data-ttu-id="ff630-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff630-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff630-121">**Nagłówek:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="ff630-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="ff630-122">**Biblioteka:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="ff630-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="ff630-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff630-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff630-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff630-124">See Also</span></span>  
 [<span data-ttu-id="ff630-125">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="ff630-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="ff630-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="ff630-126">LoadTypeLibEx</span></span>](http://msdn.microsoft.com/library/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
