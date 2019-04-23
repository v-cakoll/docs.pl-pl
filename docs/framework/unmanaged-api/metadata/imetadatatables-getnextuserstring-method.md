---
title: IMetaDataTables::GetNextUserString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ce6cfd6a331c9d9695f65eb3a670305de38d010
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191184"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="28d9d-102">IMetaDataTables::GetNextUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="28d9d-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="28d9d-103">Pobiera indeks wiersza, który zawiera następnego ciągu ustalonych w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="28d9d-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28d9d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28d9d-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28d9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28d9d-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="28d9d-106">[in] Wartość indeksu od bieżącej kolumny ciągów.</span><span class="sxs-lookup"><span data-stu-id="28d9d-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="28d9d-107">[out] Wskaźnik do indeks wiersza w ciągu następnej w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="28d9d-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28d9d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28d9d-108">Remarks</span></span>  
 <span data-ttu-id="28d9d-109">Firma Microsoft nie zaleca się użycie tej metody, ponieważ zwraca spójne wyniki.</span><span class="sxs-lookup"><span data-stu-id="28d9d-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="28d9d-110">Informacje o tabeli identyfikatora GUID, w dokumentacji Common Language Infrastructure (CLI), szczególnie "partycja II: Definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="28d9d-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="28d9d-111">Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="28d9d-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28d9d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28d9d-112">Requirements</span></span>  
 <span data-ttu-id="28d9d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28d9d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28d9d-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="28d9d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="28d9d-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28d9d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="28d9d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28d9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d9d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28d9d-117">See also</span></span>

- [<span data-ttu-id="28d9d-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="28d9d-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="28d9d-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="28d9d-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
