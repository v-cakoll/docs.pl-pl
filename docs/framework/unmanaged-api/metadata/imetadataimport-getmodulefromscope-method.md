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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777692"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="22f18-102">IMetaDataImport::GetModuleFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="22f18-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="22f18-103">Pobiera token metadanych dla modułu odwołania w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="22f18-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22f18-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22f18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22f18-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="22f18-106">[out] Wskaźnik do token reprezentujący modułu odwołania w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="22f18-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22f18-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22f18-107">Requirements</span></span>  
 <span data-ttu-id="22f18-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22f18-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22f18-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="22f18-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22f18-110">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22f18-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22f18-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22f18-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f18-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22f18-112">See also</span></span>

- [<span data-ttu-id="22f18-113">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="22f18-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="22f18-114">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="22f18-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
