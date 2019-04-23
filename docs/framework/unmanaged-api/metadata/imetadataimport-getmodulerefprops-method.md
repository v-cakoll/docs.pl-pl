---
title: IMetaDataImport::GetModuleRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e948644e4f2d91b2f1e3e3627f7adbe204dee9d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155418"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="b3f07-102">IMetaDataImport::GetModuleRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3f07-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="b3f07-103">Pobiera nazwę modułu odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="b3f07-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3f07-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3f07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3f07-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="b3f07-106">[in] Element ModuleRef metadanych tokenu który odwołuje się moduł, aby uzyskać informacje o metadanych.</span><span class="sxs-lookup"><span data-stu-id="b3f07-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="b3f07-107">[out] Bufor do przechowywania nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="b3f07-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b3f07-108">[in] Żądany rozmiar `szName` w znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="b3f07-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b3f07-109">[out] Rozmiar zwróconego `szName` w znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="b3f07-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f07-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3f07-110">Requirements</span></span>  
 <span data-ttu-id="b3f07-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3f07-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3f07-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b3f07-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3f07-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3f07-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3f07-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3f07-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f07-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3f07-115">See also</span></span>

- [<span data-ttu-id="b3f07-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3f07-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b3f07-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3f07-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
