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
ms.openlocfilehash: 9c380d363830eb6b4c47110d50cdb4d08e4568d8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499813"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="4b0dd-102">IMetaDataTables::GetColumn — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b0dd-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="4b0dd-103">Pobiera wskaźnik do wartości znajdujących się w komórce określonej kolumny i wiersza w danej tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b0dd-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b0dd-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b0dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b0dd-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="4b0dd-106">[in] Indeks tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b0dd-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="4b0dd-107">[in] Indeks kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b0dd-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="4b0dd-108">[in] Indeks wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="4b0dd-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="4b0dd-109">[out] Wskaźnik do wartości w komórce.</span><span class="sxs-lookup"><span data-stu-id="4b0dd-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b0dd-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b0dd-110">Requirements</span></span>  
 <span data-ttu-id="4b0dd-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b0dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b0dd-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4b0dd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b0dd-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b0dd-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b0dd-114">**Wersje programu .NET framework** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b0dd-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0dd-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b0dd-115">See also</span></span>
- [<span data-ttu-id="4b0dd-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b0dd-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="4b0dd-117">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b0dd-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
