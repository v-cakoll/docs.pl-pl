---
title: IMetaDataTables::GetGuid — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175281"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="cbe21-102">IMetaDataTables::GetGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="cbe21-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="cbe21-103">Pobiera identyfikator GUID z wiersza w określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="cbe21-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbe21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbe21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbe21-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="cbe21-106">[w] Indeks wiersza, z którego można uzyskać identyfikator GUID.</span><span class="sxs-lookup"><span data-stu-id="cbe21-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="cbe21-107">[na zewnątrz] Wskaźnik do wskaźnika do identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="cbe21-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbe21-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbe21-108">Remarks</span></span>  

  <span data-ttu-id="cbe21-109">Nie zaleca się stosowania tej metody, ponieważ nie zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="cbe21-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="cbe21-110">Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację wspólnej infrastruktury języka (CLI), w szczególności "Partycja II: Definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="cbe21-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="cbe21-111">Dokumentacja jest dostępna online; zobacz [ECMA C# i common language infrastructure standards](../../../standard/components.md#applicable-standards) and standard [ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="cbe21-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbe21-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbe21-112">Requirements</span></span>  
 <span data-ttu-id="cbe21-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbe21-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbe21-114">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="cbe21-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cbe21-115">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cbe21-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cbe21-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbe21-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe21-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbe21-117">See also</span></span>

- [<span data-ttu-id="cbe21-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbe21-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="cbe21-119">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cbe21-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
