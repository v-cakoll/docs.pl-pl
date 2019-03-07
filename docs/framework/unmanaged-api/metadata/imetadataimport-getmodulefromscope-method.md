---
title: IMetaDataImport::GetModuleFromScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1118c29acd926821e3b5db31694df9935bdefb9e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468809"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="6791a-102">IMetaDataImport::GetModuleFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="6791a-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="6791a-103">Pobiera token metadanych dla modułu odwołania w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="6791a-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6791a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6791a-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6791a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6791a-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="6791a-106">[out] Wskaźnik do token reprezentujący modułu odwołania w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="6791a-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6791a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6791a-107">Requirements</span></span>  
 <span data-ttu-id="6791a-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6791a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6791a-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6791a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6791a-110">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6791a-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6791a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6791a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6791a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6791a-112">See also</span></span>
- [<span data-ttu-id="6791a-113">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6791a-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6791a-114">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6791a-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
