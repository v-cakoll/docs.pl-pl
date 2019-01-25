---
title: IMetaDataTables::GetCodedTokenInfo — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11ab93e9cb4449ab77e5e9c4da81073aaf432382
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669695"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="68099-102">IMetaDataTables::GetCodedTokenInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="68099-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="68099-103">Pobiera wskaźnik do tablicy tokenów skojarzone z indeksem określony wiersz.</span><span class="sxs-lookup"><span data-stu-id="68099-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68099-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68099-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68099-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68099-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="68099-106">[in] Rodzaj kodowane token do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="68099-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="68099-107">[out] Wskaźnik do długości `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="68099-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="68099-108">[out] Wskaźnik do wskaźnika do tablicy, która zawiera listę zwracane tokenów.</span><span class="sxs-lookup"><span data-stu-id="68099-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="68099-109">[out] Wskaźnik do wskaźnika do nazwy token na `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="68099-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68099-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68099-110">Requirements</span></span>  
 <span data-ttu-id="68099-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68099-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68099-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="68099-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68099-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68099-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68099-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68099-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68099-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68099-115">See also</span></span>
- [<span data-ttu-id="68099-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="68099-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="68099-117">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="68099-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
