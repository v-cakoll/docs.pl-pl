---
title: "IMetaDataEmit::SetFieldMarshal — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldMarshal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3ef1d50d0d74a92a5bcaf23981226e5a6c852edd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="18d8a-102">IMetaDataEmit::SetFieldMarshal — Metoda</span><span class="sxs-lookup"><span data-stu-id="18d8a-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="18d8a-103">Ustawia PInvoke przekazywanie informacji dla parametru pola, zwracany — metoda lub metody odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="18d8a-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18d8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18d8a-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18d8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18d8a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="18d8a-106">[in] Token dla elementu docelowego danych.</span><span class="sxs-lookup"><span data-stu-id="18d8a-106">[in] The token for target data item.</span></span> <span data-ttu-id="18d8a-107">Jest to `mdFieldDef` lub `mdParamDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="18d8a-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="18d8a-108">[in] Podpis dla typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="18d8a-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="18d8a-109">[in] Liczba bajtów w `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="18d8a-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18d8a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18d8a-110">Requirements</span></span>  
 <span data-ttu-id="18d8a-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18d8a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18d8a-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18d8a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18d8a-113">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18d8a-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18d8a-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18d8a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d8a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18d8a-115">See Also</span></span>  
 [<span data-ttu-id="18d8a-116">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="18d8a-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="18d8a-117">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="18d8a-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
