---
title: IMetaDataEmit::SetMethodProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2aefd79e251d751a6c8354fa827863cb5aedf305
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751052"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="94c53-102">IMetaDataEmit::SetMethodProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="94c53-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="94c53-103">Ustawia lub aktualizuje funkcji przechowywaną w określonej wirtualnej adres względny, zdefiniowane przez wcześniejsze wywołanie metody [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="94c53-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c53-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94c53-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94c53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94c53-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="94c53-106">[in] Token dla metody, które mają być zmienione.</span><span class="sxs-lookup"><span data-stu-id="94c53-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="94c53-107">[in] Atrybuty elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="94c53-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="94c53-108">[in] Adres kodu.</span><span class="sxs-lookup"><span data-stu-id="94c53-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="94c53-109">[in] Flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="94c53-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94c53-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94c53-110">Requirements</span></span>  
 <span data-ttu-id="94c53-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94c53-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94c53-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="94c53-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94c53-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94c53-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94c53-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94c53-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c53-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94c53-115">See also</span></span>

- [<span data-ttu-id="94c53-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="94c53-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="94c53-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="94c53-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
