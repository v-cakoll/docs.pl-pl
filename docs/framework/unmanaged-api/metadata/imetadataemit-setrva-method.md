---
title: "IMetaDataEmit::SetRVA — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetRVA
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25f0e20e1249067dfd9162b84c07b38e9b97de15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="6270f-102">IMetaDataEmit::SetRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="6270f-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="6270f-103">Ustawia adres względny wirtualnego określonej metody.</span><span class="sxs-lookup"><span data-stu-id="6270f-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6270f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6270f-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6270f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6270f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="6270f-106">[in] Token metody docelowej lub w implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="6270f-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="6270f-107">[in] Adres obszaru kodu lub danych.</span><span class="sxs-lookup"><span data-stu-id="6270f-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6270f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6270f-108">Requirements</span></span>  
 <span data-ttu-id="6270f-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6270f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6270f-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6270f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6270f-111">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6270f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6270f-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6270f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6270f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6270f-113">See Also</span></span>  
 [<span data-ttu-id="6270f-114">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="6270f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6270f-115">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="6270f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
