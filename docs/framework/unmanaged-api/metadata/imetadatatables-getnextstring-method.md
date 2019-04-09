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
ms.openlocfilehash: 4e7e7d89f4c994c5ce37dc09d15826185ed1bb25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129379"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="ef077-102">IMetaDataTables::GetNextString — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef077-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="ef077-103">Pobiera indeks następnego ciągu w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="ef077-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef077-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef077-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef077-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef077-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="ef077-106">[in] Wartość indeksu z kolumną tabeli ciągów.</span><span class="sxs-lookup"><span data-stu-id="ef077-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="ef077-107">[out] Wskaźnik do indeksu ciągu dalej w tej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="ef077-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef077-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef077-108">Requirements</span></span>  
 <span data-ttu-id="ef077-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef077-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef077-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ef077-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef077-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef077-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ef077-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ef077-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef077-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef077-113">See also</span></span>

- [<span data-ttu-id="ef077-114">IMetaDataTables — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef077-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ef077-115">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef077-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
