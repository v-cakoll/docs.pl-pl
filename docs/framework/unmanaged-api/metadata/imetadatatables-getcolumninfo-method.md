---
title: "IMetaDataTables::GetColumnInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48272219ee6a43006a76fddfd974275ac39b6e80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="0f2da-102">IMetaDataTables::GetColumnInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f2da-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="0f2da-103">Pobiera dane o określonej kolumny w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0f2da-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f2da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f2da-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0f2da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f2da-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="0f2da-106">[in] Indeks tabeli żądany.</span><span class="sxs-lookup"><span data-stu-id="0f2da-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="0f2da-107">[in] Indeks odpowiednie kolumny.</span><span class="sxs-lookup"><span data-stu-id="0f2da-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="0f2da-108">[out] Wskaźnik do przesunięcia kolumny w wierszu.</span><span class="sxs-lookup"><span data-stu-id="0f2da-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="0f2da-109">[out] Wskaźnik do rozmiar w bajtach kolumny.</span><span class="sxs-lookup"><span data-stu-id="0f2da-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="0f2da-110">[out] Wskaźnik do typu wartości w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="0f2da-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="0f2da-111">[out] Wskaźnik na wskaźnik do nazwy kolumny.</span><span class="sxs-lookup"><span data-stu-id="0f2da-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f2da-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f2da-112">Requirements</span></span>  
 <span data-ttu-id="0f2da-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f2da-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f2da-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0f2da-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f2da-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f2da-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f2da-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f2da-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f2da-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f2da-117">See Also</span></span>  
 [<span data-ttu-id="0f2da-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f2da-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="0f2da-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f2da-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
