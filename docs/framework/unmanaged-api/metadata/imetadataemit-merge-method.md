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
ms.openlocfilehash: e7fe5cbe27c0771a71e4c03d14ab68ada7d0741a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004195"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="044cb-102">IMetaDataEmit::Merge — Metoda</span><span class="sxs-lookup"><span data-stu-id="044cb-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="044cb-103">Dodaje określony zaimportowany zakres do listy zakresów, które mają zostać scalone.</span><span class="sxs-lookup"><span data-stu-id="044cb-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="044cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="044cb-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="044cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="044cb-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="044cb-106">podczas Wskaźnik do obiektu [IMetaDataImport](imetadataimport-interface.md) , który identyfikuje importowany zakres do scalenia.</span><span class="sxs-lookup"><span data-stu-id="044cb-106">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="044cb-107">podczas Wskaźnik do obiektu [IMapToken](imaptoken-interface.md) , który określa ponowne mapowanie tokenu.</span><span class="sxs-lookup"><span data-stu-id="044cb-107">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="044cb-108">podczas Wskaźnik do obiektu [IUnknown](/cpp/atl/iunknown) , który określa błędy.</span><span class="sxs-lookup"><span data-stu-id="044cb-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="044cb-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="044cb-109">Remarks</span></span>  
 <span data-ttu-id="044cb-110">Wywołanie [IMetaDataEmit:: MergeEnd —](imetadataemit-mergeend-method.md) w celu wyzwolenia fuzji metadanych w pojedynczym zakresie.</span><span class="sxs-lookup"><span data-stu-id="044cb-110">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="044cb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="044cb-111">Requirements</span></span>  
 <span data-ttu-id="044cb-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="044cb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="044cb-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="044cb-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="044cb-114">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="044cb-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="044cb-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="044cb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044cb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="044cb-116">See also</span></span>

- [<span data-ttu-id="044cb-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="044cb-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="044cb-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="044cb-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
