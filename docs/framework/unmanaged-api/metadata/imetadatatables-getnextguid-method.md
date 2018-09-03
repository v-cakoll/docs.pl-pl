---
title: IMetaDataTables::GetNextGuid — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3273f89d61314db2ae36c572f2ca520f28e63e3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463490"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="3b1ba-102">IMetaDataTables::GetNextGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b1ba-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="3b1ba-103">Pobiera indeks następnego wartość identyfikatora GUID w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="3b1ba-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b1ba-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b1ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b1ba-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="3b1ba-106">[in] Wartość indeksu z kolumną tabeli identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="3b1ba-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="3b1ba-107">[out] Wskaźnik do indeksu następną wartość identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="3b1ba-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b1ba-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b1ba-108">Remarks</span></span>  
 <span data-ttu-id="3b1ba-109">Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="3b1ba-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="3b1ba-110">Informacje w tabeli z identyfikatorem GUID zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: metadane definicji i semantyka".</span><span class="sxs-lookup"><span data-stu-id="3b1ba-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="3b1ba-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3b1ba-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b1ba-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b1ba-112">Requirements</span></span>  
 <span data-ttu-id="3b1ba-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b1ba-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b1ba-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3b1ba-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b1ba-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b1ba-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b1ba-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b1ba-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1ba-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b1ba-117">See Also</span></span>  
 [<span data-ttu-id="3b1ba-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b1ba-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="3b1ba-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b1ba-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
