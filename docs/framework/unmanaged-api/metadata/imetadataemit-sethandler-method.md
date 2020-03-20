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
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177539"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="fe134-102">IMetaDataEmit::SetHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe134-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="fe134-103">Ustawia metodę, do którą `IUnknown` odwołuje się określony wskaźnik jako wywołanie zwrotne powiadomień dla ponownego mapowania tokenu.</span><span class="sxs-lookup"><span data-stu-id="fe134-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe134-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe134-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe134-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe134-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="fe134-106">[w] Program obsługi do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="fe134-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe134-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe134-107">Remarks</span></span>  
 <span data-ttu-id="fe134-108">Aparat metadanych wysyła powiadomienie przy użyciu `SetHandler`metody, która jest dostarczana przez , do kompilatorów, które nie generują rekordów w sposób zoptymalizowany i które chcą zoptymalizować zapisane rekordy.</span><span class="sxs-lookup"><span data-stu-id="fe134-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="fe134-109">Jeśli metoda wywołania zwrotnego `SetHandler`nie jest dostarczana za pośrednictwem , nie zostanie przeprowadzona optymalizacja przy zapisywaniu, z wyjątkiem sytuacji, gdy kilka zakresów importu zostało scalonych przy użyciu `IMapToken` scalania dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="fe134-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe134-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe134-110">Requirements</span></span>  
 <span data-ttu-id="fe134-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe134-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe134-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe134-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe134-113">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe134-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe134-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe134-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe134-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe134-115">See also</span></span>

- [<span data-ttu-id="fe134-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fe134-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fe134-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe134-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
