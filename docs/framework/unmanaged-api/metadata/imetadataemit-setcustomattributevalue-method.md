---
title: IMetaDataEmit::SetCustomAttributeValue — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: fd5e71071de9e6afebc8f1848e0af8835f22c9bf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448124"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="b1318-102">IMetaDataEmit::SetCustomAttributeValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1318-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="b1318-103">Ustawia lub aktualizuje wartość atrybutu niestandardowego zdefiniowanego przez poprzednie wywołanie do [IMetaDataEmit::D efinecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="b1318-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1318-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1318-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1318-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1318-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="b1318-106">podczas Token docelowego atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b1318-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="b1318-107">podczas Wskaźnik do tablicy zawierającej atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="b1318-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="b1318-108">podczas Rozmiar atrybutu niestandardowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b1318-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1318-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1318-109">Requirements</span></span>  
 <span data-ttu-id="b1318-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1318-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1318-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b1318-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1318-112">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1318-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1318-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1318-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1318-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1318-114">See also</span></span>

- [<span data-ttu-id="b1318-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1318-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b1318-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1318-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
