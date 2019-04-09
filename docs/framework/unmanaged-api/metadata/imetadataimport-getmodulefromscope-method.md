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
ms.openlocfilehash: f40e6bfdbebdadc41da52564348c6070c18372c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194685"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="1d476-102">IMetaDataImport::GetModuleFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d476-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="1d476-103">Pobiera token metadanych dla modułu odwołania w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="1d476-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d476-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d476-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d476-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d476-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="1d476-106">[out] Wskaźnik do token reprezentujący modułu odwołania w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="1d476-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d476-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d476-107">Requirements</span></span>  
 <span data-ttu-id="1d476-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d476-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d476-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1d476-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d476-110">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1d476-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="1d476-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1d476-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1d476-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d476-112">See also</span></span>

- [<span data-ttu-id="1d476-113">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1d476-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1d476-114">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1d476-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
