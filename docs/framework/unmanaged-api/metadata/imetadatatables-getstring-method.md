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
ms.openlocfilehash: 3f817fa3f24bebf3303c656bd02c4d93d1d1431b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781396"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="48766-102">IMetaDataTables::GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="48766-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="48766-103">Pobiera parametry dla podanego indeksu z kolumną tabeli w bieżącym zakresie odwołania.</span><span class="sxs-lookup"><span data-stu-id="48766-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48766-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48766-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48766-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48766-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="48766-106">[in] Indeks, od której należy rozpocząć wyszukiwanie następnej wartości.</span><span class="sxs-lookup"><span data-stu-id="48766-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="48766-107">[out] Wskaźnik do wskaźnika do wartości zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="48766-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48766-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48766-108">Requirements</span></span>  
 <span data-ttu-id="48766-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48766-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48766-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="48766-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48766-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48766-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48766-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48766-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48766-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48766-113">See also</span></span>

- [<span data-ttu-id="48766-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="48766-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="48766-115">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="48766-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
