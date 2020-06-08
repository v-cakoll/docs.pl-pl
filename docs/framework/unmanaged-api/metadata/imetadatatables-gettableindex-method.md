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
ms.openlocfilehash: 3638ab12fc311ece9f24608cbb36219e10f01f2d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501180"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="9488f-102">IMetaDataTables::GetTableIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="9488f-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="9488f-103">Pobiera indeks tabeli, do której odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="9488f-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9488f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9488f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9488f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9488f-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="9488f-106">podczas Token, który odwołuje się do tabeli.</span><span class="sxs-lookup"><span data-stu-id="9488f-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="9488f-107">określoną Wskaźnik do zwracanego indeksu dla tabeli, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="9488f-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9488f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9488f-108">Remarks</span></span>  
 <span data-ttu-id="9488f-109">Nie zalecamy użycia tej metody, ponieważ nie zwracają one spójnych wyników.</span><span class="sxs-lookup"><span data-stu-id="9488f-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="9488f-110">Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="9488f-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="9488f-111">Dokumentacja jest dostępna w trybie online; Zobacz [ECMA C# i Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) i [standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="9488f-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9488f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9488f-112">Requirements</span></span>  
 <span data-ttu-id="9488f-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9488f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9488f-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9488f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9488f-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9488f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9488f-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9488f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9488f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9488f-117">See also</span></span>

- [<span data-ttu-id="9488f-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="9488f-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="9488f-119">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9488f-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
