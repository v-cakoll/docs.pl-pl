---
title: "IMetaDataTables::GetNextGuid — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d3585778d9076cb313ffed69a0e126891c4ce49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="3bbed-102">IMetaDataTables::GetNextGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="3bbed-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="3bbed-103">Pobiera indeks następnego wartości identyfikatora GUID w bieżącej kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="3bbed-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bbed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bbed-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bbed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bbed-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="3bbed-106">[in] Wartość indeksu z kolumną tabeli identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="3bbed-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="3bbed-107">[out] Wskaźnik do indeksu następnej wartości identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="3bbed-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bbed-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bbed-108">Remarks</span></span>  
 <span data-ttu-id="3bbed-109">Zaleca się korzystanie z tej metody, ponieważ nie zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="3bbed-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="3bbed-110">Informacje o tabeli identyfikatora GUID w dokumentacji infrastruktury języka wspólnego (CLI), szczególnie "partycji II: metadane definicji i semantyki".</span><span class="sxs-lookup"><span data-stu-id="3bbed-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="3bbed-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# i wspólne normy infrastruktury języka](http://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) w witrynie sieci Web międzynarodowej Ecma.</span><span class="sxs-lookup"><span data-stu-id="3bbed-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bbed-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bbed-112">Requirements</span></span>  
 <span data-ttu-id="3bbed-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bbed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bbed-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3bbed-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3bbed-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3bbed-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3bbed-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bbed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bbed-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bbed-117">See Also</span></span>  
 [<span data-ttu-id="3bbed-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="3bbed-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="3bbed-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3bbed-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
