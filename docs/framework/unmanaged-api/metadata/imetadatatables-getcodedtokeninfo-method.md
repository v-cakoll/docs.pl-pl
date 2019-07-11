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
ms.openlocfilehash: b89409a08ed2dff0111b3b6e552960ac78a5882e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781531"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="da78e-102">IMetaDataTables::GetCodedTokenInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="da78e-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="da78e-103">Pobiera wskaźnik do tablicy tokenów skojarzone z indeksem określony wiersz.</span><span class="sxs-lookup"><span data-stu-id="da78e-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da78e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da78e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da78e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da78e-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="da78e-106">[in] Rodzaj kodowane token do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="da78e-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="da78e-107">[out] Wskaźnik do długości `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="da78e-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="da78e-108">[out] Wskaźnik do wskaźnika do tablicy, która zawiera listę zwracane tokenów.</span><span class="sxs-lookup"><span data-stu-id="da78e-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="da78e-109">[out] Wskaźnik do wskaźnika do nazwy token na `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="da78e-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da78e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da78e-110">Requirements</span></span>  
 <span data-ttu-id="da78e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da78e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da78e-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="da78e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da78e-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da78e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da78e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da78e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da78e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da78e-115">See also</span></span>

- [<span data-ttu-id="da78e-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="da78e-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="da78e-117">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="da78e-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
