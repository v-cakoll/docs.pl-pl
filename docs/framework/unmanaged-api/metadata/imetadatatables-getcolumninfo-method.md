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
ms.openlocfilehash: 245933b23028e2baf8a09ca07595f394b65c0ec3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698300"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="b88e5-102">IMetaDataTables::GetColumnInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="b88e5-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="b88e5-103">Pobiera dane o określonej kolumny w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b88e5-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b88e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b88e5-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b88e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b88e5-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="b88e5-106">[in] Indeks tabeli, którą chcesz.</span><span class="sxs-lookup"><span data-stu-id="b88e5-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="b88e5-107">[in] Indeks żądanej kolumny.</span><span class="sxs-lookup"><span data-stu-id="b88e5-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="b88e5-108">[out] Wskaźnik do przesunięcia kolumny w wierszu.</span><span class="sxs-lookup"><span data-stu-id="b88e5-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="b88e5-109">[out] Wskaźnik do rozmiaru, w bajtach dla kolumny.</span><span class="sxs-lookup"><span data-stu-id="b88e5-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="b88e5-110">[out] Wskaźnik do typu wartości w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="b88e5-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="b88e5-111">[out] Wskaźnik do wskaźnika na nazwę kolumny.</span><span class="sxs-lookup"><span data-stu-id="b88e5-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b88e5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b88e5-112">Requirements</span></span>  
 <span data-ttu-id="b88e5-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b88e5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b88e5-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b88e5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b88e5-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b88e5-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b88e5-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b88e5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88e5-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b88e5-117">See also</span></span>
- [<span data-ttu-id="b88e5-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="b88e5-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="b88e5-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b88e5-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
