---
title: IMetaDataTables::GetColumn — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 850a97240e0a6450b4dec759a8786e0df5bffac8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="fe01c-102">IMetaDataTables::GetColumn — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe01c-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="fe01c-103">Pobiera wskaźnik do wartości zawartych w komórce określonej kolumny i wiersza w danej tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe01c-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe01c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe01c-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe01c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe01c-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="fe01c-106">[in] Indeks tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe01c-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="fe01c-107">[in] Indeks kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe01c-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="fe01c-108">[in] Indeks wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe01c-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="fe01c-109">[out] Wskaźnik do wartości w komórce.</span><span class="sxs-lookup"><span data-stu-id="fe01c-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe01c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe01c-110">Requirements</span></span>  
 <span data-ttu-id="fe01c-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe01c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe01c-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe01c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe01c-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe01c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe01c-114">**Wersje programu .NET framework** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe01c-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe01c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe01c-115">See Also</span></span>  
 [<span data-ttu-id="fe01c-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe01c-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="fe01c-117">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe01c-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
