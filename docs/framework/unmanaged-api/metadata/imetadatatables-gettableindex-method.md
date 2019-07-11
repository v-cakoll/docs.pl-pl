---
title: IMetaDataTables::GetTableIndex — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 195642d9186016417db310402b664a1043d09e71
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781367"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="c0c24-102">IMetaDataTables::GetTableIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0c24-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="c0c24-103">Pobiera indeks dla tabeli przywoływanej przez określony token.</span><span class="sxs-lookup"><span data-stu-id="c0c24-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0c24-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0c24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0c24-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="c0c24-106">[in] Token, który odwołuje się do tabeli.</span><span class="sxs-lookup"><span data-stu-id="c0c24-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="c0c24-107">[out] Wskaźnik do zwracanego indeksu dla tabeli, której dotyczy odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c0c24-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0c24-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0c24-108">Remarks</span></span>  
 <span data-ttu-id="c0c24-109">Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="c0c24-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="c0c24-110">Informacje o tabeli identyfikatora GUID, w dokumentacji Common Language Infrastructure (CLI), szczególnie "partycja II: Definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="c0c24-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="c0c24-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c0c24-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0c24-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0c24-112">Requirements</span></span>  
 <span data-ttu-id="c0c24-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0c24-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0c24-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c0c24-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0c24-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0c24-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0c24-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0c24-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c24-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0c24-117">See also</span></span>

- [<span data-ttu-id="c0c24-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="c0c24-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c0c24-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c0c24-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
