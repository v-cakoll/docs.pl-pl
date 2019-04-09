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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fed98521c0609ebd8b5f65885d69c77814e9e85
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119343"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="922bb-102">IMetaDataTables::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="922bb-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="922bb-103">Pobiera parametry dla podanego indeksu z kolumną tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="922bb-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="922bb-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="922bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="922bb-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="922bb-106">[in] Indeks, od której należy rozpocząć wyszukiwanie następnej wartości.</span><span class="sxs-lookup"><span data-stu-id="922bb-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="922bb-107">[out] Wskaźnik do wskaźnika do wartości zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="922bb-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="922bb-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="922bb-108">Requirements</span></span>  
 <span data-ttu-id="922bb-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="922bb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="922bb-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="922bb-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="922bb-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="922bb-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="922bb-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="922bb-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="922bb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="922bb-113">See also</span></span>

- [<span data-ttu-id="922bb-114">IMetaDataTables — Interfejs</span><span class="sxs-lookup"><span data-stu-id="922bb-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="922bb-115">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="922bb-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
