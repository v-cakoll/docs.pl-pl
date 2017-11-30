---
title: "IMetaDataEmit::DefineModuleRef — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineModuleRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b3131e6cebf09b0767d1331656ff16b2b55d749
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="29c24-102">IMetaDataEmit::DefineModuleRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="29c24-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="29c24-103">Tworzy podpis metadane dla modułu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="29c24-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29c24-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29c24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29c24-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="29c24-106">[in] Nazwa drugiego pliku metadanych zwykle biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="29c24-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="29c24-107">To jest tylko nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="29c24-107">This is the file name only.</span></span> <span data-ttu-id="29c24-108">Nie należy używać pełnej nazwy ścieżki.</span><span class="sxs-lookup"><span data-stu-id="29c24-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="29c24-109">[out] Przypisane `mdModuleRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="29c24-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c24-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29c24-110">Requirements</span></span>  
 <span data-ttu-id="29c24-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c24-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c24-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29c24-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29c24-113">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29c24-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29c24-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29c24-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c24-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29c24-115">See Also</span></span>  
 [<span data-ttu-id="29c24-116">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="29c24-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="29c24-117">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="29c24-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
