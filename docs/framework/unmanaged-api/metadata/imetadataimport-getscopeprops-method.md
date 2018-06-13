---
title: IMetaDataImport::GetScopeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24ece9bb614957e02c81d3a0f0a0eefe59f3febc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446548"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="3aa93-102">IMetaDataImport::GetScopeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="3aa93-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="3aa93-103">Pobiera nazwę i opcjonalnie identyfikator wersji zestawu lub modułu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="3aa93-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3aa93-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3aa93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3aa93-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3aa93-106">[out] Bufor dla nazwy zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="3aa93-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3aa93-107">[in] Rozmiar w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="3aa93-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="3aa93-108">[out] Liczba zwracanych w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="3aa93-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="3aa93-109">[out, opcjonalnie] Wskaźnik do identyfikatora GUID, który unikatowo identyfikuje wersję zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="3aa93-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aa93-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3aa93-110">Remarks</span></span>  
 <span data-ttu-id="3aa93-111">[IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) metoda służy do ustawiania tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="3aa93-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aa93-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3aa93-112">Requirements</span></span>  
 <span data-ttu-id="3aa93-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aa93-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aa93-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3aa93-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3aa93-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3aa93-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3aa93-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aa93-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa93-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3aa93-117">See Also</span></span>  
 [<span data-ttu-id="3aa93-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3aa93-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3aa93-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3aa93-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
