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
ms.openlocfilehash: 9b8a91a2c1ef9b68dcfc293a870ce3e9b9499a8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204604"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="56e42-102">IMetaDataTables::GetNextBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="56e42-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="56e42-103">Pobiera indeks następnego duży obiekt binarny (BLOB) w tabeli.</span><span class="sxs-lookup"><span data-stu-id="56e42-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56e42-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56e42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56e42-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="56e42-106">[in] Indeks, zwrócone z kolumny obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="56e42-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="56e42-107">[out] Wskaźnik do indeksu następnego obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="56e42-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56e42-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56e42-108">Requirements</span></span>  
 <span data-ttu-id="56e42-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56e42-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56e42-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="56e42-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56e42-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56e42-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="56e42-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="56e42-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56e42-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56e42-113">See also</span></span>

- [<span data-ttu-id="56e42-114">IMetaDataTables — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56e42-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="56e42-115">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56e42-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
