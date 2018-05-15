---
title: IMetaDataEmit::SetRVA — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 371eed84883e2816892c0a6a212a4a89a287cc58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="bb919-102">IMetaDataEmit::SetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb919-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="bb919-103">Ustawia adres względny wirtualnego określonej metody.</span><span class="sxs-lookup"><span data-stu-id="bb919-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb919-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb919-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb919-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb919-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="bb919-106">[in] Token metody docelowej lub w implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="bb919-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="bb919-107">[in] Adres obszaru kodu lub danych.</span><span class="sxs-lookup"><span data-stu-id="bb919-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb919-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb919-108">Requirements</span></span>  
 <span data-ttu-id="bb919-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb919-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb919-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb919-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb919-111">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb919-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb919-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb919-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb919-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb919-113">See Also</span></span>  
 [<span data-ttu-id="bb919-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb919-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="bb919-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb919-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
