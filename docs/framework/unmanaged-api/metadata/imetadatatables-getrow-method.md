---
title: IMetaDataTables::GetRow — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177114"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="cd7ae-102">IMetaDataTables::GetRow — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd7ae-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="cd7ae-103">Pobiera wiersz w określonym indeksie wiersza, w tabeli w określonym indeksie tabeli.</span><span class="sxs-lookup"><span data-stu-id="cd7ae-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd7ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd7ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd7ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd7ae-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="cd7ae-106">[w] Indeks tabeli, z której wiersz zostanie pobrany.</span><span class="sxs-lookup"><span data-stu-id="cd7ae-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="cd7ae-107">[w] Indeks wiersza, aby uzyskać.</span><span class="sxs-lookup"><span data-stu-id="cd7ae-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="cd7ae-108">[na zewnątrz] Wskaźnik do wskaźnika do wiersza.</span><span class="sxs-lookup"><span data-stu-id="cd7ae-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd7ae-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd7ae-109">Remarks</span></span>  

  <span data-ttu-id="cd7ae-110">Nie zaleca się stosowania tej metody, ponieważ nie zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="cd7ae-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="cd7ae-111">Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację wspólnej infrastruktury języka (CLI), w szczególności "Partycja II: Definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="cd7ae-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="cd7ae-112">Dokumentacja jest dostępna online; zobacz [ECMA C# i common language infrastructure standards](../../../standard/components.md#applicable-standards) and standard [ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="cd7ae-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd7ae-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd7ae-113">Requirements</span></span>  
 <span data-ttu-id="cd7ae-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd7ae-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd7ae-115">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd7ae-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd7ae-116">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd7ae-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd7ae-117">**Wersje programu .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd7ae-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7ae-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd7ae-118">See also</span></span>

- [<span data-ttu-id="cd7ae-119">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd7ae-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="cd7ae-120">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd7ae-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
