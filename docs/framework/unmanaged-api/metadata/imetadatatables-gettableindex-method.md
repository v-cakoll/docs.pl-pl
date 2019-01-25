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
ms.openlocfilehash: de857f251bd03b4b2d3fabf458275251440a2113
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741798"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="eab31-102">IMetaDataTables::GetTableIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="eab31-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="eab31-103">Pobiera indeks dla tabeli przywoływanej przez określony token.</span><span class="sxs-lookup"><span data-stu-id="eab31-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab31-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eab31-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eab31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eab31-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="eab31-106">[in] Token, który odwołuje się do tabeli.</span><span class="sxs-lookup"><span data-stu-id="eab31-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="eab31-107">[out] Wskaźnik do zwracanego indeksu dla tabeli, której dotyczy odwołanie.</span><span class="sxs-lookup"><span data-stu-id="eab31-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eab31-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eab31-108">Remarks</span></span>  
 <span data-ttu-id="eab31-109">Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="eab31-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="eab31-110">Informacje o tabeli identyfikatora GUID, w dokumentacji Common Language Infrastructure (CLI), szczególnie "partycja II: Definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="eab31-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="eab31-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="eab31-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab31-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eab31-112">Requirements</span></span>  
 <span data-ttu-id="eab31-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab31-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab31-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="eab31-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eab31-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eab31-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eab31-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab31-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab31-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eab31-117">See also</span></span>
- [<span data-ttu-id="eab31-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="eab31-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="eab31-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="eab31-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
