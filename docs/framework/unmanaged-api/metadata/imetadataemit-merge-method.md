---
title: "IMetaDataEmit::Merge — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Merge
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42ebc188dfecde068ef8e2979970118fee91ec4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="367f9-102">IMetaDataEmit::Merge — Metoda</span><span class="sxs-lookup"><span data-stu-id="367f9-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="367f9-103">Dodaje określony zakres zaimportowane do listy zakresów do scalenia.</span><span class="sxs-lookup"><span data-stu-id="367f9-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="367f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="367f9-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="367f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="367f9-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="367f9-106">[in] Wskaźnik do [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) obiekt, który identyfikuje zakres zaimportowane do scalenia.</span><span class="sxs-lookup"><span data-stu-id="367f9-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="367f9-107">[in] Wskaźnik do [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) obiekt, który określa token mapowane ponownie.</span><span class="sxs-lookup"><span data-stu-id="367f9-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="367f9-108">[in] Wskaźnik do <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown` obiekt, który określa błędy.</span><span class="sxs-lookup"><span data-stu-id="367f9-108">[in] A pointer to an <!--<<!--zzxref:IUnknown --> `IUnknown`>--> `IUnknown` object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="367f9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="367f9-109">Remarks</span></span>  
 <span data-ttu-id="367f9-110">Wywołanie [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) aby wyzwolić połączenia metadanych w pojedynczy zakres.</span><span class="sxs-lookup"><span data-stu-id="367f9-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="367f9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="367f9-111">Requirements</span></span>  
 <span data-ttu-id="367f9-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="367f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="367f9-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="367f9-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="367f9-114">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="367f9-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="367f9-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="367f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367f9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="367f9-116">See Also</span></span>  
 [<span data-ttu-id="367f9-117">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="367f9-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="367f9-118">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="367f9-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
