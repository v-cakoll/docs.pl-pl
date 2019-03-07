---
title: IMetaDataTables::GetColumnInfo — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bcab5adf30648f6b5a614a407478977bc37c7062
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480705"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="5a498-102">IMetaDataTables::GetColumnInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a498-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="5a498-103">Pobiera dane o określonej kolumny w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5a498-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a498-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a498-104">Syntax</span></span>  
  
```  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a498-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a498-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="5a498-106">[in] Indeks tabeli, którą chcesz.</span><span class="sxs-lookup"><span data-stu-id="5a498-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="5a498-107">[in] Indeks żądanej kolumny.</span><span class="sxs-lookup"><span data-stu-id="5a498-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="5a498-108">[out] Wskaźnik do przesunięcia kolumny w wierszu.</span><span class="sxs-lookup"><span data-stu-id="5a498-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="5a498-109">[out] Wskaźnik do rozmiaru, w bajtach dla kolumny.</span><span class="sxs-lookup"><span data-stu-id="5a498-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="5a498-110">[out] Wskaźnik do typu wartości w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="5a498-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="5a498-111">[out] Wskaźnik do wskaźnika na nazwę kolumny.</span><span class="sxs-lookup"><span data-stu-id="5a498-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a498-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a498-112">Requirements</span></span>  
 <span data-ttu-id="5a498-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a498-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a498-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5a498-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a498-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a498-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a498-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a498-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a498-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a498-117">See also</span></span>
- [<span data-ttu-id="5a498-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a498-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="5a498-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a498-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
