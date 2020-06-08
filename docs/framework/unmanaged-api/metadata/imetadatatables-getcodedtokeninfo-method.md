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
ms.openlocfilehash: 8ab16ad5b2b2838125e07511ef47be737f40671c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501212"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="0ecd9-102">IMetaDataTables::GetCodedTokenInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ecd9-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="0ecd9-103">Pobiera wskaźnik do tablicy tokenów skojarzonych z określonym indeksem wiersza.</span><span class="sxs-lookup"><span data-stu-id="0ecd9-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ecd9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ecd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ecd9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ecd9-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="0ecd9-106">podczas Rodzaj zakodowanego tokenu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="0ecd9-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0ecd9-107">określoną Wskaźnik do długości `ppTokens` .</span><span class="sxs-lookup"><span data-stu-id="0ecd9-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="0ecd9-108">określoną Wskaźnik do wskaźnika do tablicy zawierającej listę zwracanych tokenów.</span><span class="sxs-lookup"><span data-stu-id="0ecd9-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="0ecd9-109">określoną Wskaźnik do wskaźnika do nazwy tokenu w `ixCdTkn` .</span><span class="sxs-lookup"><span data-stu-id="0ecd9-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ecd9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ecd9-110">Requirements</span></span>  
 <span data-ttu-id="0ecd9-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ecd9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ecd9-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0ecd9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ecd9-113">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0ecd9-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ecd9-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ecd9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ecd9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ecd9-115">See also</span></span>

- [<span data-ttu-id="0ecd9-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ecd9-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="0ecd9-117">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0ecd9-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
