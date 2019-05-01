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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043683"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="815d0-102">IMetaDataEmit2::GetDeltaSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="815d0-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="815d0-103">Pobiera wartość wskazującą, wszelkie zmiany rozmiaru metadanych, która wynika z bieżącej sesji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="815d0-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="815d0-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="815d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="815d0-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="815d0-106">[in] Jedną z [corsavesize —](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) wartości, wskazujący poziom dokładności żądanego.</span><span class="sxs-lookup"><span data-stu-id="815d0-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="815d0-107">Dla programu .NET Framework w wersji 2.0 ten parametr jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="815d0-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="815d0-108">[out] Zmiana rozmiaru metadanych.</span><span class="sxs-lookup"><span data-stu-id="815d0-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="815d0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="815d0-109">Requirements</span></span>  
 <span data-ttu-id="815d0-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="815d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815d0-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="815d0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="815d0-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="815d0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="815d0-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="815d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815d0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="815d0-114">See also</span></span>

- [<span data-ttu-id="815d0-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="815d0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="815d0-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="815d0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
