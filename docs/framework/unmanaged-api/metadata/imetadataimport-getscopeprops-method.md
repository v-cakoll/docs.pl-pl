---
title: "IMetaDataImport::GetScopeProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetScopeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b0936a9f47e2d0fa52816b78a7eecf3d244d594
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="b4661-102">IMetaDataImport::GetScopeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4661-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="b4661-103">Pobiera nazwę i opcjonalnie identyfikator wersji zestawu lub modułu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="b4661-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4661-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4661-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4661-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4661-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b4661-106">[out] Bufor dla nazwy zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="b4661-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b4661-107">[in] Rozmiar w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="b4661-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b4661-108">[out] Liczba zwracanych w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="b4661-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="b4661-109">[out, opcjonalnie] Wskaźnik do identyfikatora GUID, który unikatowo identyfikuje wersję zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="b4661-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4661-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4661-110">Remarks</span></span>  
 <span data-ttu-id="b4661-111">[IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) metoda służy do ustawiania tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="b4661-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4661-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4661-112">Requirements</span></span>  
 <span data-ttu-id="b4661-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4661-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4661-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b4661-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b4661-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4661-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b4661-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4661-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4661-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4661-117">See Also</span></span>  
 [<span data-ttu-id="b4661-118">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="b4661-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b4661-119">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b4661-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
