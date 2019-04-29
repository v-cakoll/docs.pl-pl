---
title: IMetaDataTables2::GetMetaDataStorage — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f12243571262ad7511795c48721617932fc6b30b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645116"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="91472-102">IMetaDataTables2::GetMetaDataStorage — Metoda</span><span class="sxs-lookup"><span data-stu-id="91472-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="91472-103">Pobiera rozmiar i zawartość z określonej sekcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="91472-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91472-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91472-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91472-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91472-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="91472-106">[out w] Wskaźnik do sekcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="91472-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="91472-107">[out] Rozmiar strumienia metadanych.</span><span class="sxs-lookup"><span data-stu-id="91472-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91472-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91472-108">Requirements</span></span>  
 <span data-ttu-id="91472-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91472-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91472-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="91472-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91472-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91472-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91472-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91472-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91472-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91472-113">See also</span></span>

- [<span data-ttu-id="91472-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="91472-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="91472-115">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="91472-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
