---
title: "IMetaDataTables::GetTableIndex — Metoda"
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
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d2e51b9975748642d66e5b5104dc24936b4a7e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="e3f02-102">IMetaDataTables::GetTableIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3f02-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="e3f02-103">Pobiera indeks tabeli odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="e3f02-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3f02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3f02-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3f02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3f02-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="e3f02-106">[in] Token, który odwołuje się do tabeli.</span><span class="sxs-lookup"><span data-stu-id="e3f02-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="e3f02-107">[out] Wskaźnik do zwrócony indeksu dla tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e3f02-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3f02-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3f02-108">Remarks</span></span>  
 <span data-ttu-id="e3f02-109">Zaleca się korzystanie z tej metody, ponieważ nie zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="e3f02-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e3f02-110">Informacje o tabeli identyfikatora GUID w dokumentacji infrastruktury języka wspólnego (CLI), szczególnie "partycji II: metadane definicji i semantyki".</span><span class="sxs-lookup"><span data-stu-id="e3f02-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e3f02-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# i wspólne normy infrastruktury języka](http://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) w witrynie sieci Web międzynarodowej Ecma.</span><span class="sxs-lookup"><span data-stu-id="e3f02-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3f02-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3f02-112">Requirements</span></span>  
 <span data-ttu-id="e3f02-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3f02-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3f02-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e3f02-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3f02-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3f02-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3f02-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3f02-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f02-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3f02-117">See Also</span></span>  
 [<span data-ttu-id="e3f02-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3f02-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="e3f02-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3f02-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
