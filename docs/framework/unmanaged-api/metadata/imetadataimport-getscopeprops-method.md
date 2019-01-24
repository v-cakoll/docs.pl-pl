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
ms.openlocfilehash: d7c41e05ecf4e33f7ca711befdd90275452439df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718861"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="70651-102">IMetaDataImport::GetScopeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="70651-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="70651-103">Pobiera nazwę i opcjonalnie identyfikator wersji zestaw lub moduł w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="70651-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70651-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70651-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70651-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70651-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="70651-106">[out] Bufor nazwy zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="70651-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="70651-107">[in] Rozmiar w znaków `szName`.</span><span class="sxs-lookup"><span data-stu-id="70651-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="70651-108">[out] Liczba znaków dwubajtowych zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="70651-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="70651-109">[out, opcjonalny] Wskaźnik na identyfikator GUID, który unikatowo identyfikuje wersję zestawu lub modułu.</span><span class="sxs-lookup"><span data-stu-id="70651-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70651-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70651-110">Remarks</span></span>  
 <span data-ttu-id="70651-111">[IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) metoda jest używana do ustawiania tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="70651-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70651-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70651-112">Requirements</span></span>  
 <span data-ttu-id="70651-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70651-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70651-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="70651-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70651-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70651-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70651-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70651-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70651-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70651-117">See also</span></span>
- [<span data-ttu-id="70651-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="70651-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="70651-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="70651-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
