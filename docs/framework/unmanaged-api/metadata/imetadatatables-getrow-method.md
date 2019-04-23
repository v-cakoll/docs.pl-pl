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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a02719651d8169c1122f5a46b1b8df39b28612ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197285"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="55954-102">IMetaDataTables::GetRow — Metoda</span><span class="sxs-lookup"><span data-stu-id="55954-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="55954-103">Pobiera wiersz indeksu określony wiersz w tabeli pod indeksem określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="55954-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55954-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55954-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55954-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55954-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="55954-106">[in] Indeks tabeli, z którego będą pobierane wiersza.</span><span class="sxs-lookup"><span data-stu-id="55954-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="55954-107">[in] Indeks wiersza, który można pobrać.</span><span class="sxs-lookup"><span data-stu-id="55954-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="55954-108">[out] Wskaźnik do wskaźnika do wiersza.</span><span class="sxs-lookup"><span data-stu-id="55954-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55954-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55954-109">Remarks</span></span>  
 <span data-ttu-id="55954-110">Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="55954-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="55954-111">Informacje o tabeli identyfikatora GUID, w dokumentacji Common Language Infrastructure (CLI), szczególnie "partycja II: Definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="55954-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="55954-112">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="55954-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55954-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55954-113">Requirements</span></span>  
 <span data-ttu-id="55954-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55954-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55954-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="55954-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55954-116">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55954-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55954-117">**Wersje programu .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55954-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55954-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55954-118">See also</span></span>

- [<span data-ttu-id="55954-119">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="55954-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="55954-120">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="55954-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
