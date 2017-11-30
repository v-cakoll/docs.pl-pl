---
title: "IMetaDataImport::GetSigFromToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetSigFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ab7df32641d4fcd093f1ed31eb9ed7c7954e6bf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="32681-102">IMetaDataImport::GetSigFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="32681-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="32681-103">Pobiera podpisu binarne metadane skojarzone z określonym tokenem.</span><span class="sxs-lookup"><span data-stu-id="32681-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32681-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32681-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32681-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32681-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="32681-106">[in] Token do zwrócenia podpis binarny metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="32681-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="32681-107">[out] Wskaźnik do sygnatury metadane zwrócony.</span><span class="sxs-lookup"><span data-stu-id="32681-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="32681-108">[out] Rozmiar w bajtach podpisu metadanych binarnego.</span><span class="sxs-lookup"><span data-stu-id="32681-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32681-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32681-109">Requirements</span></span>  
 <span data-ttu-id="32681-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32681-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32681-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="32681-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32681-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32681-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32681-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32681-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32681-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32681-114">See Also</span></span>  
 [<span data-ttu-id="32681-115">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="32681-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="32681-116">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="32681-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
