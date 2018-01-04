---
title: "IMetaDataEmit::SetHandler — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetHandler
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccb35c12e1d9c2fade9d8760d0a2e39807c92de9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="35064-102">IMetaDataEmit::SetHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="35064-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="35064-103">Ustawia metodę odwołuje się określony `IUnknown` wskaźnika jako wywołanie zwrotne powiadomienia dla tokenu ponowne mapowania.</span><span class="sxs-lookup"><span data-stu-id="35064-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35064-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35064-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35064-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35064-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="35064-106">[in] Program obsługi do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="35064-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35064-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35064-107">Remarks</span></span>  
 <span data-ttu-id="35064-108">Aparat metadanych wysyła powiadomienia za pomocą metody, która jest dostarczana przez `SetHandler`, aby kompilatorów, które nie generują rekordów w sposób zoptymalizowany i który chcesz zoptymalizować zapisane rekordy.</span><span class="sxs-lookup"><span data-stu-id="35064-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="35064-109">Jeśli metoda wywołania zwrotnego nie jest zapewniana za pomocą `SetHandler`, optymalizacja nie zostaną wykonane na zapisywanie z wyjątkiem przypadków, w której kilka zaimportować zakresy zostały scalone przy użyciu `IMapToken` na scalanie dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="35064-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35064-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35064-110">Requirements</span></span>  
 <span data-ttu-id="35064-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35064-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35064-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="35064-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="35064-113">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35064-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35064-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35064-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35064-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35064-115">See Also</span></span>  
 [<span data-ttu-id="35064-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="35064-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="35064-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="35064-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
