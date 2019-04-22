---
title: IMetaDataEmit2::GetDeltaSaveSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69897a7b646eb9f58e6b38588e302287b4241779
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139896"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="c320d-102">IMetaDataEmit2::GetDeltaSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="c320d-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="c320d-103">Pobiera wartość wskazującą, wszelkie zmiany rozmiaru metadanych, która wynika z bieżącej sesji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="c320d-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c320d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c320d-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c320d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c320d-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="c320d-106">[in] Jedną z [corsavesize —](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) wartości, wskazujący poziom dokładności żądanego.</span><span class="sxs-lookup"><span data-stu-id="c320d-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="c320d-107">Dla programu .NET Framework w wersji 2.0 ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="c320d-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="c320d-108">[out] Zmiana rozmiaru metadanych.</span><span class="sxs-lookup"><span data-stu-id="c320d-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c320d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c320d-109">Requirements</span></span>  
 <span data-ttu-id="c320d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c320d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c320d-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c320d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c320d-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c320d-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c320d-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c320d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c320d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c320d-114">See also</span></span>

- [<span data-ttu-id="c320d-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c320d-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="c320d-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c320d-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
