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
ms.openlocfilehash: ac0e5db4a87b49d631bad4411f03fae8c1199aea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125635"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="3d085-102">IMetaDataEmit::SetHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d085-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="3d085-103">Ustawia metodę odwołuje się określony `IUnknown` wskaźnik jako wywołania zwrotnego dla tokenu ponowne mapowania.</span><span class="sxs-lookup"><span data-stu-id="3d085-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d085-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d085-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d085-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d085-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="3d085-106">[in] Program obsługi, aby zarejestrować.</span><span class="sxs-lookup"><span data-stu-id="3d085-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d085-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d085-107">Remarks</span></span>  
 <span data-ttu-id="3d085-108">Aparat metadanych wysyła powiadomienie za pomocą metody, która jest dostarczana przez `SetHandler`, aby kompilatory, którzy nie generują rekordów w sposób zoptymalizowany i który chcesz zoptymalizować zapisanych rekordów.</span><span class="sxs-lookup"><span data-stu-id="3d085-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="3d085-109">Jeśli metoda wywołania zwrotnego nie jest oferowana w ramach `SetHandler`, bez optymalizacji będą wykonywane na zapisywanie z wyjątkiem sytuacji, w których kilka importować zakresy zostały scalone przy użyciu `IMapToken` na scalanie dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="3d085-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d085-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d085-110">Requirements</span></span>  
 <span data-ttu-id="3d085-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d085-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d085-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3d085-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d085-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d085-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3d085-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3d085-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d085-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d085-115">See also</span></span>

- [<span data-ttu-id="3d085-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3d085-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3d085-117">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3d085-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
