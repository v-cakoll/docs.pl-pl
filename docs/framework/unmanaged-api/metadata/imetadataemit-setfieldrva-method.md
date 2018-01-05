---
title: "IMetaDataEmit::SetFieldRVA — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldRVA
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 260d5458af9fb8fbc8161018c438346fd58af06f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="a8250-102">IMetaDataEmit::SetFieldRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="a8250-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="a8250-103">Ustawia wartość zmiennej globalnej względną wirtualnego adresu pola odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="a8250-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8250-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8250-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8250-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8250-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="a8250-106">[in] Token pola docelowego.</span><span class="sxs-lookup"><span data-stu-id="a8250-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="a8250-107">[in] Adres obszaru kodu lub danych.</span><span class="sxs-lookup"><span data-stu-id="a8250-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8250-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8250-108">Requirements</span></span>  
 <span data-ttu-id="a8250-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8250-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8250-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a8250-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8250-111">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8250-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8250-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8250-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8250-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8250-113">See Also</span></span>  
 [<span data-ttu-id="a8250-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8250-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a8250-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8250-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
