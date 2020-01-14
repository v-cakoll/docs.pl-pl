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
ms.openlocfilehash: d3e056bc93c2faf2b1509536b8d8d4df6886dd20
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937385"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="060e7-102">IMetaDataTables::GetTableIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="060e7-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="060e7-103">Pobiera indeks tabeli, do której odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="060e7-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="060e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="060e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="060e7-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="060e7-106">podczas Token, który odwołuje się do tabeli.</span><span class="sxs-lookup"><span data-stu-id="060e7-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="060e7-107">określoną Wskaźnik do zwracanego indeksu dla tabeli, do której się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="060e7-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="060e7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="060e7-108">Remarks</span></span>  
 <span data-ttu-id="060e7-109">Nie zalecamy użycia tej metody, ponieważ nie zwracają one spójnych wyników.</span><span class="sxs-lookup"><span data-stu-id="060e7-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="060e7-110">Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="060e7-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="060e7-111">Dokumentacja jest dostępna w trybie online; zobacz Standard ECMA [ C# i Common Language Infrastructure](../../../standard/components.md#applicable-standards) i [standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="060e7-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="060e7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="060e7-112">Requirements</span></span>  
 <span data-ttu-id="060e7-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="060e7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="060e7-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="060e7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="060e7-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="060e7-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="060e7-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="060e7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060e7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="060e7-117">See also</span></span>

- [<span data-ttu-id="060e7-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="060e7-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="060e7-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="060e7-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
