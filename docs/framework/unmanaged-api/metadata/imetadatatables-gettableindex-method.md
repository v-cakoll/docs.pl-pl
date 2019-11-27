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
ms.openlocfilehash: 48c38288e960ff2e1fe21f30b6eceae8eeaac2da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434853"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="3693b-102">IMetaDataTables::GetTableIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="3693b-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="3693b-103">Pobiera indeks tabeli, do której odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="3693b-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3693b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3693b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3693b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3693b-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="3693b-106">podczas Token, który odwołuje się do tabeli.</span><span class="sxs-lookup"><span data-stu-id="3693b-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="3693b-107">określoną Wskaźnik do zwracanego indeksu dla tabeli, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="3693b-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3693b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3693b-108">Remarks</span></span>  
 <span data-ttu-id="3693b-109">Nie zalecamy użycia tej metody, ponieważ nie zwracają one spójnych wyników.</span><span class="sxs-lookup"><span data-stu-id="3693b-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="3693b-110">Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="3693b-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="3693b-111">Dokumentacja jest dostępna w trybie online; Zobacz [standardy C# ECMA i Common Language Infrastructure](https://go.microsoft.com/fwlink/?LinkID=99212) w MSDN i [Standard ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w międzynarodowej witrynie sieci Web ECMA.</span><span class="sxs-lookup"><span data-stu-id="3693b-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3693b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3693b-112">Requirements</span></span>  
 <span data-ttu-id="3693b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3693b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3693b-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3693b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3693b-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3693b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3693b-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3693b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3693b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3693b-117">See also</span></span>

- [<span data-ttu-id="3693b-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="3693b-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="3693b-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3693b-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
