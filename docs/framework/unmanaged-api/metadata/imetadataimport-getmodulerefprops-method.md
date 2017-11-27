---
title: "IMetaDataImport::GetModuleRefProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 907743481cf036b7febf57d69ce428a250752c30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="9cf65-102">IMetaDataImport::GetModuleRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cf65-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="9cf65-103">Pobiera nazwę modułu odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="9cf65-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf65-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cf65-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cf65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cf65-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="9cf65-106">[in] Element ModuleRef token metadanych odwołuje się moduł, który można pobrać informacji o metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="9cf65-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="9cf65-107">[out] Bufor do przechowywania nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="9cf65-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9cf65-108">[in] Żądany rozmiar `szName` w znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="9cf65-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="9cf65-109">[out] Rozmiar zwróconego `szName` w znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="9cf65-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cf65-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cf65-110">Requirements</span></span>  
 <span data-ttu-id="9cf65-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cf65-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cf65-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9cf65-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9cf65-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9cf65-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9cf65-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cf65-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf65-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cf65-115">See Also</span></span>  
 [<span data-ttu-id="9cf65-116">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="9cf65-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9cf65-117">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="9cf65-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
