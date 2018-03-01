---
title: "IMetaDataTables::GetRow — Metoda"
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
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 760bee2c4a6a6efb16a32579578ab4953492c48e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="6fe11-102">IMetaDataTables::GetRow — Metoda</span><span class="sxs-lookup"><span data-stu-id="6fe11-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="6fe11-103">Pobiera wiersz w indeksie określony wiersz, w tabeli w indeksie określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6fe11-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fe11-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6fe11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fe11-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="6fe11-106">[in] Indeks tabeli, z którego będą pobierane wiersza.</span><span class="sxs-lookup"><span data-stu-id="6fe11-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="6fe11-107">[in] Indeks wiersza do pobrania.</span><span class="sxs-lookup"><span data-stu-id="6fe11-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="6fe11-108">[out] Wskaźnik na wskaźnik do wiersza.</span><span class="sxs-lookup"><span data-stu-id="6fe11-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fe11-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fe11-109">Remarks</span></span>  
 <span data-ttu-id="6fe11-110">Zaleca się korzystanie z tej metody, ponieważ nie zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="6fe11-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="6fe11-111">Informacje o tabeli identyfikatora GUID w dokumentacji infrastruktury języka wspólnego (CLI), szczególnie "partycji II: metadane definicji i semantyki".</span><span class="sxs-lookup"><span data-stu-id="6fe11-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="6fe11-112">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# i wspólne normy infrastruktury języka](http://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) w witrynie sieci Web międzynarodowej Ecma.</span><span class="sxs-lookup"><span data-stu-id="6fe11-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fe11-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fe11-113">Requirements</span></span>  
 <span data-ttu-id="6fe11-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fe11-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fe11-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6fe11-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6fe11-116">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6fe11-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6fe11-117">**Wersje programu .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fe11-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe11-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fe11-118">See Also</span></span>  
 [<span data-ttu-id="6fe11-119">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fe11-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="6fe11-120">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fe11-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
