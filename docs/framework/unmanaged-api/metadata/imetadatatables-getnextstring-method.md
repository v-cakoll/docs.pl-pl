---
title: IMetaDataTables::GetNextString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 595bc20b51ef81d7dea61620040ceb50c9418f4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589966"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="b8499-102">IMetaDataTables::GetNextString — Metoda</span><span class="sxs-lookup"><span data-stu-id="b8499-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="b8499-103">Pobiera indeks następnego ciągu w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="b8499-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8499-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8499-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8499-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8499-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="b8499-106">[in] Wartość indeksu z kolumną tabeli ciągów.</span><span class="sxs-lookup"><span data-stu-id="b8499-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="b8499-107">[out] Wskaźnik do indeksu ciągu dalej w tej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="b8499-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8499-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8499-108">Requirements</span></span>  
 <span data-ttu-id="b8499-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8499-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8499-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b8499-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8499-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8499-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8499-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8499-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8499-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8499-113">See also</span></span>
- [<span data-ttu-id="b8499-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8499-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="b8499-115">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8499-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
