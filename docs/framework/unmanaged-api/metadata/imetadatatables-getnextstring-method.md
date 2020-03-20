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
ms.openlocfilehash: a1cd932051a9ed90a29ff5eeaa818a67104192bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175255"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="879cd-102">IMetaDataTables::GetNextString — Metoda</span><span class="sxs-lookup"><span data-stu-id="879cd-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="879cd-103">Pobiera indeks następnego ciągu w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="879cd-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="879cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="879cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="879cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="879cd-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="879cd-106">[w] Wartość indeksu z kolumny tabeli ciągów.</span><span class="sxs-lookup"><span data-stu-id="879cd-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="879cd-107">[na zewnątrz] Wskaźnik do indeksu następnego ciągu w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="879cd-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="879cd-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="879cd-108">Requirements</span></span>  
 <span data-ttu-id="879cd-109">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="879cd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="879cd-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="879cd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="879cd-111">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="879cd-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="879cd-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="879cd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879cd-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="879cd-113">See also</span></span>

- [<span data-ttu-id="879cd-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="879cd-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="879cd-115">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="879cd-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
