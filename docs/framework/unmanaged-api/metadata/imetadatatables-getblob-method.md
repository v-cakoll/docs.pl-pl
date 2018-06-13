---
title: IMetaDataTables::GetBlob — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 743fb1c77e2dd74487a7498be25ea23b4919032a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447302"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="26bef-102">IMetaDataTables::GetBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="26bef-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="26bef-103">Pobiera wskaźnik do dużego obiektu binarnego (BLOB) pod indeksem określonej kolumny.</span><span class="sxs-lookup"><span data-stu-id="26bef-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26bef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26bef-104">Syntax</span></span>  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26bef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26bef-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="26bef-106">[in] Adres pamięci, z którego można pobrać `ppData`.</span><span class="sxs-lookup"><span data-stu-id="26bef-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="26bef-107">[out] Wskaźnik do rozmiar w bajtach z `ppData`.</span><span class="sxs-lookup"><span data-stu-id="26bef-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="26bef-108">[out] Pobrać wskaźnik na wskaźnik do danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="26bef-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26bef-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26bef-109">Requirements</span></span>  
 <span data-ttu-id="26bef-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26bef-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26bef-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="26bef-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26bef-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26bef-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26bef-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26bef-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bef-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26bef-114">See Also</span></span>  
 [<span data-ttu-id="26bef-115">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="26bef-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="26bef-116">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="26bef-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
