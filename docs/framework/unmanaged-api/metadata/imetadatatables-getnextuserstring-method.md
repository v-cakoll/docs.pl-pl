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
ms.openlocfilehash: 6522dbc8e49d612fc4c0d9597a9b5f12edb2cfe1
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937786"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="ac1a9-102">IMetaDataTables::GetNextUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac1a9-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="ac1a9-103">Pobiera indeks wiersza, który zawiera następny zakodowany ciąg w bieżącej kolumnie tabeli.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac1a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac1a9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac1a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac1a9-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="ac1a9-106">podczas Wartość indeksu z bieżącej kolumny ciągu.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="ac1a9-107">określoną Wskaźnik do indeksu wierszy następnego ciągu w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac1a9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac1a9-108">Remarks</span></span>  
 <span data-ttu-id="ac1a9-109">Nie zalecamy użycia tej metody, ponieważ nie zwracają one spójnych wyników.</span><span class="sxs-lookup"><span data-stu-id="ac1a9-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="ac1a9-110">Aby uzyskać informacje na temat tabeli GUID, zobacz dokumentację Common Language Infrastructure (CLI), szczególnie "partycja II: definicja metadanych i semantyka".</span><span class="sxs-lookup"><span data-stu-id="ac1a9-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="ac1a9-111">Dokumentacja jest dostępna w trybie online; zobacz Standard ECMA [ C# i Common Language Infrastructure](../../../standard/components.md#applicable-standards) i [standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="ac1a9-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac1a9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac1a9-112">Requirements</span></span>  
 <span data-ttu-id="ac1a9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac1a9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac1a9-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ac1a9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac1a9-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ac1a9-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac1a9-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac1a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1a9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac1a9-117">See also</span></span>

- [<span data-ttu-id="ac1a9-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac1a9-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ac1a9-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac1a9-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
