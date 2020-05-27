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
ms.openlocfilehash: 4fa227d18b8cb10936d93fda9bcaf413ce63ca3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003954"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="a92c9-102">IMetaDataEmit::SetHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="a92c9-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="a92c9-103">Ustawia metodę przywoływaną przez określony `IUnknown` wskaźnik jako wywołanie zwrotne powiadomienia o ponownym mapowaniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="a92c9-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a92c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a92c9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a92c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a92c9-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="a92c9-106">podczas Procedura obsługi do rejestracji.</span><span class="sxs-lookup"><span data-stu-id="a92c9-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a92c9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a92c9-107">Remarks</span></span>  
 <span data-ttu-id="a92c9-108">Aparat metadanych wysyła powiadomienie przy użyciu metody dostarczonej przez `SetHandler` , do kompilatorów, które nie generują rekordów w sposób zoptymalizowany i który chce zoptymalizować zapisane rekordy.</span><span class="sxs-lookup"><span data-stu-id="a92c9-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="a92c9-109">Jeśli nie podano metody wywołania zwrotnego za pośrednictwem programu `SetHandler` , nie będzie przeprowadzana żadna Optymalizacja przy zapisywaniu, z wyjątkiem sytuacji, gdy kilka zakresów importu zostało scalonych przy użyciu `IMapToken` scalania dla każdego zakresu.</span><span class="sxs-lookup"><span data-stu-id="a92c9-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a92c9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a92c9-110">Requirements</span></span>  
 <span data-ttu-id="a92c9-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a92c9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a92c9-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a92c9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a92c9-113">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a92c9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a92c9-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a92c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a92c9-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a92c9-115">See also</span></span>

- [<span data-ttu-id="a92c9-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a92c9-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a92c9-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a92c9-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
