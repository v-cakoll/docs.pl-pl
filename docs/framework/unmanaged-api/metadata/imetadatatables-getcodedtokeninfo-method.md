---
title: "IMetaDataTables::GetCodedTokenInfo — Metoda"
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
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 72c88751940da16a691a5eae46507986a50904a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="0c518-102">IMetaDataTables::GetCodedTokenInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c518-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="0c518-103">Pobiera wskaźnik do tablicy tokenów skojarzone z indeks określonego wiersza.</span><span class="sxs-lookup"><span data-stu-id="0c518-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c518-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c518-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c518-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c518-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="0c518-106">[in] Rodzaj kodowanego tokenu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="0c518-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0c518-107">[out] Wskaźnik do długości `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="0c518-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="0c518-108">[out] Wskaźnik do wskaźnika do tablicy, która zawiera listę zwrócił tokenów.</span><span class="sxs-lookup"><span data-stu-id="0c518-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="0c518-109">[out] Wskaźnik na wskaźnik do nazwy token w `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="0c518-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c518-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c518-110">Requirements</span></span>  
 <span data-ttu-id="0c518-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c518-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c518-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0c518-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c518-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c518-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c518-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c518-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c518-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c518-115">See Also</span></span>  
 [<span data-ttu-id="0c518-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c518-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="0c518-117">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c518-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
