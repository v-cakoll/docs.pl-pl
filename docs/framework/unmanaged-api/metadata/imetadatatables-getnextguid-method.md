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
ms.openlocfilehash: 32edbb6a0eeaf636338983c5cc2e032ddf8b5854
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443735"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="87980-102">IMetaDataTables::GetNextGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="87980-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="87980-103">Pobiera indeks następnej wartości identyfikatora GUID z bieżącej kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="87980-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87980-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87980-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87980-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87980-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="87980-106">podczas Wartość indeksu z kolumny tabeli GUID.</span><span class="sxs-lookup"><span data-stu-id="87980-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="87980-107">określoną Wskaźnik do indeksu następnej wartości identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="87980-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87980-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87980-108">Remarks</span></span>  
 <span data-ttu-id="87980-109">Nie zalecamy użycia tej metody, ponieważ nie zwracają one spójnych wyników.</span><span class="sxs-lookup"><span data-stu-id="87980-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="87980-110">Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="87980-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="87980-111">Dokumentacja jest dostępna w trybie online; Zobacz [standardy C# ECMA i Common Language Infrastructure](https://go.microsoft.com/fwlink/?LinkID=99212) w MSDN i [Standard ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w międzynarodowej witrynie sieci Web ECMA.</span><span class="sxs-lookup"><span data-stu-id="87980-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87980-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87980-112">Requirements</span></span>  
 <span data-ttu-id="87980-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87980-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87980-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="87980-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87980-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87980-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87980-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87980-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87980-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87980-117">See also</span></span>

- [<span data-ttu-id="87980-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="87980-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="87980-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="87980-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
