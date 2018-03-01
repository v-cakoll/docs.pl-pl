---
title: "IMetaDataTables::GetColumn — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 162162b972ab0e1f3de55d56c18372f2475c9846
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="fbada-102">IMetaDataTables::GetColumn — Metoda</span><span class="sxs-lookup"><span data-stu-id="fbada-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="fbada-103">Pobiera wskaźnik do wartości zawartych w komórce określonej kolumny i wiersza w danej tabeli.</span><span class="sxs-lookup"><span data-stu-id="fbada-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbada-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbada-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbada-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbada-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="fbada-106">[in] Indeks tabeli.</span><span class="sxs-lookup"><span data-stu-id="fbada-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="fbada-107">[in] Indeks kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="fbada-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="fbada-108">[in] Indeks wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="fbada-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="fbada-109">[out] Wskaźnik do wartości w komórce.</span><span class="sxs-lookup"><span data-stu-id="fbada-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbada-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbada-110">Requirements</span></span>  
 <span data-ttu-id="fbada-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbada-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbada-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fbada-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbada-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbada-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fbada-114">**Wersje programu .NET framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbada-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbada-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbada-115">See Also</span></span>  
 [<span data-ttu-id="fbada-116">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbada-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="fbada-117">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbada-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
