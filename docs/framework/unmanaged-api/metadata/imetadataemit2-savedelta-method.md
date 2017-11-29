---
title: "IMetaDataEmit2::SaveDelta — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDelta
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7f2e16d994c648f3c88a23488df75f04dbdaa47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="a9e75-102">IMetaDataEmit2::SaveDelta — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9e75-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="a9e75-103">Zapisuje zmiany z bieżącej sesji edit-and-continue do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="a9e75-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9e75-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9e75-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9e75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9e75-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="a9e75-106">[in] Nazwa pliku, w którym chcesz zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="a9e75-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="a9e75-107">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="a9e75-107">[in] Reserved.</span></span> <span data-ttu-id="a9e75-108">Musi być równy zero.</span><span class="sxs-lookup"><span data-stu-id="a9e75-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9e75-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9e75-109">Requirements</span></span>  
 <span data-ttu-id="a9e75-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9e75-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9e75-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a9e75-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9e75-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9e75-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9e75-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9e75-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e75-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9e75-114">See Also</span></span>  
 [<span data-ttu-id="a9e75-115">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="a9e75-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="a9e75-116">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="a9e75-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
