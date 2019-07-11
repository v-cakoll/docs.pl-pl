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
ms.openlocfilehash: 345c43b5a6e3c185b5e8070e9d6e1c1443673149
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781464"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="c5830-102">IMetaDataTables::GetNextGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5830-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="c5830-103">Pobiera indeks następnego wartość identyfikatora GUID w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="c5830-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5830-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5830-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5830-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5830-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="c5830-106">[in] Wartość indeksu z kolumną tabeli identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="c5830-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="c5830-107">[out] Wskaźnik do indeksu następną wartość identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="c5830-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5830-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5830-108">Remarks</span></span>  
 <span data-ttu-id="c5830-109">Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="c5830-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="c5830-110">Informacje o tabeli identyfikatora GUID, w dokumentacji Common Language Infrastructure (CLI), szczególnie "partycja II: Definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="c5830-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="c5830-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c5830-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5830-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5830-112">Requirements</span></span>  
 <span data-ttu-id="c5830-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5830-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5830-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c5830-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5830-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5830-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5830-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5830-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5830-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5830-117">See also</span></span>

- [<span data-ttu-id="c5830-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5830-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c5830-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5830-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
