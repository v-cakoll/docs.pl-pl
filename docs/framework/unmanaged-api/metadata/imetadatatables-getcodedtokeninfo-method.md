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
ms.openlocfilehash: a7a36d14b67efb3934089dc16de41a3b80ea0c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="de9df-102">IMetaDataTables::GetCodedTokenInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="de9df-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="de9df-103">Pobiera wskaźnik do tablicy tokenów skojarzone z indeks określonego wiersza.</span><span class="sxs-lookup"><span data-stu-id="de9df-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de9df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de9df-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de9df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de9df-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="de9df-106">[in] Rodzaj kodowanego tokenu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="de9df-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="de9df-107">[out] Wskaźnik do długości `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="de9df-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="de9df-108">[out] Wskaźnik do wskaźnika do tablicy, która zawiera listę zwrócił tokenów.</span><span class="sxs-lookup"><span data-stu-id="de9df-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="de9df-109">[out] Wskaźnik na wskaźnik do nazwy token w `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="de9df-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de9df-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de9df-110">Requirements</span></span>  
 <span data-ttu-id="de9df-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de9df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de9df-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de9df-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de9df-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de9df-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de9df-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de9df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9df-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de9df-115">See Also</span></span>  
 [<span data-ttu-id="de9df-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="de9df-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="de9df-117">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="de9df-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
