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
ms.openlocfilehash: 64c70fe0b657047ae35dccb763fa57120403deef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177150"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="4745b-102">IMetaDataTables::GetCodedTokenInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="4745b-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="4745b-103">Pobiera wskaźnik do tablicy tokenów skojarzonych z indeksem określonego wiersza.</span><span class="sxs-lookup"><span data-stu-id="4745b-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4745b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4745b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4745b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4745b-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="4745b-106">[w] Rodzaj zakodowany token do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="4745b-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4745b-107">[na zewnątrz] Wskaźnik do długości `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="4745b-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="4745b-108">[na zewnątrz] Wskaźnik do wskaźnika do tablicy, która zawiera listę zwróconych tokenów.</span><span class="sxs-lookup"><span data-stu-id="4745b-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="4745b-109">[na zewnątrz] Wskaźnik do wskaźnika do nazwy tokenu w `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="4745b-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4745b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4745b-110">Requirements</span></span>  
 <span data-ttu-id="4745b-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4745b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4745b-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="4745b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4745b-113">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4745b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4745b-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4745b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4745b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4745b-115">See also</span></span>

- [<span data-ttu-id="4745b-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="4745b-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="4745b-117">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4745b-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
