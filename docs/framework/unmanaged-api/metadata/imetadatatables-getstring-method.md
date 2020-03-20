---
title: IMetaDataTables::GetString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 216a1f7bd2ff5a596fa7abf7874b5e603d5a9f7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175242"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="c936a-102">IMetaDataTables::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="c936a-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="c936a-103">Pobiera ciąg w określonym indeksie z kolumny tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="c936a-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c936a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c936a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c936a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c936a-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="c936a-106">[w] Indeks, w którym należy rozpocząć wyszukiwanie następnej wartości.</span><span class="sxs-lookup"><span data-stu-id="c936a-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="c936a-107">[na zewnątrz] Wskaźnik do wskaźnika do zwracanego ciągu wartości.</span><span class="sxs-lookup"><span data-stu-id="c936a-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c936a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c936a-108">Requirements</span></span>  
 <span data-ttu-id="c936a-109">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c936a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c936a-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="c936a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c936a-111">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c936a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c936a-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c936a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c936a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c936a-113">See also</span></span>

- [<span data-ttu-id="c936a-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="c936a-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c936a-115">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c936a-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
