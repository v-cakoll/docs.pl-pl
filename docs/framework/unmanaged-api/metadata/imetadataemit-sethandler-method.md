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
ms.openlocfilehash: 6737275fb77e6f177832eb1d96214c37942bcd22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442156"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="99f9f-102">IMetaDataEmit::SetHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="99f9f-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="99f9f-103">Ustawia metodę przywoływaną przez określony `IUnknown` wskaźnik jako wywołanie zwrotne powiadomienia o ponownym mapowaniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="99f9f-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99f9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99f9f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99f9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99f9f-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="99f9f-106">podczas Procedura obsługi do rejestracji.</span><span class="sxs-lookup"><span data-stu-id="99f9f-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99f9f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99f9f-107">Remarks</span></span>  
 <span data-ttu-id="99f9f-108">Aparat metadanych wysyła powiadomienie przy użyciu metody dostarczonej przez `SetHandler`, do kompilatorów, które nie generują rekordów w sposób zoptymalizowany i który chce zoptymalizować zapisane rekordy.</span><span class="sxs-lookup"><span data-stu-id="99f9f-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="99f9f-109">Jeśli metoda wywołania zwrotnego nie zostanie podana za pośrednictwem `SetHandler`, nie będzie przeprowadzana żadna Optymalizacja przy zapisywaniu, z wyjątkiem sytuacji, gdy kilka zakresów importu zostało scalonych przy użyciu `IMapToken` scalania dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="99f9f-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99f9f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99f9f-110">Requirements</span></span>  
 <span data-ttu-id="99f9f-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99f9f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99f9f-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="99f9f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99f9f-113">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="99f9f-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99f9f-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99f9f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f9f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99f9f-115">See also</span></span>

- [<span data-ttu-id="99f9f-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="99f9f-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="99f9f-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="99f9f-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
