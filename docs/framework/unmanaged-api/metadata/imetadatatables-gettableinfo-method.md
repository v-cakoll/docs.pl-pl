---
title: IMetaDataTables::GetTableInfo — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 876f74d7fe7555f71db0bd77e68f657dfc80b179
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478963"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="7c2f3-102">IMetaDataTables::GetTableInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c2f3-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="7c2f3-103">Pobiera nazwę, rozmiar wiersza, liczba wierszy, liczba kolumn, a kolumny klucza indeksu w określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7c2f3-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c2f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c2f3-104">Syntax</span></span>  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c2f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c2f3-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="7c2f3-106">[in] Identyfikator tabeli, którego właściwości do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="7c2f3-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="7c2f3-107">[out] Wskaźnik do rozmiaru, w bajtach wiersza tabeli.</span><span class="sxs-lookup"><span data-stu-id="7c2f3-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="7c2f3-108">[out] Wskaźnik do liczby wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="7c2f3-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="7c2f3-109">[out] Wskaźnik do liczby kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="7c2f3-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="7c2f3-110">[out] Wskaźnik do indeksu kolumny klucza lub wartość -1, jeśli tabela nie ma kolumny klucza.</span><span class="sxs-lookup"><span data-stu-id="7c2f3-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="7c2f3-111">[out] Wskaźnik do wskaźnika do nazwy tabeli.</span><span class="sxs-lookup"><span data-stu-id="7c2f3-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c2f3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c2f3-112">Requirements</span></span>  
 <span data-ttu-id="7c2f3-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c2f3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c2f3-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7c2f3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c2f3-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c2f3-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c2f3-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c2f3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2f3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c2f3-117">See also</span></span>
- [<span data-ttu-id="7c2f3-118">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c2f3-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="7c2f3-119">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c2f3-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
