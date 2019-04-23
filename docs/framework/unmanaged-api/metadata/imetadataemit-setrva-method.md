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
ms.openlocfilehash: e17a6846ba0276ec7ba423ab25e3f11baf278d03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098757"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="7a1fb-102">IMetaDataEmit::SetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a1fb-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="7a1fb-103">Ustawia adres względny wirtualnej określonej metody.</span><span class="sxs-lookup"><span data-stu-id="7a1fb-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a1fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a1fb-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a1fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a1fb-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="7a1fb-106">[in] Token metody docelowej lub implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="7a1fb-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="7a1fb-107">[in] Adres obszaru kodu lub danych.</span><span class="sxs-lookup"><span data-stu-id="7a1fb-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a1fb-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a1fb-108">Requirements</span></span>  
 <span data-ttu-id="7a1fb-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a1fb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a1fb-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7a1fb-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a1fb-111">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a1fb-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a1fb-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a1fb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1fb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a1fb-113">See also</span></span>

- [<span data-ttu-id="7a1fb-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a1fb-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7a1fb-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a1fb-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
