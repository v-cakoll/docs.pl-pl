---
title: "IMetaDataTables::GetGuid — Metoda"
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
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58dbcb7ebf56f126d89a42a1f5df6247266cb38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="437b5-102">IMetaDataTables::GetGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="437b5-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="437b5-103">Pobiera identyfikator GUID z wiersza pod określonym indeksem.</span><span class="sxs-lookup"><span data-stu-id="437b5-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="437b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="437b5-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="437b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="437b5-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="437b5-106">[in] Indeks wiersza, z którego można pobrać identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="437b5-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="437b5-107">[out] Wskaźnik na wskaźnik do identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="437b5-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="437b5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="437b5-108">Remarks</span></span>  
 <span data-ttu-id="437b5-109">Zaleca się korzystanie z tej metody, ponieważ nie zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="437b5-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="437b5-110">Informacje o tabeli identyfikatora GUID w dokumentacji infrastruktury języka wspólnego (CLI), szczególnie "partycji II: metadane definicji i semantyki".</span><span class="sxs-lookup"><span data-stu-id="437b5-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="437b5-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# i wspólne normy infrastruktury języka](http://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) w witrynie sieci Web międzynarodowej Ecma.</span><span class="sxs-lookup"><span data-stu-id="437b5-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="437b5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="437b5-112">Requirements</span></span>  
 <span data-ttu-id="437b5-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="437b5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="437b5-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="437b5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="437b5-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="437b5-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="437b5-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="437b5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437b5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="437b5-117">See Also</span></span>  
 [<span data-ttu-id="437b5-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="437b5-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="437b5-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="437b5-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
