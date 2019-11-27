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
ms.openlocfilehash: 8d25f178a3c5e160e78e042d5016bb93aabf3e2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443446"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="cc837-102">IMetaDataTables::GetNextString — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc837-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="cc837-103">Pobiera indeks następnego ciągu w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="cc837-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc837-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc837-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc837-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc837-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="cc837-106">podczas Wartość indeksu z kolumny tabeli ciągów.</span><span class="sxs-lookup"><span data-stu-id="cc837-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="cc837-107">określoną Wskaźnik do indeksu następnego ciągu w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="cc837-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc837-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc837-108">Requirements</span></span>  
 <span data-ttu-id="cc837-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc837-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc837-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cc837-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc837-111">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc837-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc837-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc837-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc837-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc837-113">See also</span></span>

- [<span data-ttu-id="cc837-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc837-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="cc837-115">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc837-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
