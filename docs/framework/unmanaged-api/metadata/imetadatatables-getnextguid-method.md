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
ms.openlocfilehash: 645a9913d0de6f93e59df3dd8ba7267ddb13b41b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490253"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="e545c-102">IMetaDataTables::GetNextGuid — Metoda</span><span class="sxs-lookup"><span data-stu-id="e545c-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="e545c-103">Pobiera indeks następnej wartości identyfikatora GUID z bieżącej kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="e545c-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e545c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e545c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e545c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e545c-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="e545c-106">podczas Wartość indeksu z kolumny tabeli GUID.</span><span class="sxs-lookup"><span data-stu-id="e545c-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="e545c-107">określoną Wskaźnik do indeksu następnej wartości identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="e545c-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e545c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e545c-108">Remarks</span></span>  

  <span data-ttu-id="e545c-109">Nie zalecamy użycia tej metody, ponieważ nie zwracają one spójnych wyników.</span><span class="sxs-lookup"><span data-stu-id="e545c-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e545c-110">Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="e545c-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e545c-111">Dokumentacja jest dostępna w trybie online; Zobacz [ECMA C# i Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) i [standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="e545c-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e545c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e545c-112">Requirements</span></span>  
 <span data-ttu-id="e545c-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e545c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e545c-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e545c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e545c-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e545c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e545c-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e545c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e545c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e545c-117">See also</span></span>

- [<span data-ttu-id="e545c-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="e545c-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="e545c-119">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e545c-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
