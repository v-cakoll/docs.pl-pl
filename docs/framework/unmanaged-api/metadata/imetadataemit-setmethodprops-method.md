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
ms.openlocfilehash: 5ef6771ec3f458c20701cc330a5730367b3c5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="d9f7e-102">IMetaDataEmit::SetMethodProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9f7e-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="d9f7e-103">Ustawia lub aktualizuje funkcję przechowywane w określonej wirtualnej adres względny, zdefiniowany przez poprzednie wywołanie do metody [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="d9f7e-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9f7e-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9f7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9f7e-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="d9f7e-106">[in] Token metody zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="d9f7e-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="d9f7e-107">[in] Atrybuty elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d9f7e-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="d9f7e-108">[in] Adres kodu.</span><span class="sxs-lookup"><span data-stu-id="d9f7e-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="d9f7e-109">[in] Flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="d9f7e-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9f7e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9f7e-110">Requirements</span></span>  
 <span data-ttu-id="d9f7e-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9f7e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9f7e-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d9f7e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9f7e-113">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9f7e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9f7e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9f7e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f7e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9f7e-115">See Also</span></span>  
 [<span data-ttu-id="d9f7e-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9f7e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d9f7e-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9f7e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
