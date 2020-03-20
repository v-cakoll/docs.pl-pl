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
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175710"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="a7ccb-102">IMetaDataEmit::Merge — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7ccb-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="a7ccb-103">Dodaje określony importowany zakres do listy zakresów do scalenia.</span><span class="sxs-lookup"><span data-stu-id="a7ccb-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ccb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7ccb-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7ccb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7ccb-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="a7ccb-106">[w] Wskaźnik do obiektu [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) który identyfikuje importowany zakres do scalenia.</span><span class="sxs-lookup"><span data-stu-id="a7ccb-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="a7ccb-107">[w] Wskaźnik do obiektu [IMapToken,](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) który określa ponowne mapowanie tokenu.</span><span class="sxs-lookup"><span data-stu-id="a7ccb-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="a7ccb-108">[w] Wskaźnik do [IUnknown](/cpp/atl/iunknown) obiektu, który określa błędy.</span><span class="sxs-lookup"><span data-stu-id="a7ccb-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ccb-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7ccb-109">Remarks</span></span>  
 <span data-ttu-id="a7ccb-110">Wywołanie [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) wyzwolić połączenie metadanych w jednym zakresie.</span><span class="sxs-lookup"><span data-stu-id="a7ccb-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ccb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7ccb-111">Requirements</span></span>  
 <span data-ttu-id="a7ccb-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ccb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ccb-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7ccb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7ccb-114">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7ccb-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7ccb-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ccb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ccb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7ccb-116">See also</span></span>

- [<span data-ttu-id="a7ccb-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a7ccb-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a7ccb-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7ccb-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
