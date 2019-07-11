---
title: IMetaDataEmit::SetMethodImplFlags — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a437ff11114ea8d577b2fc3b81cd981cebb8c8d6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751068"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="aae39-102">IMetaDataEmit::SetMethodImplFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="aae39-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="aae39-103">Ustawia lub aktualizuje podpis implementacji metody dziedziczonej, która odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="aae39-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aae39-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aae39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aae39-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="aae39-106">[in] Token dla metody, które mają być zmienione.</span><span class="sxs-lookup"><span data-stu-id="aae39-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="aae39-107">[in] Kombinacja wartości [cormethodimpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenie, które określa funkcje implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="aae39-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aae39-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aae39-108">Requirements</span></span>  
 <span data-ttu-id="aae39-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aae39-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aae39-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="aae39-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aae39-111">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aae39-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aae39-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aae39-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae39-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aae39-113">See also</span></span>

- [<span data-ttu-id="aae39-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="aae39-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="aae39-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="aae39-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
