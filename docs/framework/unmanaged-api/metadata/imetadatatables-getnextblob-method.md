---
title: IMetaDataTables::GetNextBlob — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1e7181f50d94fa417bf9d00c3531747cefca82c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781473"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="afb44-102">IMetaDataTables::GetNextBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="afb44-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="afb44-103">Pobiera indeks następnego duży obiekt binarny (BLOB) w tabeli.</span><span class="sxs-lookup"><span data-stu-id="afb44-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afb44-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afb44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afb44-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="afb44-106">[in] Indeks, zwrócone z kolumny obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="afb44-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="afb44-107">[out] Wskaźnik do indeksu następnego obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="afb44-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb44-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afb44-108">Requirements</span></span>  
 <span data-ttu-id="afb44-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb44-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb44-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="afb44-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afb44-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afb44-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="afb44-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb44-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb44-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afb44-113">See also</span></span>

- [<span data-ttu-id="afb44-114">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="afb44-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="afb44-115">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="afb44-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
