---
title: "IMetaDataEmit2::GetDeltaSaveSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 562b7be418a4a4e335350adf5131178e406b5a07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="0e3e7-102">IMetaDataEmit2::GetDeltaSaveSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="0e3e7-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="0e3e7-103">Pobiera wartość wskazującą, wszelkie zmiany rozmiaru metadanych, będącą wynikiem bieżącej sesji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="0e3e7-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e3e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e3e7-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e3e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e3e7-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="0e3e7-106">[in] Jeden z [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) wartości i wskazujący poziom dokładności potrzebne.</span><span class="sxs-lookup"><span data-stu-id="0e3e7-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="0e3e7-107">Ten parametr jest ignorowany dla programu .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="0e3e7-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="0e3e7-108">[out] Zmiana rozmiaru metadanych.</span><span class="sxs-lookup"><span data-stu-id="0e3e7-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e3e7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e3e7-109">Requirements</span></span>  
 <span data-ttu-id="0e3e7-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e3e7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e3e7-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e3e7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e3e7-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e3e7-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e3e7-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e3e7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e3e7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e3e7-114">See Also</span></span>  
 [<span data-ttu-id="0e3e7-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0e3e7-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="0e3e7-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="0e3e7-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
