---
title: IMetaDataEmit::Merge — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fee3c0b82bec102d8e292a76d3df5a14d40ace8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757670"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="f1281-102">IMetaDataEmit::Merge — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1281-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="f1281-103">Dodaje określony zakres zaimportowane do listy zakresów do scalenia.</span><span class="sxs-lookup"><span data-stu-id="f1281-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1281-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1281-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1281-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1281-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="f1281-106">[in] Wskaźnik do [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) obiekt, który identyfikuje zakres zaimportowane do scalenia.</span><span class="sxs-lookup"><span data-stu-id="f1281-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="f1281-107">[in] Wskaźnik do [imaptoken —](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) obiekt, który określa tokenu mapowane ponownie.</span><span class="sxs-lookup"><span data-stu-id="f1281-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="f1281-108">[in] Wskaźnik do [IUnknown](/cpp/atl/iunknown) obiektu, który określa błędy.</span><span class="sxs-lookup"><span data-stu-id="f1281-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1281-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1281-109">Remarks</span></span>  
 <span data-ttu-id="f1281-110">Wywołaj [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) wyzwolić połączenia metadanych do jednego zakresu.</span><span class="sxs-lookup"><span data-stu-id="f1281-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1281-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1281-111">Requirements</span></span>  
 <span data-ttu-id="f1281-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1281-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1281-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f1281-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1281-114">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1281-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1281-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1281-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1281-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1281-116">See also</span></span>

- [<span data-ttu-id="f1281-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1281-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f1281-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1281-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
