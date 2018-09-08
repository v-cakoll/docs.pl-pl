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
ms.openlocfilehash: d24dbcbdd8b0ed0736f7b59564cf72dffaa5a8f8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196715"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="0ec75-102">IMetaDataTables::GetRow — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ec75-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="0ec75-103">Pobiera wiersz indeksu określony wiersz w tabeli pod indeksem określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0ec75-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec75-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ec75-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ec75-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ec75-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="0ec75-106">[in] Indeks tabeli, z którego będą pobierane wiersza.</span><span class="sxs-lookup"><span data-stu-id="0ec75-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="0ec75-107">[in] Indeks wiersza, który można pobrać.</span><span class="sxs-lookup"><span data-stu-id="0ec75-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="0ec75-108">[out] Wskaźnik do wskaźnika do wiersza.</span><span class="sxs-lookup"><span data-stu-id="0ec75-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ec75-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ec75-109">Remarks</span></span>  
 <span data-ttu-id="0ec75-110">Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="0ec75-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="0ec75-111">Informacje w tabeli z identyfikatorem GUID zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: metadane definicji i semantyka".</span><span class="sxs-lookup"><span data-stu-id="0ec75-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="0ec75-112">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0ec75-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ec75-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ec75-113">Requirements</span></span>  
 <span data-ttu-id="0ec75-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ec75-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ec75-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ec75-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ec75-116">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ec75-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ec75-117">**Wersje programu .NET framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ec75-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec75-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ec75-118">See Also</span></span>  
 [<span data-ttu-id="0ec75-119">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ec75-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="0ec75-120">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ec75-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
