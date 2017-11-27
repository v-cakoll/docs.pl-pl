---
title: "IMetaDataTables::GetTableInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetTableInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f4ccd9bbd1c7caa9bbeb548176d834dc8844213
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="ce2d4-102">IMetaDataTables::GetTableInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce2d4-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="ce2d4-103">Pobiera nazwę, rozmiar wiersza, liczbę wierszy, liczby kolumn oraz kolumny klucza indeksu określonej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ce2d4-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce2d4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ce2d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce2d4-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="ce2d4-106">[in] Identyfikator tabeli, którego właściwości do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="ce2d4-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="ce2d4-107">[out] Wskaźnik do, w bajtach rozmiar wiersza tabeli.</span><span class="sxs-lookup"><span data-stu-id="ce2d4-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="ce2d4-108">[out] Wskaźnik do liczby wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ce2d4-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="ce2d4-109">[out] Wskaźnik do liczby kolumn w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ce2d4-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="ce2d4-110">[out] Wskaźnik do indeks kolumny klucza, lub wartość -1, jeśli tabela nie ma kolumny klucza.</span><span class="sxs-lookup"><span data-stu-id="ce2d4-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="ce2d4-111">[out] Wskaźnik na wskaźnik do nazwy tabeli.</span><span class="sxs-lookup"><span data-stu-id="ce2d4-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce2d4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce2d4-112">Requirements</span></span>  
 <span data-ttu-id="ce2d4-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce2d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce2d4-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ce2d4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce2d4-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce2d4-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce2d4-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce2d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2d4-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce2d4-117">See Also</span></span>  
 [<span data-ttu-id="ce2d4-118">IMetaDataTables — interfejs</span><span class="sxs-lookup"><span data-stu-id="ce2d4-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="ce2d4-119">IMetaDataTables2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="ce2d4-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
