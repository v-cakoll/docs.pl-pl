---
title: IMetaDataEmit::SetHandler — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 511105fef030dbc189b463864035f86d39327032
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732534"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="72ffe-102">IMetaDataEmit::SetHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="72ffe-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="72ffe-103">Ustawia metodę odwołuje się określony `IUnknown` wskaźnik jako wywołania zwrotnego dla tokenu ponowne mapowania.</span><span class="sxs-lookup"><span data-stu-id="72ffe-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ffe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72ffe-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72ffe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72ffe-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="72ffe-106">[in] Program obsługi, aby zarejestrować.</span><span class="sxs-lookup"><span data-stu-id="72ffe-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72ffe-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72ffe-107">Remarks</span></span>  
 <span data-ttu-id="72ffe-108">Aparat metadanych wysyła powiadomienie za pomocą metody, która jest dostarczana przez `SetHandler`, aby kompilatory, którzy nie generują rekordów w sposób zoptymalizowany i który chcesz zoptymalizować zapisanych rekordów.</span><span class="sxs-lookup"><span data-stu-id="72ffe-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="72ffe-109">Jeśli metoda wywołania zwrotnego nie jest oferowana w ramach `SetHandler`, bez optymalizacji będą wykonywane na zapisywanie z wyjątkiem sytuacji, w których kilka importować zakresy zostały scalone przy użyciu `IMapToken` na scalanie dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="72ffe-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72ffe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72ffe-110">Requirements</span></span>  
 <span data-ttu-id="72ffe-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72ffe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72ffe-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="72ffe-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72ffe-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72ffe-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72ffe-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72ffe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ffe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72ffe-115">See also</span></span>
- [<span data-ttu-id="72ffe-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="72ffe-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="72ffe-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="72ffe-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
