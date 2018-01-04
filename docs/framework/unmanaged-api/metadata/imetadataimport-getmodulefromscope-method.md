---
title: "IMetaDataImport::GetModuleFromScope — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleFromScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b389df634a69bff6197ae11dea96fbb6344dd369
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="b7c90-102">IMetaDataImport::GetModuleFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7c90-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="b7c90-103">Pobiera token metadane dla modułu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="b7c90-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7c90-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7c90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7c90-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="b7c90-106">[out] Wskaźnik do token reprezentujący modułu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="b7c90-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7c90-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7c90-107">Requirements</span></span>  
 <span data-ttu-id="b7c90-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7c90-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7c90-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b7c90-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7c90-110">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7c90-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7c90-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7c90-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c90-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7c90-112">See Also</span></span>  
 [<span data-ttu-id="b7c90-113">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7c90-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b7c90-114">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7c90-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
