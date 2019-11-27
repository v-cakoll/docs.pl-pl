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
ms.openlocfilehash: 06894f238f9fda3111d5484bb1b2add183a5abb2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448059"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="7d16d-102">IMetaDataEmit::Merge — Metoda</span><span class="sxs-lookup"><span data-stu-id="7d16d-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="7d16d-103">Dodaje określony zaimportowany zakres do listy zakresów, które mają zostać scalone.</span><span class="sxs-lookup"><span data-stu-id="7d16d-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d16d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d16d-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d16d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d16d-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="7d16d-106">podczas Wskaźnik do obiektu [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , który identyfikuje importowany zakres do scalenia.</span><span class="sxs-lookup"><span data-stu-id="7d16d-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="7d16d-107">podczas Wskaźnik do obiektu [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) , który określa ponowne mapowanie tokenu.</span><span class="sxs-lookup"><span data-stu-id="7d16d-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="7d16d-108">podczas Wskaźnik do obiektu [IUnknown](/cpp/atl/iunknown) , który określa błędy.</span><span class="sxs-lookup"><span data-stu-id="7d16d-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d16d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d16d-109">Remarks</span></span>  
 <span data-ttu-id="7d16d-110">Wywołanie [IMetaDataEmit:: MergeEnd —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) w celu wyzwolenia fuzji metadanych w pojedynczym zakresie.</span><span class="sxs-lookup"><span data-stu-id="7d16d-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d16d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d16d-111">Requirements</span></span>  
 <span data-ttu-id="7d16d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d16d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d16d-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7d16d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d16d-114">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7d16d-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d16d-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d16d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d16d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d16d-116">See also</span></span>

- [<span data-ttu-id="7d16d-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d16d-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7d16d-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d16d-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
